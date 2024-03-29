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

## Overflowing content

Overflow is what happens when there is too much content to fit in a container. In this guide you will learn what overflow is and how to manage it.

### What is overflow?

Everything in CSS is a box. You can constrain the size of these boxes by assigning values of [width](https://developer.mozilla.org/en-US/docs/Web/CSS/width) and [height](https://developer.mozilla.org/en-US/docs/Web/CSS/height) (or [inline-size](https://developer.mozilla.org/en-US/docs/Web/CSS/inline-size) and [block-size](https://developer.mozilla.org/en-US/docs/Web/CSS/block-size)). Overflow happens when there is too much content to fit in a box. CSS provides various tools to manage overflow. As you go further with CSS layout and writing CSS, you will encounter more overflow situations.

### CSS tries to avoid "data loss"

Let's consider two examples that demostrate the default behavior of CSS when there is overflow.

The first example is a box that has been restricted by setting a height. Then we add content that exceeds the allocated space. The content overflows the box and falls into the paragraph below.

![OverflowEx1](/images/overflowEx1.png)

```
.box {
  border: 1px solid #333333;
  width: 200px;
  height: 100px;
}
    
```

```
<div class="box">This box has a height and a width. This means that if there is too much content to be displayed within the assigned height, there will be an overflow situation. If overflow is set to hidden then any overflow will not be visible.</div>

<p>This content is outside of the box.</p>
```

The second example is a word in a box. The box has been made too small for the word and so it breaks out of the box.

![OverflowEx2](/images/overflowEx2.png)

```
.word {
  border: 1px solid #333333;
  width: 100px;
  font-size: 250%;
}
    
```

```
<div class="word">Overflow</div>
```

CSS does not hide content. This would cause data loss. The problem with data loss is that you might not notice. Website visitors may not notice. If the submit button on a form disappears and no one can complete the form, this could be a big problem! Instead, CSS overflows in visible ways. You are more likely to see there is a problem. At worst, a site visitor will let you know that content is overlapping.

If you restrict a box with a width or a height, CSS trusts you to know what you are doing. CSS assumes that you are managing the potential for overflow. In general, restricting the block dimension is problematic when the box contains text. There may be more text than you expected when designing the site, or the text may be larger (for example, if the user has increaser their font size).

## The overflow property

The [overflow](https://developer.mozilla.org/en-US/docs/Web/CSS/overflow) property is how you take control of an element's overflow. It is the way you instruct the browser how it should behave. The default value of overflow is visible. With this default, we can see content when it overflows.

To crop content when it overflows, you can set overflow: hidden. This does exactly what it says: it hides overflow. Beware that this can make some content invisible. You should only do this if hiding content won't cause problems.

![overflowHIddenEX](/images/overflowHiddenEX.png)

```
.box {
  border: 1px solid #333333;
  width: 200px;
  height: 100px;
  overflow: hidden;
}
```

```
<div class="box">This box has a height and a width. This means that if there is too much content to be displayed within the assigned height, there will be an overflow situation. If overflow is set to hidden then any overflow will not be visible.</div>

<p>This content is outside of the box.</p>
```
 
Instead, perhaps you would like to add scrollbars when content overflows? Using overflow: scroll, browsers with visible scrollbars will always display them -even if there is not enough content to overflow. This offers the advantage of keeping the layour consistent, instead of scrollbars appearing or disappearing, depending upon the amount of content in the container.

![overflowExSCroll](/images/overflowExScroll.png)

```
.box {
  border: 1px solid #333333;
  width: 200px;
  height: 100px;
  overflow: scroll;
}
    
```

```
<div class="box">This box has a height and a width. This means that if there is too much content to be displayed within the assigned height, there will be an overflow situation. If overflow is set to hidden then any overflow will not be visible.</div>

<p>This content is outside of the box.</p>
```

In the example above, we only need to scroll on the y axis, however we get scrollbars in both axes. To just scroll on the y axis, you could use the overflow-y property, setting overflow-y: scroll.

![overflowYScroll](/images/overflowYScroll.png)

```
.box {
  border: 1px solid #333333;
  width: 200px;
  height: 100px;
  overflow-y: scroll;
}
```

```
<div class="box">This box has a height and a width. This means that if there is too much content to be displayed within the assigned height, there will be an overflow situation. If overflow is set to hidden then any overflow will not be visible.</div>

<p>This content is outside of the box.</p>
```

You can also scroll on the x axis using [overflow-x](https://developer.mozilla.org/en-US/docs/Web/CSS/overflow-x), although this is not a recommended way to accommodate long words. If you have a long word in a small box, you might consider using the [word-break](https://developer.mozilla.org/en-US/docs/Web/CSS/word-break) or [overflow-wrap](https://developer.mozilla.org/en-US/docs/Web/CSS/overflow-wrap) properties. In addition, some of the methods discussed in [Sizing items in CSS](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Sizing_items_in_CSS) may help you create boxes that scale better with varying amounts of content.

![overflowXScroll](/images/overflowXScroll.png)

```
.word {
  border: 5px solid #333333;
  width: 100px;
  font-size: 250%;
  overflow-x: scroll;
}
```

```
<div class="word">Overflow</div>
```

As with scroll, you get a scrollbar in the scrolling dimension whether or not there is enough content to cause a scrollbar.

If you only want scrollbars to appear when there is more content that can fit in the box, use overflow: auto. This allows the browser to determine if it should display scrollbars.

In the example below, if you remove content until it fits into the box, you should see the scrollbars disappear.

![overflowAuto](/images/overflowAuto.png)

```
.box {
  border: 1px solid #333333;
  width: 200px;
  height: 100px;
  overflow: auto;
}
```

```
<div class="box">This box has a height and a width. This means that if there is too much content to be displayed within the assigned height, there will be an overflow situation. If overflow is set to hidden then any overflow will not be visible.</div>

<p>This content is outside of the box.</p>
```


## CSS values and units

Every property used in CSS has a value type defining the set of values that are allowed for that property.

## What is a CSS value?

In CSS specifications and on the property pages here on MDN you will be able to spot value types as they will be surrounded by angle backers, such as color or lenght. When you see the value type color as valid for a particular property, that means you can use any valid color as a value for that property, as listed on the color reference page.

In the following example, we have set the color of our heading using a keyword, and the background using the rgb() function:

```
 h1 {
  color: black;
  background-color: rgb(197, 93, 161);
 }
```

A value type in CSS is a way to define a collection of allowable values. This means that if you see color as valid you don't need to wonder which of the different types of color value can be used -keywords, hex values, rgb() functions, etc. You can use any available color values, assuming they are supported by your browser. The page on MDN for each value will give you information about browser support. For example, if you look at the page for [color](https://developer.mozilla.org/en-US/docs/Web/CSS/color_value) you will see that the browser compatibility section lists different types of color values and support for them

Let's have a look at some of the types of values and units you may frequently encounter, with examples so that you can try out different possible values.

## Numbers, lengths, and percentages

- integer: an integer is a whole number such as 1024 or -55.

- number: A number represents a decime number -it may ot may not have a decimal point with a fractional component. For example, 0.255, 128, or -1.2.

- dimension: A dimension is a numberwith a unit attached to it. For example, 45deg, 5s, or 10px. dimension is an umbrella category that includes the length, angle, time, and resolution types.

- percentage: A percentage represents a fraction of some other value. For example, 50%. Percentage values are always relative to another quantity. For example, an element's length is relative to its parent element's length.

### Lenghts

The numeric type you will come across most frequently is length. For example, 10px(pixels) or 30em. There are two types of lengths used in CSS -relative and absolute. It's important to know the difference in order to understand how big things will become.

### Absolute length units

The following are all ***absolute*** length units -they are not relative to anything else, and are generally considered to always be the same size.

- ***cm***, centimeters, 1cm = 37.8px= 25.2/64in

- ***mm***, milimeters, 1mm = 1/10th of 1cm.

- ***Q***, Quarter-millimeters, 1Q = 1/40th of 1cm.

- ***in***, Inches, 1in = 2.54cm = 96px.

- ***pc***, Picas, 1pc = 1/6th of 1in.

- ***pt***, Points, 1pt = 1/72nd of 1in.

- ***px***, Pixels, 1px = 1/96th of 1in.

Most of these units are more useful when used for print, rather than screen output. For example, we don't typically use cm (centimeters) on screen. The only value that you will commonly use is px (pixels).

## Relative length units

Relative length units are relative to something else, perhaps the size of parent element's font, or the size of the viewport. The benefit of using relative units is that with some careful planning you can make it so the size of text or other elements scales relative to everything else on the page. Some of the most useful units for web development are listed in the table below.

- em : Font size of the parent, in the case of typographical properties like [font-size](https://developer.mozilla.org/en-US/docs/Web/CSS/font-size), and font size of the element itself, in the case of other properties like [width](https://developer.mozilla.org/en-US/docs/Web/CSS/width).

- ex : x-height of the element's font.

- rem : Font size of the root element.

- lh : Line height of the element.

- vw : 1% of the viewport's width.

- vh : 1% of the viewport's height.

- vmin : 1% of the viewport's smaller dimension.

- vmax : 1% of the viewport's larger dimension.

### ems and rems

***em*** and ***rem*** are the two relative lengths you are likely to encounter most frequently when sizing anything from boxes to text. It's worth understanding how these work, and the differences between them, especially when you start getting on to more complex subjects like [styling text](https://developer.mozilla.org/en-US/docs/Learn/CSS/Styling_text) or [CSS layout](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout).

## Percentages

In a lot of cases, a percentage is trated in the same way as a length. The thing with percentages is that they are always set relative to some other value. For example, if you set an element's font-size as a percentage, it will be a percentage of the font-size of the element's parent. If you use a percentage for a width value, it will be a percentage of the width of the parent.

In the below example the two percentage-sized boxes and the two pixel-sized boxes have the same class names. The sets are 40% and 200px wide respectively.

The difference is that the second set of two boxes is inside a wrapper that is 400 pixels wide. The second 200px wide box is the same width as the first one, but the second 40% box is now 40% of 400px -a lot narrower than the first one!

![percetangeEx1](/images/percentageEx1.png)

```
.wrapper {
  width: 400px;
  border: 5px solid rebeccapurple;
}

.px {
  width: 200px;
}

.percent {
  width: 40%;
}
```

```
<div class="box px">I am 200px wide</div>
<div class="box percent">I am 40% wide</div>
<div class="wrapper">
  <div class="box px">I am 200px wide</div>
  <div class="box percent">I am 40% wide</div>
</div>
```

The next example has font sizes set in percentages. Each li has a font-size of 80%; therefore, the nested list items become progressively smaller as they inherit their sizing from their parent.

![percentageEx2](/images/percentageEx2.png)

```
li {
  font-size: 80%;
}
```

```
<ul>
  <li>One</li>
  <li>Two</li>
  <li>Three
    <ul>
      <li>Three A</li>
      <li>Three B
        <ul>
          <li>Three B 2</li>
        </ul>
      </li>
    </ul>
  </li>
</ul>  
```

Note that, while many values types accept a length or a percentage, there are some that only accept length. You can see which values are accepted on the MDN property reference pages. If the allowed value includes length-percentage then you can use a length or a percentage. If the allowed value only includes length, it is not possible to use a percentage.


## Numbers

Some value types accept numbers, without any unit added to them. An example of a property which accepts a unitless number is the opacity property, which controls the opacity of an element (how transparent it is). This property accepts a number between 0 (fully transparent) and 1 (fully opaque).


## Color

![opacity](/images/opacity.png)

```
.box {
  opacity: 0.6;
}
```

```
<div class="wrapper">
  <div class="box">I am a box with opacity</div>
</div> 
```

## Color

The standard color system available in modern computers support 24-bit colors, which allows the display of about 16.7 million distinct colors via a combination of different red, green and blue channels with 256 differente value per channel ( 256 x 256 x 256 = 16,777,215). Let's have a look at some of the ways in which we can specify colors in CSS.

## Color keywords

Quite often in examples here you will see the color keywords used, as they are a simple and understandable way of specifying color. There are a number of these keywords, some of which have fairly entertaining names, you can see a full list on the page for the [color](https://developer.mozilla.org/en-US/docs/Web/CSS/color_value) value type.

## Hexadecimal RGB values

The next type of color value you are likely to encounter is hexadecimal codes. Each hex value consists of a hash/ pound symbol followed by six hexadecimal numbers, each of which can take one of 16 values between 0 and f (which represents 15)- so 0123456789abcdef. Each pair of values represents one of the channels -red, green and blue- and allows us to specify any of the 256 available values for each ( 16 x 16 = 256).

These values are a bit more complex and less easy to understand, but they are a lot more versatile than keywords -you can use hex values to represent any color you want to use in your color scheme.

![hexadecimalRGBValues](/images/rgb%20colors.png)

```
.one {
  background-color: #02798b;
}

.two {
  background-color: #c55da1;
}

.three {
  background-color: #128a7d;
}
```

```
<div class="wrapper">
  <div class="box one">#02798b</div>
  <div class="box two">#c55da1</div>
  <div class="box three">#128a7d</div>
</div>
```

## RGB and RGBA values

The third scheme we'll talk about here is RGB. An RGB value is a function - rgb()- which is given three parameters that represent the red, green and blue channel values of the colors, in much the same way as hex values. The difference with RGB is that each channel is represented not by two hex digits, but by a decimal number between 0 and 255 -somewhat easier to understand.

![RgbExample](/images/rgbExample.png)

```
.one {
  background-color: rgba(2, 121, 139, .3);
}

.two {
  background-color: rgba(197, 93, 161, .7);
}

.three {
  background-color: rgba(18, 138, 125, .9);
}
```

```
<div class="wrapper">
  <div class="box one">rgba(2, 121, 139, .3)</div>
  <div class="box two">rgba(197, 93, 161, .7)</div>
  <div class="box three">rgba(18, 138, 125, .9)</div>
</div>
```

## HSL and HSLA values

An alternative way to specify colors is the HSL color model. Instead of red, green and blue values, the hsl() function accepts hue, saturation, and lightness values, which are used to distinguish between the 16.7 million colors, but in a different way:

- Hue: The base shade of the color. This takes a value between 0 and 360, representing the angles around a color wheel.

- Saturation: How saturated is the color? This takes a value from 0-100%, where 0 is no color (it will appear as a shade of grey), and 100% is full color saturation.

- Lightness: How light or bright is the color? This takes a value from 0-100%, where 0 is no light (it will appear completely black) and 100% is full light (it will appear completely white).

![HslExample](/images/hslExample.png)

```
.one {
  background-color: hsl(188, 97%, 28%);
}

.two {
  background-color: hsl(321, 47%, 57%);
}

.three {
  background-color: hsl(174, 77%, 31%);
}
```

```
<div class="wrapper">
  <div class="box one">hsl(188, 97%, 28%)</div>
  <div class="box two">hsl(321, 47%, 57%)</div>
  <div class="box three">hsl(174, 77%, 31%)</div>
</div>
```

Just like with rgb() you can pass an alpha parameter to hsl() to specify opacity:

![HslExample2](/images/hslExample2.png)

```
.one {
  background-color: hsl(188 97% 28% / .3);
}

.two {
  background-color: hsl(321 47% 57% / .7);
}

.three {
  background-color: hsl(174 77% 31% / .9);
}
    
```

```
<div class="wrapper">
  <div class="box one">hsl(188 97% 28% / .3)</div>
  <div class="box two">hsl(321 47% 57% / .7)</div>
  <div class="box three">hsl(174 77% 31% / .9)</div>
</div>
```

You can use any of these color values in your projects. It is likely that for most projects you will decide on a color palette and then use those colors -and your chosen method of specifying color- throughout the whole project. You can mix and match color models, however for consistency it is usually best if your entire project uses the same one!

## Images

The [image](https://developer.mozilla.org/en-US/docs/Web/CSS/image) value type is used wherever an image is a valid value. This can be an actual image file pointer to via a url() function, or a gradient.

In the example below, we have demonstrated an image and a gradient in use as a value for the CSS background-image property.

![ImageEx](/images/imageEx1.png)

```
.image {
  background-image: url(star.png);
}

.gradient {
  background-image: linear-gradient(90deg, rgba(119,0,255,1) 39%, rgba(0,212,255,1) 100%);
}
```

```
div class="box image"></div>
<div class="box gradient"></div> 
```

## Position

The position value type represents a set of 2D coordinates, used to position an item such as background image (via background-position). It can take keywords such as top, left, bottom, right, and center to align items with specific bounds of a 2D box, along with lengths, which represent offsets from the top and left-hand edges of the box.

A typical position value consists of two values -the first sets the position horizontally, the second vertically. If you only specify values for one axis the other will default to center.

In the following example we have positioned a background image 40px from the top and to the right of the container using a keyword.

![backgroundEx3](/images/backgroundEx3.png)

```
.box {
  height: 300px;
  width: 400px;
  background-image: url(star.png);
  background-repeat: no-repeat;
  background-position: right 40px;
}
```

```
<div class="box"></div> 
```

## Strings and identifiers

Throughout the examples above, we've seen places where keywords are used as value (for example color keywords like red, black, rebeccapurple and goldenrod). These keywords are more accurately described as identifiers, a special value that CSS understands. As such they are not quoted -they are not treated as strings.

There are places where you use strings in CSS. For example, when specifying generated content. In this case, the value is quoted to demonstrate that it is a string. In the example below, we use unquoted color keywords along with a quoted generated content string.

![stringExample](/images/stringsExCSS1.png)

```
.box {
  width:400px;
  padding: 1em;
  border-radius: .5em;
  border: 5px solid rebeccapurple;
  background-color: lightblue;
}

.box::after {
  content: "This is a string. I know because it is quoted in the CSS."
}
```

```
<div class="box"></div> 
```

## Functions

The final type of value we will take a look at is the group of values known as functions. In programming, a function is a reusable section of code that can be run multiple times to complete a repetitive task with minimum effort on the part of both the developer and the computer. Functions are usually associated with languages like JavaScript, Python or C++, but they do exist in CSS too, as property values. We've already seen functions in action in the Colors section -rgb(), hsl(), etc. The value used to return an image from a file -url()- is also a function.

A value that behaves more like something you might find in a traditional programming language is the calc() CSS function. This function gives you the ability to do simple calculations inside your CSS. It's particularly useful if you want to work out values that you can't define when writing the CSS for your project, and need the browser to work out for you at runtime.

For example, below we are using calc() to make a box 20% + 100px wide. The 20% is calculated from the width of the parent container .wrapper and so will change if that width changes. We can't do this calculation beforehand because we don't know what 20% of the parent will be, so w euse calc() to tell the browser to do it for us.

![calc()functionCSS](/images/calc()functioncss.png)

```
.wrapper {
  width: 400px;
}

.box {
  width: calc(20% + 100px);
}
    
```

```
<div class="wrapper">
  <div class="box">My width is calculated.</div> 
</div>
```

## Sizing items in CSS

### The natural or intrinsic size of things

HTML elements have a natural size, set before they are affected by any CSS. A straightforward example is an image. An image file contains sizing information, described as its ***intrinsic size***. This size is determined by the image itself, not by any formatting we happen to apply.

If you place an image on a page and do not change its height or width, either by using attributes on the img tag orelse by CSS, it will be displayed using that intrinsic size. 

![imageEx2](/images/imageEx2.png)

```
img {
  border: 5px solid darkblue;
}
```

```
<img src="star.png" alt="star">
```

An empty div, on the other hand, has no size of its own. If you add a div to your HTML with no content, then give it a border as we did with the image, you will see a line on the page. This is the collapsed border on the element -there is no content to hold it open. In our example below, that border stretches to the width of the container, because it is a block level element, a behavior that should be starting to become familiar to you. It has no height (or size in the block dimension) because there is no content.

![divEx](/images/divEx.png)

```
.box {
  border: 5px solid darkblue;
}
```

```
<div class="box">

</div>
```

In the example above, try adding some text inside the empty element. The border now contains that text because the height of the element is defined by the content. Therefore the size of this div in the block dimension comes from the size of the content. Again, this is the intrinsic zone of the element -its size is defined by its content.

## Setting a specific size

We can, of course, give elements in our design a specific size. When a size is given to an element (the content of which then needs to fit into that size) we refer to it as an ***extrinsic size***.
Take out div from the example above -we can give it specific width and height values, and it will now have that size no matter what content is placed into it. As we discovered in overflow lesson, a set height can cause content to overflow if there is more content than the element has space to fit inside it.

![overflowEx3](/images/overflowEx3.png)

```
.box {
  border: 5px solid darkblue;
  height: 150px;
  width: 200px;
}
```

```
<div class="wrapper">
  <div class="box"></div>
  <div class="box">These boxes both have a height set, this box has content in it which will need more space than the assigned height, and so we get overflow. </div>
</div>
```

Due to this problem of overflow, fixing the height of elements with lengths or percentages is something we need to do very carefully on the web.

## Using percentages

In many ways, percentages act like length units, and as we discussed in the lesson on values and units, they can often be used interchangeably with lengths. When using a percentage you need to be aware what it is a percentage of. In the case of a box inside another container, if you give the child box a percentage width it will be a percentage of the width of the parent container.

![percentageEx3](/images/percentageEx3.png)

```
.box {
  border: 5px solid darkblue;
  width: 50%;
}
```

```
<div class="box">
  I have a percentage width.
</div>
```

This is because percentages resolve against the size of the containing block. With no percentage applied, our div would take up 100% of the available space, as it is a block level element. If we give it a percentage width, this becomes a percentage of the space it would normally fill.

## Percentage margins and padding

If you set margins and padding as a percentage, you may notive some strange behavior. In the below examplewe have a box. We have given the inner box a margin of 10% and a padding of 10%. The padding and margin on the top and bottom of the box are the same size as the margin on the left and right.

![percentageEx4](/images/percentageEx4.png)

```
.box {
  border: 5px solid darkblue;
  width: 300px;
  margin: 10%;
  padding: 10%;
}
```

```
<div class="box">
  I have margin and padding set to 10% on all sides.
</div>
```

You might expect for example the percentage top and bottom margins to be a percentage of the element's height, and the percentage left and right margins to be a percentage of the element's width. however, this is not the case!

When you use a marign and padding set in percentages, the value is calculated from the ***inline size*** of the containing block -therefore the width when working in a horizontal language. In our example, all of the margins and padding are 10% of the width. This means you have equal-sized margins and padding all around the box. This is a fact worth remembering if you do use percentages in this way.

## min- and max- sizes

In addition to giving things a fixed size, we can ask CSS to give an element a minimum or a maximum size. If you have a box that might contain a variable amount of content, and you always want it to be at least a certain height, you could set a min-height property on it. The box will always be at least this height, but will then grow taller if there is more content than the box has space for at its minimum height.

In the example below you can see two boxes, both with a defined min-height of 150 pixels. The box on the left is 150 pixels tall; the box on the right has content that needs more room, and so it has grown taller than 150 pixels.

![min-heightEx](/images/min-heightEx.png)

```
.box {
  border: 5px solid darkblue;
  min-height: 150px;
  width: 200px;
}
```

```
<div class="wrapper">
  <div class="box"></div>
  <div class="box">These boxes both have a min-height set, this box has content in it which will need more space than the assigned height, and so it grows from the minimum.</div>
</div>
```

This is very useful for dealing with variable amounts of content while avoiding overflow.

A common use of max-width is to cause images to scale down if there is not enough space to display them at their intrinsic width while making sure they don't become larger than that width.

As an example, if you were to set width: 100% on an image, and its intrinsic width was smaller than its container, the image would be forced to stretch and become larger, causing it to look pixelated.

If you instead use max-width: 100%, and its intrisic width is smaller than its container, the image will not be forced to stretch and become larger, this preventing pixelation.

In the example below, we have used the same image three times. The first image has been given width: 100% and is in a container which is larger than it, therefore it stretches to the container width. The second image has max-width: 100% set on it and therefore does not stretch to fill the container. The third box contains the same image again, also with max-width: 100% set; in this case you can see how it has scaled down to fit into the box.

![max-widthEx](/images/max-widthEx.png)

```
.box {
  width: 200px;
}
.minibox {
  width: 50px;
}
.width {
  width: 100%;
}
.max {
  max-width: 100%;
}
```

```
<div class="wrapper">
  <div class="box"><img src="star.png" alt="star" class="width"></div>
  <div class="box"><img src="star.png" alt="star" class="max"></div>
  <div class="minibox"><img src="star.png" alt="star" class="max"></div>
</div>
```

This technique is used to make images responsive, so that when viewed on a smaller device they scale down appropriately. You should, however, not use this technique to load really large images and then scale them down in the browser. Images should be appropriately sized to be no larger than they need to be for thelargest size they are displayed in the design. Downloading overly large images will cause your site to become slow, and it can cost users more money if they are on a metered connection.

## Viewport units

The viewport -which is the visible area of your page in the browser you are using to view a site- also has a size. In CSS we have units which relate to the size of the viewport -the ***vw*** unit for viewport width, and ***vh*** for viewport height. Using these units you can size something relative to the viewport of the user.

1vh is equal to 1% of the viewport height, and 1vw is equal to 1% of the viewport width. You can use these units to size boxes, but also text. In the example below we have a box which is sized as 20vh and 20vw. The box contains a letter A, which has been given a font-size of 10vh.

![viewportEx](/images/viewportEx.png)

```
.box {
  border: 5px solid darkblue;
  width: 20vw;
  height: 20vh;
  font-size: 10vh;
}
```

```
<div class="box">
  A
</div>
```

If you change the vh and vw values this will change the size of the box or font; changing the viewport size will also change their sizes because they are sized relative to the viewport. To see the example change when you change the viewport size you will need to load the example in a new browser window that you can resize (as the embedded iframe that contains the example shown above is its viewport).[Open the example](https://mdn.github.io/css-examples/learn/sizing/vw-vh.html), resize the browser window, and observe what happens to the size of the box and text.

Sizing things according to the viewport can be useful in your designs. For example, if you want a full-page hero section to show before the rest of your content, making that part of your page 100vh high will push the rest of the content below the viewport, meaning that it will only appear once the document is scrolled.


## Images, media, and form elements

We will take a look at how certain special elements are treated in CSS. Images, other media, and form elements behave a little differently from regular boxes in terms of your ability to style them with CSS. Understanding what is and isn't possible can save some frustration, and this lesson will highlight some of the main things that you need to know.

### Replaced elements

Images and video are described as [replaced elements](https://developer.mozilla.org/en-US/docs/Web/CSS/Replaced_element). This means that CSS cannot affect the internal layout of these elements -only their position on the page amongst other elements. As we will see however, there are various things that CSS can do with an image.

Certain replaced elements, such as images and video, are also described as having an ***aspect ratio***. This means that it has a size in both the horizontal (x) and vertical (y) dimensions, and will be displayed using the intrinsic dimensions of the fily by default.

### Sizing images

As you already know from following this documentation, everything in CSS generates a box. If you place an image inside a box that is smaller or larger than the intrinsic dimensions of the image file in either direction, it will either appear smaller than the box, or overflow the box. You need to make a decision about what happens with the overflow.

In the example below we have two boxes, both 200 pixels in size:

- One contains an image which is smaller than 200 pixels -it's smaller than the box and doesn't stretch to fill it.
- The other is larger than 200 pixels and overflows the box.

![imageOverflow](/images/imageEx3.png)

```
.box {
  width: 200px;
}

img {

}
```

```
<div class="wrapper">
  <div class="box"><img src="star.png" alt="star"></div>
  <div class="box"><img src="balloons.jpg" alt="balloons"></div>
</div>
```

So what can we do about the overflowing issue?

As we learned in our previous lesson, a common technique is to make the mex-width of an image 100%. This will enable the image to become smaller in size than the box but not larger. This technique will also work with other replaced elements such as videos, or iframes.

Try adding "max-width: 100%" to the img element in the example above. You will see that the smaller image remains unchanged, but the larger one becomes smaller to fit into the box.

You can make other choices about images inside containers. For example, you may want to size an image so it completely covers a box.

The ***object-fit*** property can help you here. When using object-fit the replaced element can be sized to fit a box in a variety of ways.

Below we have used the value ***cover***, which sizes the image down, maintaining the aspect ratio so that it neatly fills the box. As the aspect ratio is maintained, some parts of the image will be cropped by the box.

![objectFitExample](/images/imageEx4.png)

```
.box {
  width: 200px;
  height: 200px;
}

img {
  height: 100%;
  width: 100%;
}

.cover {
  object-fit: cover;
}

.contain {
  object-fit: contain;
}
```

```
<div class="wrapper">
  <div class="box"><img src="balloons.jpg" alt="balloons" class="cover"></div>
  <div class="box"><img src="balloons.jpg" alt="balloons" class="contain"></div>
</div>
```

If we use ***contain*** as a value, the image will be scaled down until it is small enough to fit inside the box. This will result in "letterboxing" if it is not the same aspect ratio as the box.

You could also try the value ***fill***, which will fix the box but not maintain the aspect ratio.


### Replaced elements in layout

When using various CSS layout techniques on replaced elements, you may hell find that they behave slightly differently from other elements. For example, in a flex or grid layout elements are stretched by default to fill the entire area. Images will not stretch, and instead will be aligned to the start of the grid area or flex container.

You can see this happening in the example below where we have a two column, two row grid container, which has four items in it. All of the div elements have a background color and stretch to fill the row and column. The image, however, does not stretch.

![gridEx](/images/gridEx.png)

```
.wrapper {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: 200px 200px;
  gap: 20px;
}

.wrapper > div {
  background-color: rebeccapurple;
  border-radius: .5em;
}
```

```
<div class="wrapper">
  <img src="star.png" alt="star">
  <div></div>
  <div></div>
  <div></div>
</div>
```

If you are following these lessons in order then you may not have looked at layout yet. Just keep in mind that replaced elements, when they become part of a grid or flex layout, have different default behaviors, essentially to avoid them being stretched strangely by the layout.

To force the image to stretch to fill the grid cell it is in, you'd have to do something like the followin:

```
img {
  width: 100%;
  height: 100%;
}
```

This would, however, stretch the image, so it's probably not what you'd want to do.

## Form elements

Form elements can be a tricky issue when it comes to styling with CSS. The [Web Forms module](https://developer.mozilla.org/en-US/docs/Learn/Forms) contains detailed guides to the trickier aspects of styling these, which I will not fully reproduce here. There are, however, a few key basics worth highlighting in this section.

Many form controls are added to your page by way of the input element -this defines simple form fields such as text inputs, through to more complex fields such as color and date pickers. There are some additional elements, such as textarea for multiline text input, and also elements used to contain and label parts of forms such as fieldset and legend.

HTML also contains attributes that enable web developers to indicate which fields are required, and even the type of content that needs to be entered. If the user enters something unexpected, or leaves a required field black, the browser can show an error message. Different browsers vary with one another in how much styling and customization they allow for such items.

### Styling text input elements

Elements that allow for text input, such as input type="text", and the more specific input type="email", and the textarea element are quite easy to style and tend to behave just like other boxes on your page. The default styling of these elements will differ, however, based on the operating system and browser that your user visits the site with.

In the example below we have styled some text inputs using CSS -you can see that things such as borders, margins and padding all apply as you would expect. We are using attribute selectors to target the different input types. Try changing how this form looks by adjusting the borders, adding background colors to the fields, and changing fonts and padding.

![formEx](/images/formEx.png)

```
input[type="text"],
input[type="email"] {
  border: 2px solid #000;
  margin: 0 0 1em 0;
  padding: 10px;
  width: 100%;
}

input[type="submit"] {
  border: 3px solid #333;
  background-color: #999;
  border-radius: 5px;
  padding: 10px 2em;
  font-weight: bold;
  color: #fff;
}

input[type="submit"]:hover, input[type="submit"]:focus {
  background-color: #333;
}
```

```
<form>
  <div><label for="name">Name</label>
  <input type="text" id="name"></div>
  <div><label for="email">Email</label>
  <input type="email" id="email"></div>

  <div class="buttons"><input type="submit" value="Submit"></div>
</form>
```

As explained in the lessons on [form styling](https://developer.mozilla.org/en-US/docs/Learn/Forms/Styling_web_forms) in the HTML part, many of the more complex input types are rendered by the operating system and are inaccessible to styling. You should therefore always assume that forms are going to look quite different for different visitors and test complex forms in a number of browsers.

### Inheritance and form elements

In some browsers, form elements do not inherit font styling by default. Therefore, if you want to be sure that your form fields use the font defined on the body, or on a parent element, you should add this rule to your CSS.

```
button,
input,
select,
textarea {
  font-family: inherit;
  font-size: 100%;
}
```

## Form elements and box-sizing

Across browsers, form elements use different box sizing rules for different widgets. You learned about the box-sizing property and you can use this knowledge when styling forms to ensure a consistent experience when setting widths and heights on form elements.

For consistency, it is a good idea to set margins and padding to 0 on all elements, then add these back in when styling particular controls:

```
button,
input,
select,
textarea {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}
```

### Other useful settings

In addition to the rules mentioned above, you should also set overflow: auto on text area to stop IE showing a scrollbar when there is no need for one:

```
textarea {
  overflow: auto;
}
```

## Putting it all together into a "reset"

As a final step, we can wrap up the various properties discussed above into the following "form reset" to provide a consistent base to work from. This includes all the the items mentioned in the last three sections:

```
button,
input,
select,
textarea {
  font-family: inherit;
  font-size: 100%;
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}

textarea {
  overflow: auto;
}
```

## Debugging CSS

Sometimes when writing CSS you will encounter an issue where your CSS doesn't seem to be doing what you expect. Perhaps you believe that a certain selector should match an element, but nothing happens, or a box is a different size than you expected. This documentatios will give you guidance on how to go about debuggin a CSS problem, and show you how the DevTools included in all modern browsers can help you to find out what is going on.

## How to access browser DevTools

The article [What are browser developer tools](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/Tools_and_setup/What_are_browser_developer_tools) is an up-to-date guide explaining how to access the tools in various browsers and platforms. While you may choose to mostly develop in a particular browser, and therefore will become most familiar with the tools included in that browser, it is worth knowing how to access them in the other browsers. This will help if you are seeing different rendering between multiple browsers.

You will also find that browsers have chosen to focus on different areas when creating their DevTools. For example, in Firefox there are some excellent tools for working visually with CSS layout, allowing you to inspect and edit [Grid layouts](https://firefox-source-docs.mozilla.org/devtools-user/page_inspector/how_to/examine_grid_layouts/index.html), [Flexbox](https://firefox-source-docs.mozilla.org/devtools-user/page_inspector/how_to/examine_flexbox_layouts/index.html), and [Shapes](https://firefox-source-docs.mozilla.org/devtools-user/page_inspector/how_to/edit_css_shapes/index.html). However, all of the different browsers have similar fundamental tools, e.g., for inspecting the properties and values applied to elements on your page, and making changes to them from editor.

## The DOM versus view source

Something that can trip up newcomers to DevTools is the difference between what you see when you [view the source](https://firefox-source-docs.mozilla.org/devtools-user/view_source/index.html) of a webpage, or look at the HTML file you put on the server, and what you can see in the [HTML pane](https://firefox-source-docs.mozilla.org/devtools-user/page_inspector/ui_tour/index.html#html-pane) of the DevTools. While it looks roughly similar to what you can see via View Source there are some differences.

In the rendered DOM the browser may have normalized the HTML, for example by correcting some badly-written HTML for you. If you incorrectly closed an element, for instance by opening a h2 but closing an h3, the browser will figure out what you were meaning to do and the HTML in the DOM will correctly close the open h2 with an h2. The DOM will also show any changes made by JavaScript.

View source, in comparison, is the HTML source code as stored on the server. The [HTML tree](https://firefox-source-docs.mozilla.org/devtools-user/page_inspector/how_to/examine_and_edit_html/index.html#html-tree) in your DevTools shows exactly what the browser is rendering at any given time, so it gives you an insight into what is really going on.

## Inspecting the applied CSS

Select an element on your page, either by right/ctrl-clicking on it and selecting inspect, or selecting it from the HTML tree on the left of the DevTools display. Try selecting the element with the class of box1; this is the first element on the page with a bordered box drawn around it.

![inspectingEx1](/images/inspectingEx.png)

If you look at the [Rules view](https://firefox-source-docs.mozilla.org/devtools-user/page_inspector/ui_tour/index.html#rules-view) to the right of your HTML, you should be able to see the CSS properties and values applied to that element. You will see the rules directly applied to class box1 and also the CSS that is being inherited by the box from its ancestors, in this case from body. This is useful if you are seeing some CSS being applied that you didn't expect. Perhaps it is being inherited from a parent element and you need to add a rule to overwrite it in the context of this element.

Also useful is the ability to expand out shorthand properties. In our example the margin shorthand is used.

Click on the little arrow to expand the view, showing the different loghand properties and their values.

You can toggle values in the Rules view on and off when that panel is active -if you hold your mouse over it, checkboxes will appear. Uncheck a rule's checkbox, for example border-radius, and the CSS will stop applying.

You can use this to do an A/B comparison, deciding if something looks better with a rule applied or not, and also to help debug it -for example, if a layout is going wrong and you are trying to work out which property is causing the problem.

## Editing values

In addition to turning properties on and off, you can edit their values. Perhaps you want to see if another color looks better, or wish to tweak the size of something? DevTools can save you a lot of time editing a stylesheet and reloading the page.

With box1 select, click on the watch (the small colored circle) that shows the color applied to the border. A color picker will open up and you can try out some different colors; these will update in real time on the page. In a similar fashion, you could change the width or style of the border.

![](/images/inspecting2-color-picker.png)

## Adding a new property

You can add properties using the DevTools. Perhaps you have realized that you don't want your box to inherit the body element's font size, and want to set its own specific size? You can try this out in DevTools before adding it to your CSS file.

You can click the closing curly brace in the rule to start entering a new declaration into it, at which point you can strat typing the new property and DevTools will show you an autocomplete list of matching properties. After selecting font-size, enter the value you want to try. You can also click the + button to add an additional rule with the same selector, and add your new rules there.

![](/images/inspecting3-font-size.png)

## Understanding the box model

In previous doc we have discussed the Box Model, and the fact that we have an alternate box model that changes how the size of elements are calculated based on the size you give them, plus the padding and borders. DevTools can really help you to understand how the size of an element is being calculated.

The [layout view](https://firefox-source-docs.mozilla.org/devtools-user/page_inspector/ui_tour/index.html#layout-view) shows you a diagram of the box model on the selected element, along with a description of the properties and values that change how the element is laid out. This includes a description of properties that you may not have explictly used on the element, but which do have initial values set.

In this panel, one of the detailed properties is the box-sizing property, which controls what box model the element uses.

Compare two boxes with classes box1 and box2. They both have the same width applied (400px), however box1 is visually wider. You can see in the layout panel that it is using content-box. This is the value that takes the size you give the element and then adds on the padding and border width.

The element with a class of box2 is using border-box, so here the padding and border is subtracted from the size that you have given the element. This means that the space taken up on the page by the box is the extact size that you specified -in our case width: 400px.

![](/images/inspecting4-box-model.png)


## Solving specificity issues

Sometimes during development, but in particular when you need to edit the CSS on an existing site, you will find yourself having a hard time getting some CSS to apply. No matter what you do, the element just doesn't seem to take the CSS. What is generally happening here is that a more specific selector is overriding your changes, and here DevTools will really help you out.

In our example file there are two words that have been wrapped in a em element. One is displaying as orange and the other hotpink. In the CSS we have applied:

```
em {
  color: hotpink;
  font-weight: bold;
}
```

Above that in the stylesheet however is a rule with a .special selector:

```
.special {
  color: orange;
}
```

As you will recall from the lesson on cascade and inheritance where we discussed specificity, class selectors are more specific than element selectors, and so this is the value that applies. DevTools can help you find such issues, especially if the information is buried somewhere in a huge stylesheet.

Inspect the em with the class of .special and DevTools will show you that orange is the color that applies, and also that the color property applied to the em is crossed out. You can now see that the class selector is overriding the element selector.

![](/images/inspecting5-specificity.png)

## Debugging problems in CSS

DevTools can be a great help when solving CSS problems, so when you find yourself in a situation where CSS isn't behaving as you expect, how should you go about solving it? The following steps should help.

### Take a setp back from the problem

Any coding problem can be frustrating, especially CSS problems because you often don't get an error message to search for online to help with finding a solution. If you are becoming frustrated, take a step away from the issue for a while -go for a walk, grab a drink, chat to a co-worker, or work on some other thing for a while. Sometimes the solution magically appears when you stop thinking about the problem, and even if not, working on it when feeling refreshed will be much easier.

### Do you have valid HTML and CSS?

Browsers expect your CSS and HTML to be correctly written, however browsers are also very forgiving and will try their best to display your webpages even if you have error in the markup or stylesheet. If you have mistakes in your code the browser needs to make a guess at what you meant, and it might make a different decision to what you had in mind. In addition, two differente browsers might cope with the problem in two different ways. A good first step, therefore, is to run your HTML and CSS through a validator, to pick up and fix any errors.

- [CSS Validator](https://jigsaw.w3.org/css-validator/)
- [HTML validator](https://validator.w3.org/)

### Are the property and value supported by the browser you are testing in?

Browsers ignore CSS they don't understand. If the property or value you are using is not supported by the browser you are testing in then nothing will break, but that CSS won't be applied. DevTools will generally highlight unsupported properties and values in some way. In the screenshot below the browser does not support the subgrid value of grid-template-columns.

![](/images/no-support.png)

You can also take a look at the browser compatibility tables at the bottom of each property page on MDN. These show you browser support for that property, often broken down if there is support for some usage of the property and not others.

### Is something else overriding your CSS?

This is where the information you have learned about specificity will come into much use. If you have something more specific overriding what you are trying to do, you can enter into a very frustrating game of trying to work out what. However, as described above, DevTools will show you what CSS is applying and you can work out how to make the new selector specific enough to override it.

### Make a reduced test case of the problem

If the issue isn't solved by the steps above, then you will need to do some more investigating. The best thing to do at this point is to create something known as a reduced test case. Being able to "reduce an issue" is a really useful skill. It will help you find problems in your own code and that of your colleagues, and will also enable report bugs and ask for help more effectively.

A reduced test case ia code example that demostrates the problem in the simplest possible way, with unrelated surrounding content and styling removed. This will often mean taking the problematic code out of your layout to make a small example which only shows that code or feature.

To create a reduced test case:

1. If your markup is dynamically generated -for example via CMS- make a static version of the output that shows the problem. A code sharing site like CodePen is useful for hosting reduced test cases, as then they are accessible online and you can easily share them with colleagues. You should start by doing View Source on the page and copying the HTML into CodePen, then grab any relevant CSS and JavaScript and include it too. After that, you can check whether the issue is still evident.

2. If removing the JavaScript does not make the issue go away, don't include the JavaScript. If removing the JavaScript does make the issue go away, then remove as much JavaScript as you can, leaving in whatever causes the issue.

3. Remove any HTML that does not contribute to the issue. Remove components or even main elements of the layout. Again, try to get down to the smallest amount of code that still shows the issue.

4. Remove any CSS that doesn't impact the issue.

In the process of doing this, you may discover what is causing the problem, or at least be able to turn it on and off by removing something specific. It is worth adding some components to your code as you discover things. If you need to ask for help, they will show the person helping you what you have already tried. This may well give you enough information to be able to search for likely problems and workarounds.

If you are still struggling to fix the problem then having a reduced test case gives you something to ask for help with, by posting to a forum, or showing to a co-worker. You are much more likely to get help if you can show that you have done the work of reducing the problem and identifying exactly where it happens, before asking for help. A more experienced developer might be able to quickly spot the problem and point you in the right direction, and even if not, your reduced test case will enable them to have a quick look and hopefully be able to offer at least some help.

As you become more experienced with CSS, you will find that you get faster at figuring out issues. However, even the most experienced of us sometimes find ourselves wondering what on earth is going on. Taking a methodical approach, making a reduced test case, and explaining the issue to someone else will usually result in a fix being found.

## Organizing your CSS

As you start to work on larger stylesheets and big projects you will discover that maintaining a huge CSS file can be challenging. In this article we will take a brief look at some best practices for writing your CSS to make it easily maintainable, and some of the solutions you will find in use by others to help improve maintainability.

## Tips to keep your CSS tidy

Here are some general suggestions for ways to keep your stylesheets organized and tidy.

### Does your project have a coding style guide?

If you are working with a team on an existing project, the first thing to check is whether the project has an existing style guide for CSS. The team style guide should always win over your own personal preferences. There often isn't a right or wrong way to do things, but consistency is important.

For example, have a look at the [CSS guidelines for MDN code examples](https://developer.mozilla.org/en-US/docs/MDN/Writing_guidelines/Writing_style_guide/Code_style_guide/CSS)

### Keep it consistent

If you get to set the rules for the project or are working alone, then the most important thing to do is to keep things consistent. Consistency can be applied in all sorts of ways, such as using the same naming conventions for classes, choosing one method of describing color, or maintaining consistent formatting. (For example, will you use tabs or spaces to indent your code? If spaces, how many spaces?)

Having a set of rules you always follow reduces the amount of mental overhead needed when writing CSS, as some of the decisions are already made.

## Formatting readable CSS

There are a couple of ways you will see CSS formatted. Some developers put all of the rules onto a single line, like so:

```
.box {background-color: #567895; }
h2 {background-color: black; color: white; }
```

Other developers prefer to break everything onto a new line:

```
.box {
  background-color: #567895;
}

h2 {
  background-color: black;
  color: white;
}
```

CSS doesn't mind which one you use. We perrsonally find it is more readable to have each property and value pair on a new line.

## Comment your CSS

Adding comments to your CSS will help any future developer work with your CSS file, but will also help you when you come back to the project after a break.

```
/* This is a CSS comment
It can be broken onto multiple lines. */
```

A good tip is to add a block of comments between logical sections in your stylesheet too, to help locate different sections quickly when scanning it, or even to give you something to search for to jump right into that part of the CSS. If you use a string that won't appear in the code, you can jump from section to section by searching for it -below we have used ||.

```
/* || General styles */

/* … */

/* || Typography */

/* … */

/* || Header and Main Navigation */

/* … */
```

You don't need to comment every single thing in your CSS, as much of it will be self-explanatory. What you should comment are the things where you made a particular decision for a reason.

You may have used a CSS property in a specific way to get around older browser incompatibilities, for example:

```
.box {
  background-color: red; /* fallback for older browsers that don't support gradients */
  background-image: linear-gradient(to right, #ff0000, #aa0000);
}
```

You don't need to comment every single thing in your CSS, as much of it will be self-explanatory. What you should comment are the things where you made a particular decision for a reason.

You may have used a CSS property in a specific way to get around older browser incompatibilities, for example:

```
.box {
  background-color: red; /* fallback for older browsers that don't support gradients */
  background-image: linear-gradient(to right, #ff0000, #aa0000);
}
```

Perhaps you followed a tutorial to achieve something, and the CSS isn't very self-explanatory or recognizable. In that case, you could add the URL of the tutorial to the comments. You will thank yourself when you come back to this project in a year or so and can vaguely remember that there was a great tutorial about that thing, but can't recall where it's from.


## Create logical sections in your stylesheet

It's a good idea to have all of the common styling first in the stylesheet. This means all of the styles which will generally apply unless you do something special with that element. You will typically have rules set up for:

- body
- p
- h1, h2, h3, h4, h5
- ul and ol
- The ***table*** properties
- links

In this section of the stylesheet we are providing default styling for the type on the site, setting up a default style for data tables and lists and so on.

```
/* || GENERAL STYLES */

body {
  /* … */
}

h1,
h2,
h3,
h4 {
  /* … */
}

ul {
  /* … */
}

blockquote {
  /* … */
}
```

After this section, we could define a few utility classes, for example, a class that removes the default list style for lists we're going to display as flex items or in some other way. If you have a few styling choices you know you will want to apply to lots of different elements, they can be put in this section.

```
/* || UTILITIES */

.nobullets {
  list-style: none;
  margin: 0;
  padding: 0;
}

/* … */
```

Then we can add everything that is used sitewide. That might be things like the basic page layout, navigation styling, and so on.

```
/* || SITEWIDE */

.main-nav {
  /* … */
}

.logo {
  /* … */
}
```

Finally, we will include CSS for specific things, broken down by the context, page, or even component in which they are used.

```
/* || STORE PAGES */

.product-listing {
  /* … */
}

.product-box {
  /* … */
}
```

By ordering things in this way, we at least have an idea in which part of the stylesheet we will be looking for something that we want to change.

## Avoid overly-specific selectors

If you create very specific selectors, you will often find that you need to duplicate chunks of your CSS to apply the same rules to another element. For example, you might have something like the below selector, which applies the rule to a ***p*** with a class of ***box*** inside an ***article*** with a class of ***main***.

```
article.main p.box {
  border: 1px solid #ccc;
}
```

If you then wanted to apply the same rules to something outside of main, or to something other than a p, you would have to add another selector to these rules or create a whole new ruleset. Instead, you could use the selector .box to apply your rule to any element that has the class box:

```
.box {
  border: 1px solid #ccc;
}
```

There will be times when making something more specific makes sense; however, this will generally be an exception rather than usual practice.

## Break large stylesheets into multiple smaller ones

In cases where you have very different styles for distinct parts of the site, you might want to have one stylesheet that includes all the global rules, as well as some smaller stylesheets that include the specific rules needed for those sections. You can link to multiple stylesheets from one page, and the normal rules of the cascade apply, with rules in stylesheets linked later coming after rules in stylesheets linked earlier.

For example, we might have an online stores as part of the site, with a lot of CSS used only for styling the product listings and forms needed for the store. It would make sense to have those things in a different stylesheet, only linked to on store pages.

This can make it easier to keep your CSS organized, and also means that if multiple people are working on the CSS, you will have fewer situations where two people need to work on the same stylesheet at once, leading to conflicts in source control.

# Other tools that can help

CSS itself doesn't have much in the way of in-built organization; therefore, the level of consistency in your CSS will largely depend on you. The web community has developed various tools and approaches that can help you to manage larger CSS projects. Since you are likely to come across these aids when working with other people, and since they are often of help generally, we've included a short guide to some of them.

## CSS methodologies

Instead of needing to come up with your own rules for writing CSS, you may benefit from adopting one of the approaches already designed by the community and tested across many projects. These methodologies are essentially CSS coding guides that take a very structured approach to writing and organizing CSS. Typically they tend to render CSS more verbosely than you might have if you wrote and optimized every selector to a custom set of rules for that project.

However, you do gain a lot of structure by adopting one. Since many of these systems are widely used, other developers are more likely to understand the approach you are using and be able to write their own CSS in the same way, rather than having to work out your own personal methodology from scratch.

### OOCSS

Most of the approaches you will encounter owe something to the concept of Object Oriented CSS (OOCSS), an approach made popular by the work of [Nicole Sullivan](https://github.com/stubbornella/oocss/wiki). The basic idea of OOCSS is to separate your CSS into reusable objects, which can be used anywhere you need on your site. The standard example of OOCSS is the pattern described as [The Media Object](https://developer.mozilla.org/en-US/docs/Web/CSS/Layout_cookbook/Media_objects). This is a pattern with a fixed size image, video or other element on one side, and flexible content on the other. It's a pattern we see all over websites for comments, listings, and so on.

If you are not taking an OOCSS approach you might create a custom CSS for the different places this pattern is used, for example, by creating two classes, one called ***comment*** with a bunch of rules for the component parts, and another called ***list-item*** with almost the same rules as the ***comment*** class except for some tiny differences. The differences between these two components are the list-item has a bottom orderd, and images in comments have a border whereas list-item images do not.

```
.comment {
  display: grid;
  grid-template-columns: 1fr 3fr;
}

.comment img {
  border: 1px solid grey;
}

.comment .content {
  font-size: 0.8rem;
}

.list-item {
  display: grid;
  grid-template-columns: 1fr 3fr;
  border-bottom: 1px solid grey;
}

.list-item .content {
  font-size: 0.8rem;
}
```

In OOCSS, you would create one pattern called ***media*** that would have all of the common CSS for both patterns -a base class for things that are generally the shape of the media object. Then we'd add an additional class to deal with those tiny differences, thus extending that styling in specific ways.

```
.media {
  display: grid;
  grid-template-columns: 1fr 3fr;
}

.media .content {
  font-size: 0.8rem;
}

.comment img {
  border: 1px solid grey;
}

.list-item {
  border-bottom: 1px solid grey;
}
```

In your HTML, the comment would need both the ***media*** and ***comment*** classes applied:

```
<div class="media comment">
  <img src="" alt="" />
  <div class="content"></div>
</div>
```

The list-item would have ***media*** and ***list-item*** applied:

```
<ul>
  <li class="media list-item">
    <img src="" alt="" />
    <div class="content"></div>
  </li>
</ul>
```

The work that Nicole Sullivan did in describing this approach and promoting it means that even people who are not strictly following an OOCSS approach today will generally be reusing CSS in this way -it has entered our understanding as a good way to approach things in general.

## BEM

BEM stands for Block Element Modifier. In BEM a block is a stand-alone entity such as a button, menu, or logo. An element is something like a list item or a title that is tied to the block it is in. A modifier is a flag on a block or element that changes the styling or behavior. You will be able to recognize code that uses BEM due to the extensive use of dashes and underscores in the CSS classes. For example, look at the classes applied to this HTML from the page about [BEM naming conventions](http://getbem.com/naming/).

```
<form class="form form--theme-xmas form--simple">
  <label class="label form__label" for="inputId"></label>
  <input class="form__input" type="text" id="inputId" />

  <input
    class="form__submit form__submit--disabled"
    type="submit"
    value="Submit" />
</form>
```

The additional classes are similar to those used in the OOCSS example; however, they use the stric naming conventions of BEM.

BEM is widely used in larger web projects and many people write their CSS in this way. It is likely that you will come across examples, even in tutorials, that use BEM syntax, without mentioning why the CSS is structured in such a way.
Read more about this system [BEM 101](https://css-tricks.com/bem-101/) on CSS tricks.

## Other common systems

There are a larger number of these systems in use. Other popular approaches include [Scalable and Modular Architecture for CSS (SMACSS)](http://smacss.com/), created by Jonathan Snook, [ITCSS](https://itcss.io/) from Harry Roberts, and [Atomic CSS (ACSS)](https://acss.io/), originally created by Yahoo!. If you come across a project that uses one of these approaches, then the advantage is that you will be able to search and find many articles and guides to help you understand how to code in the same style.

The disadvantage of using such a system is that they can seem overly complex, especially for smaller projects.

## Build systems for CSS

Another way to organize CSS is to take advantage of some of the tooling that is available for front-end developers, which allows you to take a slightly more programmatic approach to writing CSS. There are a number of tools, which we refer to as pre-processors and post-processors. A pre-processor runs over your raw files and turns them into a stylesheet, whereas a post-processor takes your finished stylesheet and does something to it -perhaps to optimize it in order that it will load faster.

Using any of these tools will require that your development environment be able to run scripts that do the pre- and post- processing. Many code editors can do this for you, or you can install command line tools to help.

The most popular pre-processor is [Sass](https://sass-lang.com/). This is not a Sass tutorial, so I will briefly explain a couple of the things that Sass can do, which are really helpful in terms of organization even if you don't use any of the other Sass features. If you want to learn a lot more about Sass, start with the [Sass basics](https://sass-lang.com/guide) article, then move on to their documentation.

## Defining variables

CSS now has native [custom properties](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties), making this feature increasingly less important. However, one of the reasons you might use Sass is to be able to define all of the colors and fonts used in a project as settings, then to use that variable around the project. This means that if you realize you have used the wrong shade of blue, you only need change it in one place.

If we created a variable called ***$base-color***, as in the first line below, we could then use it through the stylesheet anywhere that required that color.

```
$base-color: #c6538c;

.alert {
  border: 1px solid $base-color;
}
```

Once compiled to CSS, you would end up with the following CSS in the final stylesheet.

```
.alert {
  border: 1px solid #c6538c;
}
```

## Compiling component stylesheets

I mentioned above that one way to organize CSS is to break down stylesheets into smaller stylesheets. When using Sass you can take this to another level and have lots of very small stylesheets -even going as far as having a separate stylesheet for each component. By using the included functionality in Sass (partials), these can all be compiled together into one or a small number of stylesheets to actually link into your website.

So, for example, with [partials](https://sass-lang.com/documentation/at-rules/use#partials), you could have several style files inside a directory, say foundation/_code.scss, foundation/_lists.scss, foundation/_footer.scss, foundation/_links.scss, etc. You could then use  the Sass @use rule to load them into other stylesheets:

```
// foundation/_index.scss
@use "code";
@use "lists";
@use "footer";
@use "links";
```

If the partials are all loaded into an index file, as implied above, you can then load that entire directory into another stylesheet in one go:

```
// style.scss
@use "foundation";
```

### Post-processing for optimization

If you are concerned about adding size to oyur stylesheets, for example, by adding a lot of additional comments and whitespace, then a post-processing step could be to optimize the CSS by stripping out anything unnecessary in the production version. An example of a post-processor solution for doing this would be [cssnano](https://cssnano.co/).

# Flexbox

Flexbox is a one-dimensional layout method for arranging items in rows or columns. Items flex (expand) to fill additional space or shrink to fit into smaller spaces. This article explains all the fundamentals.

## Why flexbox?

For a long time, the only reliable cross-browser compatible tools available for creating CSS layouts were features like [floats](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Floats) and [positioning](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Positioning). These work, but in some ways they're also limiting and frustrating.

The following simple layout designs are either difficult or impossible to achieve with such tools in any kind of convenient, flexible way:

- Vertically centering a block of content inside its parent.

- Making all the children of a container take up an equal amount of the available width/height, regardless of how much width/height is available.

- Making all columns in a multiple-column layout adopt the same height even if they contain a different amount of content.

## Introducing a simple example

In this article, you'll work through a series of exercises to help you understand how flexbox works. To get started, you should make a local copy of the first starter file - [flexbox0.html](https://github.com/mdn/learning-area/blob/main/css/css-layout/flexbox/flexbox0.html) from our GitHub repo. Load it in a modern browser (like firefox or chrome) and have a look at the code in your code editor. 

![](/images/bih741v.png)

You'll see that we have a ***header*** element with a top level heading inside it and a ***section*** element containing three ***article***s. We're going to use these to create a fairly standard three column layout.

## Specifying what elements to lay out as flexible boxes

To start with, we need to select which elements are to be laid out as flexible boxes. To do this, we set a special value of ***display*** on the parent element of the elements you want to affect. In this case we want to lay out the ***article*** elements, so we set this on the ***section***:

```
section {
  display: flex;
}
```

This causes the section element to become a flex container and its children to become flex items. The result of this should be something like so:

![](/images/flexbox-example2.png)

So, this single declaration gives us everything we need. Incredible, right? We have our multiple column layout with equal-sized columns, and the columns are all the same height. This is because the default values given to flex items (the children of the flex container) are set up to solve common problems such as this.

To be clear, let's reiterate what is happening here. The element we've given a ***display*** value of ***flex*** to is acting like a block-level element in terms of how it interacts with the rest of the page, but its children are laid out as flex items. The next section will explain in more detail what this means. Note also that you can use a ***display*** value of ***inline-flex*** if you wish to lay out an element's children as flex items, but have that element behave like an inline element.

## The flex model

When elements are laid out as flex items, they are laid out along two axes:

![](/images/flex_terms.png)

- The ***main axis*** is the axis running in the direction the flex items are laid out in (for example, as a row across the page, or a column down the page.) The start and end of this axis are called the ***main start*** and ***main end***.

- The ***cross axis*** is the axis running perpendicular to the direcion the flex items are laid out in. The start and end of this axis are called the ***cross start*** and ***cross end***.

- The parent element that has ***display: flex*** set on it (the section in our example) is called the ***flex container***.

- The items laid out as flexible boxes inside the flex container are called ***flex items*** (the article elements in our example).

Bear this terminology in mind as you go through subsequent sections. You can always refer back to it if you get confused about any of the terms being used.

## Columns or rows?

Flexbox provides a property called ***flex-direction*** that specifies which direction the main axis runs (which direction the flexbox children are laid out in). By default this is set to ***row***, which causes them to be laid out in a row in the direction your browser's default language works in (left to right, in the case of an English browser).

Try adding the followin declaration to your section rule:

```
flex-direction: column;
```

You'll see that this puts the item back in a column layout, much like they were before we added any CSS. Before you move on, delete this declaration from your example.

## Wrapping

One issue that arises when you have a fixed width or height in your layout is that eventually your flexbox children will overflow their container, breaking the layout. Have a look at our flexbox-wrap0.html example and try viewing it live (take a local copy of this file now if you want to follow along with this example):

![](/images/flexbox-example3.png)

Here we see that the children are indeed breaking out of their container. One way in which you can fix this is to add the followin declaration to your section rule:

```
flex-wrap: wrap;
```

Also, add the following declaration to your article rule:

```
flex: 200px;
```

Try this now. You'll see that the layout looks much better with this included:

![](/images/flexbox-example4.png)

We now have multiple rows. Each row has as many flexbox children fitted into it as is sensible. Any overflow is moved down to the next line. The flex: 200px declaration set on the articles means that each will be at least 200px wide. We'll discuss this property in more detail later on. You might also notice that the last few children on the last row are each made wider so that the entire row is still filled.

But there's more we can do here. First of all, try changing your [flex-direction](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-direction) property value to ***row-reverse***. Now you'll see that you still have your multiple row layout, but it starts from the opposite corner of the browser window and flows in reverse.

## Flex-flow shorthand

At this point it's worth nothing that a shorthand exists for [flex-direction](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-direction) and [flex-wrap](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-wrap) : [flex-flow](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-flow). So, for example, you can replace: 

```
flex-direction: row;
flex-wrap: wrap;
```
with

```
flex-flow: row wrap;
```

## Grids

CSS grid layout is a two-dimensional layout system for the web. It lets you lay content out in rows and columns. It has many features that make building complex layouts straightforward.

### What is grid layout?

A grid is a collection of horizontal and vertical lines creating a pattern against which we can line up our design elements. They help us to create layouts in which our elements won't jump around or change width as we move from page to page, providing greater consistency on our websites.

A grid will typically have columns, rows, and then gaps between each row and column. The gaps are commonly regerred to as ***gutters***.

![](/images/grid.png)

## Creating your grid in CSS

Having decided on the grid that you design needs, you can use CSS grid layout to create it. We'll look at the basic features of grid layout first and then explore how to create a simple grid system for your project.

The following video provides a nice visual explanation of using CSS Grid https://youtu.be/KOvGeFUHAC0.

## Defining a grid

As a starting point, download and open [the starting point file](https://github.com/mdn/learning-area/blob/main/css/css-layout/grids/0-starting-point.html) in your text editor and browser (you can also [see it live here](https://mdn.github.io/learning-area/css/css-layout/grids/0-starting-point.html)). You will see an example with a container, which has some child items. These display in normal flow by default, so the boxes display one below the other. We'll be working with this file for the first part of this lesson, making changes to see how its grid behaves.

To define a grid we use the ***grid*** value of the ***display*** property. AS with Flexbox, this enables Grid Layout; all of the direct children of the container become grid items. Add this to the CSS inside your file:

```
.container {
  display: grid;
}
```

Unlike flexbox, the items will not immediately look any different. Declaring ***display: grid;*** gives you a one column grid, so your items will continue to display one below the other as they do in normal flow.

To see something that looks more grid-like, we'll need to add some columns to the grid. Let's add three 200-pixel columns. You can use any length unit or percentage to create these column tracks.

```
.container {
  display: grid;
  grid-template-columns: 200px 200px 200px;
}
```

Add the second declaration to your CSS rule, then reload the page. You should see that the items have rearranged themselves such that there's one in each cell of the grid.

![griEx2](/images/gridEx2.png)

## Flexible grids with the fr unit

In addition to creating grid using lengths and percentages, we can use ***fr***. The fr unit represents one fraction of the available space in the grid container to flexibly size grid rows and columns.

Change your track listing to the followin definition, creatine three ***1fr*** tracks:

```
.container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
}
```

You now have flexible tracks. The ***fr*** unit distributes space proportionally. You can specify different positive values for your tracks like so:

```
.container {
  display: grid;
  grid-template-columns: 2fr 1fr 1fr;
}
```

The first track gets ***2fr*** of the available space and the other two tracks get ***1fr***, making the first track larger. You can mix fr units with fixed length units. In this case, the space needed for the fixed tracks is used up first before the remaining space is distributed to ther other tracks.

![gridEx3](/images/gridEx3.png)

## Gaps between tracks

- [column-gap](https://developer.mozilla.org/en-US/docs/Web/CSS/column-gap) for gaps between columns
- [row-gap](https://developer.mozilla.org/en-US/docs/Web/CSS/row-gap) for gaps between rows
- [gap](https://developer.mozilla.org/en-US/docs/Web/CSS/gap) as a shorthand for both

```
.container {
  display: grid;
  grid-template-columns: 2fr 1fr 1fr;
  gap: 20px;
}
```

These gaps can be any length unit or percentage, but not an ***fr*** unit.

![](/images/gridEx4.png)

## Repeating track listings

You can repeat all of merely a section of your track listing using the CSS repeat() function. Change your track listing to the following:

```
.container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}
```

You'll now get three ***1fr*** tracks just as before. The first value passed to the ***repeat()*** function specifies the number of times you want the listing to repeat, while the second value is a track listing, which may be one or more tracks that you want to repeat.

## The implicit and explicit grid

We've only specified column tracks so far, yet rows are being created to hold our content. This is an example of the explicit versus the implicit grid.

The difference: 
- Explicit grid: created using ***grid-template-columns*** or ***grid-template-rows***.
- Implicit grid: Extends the defined explicit grid when content is placed outside of that grid, such as into our rows by drawing additional grid lines.

By default, tracks created in the implicit grid are ***auto*** sized, which in general means that they're large enough to accommodate their content. If you wish to give implicit grid tracks a size, you can use the [grid-auto-rows](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-auto-rows)  and [grid-auto-columns](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-auto-columns) properties. If you add grid-auto-rows with a value of 100px to your CSS, you'll see that those created rows are now 100 pixels tall.

```
.container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-auto-rows: 100px;
  gap: 20px;
}
```

![](/images/gridEx5.png)

## The minmax() function

Our 100-pixel tall tracks won't be very useful if we add content into those tracks that is taller than 100 pixels, in which case it would cause an overflow. It might be better to have tracks that are at least 100 pixels tall and can still expand if more content becomes added. A fairly basic fact about the web is that you never really know how tall something is going to be — additional content or larger font sizes can cause problems with designs that attempt to be pixel perfect in every dimension.

The [minmax()](https://developer.mozilla.org/en-US/docs/Web/CSS/minmax) function lets us set a minimum and maximum size for a track, for exmaple, ***minmax(100px, auto)***. The minimum size is 100 pixels, but the maximum is ***auto***, which will expand to accommodate more content. Try changing ***grid-auto-rows*** to use a minmax value:

```
.container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-auto-rows: minmax(100px, auto);
  gap: 20px;
}
```

If you add extra content, you'll see that the track expands to allow it to fit. Note that the expansion happens right along the row.

## As many columns as will fit

We can combine some of the lessons we've learned about track listing, repeat notation, and [minmax()](https://developer.mozilla.org/en-US/docs/Web/CSS/minmax) to create a useful pattern. Sometimes it's helpful to be able to ask grid to create as many columns as will fit into the container. We do this by setting the value of ***grid-template-columns*** using the [repeat()](https://developer.mozilla.org/en-US/docs/Web/CSS/repeat) function, but instead of passing in a number, pass in the keyword ***auto-fill***. For the second parameter of the function we use ***minmax()*** with a minimum value equal to the minimum track size that we would like to have and a maximum of ***1fr***.

```
.container {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  grid-auto-rows: minmax(100px, auto);
  gap: 20px;
}
```
![](/images/minmaxfunct.png)

This works because grid is creating as many 200-pixel columns as will fit into the container, then sharing whatever space is leftover among all the columns. The maximum is ***1fr*** which, as we already know, distributes space evenly between tracks.

## Line-based placement

We now move on from creating a grid to placing things on the grid. Our grid always has lines -these are numbered beginning with 1 and relate to the [writing mode](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Writing_Modes) of the document. For example, column line 1 in English (written left-to-right) would be on the left-hand side of the grid and row line 1 at the top, while in Arabic (written right-to-left), column line 1 would be on the right-hand side.

We can arrange things in accordance with these lines by specifying the start and end line. We do this using the following properties.

- [grid-column-start](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-column-start)
- [grid-column-end](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-column-end)
- [grid-row-start](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-row-start)
- [grid-row-end](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-row-end)

These properties can all have a line number as their value- You can also use the shorthand properties:

- [grid-column](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-column)
- [grid-row](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-row)

These let you specify the start and end lines at once, separated by a forward slash ***/***.

Let's instead arrange all of the elements for our site by using the grid lines. Add the following rules to the bottom of your CSS:

```
header {
  grid-column: 1 / 3;
  grid-row: 1;
}

article {
  grid-column: 2;
  grid-row: 2;
}

aside {
  grid-column: 1;
  grid-row: 2;
}

footer {
  grid-column: 1 / 3;
  grid-row: 3;
}
```

![](/images/gridEx6.png)

## Positioning with grid-template-areas

An alternative way to arrange items on your grid is to use the [grid-template-areas](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-areas) property and give the various elements of your design a name.

Remove the line-based positioning from the last example and add the following CSS.

```
.container {
  display: grid;
  grid-template-areas:
    "header header"
    "sidebar content"
    "footer footer";
  grid-template-columns: 1fr 3fr;
  gap: 20px;
}

header {
  grid-area: header;
}

article {
  grid-area: content;
}

aside {
  grid-area: sidebar;
}

footer {
  grid-area: footer;
}
```

Reload the page and you will see that your items have been placed just as before without us needing to use any line numbers!

![](/images/gridEx7.png)

The rules for ***grid-template-areas*** are as follows:

- You need to have every cell of the grid filled.
- To span across two cells, repeat the name.
- To leave a cell empty, use a . (period).
- Areas must be rectangular -for example, you can't have an L-shaped area.
- Areas can't be repeated in different locations.

You can play around with our layout, changing the footer to only sit underneath the article and the sidebar to span all the way down. This is a very nice way to describe a layout because it's clear just from looking at the CSS to know exactly what's happening.

## Grid frameworks in CSS grid

Grid "frameworks" tend to be based around 12 or 16 column grids. With CSS grid, you don't need any third party tool to give you such a framework -it's already there in the spec.

[Download the starting point file](https://github.com/mdn/learning-area/blob/main/css/css-layout/grids/11-grid-system-starting-point.html). This has a container with a 12-column grid defined and the same markup we used in the previous two examples. We can now use line-based placement to place our content on the 12-column grid.

```
header {
  grid-column: 1 / 13;
  grid-row: 1;
}

article {
  grid-column: 4 / 13;
  grid-row: 2;
}

aside {
  grid-column: 1 / 4;
  grid-row: 2;
}

footer {
  grid-column: 1 / 13;
  grid-row: 3;
}
```

![](/images/gridEx8.png)

If you use the [Fireforx Grid Inspector](https://firefox-source-docs.mozilla.org/devtools-user/page_inspector/how_to/examine_grid_layouts/index.html) to overlay the grid lines on your design, you can see how our 12-column grid works.

![](/images/GridEx9.png)


## Positioning 

Positioning allows you to take elements out of normal document flow and make them behave differently, for example, by sitting on top of one another or by always remaining in the same place inside the browser viewport.

### Introducing positioning

Positioning allows us to produce intereseting results by overriding normal document flow. What if you want to slightly alter the position of some boxes from their default flow position to give a slightly quircky, distressed feel? Positioning is your tool. Or what if you want to create a UI element that floats over the top of other parts of the page and/or always sits in the same place inside the browser window no matter how much the page is scrolled? Positioning makes such layout work possible.

There are a number of different types of positioning that you can put into effect on HTML elements. To make a specific type of positioning active on an element, we use the [position](https://developer.mozilla.org/en-US/docs/Web/CSS/position) property.

## Static positioning

Static positioning is the default that every element gets. It just means "put the element into its normal position in the document flow -nothing special to see here."

To see this (and get you example set up for the future sections) first add a ***class*** of ***positioned*** to the second ***p*** in the HTML:

```
<p class="positioned">…</p>
```

Now add the followin rule to the bottom of your CSS:

```
.positioned {
  position: static;
  background: yellow;
}
```

If you save and refresh, you'll see no difference at all, except for the updated background color of the 2nd paragraph. This is fine -as we said before, static positioning is the default behavior!

## Relative positioning

Relative positioning is the first position type we'll take a look at. This is very similar to static positioning, except that once the positioned element has taken its place in the normal flow, you can then modify its final position, including making it overlap other element on the page. Go ahead and update the ***position*** declaration in your code:

```
position: relative;
```

If you save and refresh at this stage, you won't see a change in the result at all. So how do you modify the element's position? You need to use the: top, bottom, left and right properties, which we'll explain in the next section.

## Introducing top, bottom, left, and right

[top](https://developer.mozilla.org/en-US/docs/Web/CSS/top), [bottom](https://developer.mozilla.org/en-US/docs/Web/CSS/bottom), [left](https://developer.mozilla.org/en-US/docs/Web/CSS/left) and [right](https://developer.mozilla.org/en-US/docs/Web/CSS/right) are used alongside [position](https://developer.mozilla.org/en-US/docs/Web/CSS/position) to specify exactly where to move the positioned element to. To try this out, add the following declarations to the ***.positioned*** rule in your CSS:

```
top: 30px;
left: 30px;
```

## Absolute positioning

setting position: absolute. 
Let's try changing the position declaration in your code as follows:

```
position: absolute;
```

If you now save and refresh, you should see something like so:

![absoluteEX](/images/absoluteEX.png)

First of all, note that the gap where the positioned element should be in the document flow is no longer there — the first and third elements have closed together like it no longer exists! Well, in a way, this is true. An absolutely positioned element no longer exists in the normal document flow. Instead, it sits on its own layer separate from everything else. This is very useful: it means that we can create isolated UI features that don't interfere with the layout of other elements on the page. For example, popup information boxes, control menus, rollover panels, UI features that can be dragged and dropped anywhere on the page, and so on.

Second, notice that the position of the element has changed. This is because top, bottom, left and right behave in a different way with absolute positioning. Rather than positioning the element based on its relative position within the normal document flow, they specify the distance the element should be from each of the containing element's sides. So in this case, we are saying that the absolutely positioned element should site 30px from the top of the "containing element" and 30px from the left. (In this case, the "containing element" is the ***initial containing block***)

## Positioning contexts

Which element is the "containing element" of an absolutely positioned element? This is very much dependent on the position property of the ancestors of the positioned element (See [Identifying the containing block](https://developer.mozilla.org/en-US/docs/Web/CSS/Containing_block#identifying_the_containing_block)).

If no ancestor elements have their position property explicitly defined, then by default all ancestor elements will have a static position. The result of this is the absolutely positioned element will be contained in the initial containing block. The initial containing block has the dimensions of the viewport and is also the block that contains the html element. In other words, the absolutely positioned element will be displayed outside of the html element and be positioned relative to the initial viewport.

The positioned element is nested inside the body in the HTML source, but in the final layout it's 30px away from the top and the left edges of the page. We can change the ***positioning context***, that is, which element the absolutely positioned element is positioned relative to. This is done by setting positioning on one of the element's ancestors: to one of the elements it's nested inside of (you can't position it relative to an element it's not nested inside of). To see this, add the following declaration to your ***body*** rule:

```
position: relative;
```

This should give the followin result:

![](/images/positionedEX.png)

The positioned element now sits relative to the body element.

## Introducing z-index

When elements start to overlap, what determines which elements appear over others and which elements appear under others? In the example we've seen so far, we only have one positioned element in the positioning context, and it appears on the top since positioned elements win over non-positioned elements. What about when we have more than one?

Try adding the following to your CSS to make the first paragraph absolutely positioned too:

```
p:nth-of-type(1) {
  position: absolute;
  background: lime;
  top: 10px;
  right: 30px;
}
```

At this point you'll see the first paragraph colored lime, moved out of the document flow, and positioned a bit above from where it originally was. It's also stacked below the original ***.positioned*** paragraph where the two overlap. This is because the ***.positioned*** paragraph is the second paragraph in the source order, and positioned elements later in the source order win over positioned elements earlier in the source order.

Can you change the stacking order? Yes, you can, by using the [z-index](https://developer.mozilla.org/en-US/docs/Web/CSS/z-index) property. "z-index" is a reference to the z-axis. You may recall from previous points in the course where we discussed web pages using horizontal (x-axis) and vertical (y-axis) coordinates to work out positioning for things like background images and drop shadow offsets. For languages that run left to right, (0,0) is at the top left of the page (or element), and the x- and y-axes run across to the right and down the page.

Web pages also have a z-axis: an imaginary line that runs from the surface of your screen towards your face (or whatever else you like to have in front of the screen). [z-index](https://developer.mozilla.org/en-US/docs/Web/CSS/z-index) values affect where positioned elements sit on that axis; positive values move them higher up the stack, negative values move them lower down the stack. By default, positioned elements all have a ***z-index*** of ***auto***, which is effectively 0.

To change the stacking order, try adding the following declaration to your ***p:nth-of-type(1)*** rule:

```
z-index: 1;
```

You should now see the lime paragraph on top:

![](/images/zindex.png)

Note that ***z-index*** only accepts unitless index values; you can't specify that you want one element to be 23 pixels up the Z-axis — it doesn't work like that. Higher values will go above lower values and it's up to you what values you use. Using values of 2 or 3 would give the same effect as values of 300 or 40000.

## Fixed positioning

This works in exactly the same way as absolute positioning, with one key difference: whereas absolute positioning fixes an element in place relative to its nearest positioned ancestor (the initial containing block if there isn't one), fixed positioning usually fixes an element in place relative to the visible portion of the viewport. (An exception to this occurs if one of the element's ancestors is a fixed containing block because its [transform property](https://developer.mozilla.org/en-US/docs/Web/CSS/transform) has a value other than none.) This means that you can create useful UI items that are fixed in place, like persistent navigation menus that are always visible no matter how much the page scrolls.

Let's put together a simple example to show what we mean. First of all, delete the existing ***p:nth-of-type(1)*** and ***.positioned*** rules from your CSS.

```
body {
  width: 500px;
  height: 1400px;
  margin: 0 auto;
}
```

Now we're going to give the h1 element ***position: fixed;*** and have it sit at the top of the viewport. Add the following rule to your CSS:

```
h1 {
  position: fixed;
  top: 0;
  width: 500px;
  margin-top: 0;
  background: white;
  padding: 10px;
}
```

The ***top:0;*** is required to make it stick to the top of the screen. We give the heading the same width as the content column and then a white background and some padding and margin so the content won't be visible underneath it.

If you save and refresh, you'll see a fun little effect of the heading staying fixed — the content appears to scroll up and disappear underneath it. But notice how some of the content is initially clipped under the heading. This is because the positioned heading no longer appears in the document flow, so the rest of the content moves up to the top. We could improve this by moving the paragraphs all down a bit. We can do this by setting some top margin on the first paragraph. Add this now:

```
p:nth-of-type(1) {
  margin-top: 60px;
}
```

You should now see the finished example:

![fixedPositioning](/images/fixedPositioning.png)

## Sticky positioning

There is another position value available called ***position: sticky***, which is somewhat newer than the others. This is basically a hybrid between relative and fixed position. It allows a positioned element to act like it's relatively positioned until it's scrolled to a certain threshold (e.g., 10px from the top of the viewport), after which it becomes fixed.

### Basic example

Sticky positioning can be used, for example, to cause a navigation bar to scroll with the page until a certain point and then stick to the top of the page.

```
.positioned {
 position: sticky;
 top: 30px;
 left: 30px;
}
```

![stickyEX](/images/stickyEX.png)

### Scrolling index

An interesting and common use of ***position: sticky*** is to create a scrolling index page where different headings stick to the top of the page as they react it. The markup for such an example might look like so:

```
<h1>Sticky positioning</h1>

<dl>
  <dt>A</dt>
  <dd>Apple</dd>
  <dd>Ant</dd>
  <dd>Altimeter</dd>
  <dd>Airplane</dd>
  <dt>B</dt>
  <dd>Bird</dd>
  <dd>Buzzard</dd>
  <dd>Bee</dd>
  <dd>Banana</dd>
  <dd>Beanstalk</dd>
  <dt>C</dt>
  <dd>Calculator</dd>
  <dd>Cane</dd>
  <dd>Camera</dd>
  <dd>Camel</dd>
  <dt>D</dt>
  <dd>Duck</dd>
  <dd>Dime</dd>
  <dd>Dipstick</dd>
  <dd>Drone</dd>
  <dt>E</dt>
  <dd>Egg</dd>
  <dd>Elephant</dd>
  <dd>Egret</dd>
</dl>
```

The CSS might look as follows. In normal flow the ***dt*** elements will scroll with the content. When we add ***position: sticky*** to the ***dt*** element, along with a ***top*** value of 0, supporting browsers will stick the headings to the top of the viewport as they react that position. Each subsequent header will then replace the previous one as it scrolls up to that position.

```
dt {
  background-color: black;
  color: white;
  padding: 10px;
  position: sticky;
  top: 0;
  left: 0;
  margin: 1em 0;
}
```

![stickyEX2](/images/stickyEX2.png)

Sticky elements are "sticky" relative to the nearest ancestor with a "scrolling mechanism", which is determined by its ancestor's position property.

## Multiple-column layout

The multiple-column layout specification provides you with a method for laying content out in columns, as you might see in a newspaper. This article explains how to use this feature.

### A three-column layout

Our starting point file contains some very simple HTML: a wrapper with a class of ***container***, inside of which is a heading and some paragraphs.

The ***div*** with a class of ***container*** will become our multicol container. We enable multicol by using one of two properties: [column-count](https://developer.mozilla.org/en-US/docs/Web/CSS/column-count) or [column-width](https://developer.mozilla.org/en-US/docs/Web/CSS/column-width). The ***column-count*** property takes a number as its value and creates that number of columns. If you add the following CSS to your stylesheet and reload the page, you'll get three columns:

```
.container {
  column-count: 3;
}
```

The columns that you create have flexible widths -the browser works out how much space to assign each column.

![](/images/multicolumns.png)

### Setting column-width

Change your CSS to use ***column-width*** as follows:

```
.container {
  column-width: 200px;
}
```

The browser will now give you as many columns as it can of the size that you specify; any remaining space is then shared between the existing columns. This means that you won't get exactly the width that you specify unless your container is exactly divisible by that width.

![](/images/multicolumns2.png)

## Styling the columns

The columns created by multicol cannot be styled individually. There's no way to make one column bigger than other columns or to change the background or text color of a single column. You have two opportunities to change the way that columns display:

- Changing the size of the gap between columns using the [column-gap](https://developer.mozilla.org/en-US/docs/Web/CSS/column-gap).
- Adding a rule between columns with [column-rule](https://developer.mozilla.org/en-US/docs/Web/CSS/column-rule).

Using your example above, change the size of the gap by adding a ***column-gap*** property. You can play around with different values -the property accepts any length unit.

Now add a rule between the columns with ***column-rule***. In a similar way to [border](https://developer.mozilla.org/en-US/docs/Web/CSS/border) property that you encountered in previous lessons, ***column-rule*** is a shorthand for [column-rule-color](https://developer.mozilla.org/en-US/docs/Web/CSS/column-rule-color), [column-rule-style](https://developer.mozilla.org/en-US/docs/Web/CSS/column-rule-style), and [column-rule-width](https://developer.mozilla.org/en-US/docs/Web/CSS/column-rule-width) and accepts the same values as ***border***.

```
.container {
  column-count: 3;
  column-gap: 20px;
  column-rule: 4px dotted rgb(79, 185, 227);
}
```

![](/images/multicolumns3.png)

Something to take note of is that the rule doesn't take up any width of its own. It lies across the gap you created with ***column-gap***. To make more space on either side of the rule, you'll need to increase the ***column-gap*** size.

## Spanning columns

You can cause an element to span across all the columns. In this case, the content breaks where the spanning element's introduced and then continues below the element, creating a new set of columns. To cause an element to span all the columns, specify the value of ***all*** for the [column-span](https://developer.mozilla.org/en-US/docs/Web/CSS/column-span) property.

Note: It isn't possible to cause an element to span just some columns. The property can only have the values of none (which is the default) or all.

![](/images/multicolumns4.png)

## Columns and fragmentation

The content of a multi-column layout is fragmented. It essentially behaves the same way as content behaves in paged media, such as when you print a webpage. When you turn your content into a multicol container, it fragments into columns. In order for the content to do this, it must break.

### Fragmented boxes

Sometimes, this breaking will happen in places that lead to a poor reading experience. In the example below, I have used multicol to lay out a series of boxes, each of which has a heading and some text inside. The heading becomes separated from the text if the columns fragment between the two.

```
<div class="container">
  <div class="card">
    <h2>I am the heading</h2>
    <p>
      Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla luctus
      aliquam dolor, eu lacinia lorem placerat vulputate. Duis felis orci,
      pulvinar id metus ut, rutrum luctus orci. Cras porttitor imperdiet nunc,
      at ultricies tellus laoreet sit amet. Sed auctor cursus massa at porta.
      Integer ligula ipsum, tristique sit amet orci vel, viverra egestas ligula.
    </p>
  </div>

  <div class="card">
    <h2>I am the heading</h2>
    <p>
      Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla luctus
      aliquam dolor, eu lacinia lorem placerat vulputate. Duis felis orci,
      pulvinar id metus ut, rutrum luctus orci. Cras porttitor imperdiet nunc,
      at ultricies tellus laoreet sit amet. Sed auctor cursus massa at porta.
      Integer ligula ipsum, tristique sit amet orci vel, viverra egestas ligula.
    </p>
  </div>

  <div class="card">
    <h2>I am the heading</h2>
    <p>
      Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla luctus
      aliquam dolor, eu lacinia lorem placerat vulputate. Duis felis orci,
      pulvinar id metus ut, rutrum luctus orci. Cras porttitor imperdiet nunc,
      at ultricies tellus laoreet sit amet. Sed auctor cursus massa at porta.
      Integer ligula ipsum, tristique sit amet orci vel, viverra egestas ligula.
    </p>
  </div>
```

´´´
.container {
  column-width: 250px;
  column-gap: 20px;
}

.card {
  background-color: rgb(207, 232, 220);
  border: 2px solid rgb(79, 185, 227);
  padding: 10px;
  margin: 0 0 1em 0;
}
´´´

![](/images/multicolumns5.png)

## Setting break-inside

To control this behavior, we can use properties from the [CSS Fragmentation](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Fragmentation) specification. This specification gives us properties to control the breaking of content in multicol and in paged media. For example, by adding the property [break-inside](https://developer.mozilla.org/en-US/docs/Web/CSS/break-inside) with a value of ***value*** to the rules for ***.card***. This is the container of the heading and text, so we don't want it fragmented.

```
.card {
  break-inside: avoid;
  background-color: rgb(207, 232, 220);
  border: 2px solid rgb(79, 185, 227);
  padding: 10px;
  margin: 0 0 1em 0;
}
```

The addition of this property causes the boxes to stay in one piece -they now do not fragment across the columns.

![](/images/multicolumns6.png)

## Responsive design

Responsive web design (RWD) is a web design approach to make web pages render well on all screen sizes and resolutions while ensuring good usability. It is the way to design for a multi-device web. 

HTML is fundamentally responsive, or fluid. If you create a web page containing only HTML, with no CSS, and resize the windows, the browser will automatically reflow the text to fit the viewport.

While the default responsive behavior may sound like no solution is needed, long lines of text displayed full screen on a wide monitor can be difficult to read. If wide screen line length is reduced with CSS, such as by creating columns or adding significant padding, the site may look squashed for the user who narrows their browser window or opens the site on a mobile device.

![](/images/responsiveEx1.png)

Creating a non-resizable web page by setting a fixed width doesn't work either; that leads to scroll bars on narrow devices and too much empty space on wide screens.

Responsive web design, or RWD, is a design approach that addresses the range of devices and device sizes, enabling automatic adaption to the screen, whether the content is viewed on a tablet, phone, television, or watch.

Responsive web design isn't a separate technology — it is an approach. It is a term used to describe a set of best practices used to create a layout that can respond to any device being used to view the content.

Modern CSS layout methods are inherently responsive, and, since the publication of Gillenwater's book and Marcotte's article, we have a multitude of features built into the web platform to make designing responsive sites easier.

The rest of this article will point you to the various web platform features you might want to use when creating a responsive site.

## Media Queries

[Media queries](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries) allow us to run a series of test (e.g. whether the user's screen is greater than a certain width, or a certain resolution) and apply CSS selectively to style the page appropriately for the user's needs.

For example, the followin media query tests to see if the current web page is being displayed as screen media (therefore not a printed document) and the viewport is at least ***80rem*** wide. The CSS for the ***.container*** selector will only be applied if these two things are true.

```
@media screen and (min-width: 80rem) {
  .container {
    margin: 1em 2em;
  }
}
```

You can add multiple media queries within a stylesheet, tweaking your whole layout or parts of it to best suit the various screen sizes. The points at which a media query is introduced, and the layout changed, are known as breakpoints.

A common approach when using Media Queries is to create a simple single-column layout for narrow-screen devices (e.g. mobile phones), then check for wider screens and implement a multiple-column layout when you know that you have enough screen width to handle it. Designing for mobile first is known as mobile first design.

If using breakpoints, best practices encourage defining media query breakpoints with [relative units](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Values_and_units#relative_length_units) rather than absolute sizes of an individual device.

There are different approaches to the styles defined within a media query block; ranging from using media queries to [link](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/link) style sheets based on browser size ranges to only including custom properties variables to store values associated with each breakpoint.

Media queries can help with RWD, but are not a requirement. Flexible grids, relative units, and minimum and maximum unit values can be used without queries.
Find out more in the MDN documentation for [Media Queries](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries).

## Responsive layout technologies

Responsive sites are built on flexible grids, meaning you don't need to target every possible device size with pixel perfect layouts.

By using a flexible grid, you can change a feature or add in a breakpoint and change the design at the point where the content starts to look bad. For example, to ensure line lengths don't become unreadably long as the screen size increases you can use [columns](https://developer.mozilla.org/en-US/docs/Web/CSS/columns); If a box becomes squashed with two words on each line as it narrows you can set a breakpoint.

Several layout methods, including [multiple-column-layout](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Multiple-column_Layout), [Flexbox](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Flexbox), and [Grid](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Grids) are responsive by default. They all assume that you are trying to create a flexible grid and give you easier ways to do so.

## Multicol

With multicol, you specify a ***column-count*** to indicate the maximum number of columns you want your content to be split into. The browser then works out the size of these, a size that will change according to the screen size.

```
.container [
  column-count: 3;
]
```

If you instead specify a ***column-width***, you are specifying a minimum width. The browser will create as many columns of that width as will comfortably fit into the container, then share out the remaining space between all the columns. Therefore the number of columns will change according to how much space there is.

```
.container {
  column-width: 10em;
}
```

You can use the [columns](https://developer.mozilla.org/en-US/docs/Web/CSS/columns) shorthand to provide a maximum number of columns and a minimum column width. This can ensure line lengths don't become unreadably long as the screen size increases or too narrow as the screen size decreases.

## Flexbox

In flexbox, flex items shrink or grow, distributing space between the items according to the space in their container. By changing the values for ***flex-grow*** and ***flex-shrink*** you can indicate how you want the items to behave when they encounter more or less space around them.

In the example below the flex items will each take an equal amount of space in the flex container, using the shorthand of ***flex: 1*** as described in the layout epic [Flexbox: flexible sizing of flex items](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Flexbox#flexible_sizing_of_flex_items).

```
.container {
  display: flex;
}

.item {
  flex: 1;
}
```

## CSS grid

In CSS Grid Layout the ***fr*** unit allows the distribution of available space across grid tracks. The next example creates a grid container with three tracks sized at ***1fr***. This will create three column tracks, each taking one part of the available space in the container. You can find out more about this approach to create a grid in the Learn Layout Grids topic, under [flexible grids with the fr unit](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Grids#flexible_grids_with_the_fr_unit).

## Responsive images

To ensure media is never larger than its responsive container, the following approach can be used:

```
img,
picture,
video {
  max-width: 100%;
}
```

This scales media to ensure they never overflow their containers. Using a single large image and scaling it down to fit small devices wastes bandwidth by downloading images larger than what is needed.

Responsive images, using the ***picture*** element and the ***img srcset*** and ***sizes*** attributes enables serving images targeted to the user's viewport and the device's resolution. For example, you can include a square image for mobile, but show the same scene as a landscape image on desktop.

The ***picture*** element enables providing multiple sizes along "hints" (metadata that describes the screen size and resolution the image is best suited for), and the browser will choose the most appropiate image for each device, ensuring that a user will download an image size appropiate for the device they are using. Using ***picture*** along with ***max-width*** removes the need for sizing images with media queries. It enables targeting miages with different aspect ratios to different viewport sizes.

You can also art direct images used at different sizes, thus providing a different crop or completely different image to different screen sizes.

## Responsive typography

Responsive typography describes changing font sizes within media queries or using viewport units to reflect lesser or greater amounts of screen real estate.

### Using media queries for responsive typography

In this example, we want to set our level 1 heading to be ***4rem***, meaning it will be four times our base font size. That's a really large heading! We only want this jumbo heading on larger screen sizes, therefore we first create a smaller heading then use media queries to overwrite it with the larger size if we know that the user has a screen size of at least ***1200px***.

```
html {
  font-size: 1em;
}

h1 {
  font-size: 2rem;
}

@media (min-width: 1200px) {
  h1 {
    font-size: 4rem;
  }
}
```

We have edited our responsive grid example above to also include responsive type using the method outlined. You can see how the heading switches sizes as the layout goes to the two column version.

On mobile the heading is smaller:

![](/images/responsiveEx2.png)

On desktop, however, we see the larger heading size:

![](/images/responsiveEx3.png)

As this approach to typography shows, you do not need to restrict media queries to only changing the layout of the page. They can be used to tweak any element to make it more usable or attractive at alternate screen sizes.

### Using viewport units for responsive typography

Viewport units ***vw*** can also be used to enable responsive typography, without the need for setting breakpoints with media queries. ***1vw*** is equal to one percent of the viewport width, meaning that if you set your font size using ***vw***, it will always relate to the size of the viewport.

```
h1 {
  font-size: 6vw;
}
```

The problem with doing the above is that the user loses the ability to zoom any text set using the ***vw*** unit, as that text is always related to the size of the viewport. **Therefore you should never set text using viewport units alone.**

There is a solution, and it involves using ***calc()***. If you add the ***vw*** unit to a value set using a fixed size such as ***em*** or ***rem*** then the text will still be zoomable. Essentially, the ***vw*** unit adds on top of that zoomed value:

```
h1 {
  font-size: calc(1.5rem + 3vw);
}
```

This means that we only need to specify the font size for the heading once, rather than set it up for mobile and redefine it in the media queries. The font then gradually increases as you increase the size of the viewport.

## The viewport meta tag

If you look at the HTML source of a responsive page, you will usually see the following ***meta*** tag in the ***head*** of the document.

```
<meta name="viewport" content="width=device-width,initial-scale=1" />
```

This [Viewport](https://developer.mozilla.org/en-US/docs/Web/HTML/Viewport_meta_tag) meta tag tells mobile browsers that they should set the width of the viewport to the device width, and scale the document to 100% of its intended size, which shows the document at the mobile-optimized size that you intended.

Why is this needed? Because mobile browsers tend to lie about their viewport width.

This meta tag exists because when smartphones first arrived, most sites were not mobile optimized. The mobile browser would, therefore, set the viewport width to 980 pixels, render the page at that width, and show the result as a zoomed-out version of the desktop layout. Users could zoom in and pan around the website to view the bits they were interested in, but it looked bad.

By setting ***width=device-width*** you are overriding a mobile device's default, like Apple's default ***width=980px***, with the actual width of the device. Without it, your responsive design with breakpoints and media queries may not work as intended on mobile browsers. If you've got a narrow screen layout that kicks in at 480px viewport width or less, but the device is saying it is 980px wide, that user will not see your narrow screen layout.

**So you should always include the viewport meta tag in the head of your documents.**

## Beginner's guide to media queries

The CSS Media Query gives you a way to apply CSS only when the browser and device environment matches a rule that you specify, for example "viewport is wider than 480 pixels". Media queries are a key part of responsive web design, as they allow you to create different layouts depending on the size of the viewport, but they can also be used to detect other things about the environment your site is running on, for example whether the user is using a touchscreen rather than a mouse.

## Media Query Basics

The simplest media query syntax looks like this:

```
@media media-type and (media-feature-rule) {
  /* CSS rules go here */
}
```

It consists of:

- A media type, which tells the browser what kind of media this code is for (e.g. print, or screen).

- A media expression, which is a rule, or test that must be passed for the contained CSS to be applied.

- A set of CSS rules that will be applied if the test passes and the media type is correct.

### Media types

The possible types of media you can specify are:

- all
- print
- screen

The following media query will only set the body to 12pt if the page is printed. It will not apply when the page is loaded in a browser.

```
@media print {
  body {
    font-size: 12pt;
  }
}
```

### Media feature rules

After specifying the type, you can then target a media feature with a rule.

#### Width and height

The feature we tend to detect most often in order to create responsive designs (and that has widespread browser support) is viewport width, and we can apply CSS if the viewport is above or below a certain width — or an exact width — using the ***min-width***, ***max-width***, and ***width*** media features.

These features are used to create layouts that respond to different screen sizes. For example, to change the body text color to red if the viewport is exactly 600 pixels, you would use the following media query.

```
@media screen and (width: 600px) {
  body {
    color: red;
  }
}
```

[Open this example](https://mdn.github.io/css-examples/learn/media-queries/width.html) in the browser or [view the source](https://github.com/mdn/css-examples/blob/main/learn/media-queries/width.html).

The ***width*** (and ***height***) media features can be used as ranges, and therefore be prefixed with ***min-*** or ***max-*** to indicate that the given value is a minimun, or a maximum. For example, to make the color blue if the viewport is 600 pixels or narrower, use ***max-width***:

```
@media screen and (max-width: 600px) {
  body {
    color: blue;
  }
}
```

[Open this example](https://mdn.github.io/css-examples/learn/media-queries/max-width.html) in the browser, or [view the source](https://github.com/mdn/css-examples/blob/main/learn/media-queries/max-width.html).

In practice, using minimum or maximum values is much more useful for responsive design so you will rarely see ***width*** or ***height*** used alone.

There are many other media features that you can test for, although some of the newer features introduced in Levels 4 and 5 of the media queries specification have limited browser support. Each feature is documented on MDN along with browser support information, and you can find a complete list at [Using Media Queries: Syntax](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries#syntax).

#### Orientation

One well-supported media feature is ***orientation***, which allows us to test for portrait or landscape mode. To change the body text color if the device is in landscape orientation, use the following media query.

```
@media (orientation: landscape) {
  body {
    color: rebeccapurple;
  }
}
```

[Open this example](https://mdn.github.io/css-examples/learn/media-queries/orientation.html) in the browser, or [view the source](https://github.com/mdn/css-examples/blob/main/learn/media-queries/orientation.html).

A standard desktop view has a landscape orientation, and a design that works well in this orientation may not work as well when viewed on a phone or tablet in portrait mode. Testing for orientation can help you to create a layout which is optimized for devices in portrait mode.

#### Use of pointing devices

As part of the Level 4 specification, the ***hover*** media feature was introduced. This feature means you can test if the user has the ability to hover over an element, which essentially means they are using some kind of pointing device; touchscreen and keyboard navigation does not hover.

```
@media (hover: hover) {
  body {
    color: rebeccapurple;
  }
}
```

[Open this example](https://mdn.github.io/css-examples/learn/media-queries/hover.html) in the browser, or [view the source](https://github.com/mdn/css-examples/blob/main/learn/media-queries/hover.html).

If we know the user cannot hover, we could display some interactive features by default. For users who can hover, we might choose to make them available when a link is hovered over.

Also in Level 4 is the ***pointer*** media feature. This takes three possible values, ***none***, ***fine*** and ***coarse***. A ***fine*** pointer is something like a mouse or trackpad. It enables the user to precisely target a small area. A ***coarse*** pointer is your finger on a touchscreen. The value ***none***means the user has no pointing device; perhaps they are navigating with the keyboard only or with voice commands.

Using ***pointer*** can help you to design better interfaces that respond to the type of interaction a user is having with a screen. For example, you could create larger hit areas if you know that the user is interacting with the device as a touchscreen.

## More complex media queries

With all of the different possible media queries, you may want to combine them, or create lists of queries — any of which could be matched.

### "and" logic in media queries

To combine media features you can use ***and*** in much the same way as we have used ***and*** above to combine a media type and feature. For example, we might want to test for a ***min-width*** and ***orientation***. The body text will only be blue if the viewport is at least 600 pixels wide and the device is in landscape mode.

```
@media screen and (min-width: 600px) and (orientation: landscape) {
  body {
    color: blue;
  }
}
```

### "or" logic in media queries

If you have a set of queries, any of which could match, then you can comma separate these queries. In the below example the text will be blue if the viewport is at least 600 pixels wide OR the device is in landscape orientation. If either of these things are true the query matches.

```
@media screen and (min-width: 600px), screen and (orientation: landscape) {
  body {
    color: blue;
  }
}
```

### "not" logic in media queries

You can negate an entire media query by using the ***not*** operator. This reverses the meaning of the entire media query. Therefore in this next example the text will only be blue if the orientation is portrait.

```
@media not all and (orientation: landscape) {
  body {
    color: blue;
  }
}
```

## How to choose breakpoints

In the early days of responsive design, many designers would attempt to target very specific screen sizes. Lists of the sizes of the screens of popular phones and tablets were published in order that designs could be created to neatly match those viewports.

There are now far too many devices, with a huge variety of sizes, to make that feasible. This means that instead of targeting specific sizes for all designs, a better approach is to change the design at the size where the content starts to break in some way. Perhaps the line lengths become far too long, or a boxed out sidebar gets squashed and hard to read. That's the point at which you want to use a media query to change the design to a better one for the space you have available. This approach means that it doesn't matter what the exact dimensions are of the device being used, every range is catered for. The points at which a media query is introduced are known as **breakpoints**.

The [Responsive Design Mode](https://firefox-source-docs.mozilla.org/devtools-user/responsive_design_mode/index.html) in Firefox DevTools is very useful for working out where these breakpoints should go. You can easily make the viewport smaller and larger to see where the content would be improved by adding a media query and tweaking the design.

![](/images/breakpoints.png)

## Active learning: mobile first responsive design

Broadly, you can take two approaches to a responsive design. You can start with your desktop or widest view and then add breakpoints to move things around as the viewport becomes smaller, or you can start with the smallest view and add layout as the viewport becomes larger. This second approach is described as mobile first responsive design and is quite often the best approach to follow.

The view for the very smallest devices is quite often a simple single column of content, much as it appears in normal flow. This means that you probably don't need to do a lot of layout for small devices — order your source well and you will have a readable layout by default.

The below walkthrough takes you through this approach with a very simple layout. In a production site you are likely to have more things to adjust within your media queries, however the approach would be exactly the same.

### Walkthrough: a simple mobile-first layout

Our starting point is an HTML document with some CSS applied to add background colors to the various parts of the layout.

```
* {
  box-sizing: border-box;
}

body {
  width: 90%;
  margin: 2em auto;
  font: 1em/1.3 Arial, Helvetica, sans-serif;
}

a:link,
a:visited {
  color: #333;
}

nav ul,
aside ul {
  list-style: none;
  padding: 0;
}

nav a:link,
nav a:visited {
  background-color: rgba(207, 232, 220, 0.2);
  border: 2px solid rgb(79, 185, 227);
  text-decoration: none;
  display: block;
  padding: 10px;
  color: #333;
  font-weight: bold;
}

nav a:hover {
  background-color: rgba(207, 232, 220, 0.7);
}

.related {
  background-color: rgba(79, 185, 227, 0.3);
  border: 1px solid rgb(79, 185, 227);
  padding: 10px;
}

.sidebar {
  background-color: rgba(207, 232, 220, 0.5);
  padding: 10px;
}

article {
  margin-bottom: 1em;
}
```

We've made no layout changes, however the source of the document is ordered in a way that makes the content readable. This is an important first step and one which ensures that if the content were to be read out by a screen reader, it would be understandable.

```
<body>
  <div class="wrapper">
    <header>
      <nav>
        <ul>
          <li><a href="">About</a></li>
          <li><a href="">Contact</a></li>
          <li><a href="">Meet the team</a></li>
          <li><a href="">Blog</a></li>
        </ul>
      </nav>
    </header>
    <main>
      <article>
        <div class="content">
          <h1>Veggies!</h1>
          <p>…</p>
        </div>
        <aside class="related">
          <p>…</p>
        </aside>
      </article>

      <aside class="sidebar">
        <h2>External vegetable-based links</h2>
        <ul>
          <li>…</li>
        </ul>
      </aside>
    </main>

    <footer><p>&copy;2019</p></footer>
  </div>
</body>
```

This simple layout also works well on mobile. If we view the layout in Responsive Design Mode in DevTools we can see that it works pretty well as a straightforward mobile view of the site.

From this point, start to drag the Responsive Design Mode view wider until you can see that the line lengths are becoming quite long, and we have space for the navigation to display in a horizontal line. This is where we'll add our first media query. We'll use ems, as this will mean that if the user has increased their text size, the breakpoint will happen at a similar line-length but wider viewport, than someone with a smaller text size.

**Add the below code into the bottom of your step1.html CSS.**

```
@media screen and (min-width: 40em) {
  article {
    display: grid;
    grid-template-columns: 3fr 1fr;
    column-gap: 20px;
  }

  nav ul {
    display: flex;
  }

  nav li {
    flex: 1;
  }
}
```

This CSS gives us a two-column layout inside the article, of the article content and related information in the aside element. We have also used flexbox to put the navigation into a row.

Let's continue to expand the width until we feel there is enough room for the sidebar to also form a new column. Inside a media query we'll make the main element into a two column grid. We then need to remove the margin-bottom on the article in order that the two sidebars align with each other, and we'll add a border to the top of the footer. Typically these small tweaks are the kind of thing you will do to make the design look good at each breakpoint.

**Again, add the below code into the bottom of your step1.html CSS.**

```
@media screen and (min-width: 70em) {
  main {
    display: grid;
    grid-template-columns: 3fr 1fr;
    column-gap: 20px;
  }

  article {
    margin-bottom: 0;
  }

  footer {
    border-top: 1px solid #ccc;
    margin-top: 2em;
  }
}
```

If you look at the final example at different widths you can see how the design responds and works as a single column, two columns, or three columns, depending on the available width. This is a very simple example of a mobile first responsive design.

## Do you really need a media query?

Flexbox, Grid, and multi-column layout all give you ways to create flexible and even responsive components without the need for a media query. It's always worth considering whether these layout methods can achieve what you want without adding media queries. For example, you might want a set of cards that are at least 200 pixels wide, with as many of these 200 pixels as will fit into the main article. This can be achieved with grid layout, using no media queries at all.

This could be achieved using the following:

```
<ul class="grid">
  <li>
    <h2>Card 1</h2>
    <p>…</p>
  </li>
  <li>
    <h2>Card 2</h2>
    <p>…</p>
  </li>
  <li>
    <h2>Card 3</h2>
    <p>…</p>
  </li>
  <li>
    <h2>Card 4</h2>
    <p>…</p>
  </li>
  <li>
    <h2>Card 5</h2>
    <p>…</p>
  </li>
</ul>
```

```
.grid {
  list-style: none;
  margin: 0;
  padding: 0;
  display: grid;
  gap: 20px;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
}

.grid li {
  border: 1px solid #666;
  padding: 10px;
}
```

With the example open in your browser, make the screen wider and narrower to see the number of column tracks change. The nice thing about this method is that grid is not looking at the viewport width, but the width it has available for this component. It might seem strange to wrap up a section about media queries with a suggestion that you might not need one at all! However, in practice you will find that good use of modern layout methods, enhanced with media queries, will give the best results.

## Legacy layout methods

Grid systems are a very common feature used in CSS layouts, and before CSS grid layout they tended to be implemented using floats or other layout features. You imagine your layout as a set number of columns (e.g. 4, 6, or 12), and then fit your content columns inside these imaginary columns. 

## Layout and grid systems before CSS Grid Layout

It may seem surprising to anyone coming from a design background that CSS didn't have an inbuilt grid system until very recently, and instead we seemed to be using a variety of sub-optimal methods to create grid-like designs. We now refer to these as "legacy" methods.

For new projects, in most cases CSS Grid Layout will be used in combination with one or more other modern layout methods to form the basis for any layout. You will however encounter "grid systems" using these legacy methods from time to time. It is worth understanding how they work, and why they are different to CSS Grid Layout.

We will explain how grid systems and grid frameworks based on floats and flexbox work. Having studied Grid Layout you will probably be surprised how complicated this all seems! This knowledge will be helpful to you if you need to create fallback code for browsers that do not support newer methods, in addition to allowing you to work on existing projects which use these types of systems.

It is worth bearing in mind, as we explore these systems, that none of them actually create a grid in the way that CSS Grid Layout creates a grid. They work by giving items a size, and pushing them around to line them up in a way that looks like a grid.

## A two column layout

Let's start with the simplest possible example — a two column layout. You can follow along by creating a new index.html file on your computer, filling it with a simple HTML template, and inserting the below code into it at the appropriate places. At the bottom of the section you can see a live example of what the final code should look like.

First of all, we need some content to put into our columns. Replace whatever is inside the body currently with the following:

```
<h1>2 column layout example</h1>
<div>
  <h2>First column</h2>
  <p>
    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nulla luctus
    aliquam dolor, eu lacinia lorem placerat vulputate. Duis felis orci,
    pulvinar id metus ut, rutrum luctus orci. Cras porttitor imperdiet nunc, at
    ultricies tellus laoreet sit amet. Sed auctor cursus massa at porta. Integer
    ligula ipsum, tristique sit amet orci vel, viverra egestas ligula. Curabitur
    vehicula tellus neque, ac ornare ex malesuada et. In vitae convallis lacus.
    Aliquam erat volutpat. Suspendisse ac imperdiet turpis. Aenean finibus
    sollicitudin eros pharetra congue. Duis ornare egestas augue ut luctus.
    Proin blandit quam nec lacus varius commodo et a urna. Ut id ornare felis,
    eget fermentum sapien.
  </p>
</div>

<div>
  <h2>Second column</h2>
  <p>
    Nam vulputate diam nec tempor bibendum. Donec luctus augue eget malesuada
    ultrices. Phasellus turpis est, posuere sit amet dapibus ut, facilisis sed
    est. Nam id risus quis ante semper consectetur eget aliquam lorem. Vivamus
    tristique elit dolor, sed pretium metus suscipit vel. Mauris ultricies
    lectus sed lobortis finibus. Vivamus eu urna eget velit cursus viverra quis
    vestibulum sem. Aliquam tincidunt eget purus in interdum. Cum sociis natoque
    penatibus et magnis dis parturient montes, nascetur ridiculus mus.
  </p>
</div>
```

Each one of the columns needs an outer element to contain its content and let us manipulate all of it at once. In this example case we've chosen ***div's***, but you could choose something more semantically appropriate like ***article's***, ***section's***, and ***aside's***, or whatever.

Now for the CSS. First, of all, apply the following to your HTML to provide some basic setup:

```
body {
  width: 90%;
  max-width: 900px;
  margin: 0 auto;
}
```

The body will be 90% of the viewport wide until it gets to 900px wide, in which case it will stay fixed at this width and center itself in the viewport. By default, its children (the h1 and the two ***divs***) will span 100% of the width of the body. If we want the two ***divs*** to be floated alongside one another, we need to set their widths to total 100% of the width of their parent element or smaller so they can fit alongside one another. Add the following to the bottom of your CSS:

```
div:nth-of-type(1) {
  width: 48%;
}

div:nth-of-type(2) {
  width: 48%;
}
```

Here we've set both to be 48% of their parent's width — this totals 96%, leaving us 4% free to act as a gutter between the two columns, giving the content some space to breathe. Now we just need to float the columns, like so:

```
div:nth-of-type(1) {
  width: 48%;
  float: left;
}

div:nth-of-type(2) {
  width: 48%;
  float: right;
}
```

Putting this all together should give us a result like so:

![](/images/2columnEX.png)

You'll notice here that we are using percentages for all the widths — this is quite a good strategy, as it creates a ***liquid layout***, one that adjusts to different screen sizes and keeps the same proportions for the column widths at smaller screen sizes. Try adjusting the width of your browser window to see for yourself. This is a valuable tool for responsive web design.

## Creating simple legacy grid frameworks

The majority of legacy frameworks use the behavior of the [float](https://developer.mozilla.org/en-US/docs/Web/CSS/float) property to float one column up next to another in order to create something that looks like a grid. working through the process of creating a grid with floats shows you how this works and also introduces some more advanced concepts to build on the things you learned in the lesson on [floats and clearing](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Floats).

The easiest type of grid framework to create is a fixed width one — we just need to work out how much total width we want our design to be, how many columns we want, and how wide the gutters and columns should be. If we instead decided to lay out our design on a grid with columns that grow and shrink according to browser width, we would need to calculate percentage widths for the columns and gutters between them.


## Supporting older browsers

There will be visitors to your site who use older browsers, or browsers which may not support the features you have used. This will always be the case on the web — as new features are developed, different browsers will prioritize different things. This article explains how to use modern web techniques without locking out users of older technology.

### What is the browser landscape for your site?

Every website is different in terms of target audience. Before deciding on the approach to take, find out the number of visitors coming to your site using older browsers. This is straightforward if you have an existing website which you are adding to or replacing, as you probably have analytics available which can tell you the technology people are using. If you have no analytics or this is a brand new site, then there are sites such as [Statcounter](https://gs.statcounter.com/) that can provide statistics filtered by location.

You should also consider the type of devices and the way people use your site, for example, you may expect a higher than an average number of mobile devices. Accessibility and people using assistive technology should always be considered, but for some sites that may be even more critical. In my experience, developers are often very worried about the experience of 1% of users in an old version of Internet Explorer, while not considering at all the far greater number who have accessibility needs.


### What is the support for the features you want to use?

Once you know the browsers that come to your site, you can assess any technology that you want to use against how well it is supported and how easily you can provide an alternative for visitors who do not have that technology available. We are trying to make this easy for you at MDN, by providing browser compatibility information on each page detailing a CSS property. For example, take a look at the page for [grid-template-columns](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-columns). At the bottom of this page is a table, which lists major browsers along with the version they began supporting this property.

![](/images/browser-table.png)

Another popular way to find out about how well a feature is supported is the [Can I Use](https://caniuse.com/) website. This site lists the majority of Web Platform features with information about their browser support status. You can view usage statistics by location — useful if you work on a site that has users mostly for a specific area of the world. You can even link your Google Analytics account to get analysis based on your user data.

Understanding the technology your users have, and the support for things you might want to use puts you in a good place to make all of your decisions and to know how best to support all of your users.


### Support doesn't mean "Looks the same"

A website can't possibly look the same in all browsers, because some of your users will be viewing the site on a phone and others on a large desktop screen. Similarly, some of your users will have an old browser version, and others the latest browser. Some of your users might be hearing your content read out to them by a screen reader, or have zoomed in on the page to be able to read it. Supporting everyone means serving a version of your content that is designed defensively, so that it will look great on modern browsers, but will still be usable at a basic level for users of older browsers.

A basic level of support comes from structuring your content well so that the normal flow of your page makes sense. A user with a very limited feature phone might not get much of your CSS, but the content will flow in a way that makes reading easy. Therefore, a well-structured HTML document should always be your starting point. If you remove your stylesheet, does your content make sense?

One option is to leave this plain view of the site as the fallback for people using very old or limited browsers. If you have a tiny number of people coming to the site in these browsers it may not make commercial sense to pour time into trying to give them a similar experience to people on modern browsers. It would be better to spend the time on things which make the site more [accessible](https://developer.mozilla.org/en-US/docs/Web/Accessibility), thus serving far more users. There is a middle ground between a plain HTML page and all the bells and whistles, and CSS has actually made creating these fallbacks pretty straightforward.

## Creating fallbacks in CSS

CSS specifications contain information that explains what the browser does when two layout methods are applied to the same item. This means that there is a definition for what happens if a floated item, for example, is also a Grid Item using CSS Grid Layout. Couple this information with the knowledge that browsers ignore CSS that they don't understand, and you have a way to create simple layouts using the [legacy techniques](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Legacy_Layout_Methods) we have already covered, which are then overwritten by your Grid layout in modern browsers that understand it.

### Falling back from grid to float

In the example below, we have floated three ***divs*** so they display in a row. Any browser that does not support [CSS Grid Layout](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Grids) will see the row of boxes as a floated layout. A floated item that becomes a grid item loses the float behavior, which means that by turning the wrapper into a Grid Container, the floated items become Grid Items. If the browser supports Grid Layout it will display the grid view, if not it ignores the display: grid and related properties and the floated layout is used.

```
* {
  box-sizing: border-box;
}

.wrapper {
  background-color: rgb(79, 185, 227);
  padding: 10px;
  max-width: 400px;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
}

.item {
  float: left;
  border-radius: 5px;
  background-color: rgb(207, 232, 220);
  padding: 1em;
}
```

```
<div class="wrapper">
  <div class="item">Item One</div>
  <div class="item">Item Two</div>
  <div class="item">Item Three</div>
</div>
```

![](/images/fallback%20methods.png)

### Fallback methods

There are a number of layout methods which can be used in a similar way to this float example. You can choose the one that makes the most sense for the layout pattern you need to create.

Float and clear
As shown above, the float and clear properties cease to affect the layout if floated or cleared items become flex or grid items.

display: inline-block
This method can be used to create column layouts, if an item has display: inline-block set but then becomes a flex or grid item, the inline-block behavior is ignored.

display: table
This method can be used to create table layouts, if an item has display: table, display: table-cell, etc., set but then becomes a flex or grid item, the display value is ignored.

Multiple-column Layout
For certain layouts you could use multi-col as a fallback, if your container has any of the column-* properties defined on it and then becomes a grid container, the multicol behavior will not happen.

Flexbox as a Fallback for Grid
Flexbox has greater browser support than Grid due to being supported by IE10 and 11. If you make a flex container into a grid container, any flex property applied to the children will be ignored.

For many layout tweaks in older browsers, you may find you can give a decent experience by using CSS in this way. We add a simpler layout based on older and well-supported techniques, then use the newer CSS to create the layout that over 90% of your audience will see. There are cases, however, when the fallback code will need to include something that the new browsers will also interpret. A good example of this is if we were to add percentage widths to our floated items to make the columns more like the grid display, stretching to fill the container.

In the floated layout, the percentage is calculated from the container — 33.333% is a third of the container width. In Grid however that 33.333% is calculated from the grid area the item is placed in, so it actually becomes a third of the size we want once the Grid Layout is introduced.

```
* {
  box-sizing: border-box;
}

.wrapper {
  background-color: rgb(79, 185, 227);
  padding: 10px;
  max-width: 400px;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
}

.item {
  float: left;
  border-radius: 5px;
  background-color: rgb(207, 232, 220);
  padding: 1em;
  width: 33.333%;
}
```

```
<div class="wrapper">
  <div class="item">Item One</div>
  <div class="item">Item Two</div>
  <div class="item">Item Three</div>
</div>
```

![](/images/fallbacksEX.png)

To deal with this issue we need to have a way to detect if Grid is supported and therefore if it will override the width. CSS has a solution for us here.

## Feature queries

Feature queries allow you to test whether a browser supports any particular CSS feature. This means that you can write some CSS for browsers that don't support a certain feature, then check to see if the browser has support and if so throw in your fancy layout.

If we add a feature query to the above example, we can use it to set the widths of our items back to auto if we know that we have grid support.

```
* {
  box-sizing: border-box;
}

.wrapper {
  background-color: rgb(79, 185, 227);
  padding: 10px;
  max-width: 400px;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
}

.item {
  float: left;
  border-radius: 5px;
  background-color: rgb(207, 232, 220);
  padding: 1em;
  width: 33.333%;
}

@supports (display: grid) {
  .item {
    width: auto;
  }
}
```

```
<div class="wrapper">
  <div class="item">Item One</div>
  <div class="item">Item Two</div>
  <div class="item">Item Three</div>
</div>
```

![](/images/asd1.png)

Support for feature queries is very good across modern browsers. However, you should note that browsers that do not support CSS Grid also tend not to support feature queries. This means that an approach as detailed above will work for those browsers. What we are doing is writing our old CSS first, outside of any feature query. Browsers that do not support Grid, and do not support the feature query will use that layout information they can understand and completely ignore everything else. The browsers that support the feature query also support CSS Grid and so will run the grid code and the code inside the feature query.

The specification for feature queries also contains the ability to test if a browser does not support a feature — this is only helpful if the browser does support feature queries. In the future, an approach of checking for lack of support will work, as the browsers that don't have feature query support go away. For now, however, use the approach of doing the older CSS, then overwriting it, for the best support.

## The IE10 and 11 prefixed version of Grid

The CSS Grid specification was initially prototyped In Internet Explorer 10; this means that while IE10 and IE11 do not have modern grid support, they do have a version of Grid layout that is very usable, although different to the modern specification documented on this site. The IE10 and 11 implementations is -ms- prefixed, which means you can use it for these browsers and it will be ignored by non-Microsoft browsers. Edge does still understand the old syntax, however, so take care that everything is safely overwritten in your modern grid CSS.

The guide to Progressive Enhancement in Grid Layout can help you understand the IE version of the grid, and we have included some additional useful links at the end of this lesson. However, unless you have a very high number of visitors in older IE versions, you may find it better to focus on creating a fallback that works for all non-supporting browsers.

## Testing older browsers

With the majority of browsers supporting Flexbox and Grid, it can be reasonably hard to test older browsers. One way is to use an online testing tool such as Sauce Labs, as detailed in the Cross browser testing module.

You can also download and install virtual machines, and run older versions of browsers in a contained environment on your computer. If you are still required to support Internet Explorer, Microsoft provides a range of Virtual Machines available for free download. These are available for Mac, Windows and Linux operating systems and so are a great way to test in old and modern Windows browsers even if you are not using a Windows computer.



