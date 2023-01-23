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

## Styling things based on their location in a document.

In our document, there are two em elements, one inside a paragraph and other inside a list item. To select only an em that is nested inside an li element, you can use a selector called the descendant combinator, which takes the form of a space between two others selectors.

```
li em {
    color: red;
}
```

The selector will select any em element that is inside (a descendant of) an li. 

Something else you might like to try is styling a paragraph when it comes directly after a heading at the same hierarchy level in the HTML. To do so, place a + (an adjacent sibling combinator) between the selectors.

```
h1 + p {
    font-size: 200%;
}
```


## Styling things based on state

The final type of styling we shall take a look is the ability to style things based on their state. A straightforward example of this is when styling links. When we style a link, we need to target the a (anchor) element. This has different states depending on whether it is unvisited, visited, being hovered over, focused via the keyboard or in the process of being clicked (activated). You can use CSS to target these different states, the CSS below styles unvisited links pink and visited links green.

```
 a:link {
    color: pink;
 }

  a:visited {
    color: green;
  }
```

You can change the way the link looks when the user hovers over it, for example by removing the underline, which is achieved by the next rule:

```
 a:hover {
    text-decoration: none;
 }
```

## Combining selectors and combinators

It's worth nothing that you can combine multiple selectors and combinators together, for example:

```
 /* selects any <span> that is inside a <p>, which is inside an <article> */
 article p span {

 }

 /* selects any <p> that comes directly after a <ul>, which comes directly after an <h1> */ 
 h1 + ul + p {

 }
```

You can combine multiple types together too. Try adding the following into your code:

```
 body h1 + p .special {
    color: yellow;
    background-color: black;
    padding: 5px;
 }

 /* this will style any element with a class of special, which is inside a <p>, which comes just after an <h1>, which is inside a <body> */

```


## Selectors

A selector targets HTML to apply styles to content. If CSS is not applying to content as expected, your selector may not match the way you think it should match.
Each CSS rule starts with a selector -or a list of selectors- in order to tell the browser which element or elements the rules should apply to. All the examples below are valid selectors or list of selects.

```
 h1
 a:link
 .manythings
 #onething
 *
 .box p
 .box p:first-child
 h1, h2, .intro
```


## Specificity

You may encounter scenarios where two selectors select the same HTML element. Consider the stylesheet below, with a p selector that sets paragraph text to blue. However, there is also a class that sets the text of selected elements to red.

```
.special {
    color: red;
}

p {
    color: blue;
}
```

Suppose that in our HTML document, we have a paragraph with a class of special. Both rules apply. Which selector prevails? The CSS language has rules to control which selector is stronger in the event of a conflict. These rules are called cascade and specificity. In the code block we define two rules for the p selector, but the paragraph text will be blue. This is because the declaration that sets the paragraph text to blue appears later in the stylesheet. Later styles replace conflicting styles that appear earlier in the stylesheet. This is the cascade rule. However, in the case of our earlier example with the conflict between the class selector and the element selector, the class prevails, rendering the paragraph text red. A class is rated as being more specific, as in having more specificity than the element selector, so it cancels the other conflicting style declaration.