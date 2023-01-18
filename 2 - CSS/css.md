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