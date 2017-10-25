# System Design

scalability for dummies: clones (p1)

load balancer: evenly distributes the load from user requests on a group of application servers, meaning that a user might interact many times with the service, and even though they might hit different servers on their requests, they should always get the same results back

1st golden rule of scalability: every server contains the exact same codebase and does not store any user related data, like sessions or profile pictures, on local disc or memory; rather, this information is stored on an external centralized data store which is accessible to all application servers; this data store can just be an external database, but if you are maximizing for performance, you might want to use an external persistent cache (like Redis); might want to read up a bit more on the data structure that an external persistent cache is, and the tradeoffs (sort of like RAM vs. Disk?)

there is an issue when you deploy your code: how do you get the code change to all of your servers, and keeping them all up to date (no server left behind on old code?); this is solved by a tool called Capistrano, should read more into it maybe?

you want to keep track of an image file after you’ve deployed the same codebase to all servers (AWS calls this an AMI, Amazon Machine Image); this image file will be the super clone that all new instances (clones) will be based on

scalability for dummies: database (p2)

if your application is getting slower and slower and is running a relational database (such as MySQL), there are two paths by which you can resolve this problem:

(1) keep sticking with the relational database management system but start doing a master-slave replication (write to master, read from slaves) and keep upgrading the master server by adding RAM, RAM, and more RAM. unfortunately as the database keeps growing, it gets more expensive to keep the database running, since you might try to do things like sharding, demoralization, and SQL tuning?

sql vs. nosql (pick one like mongodb and just know it very well and why you like it, but also the tradeoffs and maybe like postgresql and why that might be better idk)
asset guarantees

(2) instead you can denormalize your data right away and have no more joins; you can stick with MySQL and just use it like a NoSQL database, but it would be better and easier to scale a NoSQL database like MongoDB. Your joins now have to be written in the application code; however even if you do this, your database requests will still become slower and slower- you will eventually need to introduce a cache

scalability for dummies: cache (p3)

scalability harvard lecture:

vertical scaling: throwing money and resources at the problem, increasing disk space, more CPUs with multiple cores, RAM, etc. but there is a ceiling to this, because there are some real world constraints of how good a machine you can buy, and as such this isn’t a full solution

horizontal scaling: 

load balancers have a public IP address which they can be contacted by the client, and then they can determine which server to send the client’s request to, which can be contacted through private IP addresses, meaning that the servers that hold the application data won’t be as subject to attacks by adversaries and also the load will be distributed across all the servers; the load balancer will have to figure out which servers are able to handle the load to send the request to

one way to use a load balancer is round robin: this is just sending the request to one of the servers randomly

it actually benefits us to have multiple masters, so that even if one master goes down, then the process of converting a slave to a master would not prevent writes from happening because the master that is still up could be written to

single points of failure: where we don’t have a replicated backup server in case the server in question fails (for example, if there is only one load balancer, or if there is only one master server)

tiered system: we have a load balancer that distributes the application request to multiple web servers, which take read queries and feed them into a load balancer (which then sends the read query to many slaves), and write queries directly to a master, which then replicates the write to the slaves

a load balancer can also be implemented into a normal web server, a load balancer doesn’t necessarily have to be on its own, it can run a web server on itself

load balancers often come in pairs, active-active, with two active load balancers, which will send heartbeats to each other and if the heartbeat stops, then the other load balancer knows to take all the load and requests (active-passive also works this way, where the passive load balancer can detect when the active one has died, and turn into active mode)

partitioning the database is a common paradigm, for example putting users a-g in a database, and users h-z in another database, but this could be problematic if we have users in the first database interacting with users in the second database

if we want to implement sticky sessions, we’ll need to have a way to either share state or we can have the load balancer listen at the http level and has a cookie in itself that keeps track of which server to send a user to

redundancy seems to be a common thing, we never want a single source of truth