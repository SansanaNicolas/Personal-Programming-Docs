# CSS: Cascading Style Sheets.

Cascading Style Sheets (CSS) is a stylesheet language used to desecribe the presentation of a document written in HTML or XML. CSS desecribes how elements should be rendered on screen, on paper, in speech or on other media.
CSS is among the core languages of the open web and is standardized across web browsers according to W3C specifications.


## Adding CSS to our document.

The first thing we need to do is to tell the HTML document that we have some CSS rules we want it to use. There are three different ways to apply CSS to an HTML document that you'll commonly come across, however, for now we will look at the most usual and useful way of doing so linking CSS from the head of your document. 
1) create a file in the same folder as your HTML document and save it as "style.css". The .css extension shows that this is a CSS file.
2) To link styles.css to index.html, add the following line somewhere inside the "head" of the HTML document:

```
<link rel="stylesheet" href="styles.css" />
```

The link element tells the browser that we have a stylesheet, using the rel attribute, and the colaction of that stylesheet as the value of the href attribute. You can test that the CSS works by adding a rule to style.css; Using your code editor, add the following to your CSS file:

```
h1 {
    color: red;
}
```

Save your HTML and CSS files and reload the page in a web browser. The level one heading at the top of the document should now be red.


## Styling HTML elements

By makingour heading red, we have already demostrated that we can target and style an HTML element. We do this by targeting an element selector (this is a selector that directly matches an HTML element name). To target all paragraphs in the document, you would use the selector p. To turn all paragraphs green, you would use:

```
p {
    color: green;
}
```

You can target multiple selectors at the same time by separating the selectors with a comma. If you want all paragraphs and all list items to be green, your rule would look like this:

```
p,
li {
    color: green;
}
```


## Changing the default behavior of elements

Browsers have internal stylesheets containing default styles, which they apply to all pages by default, without them all of the text would run together in a clump and we would have to style everything from scratch. All moderno browsers display HTML content by default in pretty much the same way. However, you will often want something other than the choice the browser has made. This can be done by choosing the HTML element that you want to change and using a CSS rule to change the way it looks. A good example is ul, an unordered list. It has list bullets. If you don't want those bullets, you can remove them like so:

```
li {
    list-style-type: none;
}
```

## Adding a class

We have styled elements based on their HTML element names. This works as long as you want all of the element of that type in your document to look the same. Most of the time that isn't the case and so you will need to find a way to select a subset of the elements without changing the others. The most common way to do this is to add a class to you HTML element and targe that class. In your HTML document, add a class attribute to the second list item. Your list will now look like this:

```
<ul>
   <li>Item one</li>
   <li class="special">Item two</li>
   <li>Item <em>three</em></li>
</ul>
```

In your css you can target the class of "special" by creating a selector that starts with a full stop character. Add the following to your CSS file:

```
 .special {
    color: orange;
    font-weight: bold;
 }
```
Save and refresh to see what the result is.

you can apply the class of the special to any element on your page that you want to have the same look as this list item. Sometimes you will see rules with a selector that lists the HTML element selector along with the class: 

```
li.special {
    color: orange;
    font-weight: bold;
}
```

This syntax means "target any li element that has a class of special". If you were to do this, then you would no longer be able to apply the class to a span or another element by adding the class to it; you would have to add that element to the list of selectors:

```
 li.special,
 span.special {
    color: orange;
    font-weight: bold;
 }
```

Some classes might be applied to many elements and you don't want to have to keep editing your CSS every time something new needs to take on that style. Therefore, it's sometimes best to bypass the element and refer to the class, unless you know that you want to create some special rules for one element alone, and perhaps want to make sure they are not applied to other things.