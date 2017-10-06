# HTML

## Semantics

It's not just about what you visually get as a result of the HTML, often the elements you use convey more about the semantics of the content in your web page. For example, you can use ```<strong></strong>``` to convey strong importance, but HTML will also bold that text by default. However, this bolding can also be achieved by using ```<b></b>``` or even using CSS, but the goal is actually not the bolding, but the semantic idea that whatever content is inside of those tags is meant to be of strong importance. Another example are ```<em></em>``` tags and ```<i></i>``` tags.

The reason this distinction is important is because semantics is very important to SEO (search engine optimization) as well as for accessibility, both important factors in any web projects you want to undertake. Like I mentioned above, there are also tags that achieve the same styling, but do not convey the same semantics, e.g. using the ```<b></b>``` tags for bolding. These used to be considered presentational components, and would almost never be used (just because CSS is much better supported now, and that's where the majority of the styling should be). However, in HTML5, these b, i, and u tags were redefined to have semantic meaning, for what italics, bold, and underlines traditionally mean. However, it is important to distinguish this from em and strong, and you might want to refresh yourself on their exact purpose. Additionally, you almost never want to use the ```<u></u>``` tag to underline, because underlines are very strongly associated with hyperlinks on the internet.

