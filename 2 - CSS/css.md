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

## Properties and values

At its most basic level, CSS consists of two components: 
- Properties: These are human-readable identifiers that indicate which stylist features you want to modify. For example: font-size, width, background- color.
- Values: Each property is assigned a value. This value indicates how to style the property.

The example below highlights a single property and value. The property name is "color" and the value is "blue".

```
 h1 {
    color: blue;
    background-color: yellow;
 }

 p {
    color: red;
 }
```

When a property is paired with a value, this pairing is called a CSS declaration. CSS declarations are found within CSS declaration Blocks.

Finally, CSS declaration blocks are paired with selectors to produce CSS rulesets (or CSS rules). The above example contains two rules: one for the h1 selector and one for the p selector.

Setting CSS properties to specific values is the primary way of defining layour and styling for a document. The CSS engine calculates which declarations apply to every single element of a page. 

CSS properties and values are case-insensitive. The property and value in a property-value pair are separated by a colon (:).

## Functions 

While most values are relatively simple keywords or numeric values, there are some values that take the form of a function.

The calc() function.
An example would be calc() function, which can do simple math within CSS:

```
 <div class="outer"><div class="box">The inner box is 90% - 30px.</div></div>
```
```
 .outer {
  border: 5px solid black;
}

.box {
  padding: 10px;
  width: calc(90% - 30px);
  background-color: rebeccapurple;
  color: white;
}
```

this renders as: 

![calc function](/images/calc().png)

A function consists of the function name, and parentheses to enclose the values for the function. In the case of the calc() example above, the values define the width of this box to be 90% of the containing block width, minus 30 pixels. The result of the calculation isn't something that can be computed in advance and entered as a static value.

### Transform functions.

Another example would be the various values for transform, such as rotate().

```
<div class="box"></div>
```

```
.box {
  margin: 30px;
  width: 100px;
  height: 100px;
  background-color: rebeccapurple;
  transform: rotate(0.8turn);
}
```

The output from the above code looks like this:

![rotate function](/images/rotate().png)


## @rules

CSS @rules (pronounced "at-rules") provide instruction for what CSS should perform or how it should behave. Some @rules are simple with just a keyword and a value. For example, @import imports a stylesheet into another CSS stylesheets.

```
 @import "style2.css";
```

One common @rule that you are likely to encounter is @media, which is used to create media queries. Media queries use conditional logic for applying CSS styling.

In the example below, the stylesheet, defines a default pink background for the body element. However, a media query follows that defines a blue background if the browser viewport is wider than 30em.

```
 body {
    background-color: pink;
 }

 @media (min-width: 30em) {
    body {
        background-color: blue;
    }
 }
```

You will encounter other @rules throughout these tutorials.


## Shorthands.

Some properties like ***font, background, padding, border and margin*** are called ***shorthand properties***, this is because shorthand properties set several values in a single line.
For example: this one line of code:

```
 /* In 4-value shorthands like padding and margin, the values are applied in the order: top, right, bottom, left (clockwise from the top). There are also other shorthand types, for example 2-value shorthands, which set padding/margin for top/bottom, then left/ right */
  padding: 10px 15px 15px 5px;
```

Is equivalent to these four lines of code: 

 ```
  padding-top: 10px;
  padding-right: 15px;
  padding-bottom: 15px;
  padding-left: 5px;
 ```

 This one line:

 ```
  background: red url(bg-graphic.png) 10px 10px repeat-x fixed;
 ```

 Is equivalent to these five lines:

 ```
 background-color: red;
 background-image: url(bg-graphic.png);
 background-position: 10px 10px;
 background-repeat: repeat-x;
 background-attachment: fixed;
 ```

## Comments

As with any coding work, it is best practive to write comments along with CSS. This helps you to remember how the code works as you come back later for fixes or enhancement. It also helps others understand the code. CSS comennts begin with /* and end with */.

"Commenting out" code is also useful for temporarily disabling sections of code for testing. In the example below, the rules for .special are disabled by "commenting out" the code.

```
 /*.special {
    color: red;
 }*/

 p {
    color: blue;
 }
```

## White spaces

White space means actual spaces, tabs and new lines. Just as browsers ignore white space in HTML, browsers ignore white space inside CSS. The value of white space is how it can improve readability.


# How does CSS actually work?

When a browser displays a document, it must combine the document's content with its style information. It processes the document in a number of stages, which we've listed below. Bear in mind that this is a very simplified version of what happens when a browser loads a webpage, and that different browsers will handle the process in different ways. But this is roughly what happens.

1. The browser loads the HTML (e.g. receives it from the network).
2. It converts the HTML into a DOM (Document Object Model). The DOM represents the document in the computer's memory. The DOM is explained in a bit more detail in a few moments.
3. The browser then fetches most of the resources that are linked to by the HTML document, such as embedded images, videos, and even linked CSS! JavaScript is handled a bit later on in the process, and we won't talk about it here to keep things simpler.

4. The browser parses the fetched CSS, and sorts the different rules by their selector types into different "buckets", e.g. element, class, ID, and so on. Based on the selectors it finds, it works out which rules should be applied to which nodes in the DOM, and attaches style to them as required (this intermediate step is called a render tree)
.
5. The render tree is laid out in the structure it should appear in after the rules have been applied to it.
6. The visual display of the page is shown on the screen (this stage is called painting.)

The following diagram also offers a simple view of the process.

![Css diagram](/images/css%20diagram.png)

## About the DOM

A DOM has a tree-like structure. Each element, attribute, and piece of text in the markup language becomes a DOM node in the tree structure. The nodes are defined by their relationship to other DOM nodes. Some elements are parents of child nides, and child nodes have siblings.

Understanding the DOM helps you design, debug and maintain you CSS because the DOM is where your CSS and the document's content meet up. When you start working with browser DevTools you will be navigating the DOM as you select items in order to see which rules apply.

## A real DOM representation

Let's look at an example to see how a real HTML snippet is converted into a DOM, take the following HTML code:

```
 <p>
  Let's use:
  <span>Cascading</span>
  <span>Style</span>
  <span>Sheets</span>
 </p>
```

In the DOM, the node corresponding to our p element is a parent. Its children are a text node and the three nodes corresponding to our span elements. The span nodes are also parentsm with text nodes as their childer:

```
 P
├─ "Let's use:"
├─ SPAN
|  └─ "Cascading"
├─ SPAN
|  └─ "Style"
└─ SPAN
    └─ "Sheets"
```

This is how a browser interprets the previous HTML snippet, it renders the above DOM tree and then outputs it in the browser like so:

```
 Let's use: Cascading Style Sheets
```

## Applying CSS to the DOM

Let's say we add some CSS to our document, to style it. Again, the HTML is as follows:

```
 <p>
  Let's use:
  <span>Cascading</span>
  <span>Style</span>
  <span>Sheets</span>
</p>
```

Let's suppose we apply the following CSS to it:

```
 span {
  border: 1px solid black;
  background-color: lime;
}
```

The browser parses the HTML and creates a DOM from it. Next, it parses the CSS. Since the only rule available in the CSS has a span selector, the browser sorts the CSS very quickly! It applies that rule to each one of the three spanS, then paints the final visual representation to the screen.

The updated output is as follows:

![CSS DOM](/images/CSSdom.png)


## Conflicting rules

CSS stands for Cascading Style Sheets, and that first word cascading is incredibly important to understand, the way that the cascade behaves is key to understanding CSS.
At some point, you will be working on a project and you will find that the CSS you thought should be applied to an element is not working, often, the problem is that you create two rules that apply different values of the same property to the same elect. Cascade and the closely-related concept of specificity are mechanisms that control which rule applies when there is such a conflict. The rule that's styling your element may not be the one you expect, so you need to understand how these mechanisms work. Also significant here is the concept of inheritance, which means that some CSS properties by default inherit values set on the current element's parent element and some don't. This can also cause some behavior that you might not expect. These can seem like a tricky set of concepts to understand. As you get more practice writing CSS, the way it works wil become more obvious to you.

## Cascade

Stylesheets cascade -at a very simple level, this means that the origin, the cascade layer, and the order of CSS rules matter. When two rules from the same cascade layer apply and both have equal specificity, the one that is defined last in the stylesheet is the one that will be used.

## Specificity

Specificity is the algorithm that the browser uses to decide which property value is applied to an element. If multiple style blocks have different selectors that configure the same property with different values and target the same element, specificity decides the property value that gets applied to the element. Specificity is basically a measure of how specific a selector's selection will be:
- An element selector is less specific; It will select all elements of that type that appear on a page, so it has less weight. Pseudo-element selectors have the same specificity as regular element selectors.
- A class selector is more specific; It will select only the elements on a page that have a specific class attribute value, so it has more weight. Attribute selectors and pseudo-classes have the same weight as a class.

## Inheritance

Inheritance also needs sto be understood in this content -Some CSS property values set on parent elements are inherited by their child elements, and some aren't.
For example, if you set a color and font-family on an element, every element inside it will also be styled with that color and font, unless you've applied different color and font values directly to them.
Some properties do not inherit -For example, if you set a width of 50% on an element, all of its descendants do not get a width of 50% of their parent's width. If this was the case, CSS would be very frustrating to use!

## Understanding how the concepts work together

These three concepts (cascade, specificity and inheritance) together control which CSS applies to what element. In the sections below, we'll see how they work together. It can sometimes seem a little bit complicated, but you will start to remember them as you get more experienced with CSS, and you can always look up the details if you forget! Even experienced developers don't remember all the details.

## Understanding inheritance

We'll start with inheritance. In the example below, we have a UL element with two levels of unordered lists nested inside it. We have given the outer UL a border, padding, and font color.
The color property is an inherited property. So, the color property value is applied to the direct children and also to the indirect childer -The inmediate child LIs and those inside the first nested list. We have then added the class special to the second nested list and applied a different color to it. This then inherits down through its children.

![inheritcss](/images/inheritcss.png)

``` 
HTML

<ul class="main">
    <li>Item One</li>
    <li>Item Two
        <ul>
            <li>2.1</li>
            <li>2.2</li>
        </ul>
    </li>
    <li>Item Three
        <ul class="special">
            <li>3.1
                <ul>
                    <li>3.1.1</li>
                    <li>3.1.2</li>
                </ul>
            </li>
            <li>3.2</li>
        </ul>
    </li>
</ul>

```

```
CSS

.main {
    color: rebeccapurple;
    border: 2px solid #ccc;
    padding: 1em;
}

.special {
    color: black;
    font-weight: bold;
}
```

Properties like width (as mentioned earlier), margin, padding, and border are not inherited properties. If a border were to be inherited by the children in this list example, every single list and list item would gain a border -Probably not an effect we would ever want!

Though every CSS property page lists whether or not the property is inherited, you can ofter guess the same intuitively if you know what aspect the property value will style.

## Controlling inheritance

CSS provides five special universal property values for controlling inherintace. Every CSS property accepts these values.

- inherit: Sets the property value applied to a select element to be the same as that of its parent element. Effectively, this "turns on inheritance".

- inital: Sets the property value applied to a selected element to the initial value of that property.

- revert: Resets the property value applied to a selected element to the browser's default styling rather than the defaults applied to that property. This value acts like unset in many cases.

- revert-layer: Resets the property value applied to a selected element to the value established in a previous cascade layer.

- unset: Resets the property to its natural value, which means that if the porperty is naturally inherited it acts like inherit, otherwise it acts like initial. 

## Understanding the cascade

We now understand that inheritance is why a paragraph nested deep in the structure of your HTML is the same color as the CSS applied to the body. Also we have an understading of how to change the CSS applied to something at any point in the document -Whether by assigning CSS to an element or by creating a class. We will now look at how cascade defines which CSS rules apply when more than one style block apply the same property, but with different values, to the same element.
There are three factors to consider, listed here in increasing order of importance. Later ones overrule earlier ones:
1. Source order
2. Specificity
3. Importance

We will look at these to see how browsers figure out exactly what CSS should be applied.


## Source order 

We have already seen how source order matters to the cascade. If you have more than one rule, all of which have exactly the same weight, then the one that comes last in the CSS will win. You can think of this as: the rule that is nearer the element itself overwrites the earlier ones until the last one wins and gets to style the element.
Source order only matters when the specificity weight or the rules is the same, so let's took at specificity:

## Specificity

You will often run into a situation where you know that a rule comes later in the stylesheet, but an earlier, conflicting rule is applied. This happens because the earlier rule has a ***higher specificity*** -it is more specific, and therefore, is being chosen by the browser as the one that should style the element. 
A Class selector has more weight than an element selector, so the properties defined in the class style block will override those defined in the element style block.
Something to note here is that although we are thinking about selectors and the rules that are applied to the text or component they select, it isn't the entire rule that is overwritten, only the properties that are declared in multiple places.
This behavior helps avoid repetition in your CSS. A common practice is to define generic styles for the basic elements, and then create classes for those that are different.

The amount of specificity a selector has is measured using three different values (or components), which can be thought of as ID, CLASS, and ELEMENT columns in the hundreds, tens, and ones place:

- Identifies: Score one in this column for each ID selector contained inside the overall selector.
- Classes: Score one in this column for each class selector, attribute selector, or pseudo-class contained inside the overall selector.
- Elements: Score one in this column for each element selector or pseudo-element contained inside the overall selector. 

THe following table shows a few isolated examples to get you in the mood. Try going through these, and make sure you understand why they have the specificity that we have given them.

![selectorvalue](/images/selectorsValue.png)


## Inline Styles

Inline styles, that is, the style declaration inside a style attribute, take precedence over all normal styles, no matter the specificity. Such declarations don't have selectors, but their specificity can be construed as 1-0-0-0; Always more than any other specificity weight no matter how many IDs are in the selectors.

## !important

There's a special piece of CSS that you can use to overrule all of the above calculations, even inline styles -the !important flag. However, you should be very careful while using it. This flag is used to make an individual property and value pair the most specific rule, thereby overriding the normal rules of the cascade, including normal inline styles.

One situation in which you may have to use the !important flag is when you are working on a CMS where you can't edit the core CSS modules, and you really want to override an inline style or an important declaration that can't be overridden in any other way. But really, don't use it if you can avoid it.

## The effect of CSS location

Finally, it's important to note that the precedence of a CSS declaration depends on what stylesheet and cascade layer it is specified in.

It's possible for users to set custom stylesheets to override the developer's styles. For example, a visually impaired user might want to set the font size on all web pages they visit to be double the normal size to allow for easier reading.

It's also possible to declare developer styles in cascade layers: you can make non-layered styles override styles declared in layers or you can make styles declared in later layers override styles from earlier declared layers. For example, as a developer you may not be able to edit a third-party stylesheet, but you can import the external stylesheet into a cascade layer so that all of your styles easily override the imported styles without worrying about third-party selector specificity.

## Order of overriding declarations

1. Declarations in user agent style sheets (e.g., the browser's default styles, used when no other styling is set).

2. Normal declarations in user style sheets (custom styles set by a user).

3. Normal declarations in author style sheets (these are the styles set by us, the web developers).

4. Important declarations in author style sheets.

5. Important declarations in user style sheets.

6. Important declarations in user agent style sheets.

## Order of cascade layers

Even though cascade layers is an advanced topic and you may not use this feature right away, it's important to understand how layers cascade.

When you declare CSS in cascade layers, the order of precedence is determined by the order in which the layers are declared. CSS styles declared outside of any layer are combined together, in the order in which those styles are declared, into an unnamed layer, as if it were the last declared layer. With competing normal (not important) styles, later layers take predecende over earlier defined layers. For styles flagged with !important, however, the order is reversed, with important styles in earlier layers taking precedence over important styles declared in subsequent layers or outside of any layer. Inline styles take precedence over all author styles, no matter the layer.

When you have multiple style blocks in differente layers providing competing values for a property on a single element, the layer in which the styles are declared on a single element, the layer in which the styles are declared deetermine the predecende. Specificity between layers doesn't matter, but specificty within a single layer still does.

## CSS SELECTORS

In CSS, selectors are used to target the HTML elements on our web pages that we want to style. There are a wide variety of CSS selectors available, allowing for fine-grained precision when selecting elements to style.

A CSS selector is the first part of a CSS rule. It's a pattern of elements and other terms that tell the browser which HTML elements should be selected to have the CSS property values inside the rule applied to them. The element or elements which are selected by the selector are referred to as the subject of the selector.

![CssSelectors](/images/cssSelectors.png)

In others articles you may have met some different selectors, and learned that there are selectors that target the document in different ways - for example by selecting an element such as h1, or a class such as .special.

In CSS, selectors are defined in the CSS selectors specification; like any other part of CSS they need to have support in browsers for them to work. The majority of selectors that you will come across are defined in the [level 3 selectors specification](https://www.w3.org/TR/selectors-3/) and [level 4 selector specification](https://www.w3.org/TR/selectors-4/) which are both mature specifications, therefore you will find excellent browser support for these selectors.

## Selector lists

If you have more than one thing which uses the same CSS then the individual selectors can be combined into a selector list so that the rule is applied to all of the individual selectors. For exmaple, if I have the same CSS for an h1 and also a class of .special, I could write this as two separate rules.

```
 h1 {
  color: blue;
}

.special {
  color: blue;
}
```

I could also combine these into a selector list, by adding a comma between them.

```
 h1, .special {
  color: blue;
}
```

White space is valid before or after the comma. You may also find the selectors more readable if each is on a new line.

```
 h1,
.special {
  color: blue;
}
```

## Types of selectors

There are a few different groupings of selectors, and knowing which type of selector you might need will help you to find the right tool for the job. In this documentation we will look at the different groups of selectors in more detail.

### Type, Class, and ID selectors

This group includes selectors that target an HTML element such as an h1.

```
h1 {

}
```

It also includes selectors which target a class:

```
 .box {

 }
```

or, an ID:

```
 #unique {

 }
```

## attribute selectors

This group of selectors gives you different ways to select elements based on the presence of a certain attribute on an element:

```
 a[title] {

 }
```

Or even make a selection based on the presence of an attribute with a particular value:

```
 a[href="https://example.com"] {

}
```

## Pseudo-classes and pseudo-elements

This group of selectors includes pseudo-classes, which style certain states of an element. The :hover pseudo-class for example selects an element only when it is being hovered over by the mouse pointer:

```
 a:hover {

 }
```

It also includes pseudo-elements, which select a certain part of an element rather than the element itself. For example, ::first-line always selects the first line of text inside an element (a p in the below case), acting as if a span was wrapped around the first formatted line and then selected.

```
 p::first-line {

 }
```

## Combinators

The final group of selectors combine other selectors in order to target elements within our documents. The following, for example, selects paragraphs that are direct children of article elements using the child combinator (>):

```
 article > p {
    
 }
```


## The Box model

Everything in CSS has a box around it, and understanding these boxes is key to being able to create more complex layouts with CSS, or to align items with other items.

### Block and inline boxes

In CSS we have several types of boxes that generally fit into the categories of block boxes and inline boxes. The type refers to how the box behaves in terms of page flow and in relation to other boxes on the page. Boxes have an innet display type and an outer display type. In general, you can set various values for the display type using the display property, which can have various values.

### Outer display type

If a box has an outer display type of ***block***, then:

- The box will break onto a new line.
- The width and height properties are respected.
- Padding, margin and border will cause other elements to be pushed away from the box.
- If width is not specified, the box will extend in the inline direction to fill the space available in its container. In most cases, the box will become as wide as its container, filling up 100% of the space available.

Some HTML elements, such as ***h1*** and ***p***, use ***block*** as their outer display type by default.

If a box has an outer display type of ***inline***, then:

- The box will not break onto a new line.
- The width and height properties will not apply.
- Vertical padding, margins, and borders will apply but will not cause other inline boxes to move away from the box.
- Horizontal padding, margins, and border will apply and will cause other inline boxes to move away from the box.

Some HTML elements, such as ***a***, ***span***, ***em*** and ***strong*** use ***inline*** as their outer display type by default.

## Inner display type

Boxes also have an inner display type, which dictates how elements inside that box are laid out.

Block and inline layout is the default way things behave on the web. By default and without any other instruction, the elements [inside a box](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Normal_Flow) are also laid out in normal flow and behave as block or inline boxes.

You can change the inner display type for example by setting ***display: flex;***. The element will still use the outer display type ***block*** but this changes the inner displat type to ***flex***. Any direct children of this box will become flex items and behave according to the [Flexbox](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Flexbox) specification.

When you move on to learn about CSS layout in more detail, you will encounter [flex](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Flexbox), and various other inner values that your boxes can have, for example [grid](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Grids).

## What is the CSS box model?

The CSS box model as a whole applies to block boces and defines how the different parts of a box -margin, border, padding and content- work together to create a box that you can see on a page. Inline boxes use just some of the behavior defined in the box model. To add complexity, there's a standard and an alternate box model. By default, browsers use the standard box model.

### Parts of a box

Making up a block box in CSS we have the:

- ***Content box***: The area where you content is displayed; size it using properties like ***inline-size*** and ***block-size*** or ***width*** and ***height***.
- ***Padding box***: The padding sits around the content as white space; size it using ***padding*** and related properties.
- ***Border box***: The border box wraps the content and any padding; size it using ***border*** and related properties.
- ***Margin box***: The margin is the outermost layer, wrapping the content, padding, and border as whitespace between this box and other elements; size it using ***margin*** and related properties. 

The below diagram shows these layers:

![boxmodel](/images/boxmodel.png)

## The standard CSS box model

In the standard box model, if you give a box an ***inline-size*** and ***block-size*** (or ***width*** and a ***height***) attributes, this defines the inline-size and block-size (width and height in horizontal languages) of the content box. Any padding and border is then added to those dimensions to get the total size taken up by the box (see image below).

If we assume that a box has the following CSS:

```
 .box {
    width: 350px;
    height: 150px;
    margin: 10px;
    padding: 25px;
    border: 5px solid black;
 }
```

The actual space taken up by the box will be 410px wide (350 + 25 + 25 + 5 + 5) and 210px high (150 + 25 + 25 + 5 + 5).

![boxmodelHeightAndWidth](/images/boxmodelHeightWidth.png)

## The alternative CSS box model

In the alternative box model, any width is the width of the visible box on the page. The content area width is that width minus the width for the padding and border (see image below). No need to add up the border and padding to get the real size of the box.

To turn on the alternative model for an element, set ***box-sizing: border-box*** on it: 

```
 .box{
    box-sizing: border-box;
 }
```

If we assume the box has the same CSS as above:

```
 .box {
    width: 350px;
    inline-size: 350px;
    height: 150px;
    block-size: 150px;
    margin: 10px;
    padding: 25px;
    border: 5px solid black;
 }
```

Now, the actual space taken up by the box will be 350px in the inline direction and 150px in the block direction.

![boxSizingBorderBox](/images/boxSizingBorderBox.png)

To use the alternative box model for all of your elements (which is a common choice among developers), set the ***box-sizing*** property on the ***html*** element and set all other elements to inherit that value:

```
 html {
    box-sizing: border-box;
 }
 *,
 *::before,
 *::after {
    box-sizing: inherit;
 }
```

To understand the underlying idea, you can read the [CSS tricks article on box-sizing](https://css-tricks.com/inheriting-box-sizing-probably-slightly-better-best-practice/).

## Use browser DevTools to view the box model

Your [browser developer tools](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Tools_and_setup/What_are_browser_developer_tools) can make understanding the box model far easier. If you inspect an element in Chrome's DevTools, you can see the size of the element plus its margin, padding, and border. Inspecting an element in this way is a great way to find out if your box is really the size you think it is.

![devTools](/images/devTools.png)

## Margins, padding, and borders

You've already seen the ***margin***, ***padding***, and ***border*** properties at work above. The properties used in that example are ***shorthands*** and allow us to set all four sides of the box at once. These shorthands also have equivalent longhand properties, which allow control over the different sides of the box individually.

Let's explore these properties in more detail.

## Margin

The margin is an invisible space around your box. It pushes other elements away from the box. Margins can have positive or negative values. Setting a negative margin on one side of your box can cause it to overlap other things on the page. Whether you are using the standard or alternative box model, the margin is always added after the size of the visible box has been calculated.

We can control all margins of an element at once using the ***margin*** property, or each side individually using the equivalent longhand properties:

- margin-top
- margin-right
- margin-bottom
- margin-left

## Margin collapsing

Depending on whether two elements whose margins touch have positive or negative margins, the results will be different:

- Two positive margins will combine to become one margin. Its size will be equal to the largest individual margin.
- Two negative margins will collapse and the smallest (furthest from zero) value will be used.
- If one margin is negative, its value will be subtracted from the total.

## Borders

The border is drawn between the margin and the padding of a box. If you are using the standard box model, the size of the border is added to the ***width*** and ***height*** of the content box. If you are using the alternative box model then the size of the border makes the content box smaller as it takes up some of that available ***width*** and ***height*** of the element box.

For styling borders, there are a large number of properties -there are four borders, and each border has a style, width, and color that we might want to manipulate.

Youcan set the width, style, or color of all four borders at once using the [***border***](https://developer.mozilla.org/en-US/docs/Web/CSS/border) property.

To set the properties of each side individually, use:

- border-top
- border-right
- border-bottom
- border-left

To set the width, style, or color of all sides, use:

- border-width
- border-style
- border-color

To set the width, style, or color of a single side, use one of the more granular longhand properties:

- border-top-width
- border-top-style
- border-top-color
- border-right-width
- border-right-style
- border-right-color
- border-bottom-width
- border-bottom-style
- border-bottom-color
- border-left-width
- border-left-style
- border-left-color

In the example below, we have used various shorthands and loghands to create borders. 

![bordersExercise](/images/bordersExer.png)

```
.container {
  border-top: 5px dotted green;
  border-right: 1px solid black;
  border-bottom: 20px double rgb(23,45,145);
}

.box {
  border: 1px solid #333333;
  border-top-style: dotted;
  border-right-width: 20px;
  border-bottom-color: hotpink;
}
```

```
<div class="container">
  <div class="box">Change my borders.</div>
</div>
```

## Padding

The padding sits between the border and the content area and is used to push the content away from the border. Unlike margins, you cannot have a negative padding. Any background applied to your element will display behind the padding.

The [padding](https://developer.mozilla.org/en-US/docs/Web/CSS/padding) property controls the padding on all sides of an element. To control each side individually, use these longhand properties:

- padding-top
- padding-right
- padding-bottom
- padding-left


## The box model and inline boxes

All of the above fully applies to block boxes. some of the properties can apply to inline boxes too, such as those created by a span element

## Using display: inline-block

***display: inline-block*** is a special value of ***display***, which provides a middle ground between ***inline*** and ***block***. Use it if you don't want an item to break onto a new line, but do want it to respect width and height and avoid the overlapping seen above.

AN element wih ***display: inline-block*** does a subset of the block things we already know about:

- The ***width*** and ***height*** properties are respected.
- ***padding***, ***margin***, and ***border*** will cause other elements to be pushed away from the box.

It doesn't, however, break onto a new line, and will only become larger than its content if you explicitly add ***width*** and ***height*** properties.

## Styling backgrounds in CSS

The CSS background property is a shorthand for a number of background longhand properties that we will meet in this lesson. If you discover a complex background property in a stylesheet, it might seem a little hard to understand as so many values can be passed in at once.

## Background colors

The background-color property defines the background color on any element in CSS. The property accepts any valid color. A background-color extends underneath the content and padding box of the element.

In the example below, we have used various color values to add a background color to the box, a heading, and a span element.

![backgroundcolor](/images/backgroundColor.png)

```
.box {
  background-color: #567895;
}

h2 {
  background-color: black;
  color: white;
}
span {
  background-color: rgba(255,255,255,.5);
}
```

```
<div class="box">
  <h2>Background Colors</h2>
  <p>Try changing the background <span>colors</span>.</p>
</div>
    
```

## Background images

The background-image property enables the display of an image in the background of an element. In the example below, we have two boxes -one has a background image which is larger than the box (left image), the other has a small image of a single star.

This example demostrates two things about background images. By default, the large image is not scaled down to fit the box, so we only see a small corner of it, whereas the small image is tiled to fill the box.


![backgroundExample](/images/backgroundEx.png)

```
.a {
  background-image: url(balloons.jpg);
}

.b {
  background-image: url(star.png);
}
```

```
<div class="wrapper">
  <div class="box a"></div>
  <div class="box b"></div>
</div>
    
```

If you specify a background color in addition to a background image then the image displays on top of the color. Try adding a background-color property to the example above to see that in action.

## Controlling background-repeat

The [background-repeat](https://developer.mozilla.org/en-US/docs/Web/CSS/background-repeat) property is used to control the tiling behavior of images. The available values are:

- no-repeat: stop the background from repeating altogether.
- repeat-x: repeat horizontally.
- repeat-y: repeat vetically.
- repeat: the default; repeat in both directions.

## Sizing the brackground image

In case we use the backgroud-size property, can take length or pencentage values, to size the image to fit inside the background.

You can also user keywords:

- Cover: The browser will make the image just large enough so that it completely covers the box area while still retaining its aspect ratio. In this case, part of the image is likely to end up outside the box.
- Contain: The browser will make the image the right size to fit inside the box. In this case, you may end up with gaps on either side or on the top and bottom of the image, if the aspect ratio of the image is different from that of the box.

## Positioning the background image

The background-position property allows you to choose the position in which the background image appears on the box it is applied to. This uses a coordinate system in which the top-left-hand corner of the box is (0,0), and the box is positioned along the horizontal (x) and vertical (y) axes.

The most common background-position values take two individual values -a horizontal value followed by a vertical value. You can use keywords such as top and right (look up the others on the [background-position](https://developer.mozilla.org/en-US/docs/Web/CSS/background-position) page):

```
.box {
  background-image: url(star.png);
  background-repeat: no-repeat;
  background-position: top center;
}
```
And [Lengths](https://developer.mozilla.org/en-US/docs/Web/CSS/length), and [percentages](https://developer.mozilla.org/en-US/docs/Web/CSS/percentage):

```
.box {
  background-image: url(star.png);
  background-repeat: no-repeat;
  background-position: 20px 10%;
}
```

You can also mix keyword values with lengths or percentages, in which case the first value must refer to the horizontal position or offset and the second vertical. For example:

```
.box {
  background-image: url(star.png);
  background-repeat: no-repeat;
  background-position: 20px top;
}
```

Finally, you can also use a 4-value syntax in order to indicate a distance from certain edges of the box -the length unit, in this case, is an offset from the value that precedes it. So in the CSS below we are positioning the background 20px from the top and 10 from the right:

```
.box {
  background-image: url(star.png);
  background-repeat: no-repeat;
  background-position: top 20px right 10px;
}
```

## Gradient backgrounds

A gradient -when used for a background- acts just like an image and is also set by using the background-image property.
You can read more about the different types of grandients and things you can do with them on the MDN page for the [gradient](https://developer.mozilla.org/en-US/docs/Web/CSS/gradient) data type. A fun way to play with gradients is to use one of the many CSS Gradient Generators available on the web, such as [this one](https://cssgradient.io/). You can create a gradient then copy and paste out the source code that generates it.

![gradientCSS](/images/gradient.png)

```
.a {
  background-image: linear-gradient(105deg, rgba(0,249,255,1) 39%, rgba(51,56,57,1) 96%);
}

.b {
  background-image: radial-gradient(circle, rgba(0,249,255,1) 39%, rgba(51,56,57,1) 96%);
  background-size: 100px 50px;
}
```

```
<div class="wrapper">
  <div class="box a"></div>
  <div class="box b"></div>
</div>
```

## Multiple background images

It's also possible to have multiple background images -you specificy multiple background-image values in a single property value, separating each one with a comma.

When you do this you may end up with background images overlapping each other. The backgrounds will layers with the last listed background image at the bottom of the stack, and each previous image stacking on top of the one that follows it in the code.

The other background-* properties can also have comma-separated values in the same way as background-image:

```
background-image: url(image1.png), url(image2.png), url(image3.png),
  url(image4.png);
background-repeat: no-repeat, repeat-x, repeat;
background-position: 10px 20px, top right;
```

Each value of the different properties will match up to the values in the same position in the other properties. Above, for example, image1's background-repeat value will be no-repeat.
However, what happens when different properties have different numbers of values? The answer is that the smaller numbers of values will cycle -in the above example there are four background images but only two background-position values. The first two positino values will be applied to the first two images, then they will cycle back around again -image3 will be given the first position values, and image4 will be given the second position value.

![BackgroundImage](/images/backgroundImage.png)

```
.box {
  background-image: url(star.png), url(big-star.png);
}
```

```
<div class="wrapper">
  <div class="box"></div>
</div>
```

## Background attachment

Another option we have available for backgrounds is specifyin how they scroll when the content scrolls. This is cnotrolled using the background-attachment property, which can take the following values:

- Scroll: causes the element's background to scroll when the page is scrolled. If the element content is scrolled, the background does not move. In effect, the background is fixed to the same position on the page, so it scrolls as the page scrolls.

- Fixed: causes an element's background to be fixed to the viewport so that it doesn't scroll when the page or element content is scrolled. It always remain in the same position on the screen.

- Local: fixes the background to the element it is set on, so when you scroll th element, the background scrolls with it.

The [background-attachment](https://developer.mozilla.org/en-US/docs/Web/CSS/background-attachment) property only has an effect when there is content to scroll, so we've made a demo to demostrate the differences between the three values -have a look at [background-attachment.html](https://mdn.github.io/learning-area/css/styling-boxes/backgrounds/background-attachment.html) (also [see the source code](https://github.com/mdn/learning-area/tree/main/css/styling-boxes/backgrounds) here).

## Using the background shorthand property

As I mentioned at the beginning, you will often see backgrounds specified using the background property. This shorthand lets you set all of the different properties at once.

If using multiple backgrounds, you need to specify all of the properties for the first background, then add your next background after a comma. In the example below we have a gradient with a size and position, then a image background with no-repeat and a position, then a color.

There are a few rules that need to be followed when writing background image shorthand values, for example:

- A background-color may only be specified after the final comma.

- The value of background-size may only be included immediately after background-position, separated with the '/' character, like this: center/80%.

![backgroundEX2](/images/backgroundEx2.png)

```
.box {
  background:   
    linear-gradient(105deg, rgba(255,255,255,.2) 39%, rgba(51,56,57,1) 96%) center center / 400px 200px no-repeat,
url(big-star.png) center no-repeat, 
    rebeccapurple;
}
```

```
<div class="box"></div>
```

## Accessibility considerations with backgrounds

When placing text on top of a background image or color, you should take care that you have enough contrast for the text to be legible for your visitors. If specifying an image, and if text will be placed on top of that image, you should also specify a background-color that will allow the text to be legible if the images does not load.

Screen readers cannot parse background images; therefore, they should be purely decoration. Any important content should be part of the HTML page and not contained in a background.

## Borders

When learning about Box Model, we discovered how borders affect the size of our box. We will look at how to use borders creatively. Typically when we add borders to an element with CSS we use a shorthand property that sets the color, width, and style of the border in one line of CSS.

We can set a border for all four sides of a box with [border](https://developer.mozilla.org/en-US/docs/Web/CSS/border):

```
.box {
  border: 1px solid black;
}
```

Or we can target one edge of the box, for example:

```
.box {
  border-top: 1px solid black;
}
```

The individual properties for these shorthands would be:

```
.box {
  border-width: 1px;
  border-style: solid;
  border-color: black;
}
```

And for the longhands:

```
.box {
  border-top-width: 1px;
  border-top-style: solid;
  border-top-color: black;
}
```

There are a variety of styles that you can use for borders.

![bordersEX2](/images/bordersEx2.png)

```
.box {
  background-color: #567895;
  border: 5px solid #0b385f;
  border-bottom-style: dashed;
  color: #fff;
}

h2 {
  border-top: 2px dotted rebeccapurple;
  border-bottom: 1em double rgb(24, 163, 78);
}
```

```
<div class="box">
  <h2>Borders</h2>
  <p>Try changing the borders.</p>
</div>
```

## Rounded corners

Rounding corners on a box is achieved by using the border-radius property and associated longhands which relate to each corner of the box. Two lengths or percentages may be used as a value, the first value defining the horizontal radius, and the second the vertical radius. In a lot of cases, you will only pass in one value, which will be used for both.

For example, to make all four corners of a box have a 10px radius:

```
.box {
  border-radius: 10px;
}
```

Or to make the top right corner have a horizontal radius of 1em, and a vertical radius of 10%:

```
.box {
  border-top-right-radius: 1em 10%;
}
```

We have set all four corners in the example below and then changed the values for the top right corner to make it differnet.

![bordersEX3](/images/bordersEx3.png)

```
.box {
  border: 10px solid rebeccapurple;
  border-radius: 1em;
  border-top-right-radius: 10% 30%;
}
```

```
<div class="box">
  <h2>Borders</h2>
  <p>Try changing the borders.</p>
</div>
```

