# Python

## Explanation

Similar to Ruby, Python is a high-level, interpreted programming language (written in C) that uses whitespace for code blocks. This illustrates the main design philosophy of Python–to be very clear and concise to read. Python, like Ruby, features dynamic typing (one does not need to explicitly declare the type of data a variable will hold) and has automatic memory management (some languages, like C, require you to explicitly ask for memory, and then explicitly require you to free the memory after usage).

## Purpose

Python is widely used in academia today, and has many applications in academia. In particular, Python has seen a rise in use in the realm of machine learning.

## Pros & Cons

## Syntax

## Built-in Data Structures

## Commonly Used Functions

* `+, -, *, **, and %` all work like you would expect them to; you can also utilize the `+` and `*` with strings just like in Ruby (for example, `'hey' * 3 => 'heyheyhey'`); another interesting thing is that if the first operand is not included, Python will implicitly put 0 as the first operand

* you can take the modulo of something even with floats

* `/` will return a float rather than an integer, even if the dividend is cleanly divided; if division which returns an integer is preferred, then use `//` instead (which essentially performs to functions, dividing and flooring)

* there are a few bit operations we can do with Python

## Differences from Ruby

## Rough Notes

python

instead of interpolation, you use .format(var1, var2, etc.) and the place where you want to put the variable in the string, just write {} corresponding to each variable; alternatively, you can write the name of the variable into the {} if you want to specify; additionally, you can do additional stuff by writing 0: inside of the curly braces; for example, 0:.3f will return 0.333 if the variable is 1.0/3

print always has a newline, and there is no puts method; thus, if you don’t want a newline, you specify it with giving print a second argument, end=‘“ (or whatever you might want to end with)

be familiar with the escape sequence and how it’s used in strings; you might see a string arbitrarily partitioned onto two lines with the \, which is equivalent to the words together on the same line

if you want a purely raw string (especially for regex purposes) type r in front of the string, e.g. r”hello \ there \\” which won’t interpret any special processes

the escape sequence character \ is not just used for strings, but for everything in python; so like ; denotes the end of a logical line, / extends the logical line past the physical line onto a second physical line, e.g. i = \ 5 (on two lines) is the same as i = 5

make sure your indentation is always uniform (4 spaces) because that’s how python interprets blocks (same indentation = same block)

/ always returns a float; if you want the same / as ruby, which is dividing and flooring, use //

<< and >> are not shoveling, they are for shifting bits and will shift the binary representation, then return the decimal value

&, |, and ^ (~ if you want to invert- kinda weird cause it returns negative?) are bitwise operations of the binary reps of the numbers, to their decimal

have to write not instead of !, and instead of &&, or instead of ||

there is the syntactic sugar from Ruby of +=, -=,  *=, etc.

there is an order of evaluation for operators in python (including booleans, if else, lambdas) but you should use parentheses to be explicit and clear

we can use the print statement with two arguments, but instead of doing the end=, the second argument is also something that can be printed (a string, int, etc.) and it will print both with them separated by a space

with control flow statements (if, for, while) we write the condition and then write a : at the end of it, to denote the end of the condition; instead of elsif, there is elif; don’t need to close with end

we can simply call input(), which will prompt the user for an input; we can put a string argument inside the input function which will prompt the user for input after a displayed message

int() is a function that will take the argument and convert it to an integer

elif and else are optional to an if conditional

interesting, a while loop can have an else clause that is run when the while loop isn’t true, and runs once; the else is not executed if you break out of the while loop with a break statement

True and False are booleans and can also be represented by 1 and 0 (exactly the same, or truthiness is the same?): interesting, True and 1 are equivalent (==) as are False and 0, they return True when tested for equivalency; also note that unlike ruby, the booleans must be capitalized, otherwise it's just a variable called true or false

the catch all term for ordered collection of items in python is sequence: this could be ranges or lists (I think)

the for loop we will use to iterate through sequences is: `for var in range(1, 5):` with an optional else; the var represents each element in the sequence, and the range could be replaced with a list or other type of sequence

note that range returns the sequence including the first number, up until but not including (like the … in ruby) the second argument; range can also take an optional third argument if you want a different jump (e.g. instead of default increasing by 1, increasing by 2 by range(1, 5, 2))

break works exactly like ruby; it will exit the looping structure, and if there is an optional else conditional, then that will not be run

instead of next, python has continue; this will skip the rest of the code in the loop and proceed to the next iteration of the loop (even a while loop, which I think next doesn’t work for in Ruby)

to define a function, python is almost exactly the same as ruby; def funcNameHere(args): no closing end needed

variables are local to a function (function scoped, and also through classes and modules!)

if you want to change the scope of a variable to be globally scoped (meaning changing it inside a function will result in it changing) you can specify with global x; this doesn’t have to be when the variable is first initialized, either, it can be later (even inside a function)

we can also supply optional arguments that take default values just like in ruby, by using the = in the parameter; they should be equal to a constant (I guess to make sure the function is deterministic?); however NOTE that default values must be given after all the parameters without default values, e.g. def func(a, b=5) is valid but def func(a=5, b) is not!

when we invoke a function, we might not want to supply arguments to all the parameters (if there are some default ones); rather than have to be meticulous about the order and plug in default values for arguments, we can specify the variable when we invoke, e.g. func(c=5, a=100) even if the function is func(a,c) and it will correspond to the relevant parameter (these are known as keyword arguments)

if you want an optional number of arguments, we can use * and ** (similar to ruby); *param will collect all arguments that are comma separated into a tuple, while **param will collect all keyword arguments (see above) into a dictionary; note that the ordering of the dictionary seems a bit strange, I’m not exactly sure how (perhaps in reverse order that it’s inputted, like a stack?)

return can be used to return early from a function; however, unlike ruby, the last line of code run will implicitly return None, which is essentially equivalent to nil from Ruby; thus, you should almost always use a return unless for some reason you want to return None

ERROR: make sure when you’re defining a function, if it doesn’t take arguments, you still need to include the parentheses i.e. def hello(): not def hello:

interesting, in interactive python, there is no difference between what is printed to the console and what is returned

if you want to have a placeholder for the content of a function, use the pass statement; otherwise, python will throw an error (this is mostly useful when creating a class and you have methods you don’t want to implement yet)

you can (and should) add things called DocStrings in the function def (right after def func():) which sort of gives some explanation as to what the function does; to denote a doc string, use the triple single quote to start and end; you can access a docstring of a function by typing `function_name.__doc__`; writing help(func) actually just fetches the __doc__ attribute and displays it

ERROR: make sure to run files with the command python3, or else weird things happen?

modules

we can reuse functions inside the same file, but what if we wanted to reuse those functions in a different python file? we can do this by importing modules, where a module is just a regular python file! (alternatively you can also write modules in C to be imported…crazy)

to use a module in another file, just write `import module_name` at the top of a file; this will import all the functions (and classes?) of the file into the new file, and can be accessed through the module_name (e.g. if there was a list of arguments from the sys module, we access it by sys.argv)

the module is either built into python (like sys) or it can be in one of the system paths (which you can see through the module sys, sys.path); in most cases just have the module files in the same directory and it will import just fine

remember, we access variables and functions from the module with the dot notation, e.g. math.sqrt(); however, we can directly import the function or variable by writing from sys import argv, path for example but this is often bad practice because you want to avoid name clashes and have readable code

if you want to import a module but give it an alias to call it by, e.g. `import ridiculously_long_module_name as short_name`

when a module is first imported, a .pyc file is created for it; this is the bytecode that can be run directly on the python converter, and reduces the load next time someone runs the import because it won’t have to convert the other file to a .pyc (bytecode) file

when a module is imported, it is executed, and the context of its execution matters; if it is being executed as its own file, then its __name__ property will be set to __main__; if it is being executed as part of an import,, then its __name__ property will be something different (we can use this to configure a module to know when its being imported)

aside: every Python module has a __name__ defined for it, __main__ just means the module is being run standalone by the user

every python (.py) file is a module; the functions and variables you write into the code can be imported and used in other python programs; make sure to include the file in either the same repository or a repository in sys.path in order to import it!

if you want to import all the functions and variables from a module but don’t want to use the dot access method to get at them, you can use `from module import *` which means you will import all of the functions and variables; however, it does not import anything that begins with double underscores (__) this is presumably to avoid conflicts with what you are importing into; in general, you don’t want to use from module import * though

there is a nice function called dir(), which will return a list of names defined by an object (including functions, classes, and variables); e.g. dir(sys) will return a list of ‘__displayhook__’, ‘__doc__’, ‘argv’, etc. but you need to make sure to have imported the module first; if you just run dir() in the file itself, this will return the list of names defined for that particular module; it should be noted that dir works on any object! so you can run dir(str) or dir(list) or dir(dict) to see what methods and variables are defined for those objects, although sometimes using help(list) for example will provide more clarity as to the important methods and attributes and what they do

there is a function called del() which can take a variable/name and remove access to that particular variable, as if it never existed

modules (remember, just python .py files!) are often organized in repositories so that many modules can be organized and found under one folder; this is known as a package, and we can import from packages by writing `from package_name import specific_submodule` (if the module lives in a subfolder, then you would write package_name.folder_name rather than just package_name; each folder should contain a __init__.py file, which tells python that it is a package repository

tl;dr: just like how functions are reusable parts of a program, modules are reusable complete programs, and packages are a way to organize modules

data structures

data structures are literally just structures that hold data together, i.e., used to store a collection of related data

there are four built-in data structures in Python: list, tuple, dictionary. and set; however, there are more that can be made yourself or found in the collections module (for example, from collections import deque will give you access to the queue data structure with fast fifo properties)

a list is simply an ordered collection of items (i.e. a sequence of items), essentially similar to a shopping list; to specify the creation of a list, we write `list_name = [“hi”, “hello”, “hey”]` just as we do in Ruby; unlike strings, lists are a mutable data type; you can do all the things with a list that you can in Ruby

objects in Python are similar to Ruby; cursorily, objects are instantiations of a class and have methods that are just functions specifically for use with that class only, e.g. the list class has an append method that can only be used with it; methods are accessed through dot notation (just like modules); in addition to methods, classes can also have fields which are variables defined for a particular class only, and are also accessed with the dot notation e.g. mylist.field

strange: some methods in Python are used with dot notation, but other functions, like len, are using with parentheses; I guess the ones with parentheses are considered functions but the dot notation are all methods? it might make sense because len for example can be used with lists and strings (e.g. len(“hello”) and len([“hi”, “ho”])); it seems that those functions will actually call a method that is defined for that particular object

strange: one interesting thing about Ruby vs. Python that I’ve yet to understand completely are the return values from each line; in Ruby, each line would have a return value defined for it, but it seems like Python there doesn’t necessarily have to be a return value

reminder, you can run help(class_name) to return a list of methods and fields that have been defined for that particular class

don’t forget, you need to make sure to invoke methods you call, and unlike Ruby, python does not implicitly realize you want to invoke a method when you don’t include parentheses; if a method does not take any arguments, you still need to invoke with empty parentheses (like javascript) e.g. arr.sort();

a list has defined for it several methods; to add something to a list, you use .append(); to delete something from a list, you use the del method for variables e.g. del shoplist[0] will delete the first item in the shoplist; also, if you want to just specify the value, shoplist.remove(“apple”) will delete the first object that has the value “apple” (starting from the beginning of the list); if you want to insert something into the list that's not just at the end, you can use .insert(index, value) where you insert the value right before whatever is at the index specified; we can sort the list in ascending order (which will mutate it) by doing list.sort(); we can reverse a list by doing list.reverse(); and also if we want to just remove the last item from a list, we can use the .pop() method which also returns the last item from the list

in general, lists store homogeneous data (e.g. a list of people’s names), while tuples (as we will soon see) are used primarily to group different types of objects; also, that’s not the only reason we use tuples or lists (tuples are immutable while lists are not!) but we will get into that later

tuples are used to hold together multiple objects, and are similar to lists (they are both sequences that can be iterated through!) except they don’t have as much functionality as lists have; the biggest difference is that tuples are immutable

to define a tuple, just specify with a comma separated line of objects, which can optionally take parentheses (which you should include, to be explicit; remember, explicit is always better in python!); e.g. tup = (“hi”, “hey”, “ho”); if you want to define an empty tuple, you would do tup = (); if you want to specify a tuple with 1 item, you have to do tup = (“item_1", ) to differentiate it from an expression!

strange: even though tuples are immutable, they can hold objects that are mutable (e.g. a list); there are no methods you can use to mutate a tuple once it has been created, but it will not know if the objects it references have changed or not! interestingly, the tuple has not really changed (it still holds references to the same locations in memory), and it cannot change (immutability is not magic, it is merely the absence of mutating methods); however if a tuple contains a list, then it is not a hashable key (hashable keys must be immutable and not contain any references to mutable objects)

you can contain tuples within tuples (or lists within tuples), which you can access by doing a double access with the brackets (just like in Ruby, with multidimensional arrays)

dictionaries are an address-book like object (just another name for hashes) where you provide keys (name) to get the values (details); each key must be unique in order to uniquely identify the value, but values do not have to be unique

you can only use immutable objects as hashable keys; this makes sense, because otherwise the object at that reference could change, leading to issues about how the dictionary is made (either copies will have to be made at the time the key is hashed, or problems will occur); only use “simple objects” as keys

to create a dictionary, we use curly braces just like in Ruby, and can specify key value pairs with colons just like ruby; e.g. d = {key1 : value1, key2 : value2, etc.} (or we can have these each on their own line, comma separated)

to delete a key-value pair from the dictionary, just write `del dictio[key_name]` and it will go to that key and delete the key-value pair; if you want to add a key-value pair, just create one by doing `dictio[new_key_name] = val` and it will automatically create one; interestingly, we can also get the length of a dictionary by using the len(dictionary_name) method, just like with lists, strings, and tuples

we can actually iterate through a dictionary by accessing the items in a dict by using dict_name.items, and that will provide a sequence with two variable names instead of one, e.g. `for name, address in dict_name.items(): print(‘contact {} at {}’.format(name, address))`

we can also check if a key is in a dictionary, we can actually use the `in` method, e.g. if ‘zaina’ in dicto: which will return a boolean; if we want to check if a value is in a dictionary, we need to do if ‘1’ in dicto.values() which will also return a boolean

so three data types we’ve encountered: lists, tuples, and strings, are all under the umbrella of a sequence, which all share similar methods that can be done on them since they are ordered

it turns out you can use the in method for any sequence! (weirdly, it works with dicts above even though they aren’t sequences per se…); anyway, you can use in and not in to return a boolean to check if lists, tuples or strings contain a particular object

probably the biggest advantage is you can use index operations to fetch a particular item or subsets of items from the sequence directly; this is similar to Ruby, but rather than use .. ranges to split a sequence, we use :

to access one particular element from the sequence at an index, write e.g. `list[2]` to get the third element’; to get the last element, you can do `list[-1]` (and the second last, you can get by `list[-2]` and so on); this is known as a subscription operation

to slice a sequence, you need to understand the bracket notation; i.e. list[idx1:idx2:idx3] ; idx1 specifies where the first cut will be, including that particular index; idx2 specifies where the last cut will be, not including that index; idx3 specifies the step size for cuts, and defaults to 1; if you leave out idx1, then the assumption is the first element is where the first cut will be (so including the first element); if you leave out idx2, then the assumption is the last element is where the final cut will be (including the final element); we can also slice to negative indices, for example name[:-1] will get every element except the last, since it stops at the last index and is not inclusive of it

one incredibly important thing to note is that we can create a copy of a sequence by writing list[:]; this will come in handy if we ever want a duplicate copy to do some slicing while retaining the old sequence; recall, if you set a new variable equal to an old variable, they are both referencing the same data structure, you need to actually do the [:] if you want a copy that will not mutate the original

remember all of this can be done with any sequence: lists, tuples, strings, etc.

also realize that these don’t mutate the original sequence, they return copies of whatever it is that you wanted out of that sequence

another data structure are sets, which are unordered collections of simple objects (with only 1 object, you cannot have multiples of the same); think of a venn diagram, each circle sort of is a set; sets are used when the existence of an object is more important than the order or how many times it occurs

sets can be initialized by writing `set_name = set([“item1”, “item2”, etc.])`; note that you can only include immutable objects inside a set, just like hash keys

sets are convenient to check for membership, whether it is a subset of another set, or the intersection of two sets, etc. things that you could easily derive from a venn diagram; you can use the in and not in just like from sequences; .copy() if you want to make a copy (it looks like you can use this method on many data structures, including lists???) .add(object) to add an object to a set, name_of_superset.issuperset(name_of_subset) to check if a set is contained within another set, .remove(object) to get rid of a object from a set, and subset1 & subset2 to get the intersection of the same elements from a set 

just recall basic set theory from math, it’s why sets are useful

strange: .copy() vs. [:], which is preferred, and is the .copy() method available for all data structures?

recall, make sure you are thinking about whether you have different instantiations of an object in different variables, or the same reference to an object just in different variables; if you haven’t created a copy or grabbed a return value from something, it most likely is still the same object; we can use the [:] to get a new object returned if it is a sequence; another weird thing to remember is if you use the keyword arguments, that will point to the same array even if you use the method multiple times because the keyword argument is only evaluated the first time python defines the method (it’s a bit strange, but intuitively makes sense, just a gotcha)

recall that strings are also objects (although I guess not really a data structure? kinda weird distinguishing it, but maybe because it is not a collection of data, just it’s own immutable thing)

there are a couple methods to be aware of: .format(var1, var2, etc.) obviously, but also .startswith(str), which will check if the string starts with a particular string; char in or not in str, which works exactly like you would think; string.find(str) which will look and see if that string is inside of the other string, which will return the first index of the match where the string is found or -1 otherwise; and .join, which works similar to ruby, but takes the delimiter (the joiner) as the object it is called on and as an argument takes a list, e.g. delimiter.join(mylist) will join the list with whatever the delimiter string is

instead of ! (bang), we write not in Python

a lot of command line functionality can be accessed in python by importing the module os

to get the current time and other various related things, import time

there is a very convenient string method .replace(char_to_replace, char_to_replace_with) which makes it easy to replace something in a string

while we have used the os module to create archives (in particular os.system to run in the terminal) it is actually more apt to use the zipfile or tarfile modules (which are built into python) to do this

software development process: (1) What (Analysis) ; (2) How (Design) ; (3) Do It (Implementation) ; (4) Test (Testing and Debugging) ; (5) Use (Operation or Deployment) ; (6) Maintain (Refinement)

strange: clarity on self ???