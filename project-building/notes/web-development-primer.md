# Primer

Essentials

## Folder Structure

The first thing to have out of the way is the way your web app will be structured; at its most elementary, a website should have the following: an index.html page, an images folder, a styles folder (for CSS files), and a scripts folder (for JavaScript files). 

## HTML

HyperText Markup Languages is the base for all web pages on the internet.

## CSS

When you create a CSS file that you want to use with particular HTML file, you need to make sure to link to it in the head part of the HTML file; e.g. 

```HTML
<link href="styles/style.css" rel="stylesheet" type="text/css">
```

CSS primarily relies on selectors in order to identify the elements for which to style. The selector is the piece of code in the CSS right before the curly braces; you can have multiple selectors by comma separating them. Additionally, the selectors can be specified not just merely by the name of the element, but also by an ID selector (id="my-id" | #my-id) which will specifically only select one HTMl element; classes (class="my-class" | .my-class) which selects for multiple elements that fall under the same class; as well as attribute selectors (img[src] | src="blah") which will specifically only select for elements which have a particular attribute; and finally pseudo-class specifiers, which can select for elements in a particular state (a:hover | when the element is in the state of being hovered over).

We can also import fonts which we can use in our website by importing from Google Fonts; we need to make sure to include this in the header of the HTML file, and then we can use it in the CSS file that is imported into the header.

If you want to make comments in CSS, use /* and */. Any text in between them will be a comment.
