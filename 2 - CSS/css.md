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
