# HTML (Hyper Text Markup Languaje)

The HyperText Markup Language or HTML is the standard markup language for documents designed to be displayed in a web browser. It can be assisted by technologies such as Cascading Style Sheets (CSS) and scripting languages such as JavaScript.

"Hypertext" refers to links that connect web pages to one another, either within a single website or between websites. Links are a fundamental aspect of the WEB. By uploading content to the internet and linking it to pages created by other people, you become an active participant in the World Wide Web.

HTML uses "markup" to annotate text, images, and other content for display in a Web browser. HTML markup includes special "elements" such as: 

```
<head>, <title>, <body>, <header>, <footer>, <article>, <section>, <p>, <div>, <span>, <img>, <aside>, <canvas>, <datalist>, <details>, <embed>, <nav>, <output>, <progress>, <video>, <ul>, <ol>, <li> and many others.

```

An HTML element is set off from other text in a document by "tags", which consist of the element name surrounded by "<" and ">". The name of an element inside a tag is case insensitive. That is, it can be written in uppercase, lowercase or a mixture. For example, the "title" tag can be written as "Title", "TITLE" or in any other way. The convention and recommended practice is to write tags in lowercase.


## Basic Estructure

```
<!DOCTYPE html>
    <html lang="en">
      <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>Document</title>
      </head>
      <body>
      </body>
    </html>

```

- ```<!DOCTYPE html>```
Specifies the type of document and defines that it's under the HTML5 standard.

- ```<html lang="en">```
The html element represents the root of an html document. All others elements descend from this element. The lang attribute tells us the language in which the content of the document will be written.

- ```<head>```
The head element provides general information (metadata) about the document, including its title and links to scripts and style sheets.

- ```<body>```
In the body will go all the textual and multimedia content that we want to show in the document (everything that the user will see in the browser).

- ```<meta charset="UTF-8"/>```
The charset defines the character set that the document will use, UTF-8 is the universal encoding to support non-English characters.

- ```<meta name="viewport" content="width=device-width,initial-scale=1.0" />```
The viewport meta tag defines how the content will be displayed on any devide, be it mobile, tablet or desktop. This label is essential when we do responsive design.

- ```<title>Web Name</title>```
The title tag represents the title of our document, it's seen in the browser tab, it's also the text that's seen in search engine results, the title must not exceed 65 characters.

## HTML elements reference

- ```<html>```
 The HTML element represents the root (top-level element) of and HTML document, so it's also referred to as the root element. All other elements must be descendants of this element.


## Document metadata

- ```<base>```
The base html element specifies the base URL to use all relative URLs in a document. There can be only one base element in a document.

- ```<head>```
The head html element contains machine-readable information (metadata) about the document, like its title, scripts and style sheets.

- ```<link>```
The link html element specifies relationships between the current document and an external resource. This element is most commonly used to link to CSS, but is also used to establish site icons (both "favicon" style icons and icons for the home screen and apps on mobile devices) among others things.

- ```<meta>```
The meta html element represents Metadata that cannot be represented by other HTML meta-related element, like: base, link, script, style or title.

-```<style>```
The style html element contains style information for a document or part of a document. It contains CSS, which is applied to the contents of the document containing the style element.

-```<title>```
The title html element defines the document's title that is shown in a browser's title bar or a page's tab. It only contains text; tags within the element are ignored.


## Sectioning root

- ```<body>```
The body html element represents the content of an html document. There can be only one body element in a document.


## Content sectioning

Content sectioning elements allow you to organize the document content into logical pieces. Use the sectioning elements to create a broad outline for your page content, including header and footer navigation, and heading elements to identify sections of content.


- ```<address>```
This element indicates that the enclosed HTML provides contact information for a person or people, or for and organization.


- ```<article>```
This element represents a self-contained composition in a document, page, application or site, which is intended to be independently distributable or reusable. Examples include: a forum post, a magazine or newspaper article, a blog entry, a product card or any other independent item of content.


- ```<aside>```
This element represents a portion of a ducment whose content is only indirectly related to the document's main content. Asides are frequently presented as sidebars or call-out boxes.


- ```<footer>```
a footer for its nearest ancestor sectioning content or sectioning root element. A footer typically contains information about the author of the section, copyright data or links to related documents.


- ```<header>```
The header element represents introductory content, typically a group of introductory or navigational aids. It may contain some heading elements but also a logo, a search form, an author name, and other elements.


- ```<h1>, <h2>, <h3>, <h4>, <h5>, <h6>```

The h1 to h6 html elements represent six levels of section headings. H1 is the highest section level and h6 is the lowest.


- ```<main>```
The main element represents the dominant content of the body of a document. The main content area consists of content that is directly related to or expands upon the central topic of a document, or the central funcionality of an application.


- ```<nav>```
The nav element represents a section of a page whose purpose is to provide navigation links, either within the current document or to others documents. Common examples of navigation sections are menus, tables of contents, and idexes.


- ```<section>```
The section element represents a generic standalone section of a document, which doesn't have a more specific semantic element to represent it. Sections should always have a heading, with very fer exceptions.


## Text Content

Use HTML text content elements to organize blocks or sections of content placed between the opening body and closing body tags. important for accessibility and SEO, these elements identify the purpose or structure of that content.

- ```<blockquote>```
This element indicates that the enclosed text is an extended quotation. Usually, this is rendered visually by indentation. A URL for the source of the quotation may be given using the cite attribute, while a text representation of the source can be given using the cite element.


- ```<dd>```
This element provides the description, definition or value for the preceding term (dt) in a description list (dl).


- ```<div>```
This element is the generic containner for flow content. It has no effect on the content or layout until styled in some way using CSS.


- ```<dl>```
This element represents a description list. The element encloses a list of groups of terms (specified using the dt element) and descriptions (provided by dd elements). Common uses for this element are to implement a glossary or to display metadata (a list of key-value pairs).


- ```<dt>```
This element specifies a term in a description or definition list, and as such must be inside a dl element. It's usually followed by a dd element; however, multiple dt elements in a row indicate several terms that are all defined by the inmediate next dd element.


- ```<figcaption>```
The figcaption html element represents a caption or legend describing the rest of the contents of its parent figure element.

- ```<figure>```
This html element represents self-contained content, potentially with an optional caption, which is specified using the figcaption element. The figure, its caption, and its content are referenced as a single unit.


- ```<hr>```
The hr html element represents a thematic break between paragraph-level elements: for example, a change of scene in a story, or a shift of topin within a section.

- ```<li>```
The li html element is used to represent an item in a list. It must be contained in a parent element: an ordered list (ol), an unordered list (ul) or a menu (menu). In menus and unordered lists, list items are usually displayed using bullet points. In ordered lists, they are usually displayed with an ascending counter on the left, such as a number or letter.

- ```<ol>```
The OL html elements represents an ordered list of items, typically rendered as a numbered list.

- ```<ul>```
The UL html element represents an unordered list of items, typically rendered as a bulleted list.

- ```<menu>```
The menu html element is described in the Html specification as a semantic alternative to UL, but treated by browsers (and exposed through the accessibility tree) as no different than UL. It represents an unordered list of items (which are represented by LI elements).

- ```<p>```
The P html elements represents a paragraph. Paragraphs are usually represented in visual media as blocks of text separated from adjacent blocks by blanc lines and/or first-line indentation, but HTML paragraphs can be any structural grouping of related content, such as images or form fields.

- ```<pre>```
The pre html element represents preformatted text which is to be presented exactly as written int he HTML file. The text is typically rendered using a non-proportional, or monospaced, font. Whitespace inside this element is displayed as written.


## Inline text semantics.

- ```<a>```
The a HTML element (or anchor element) with its href attribute creates a hyperlink to web pages, files, email addresses, locations in the same page, or anything else a URL can address.

- ```<abbr>```
This element represents an abbreviation or acronym. The optional title attribute can amplify or describe the abbreviation. If present, the title attribute must contain the full description and nothing else.

- ```<b>```
The b HTML element is used to draw the reader's attention to element's contents, which are not otherwise granted special importance. This was formerly known as the Boldface element, and most browsers still draw the text in boldface. You should not use b element for styling text, instead, you should use the CSS font-weight property to create boldface text, or the strong element to indicate that text is of special importance.

- ```<br>```
The br html element produces a line break in text (carriage-return). It useful for writing a poem or an address, where the division of lines is significant.


- ```<cite>```
The cite html element is used to mark up the title of a cited creative work. The reference may be in an abbreviated from according to context-appopriate conventions related to citation metadata.

- ```<code>```
This element displays its contents styled in a fashion intended to indicate that the text is a short fragment of computed code. By default, the context text is displayed using the user agent default monospace font.


- ```<data>```
The data html element links a given piece of content with a machine-readable translation. If the content is time- or date- related, the time element must be used.


- ```<em>```
This element marks text that has stress emphasis. The em element can be nested, with each level of nesting indicating a greater degree of emphasis.


- ```<i>```
The i HTML element represents a range of text that is set off from the normal text for some reason, such as idiomatic text, technical terms, taxonomical designations, among others.

- ```<mark>```
The mark HTML element represents text which is marked or highlighted for reference or notation purposes due to the marked passage's relevance in the enclosing context.


- ```<q>```
This element indicates that the enclosed text is a short inline quotation. Most modern browsers implement this by surrounding the text in quotation marks. This element is intended for short quotations that don't require paragraph breaks, for long quotations use the blockquote element.


- ```<s>```
The s HTML element renders text with a strikethrough or a line through. Use the s element to represent things that are no longer relevant or no longer accurate. However, s element is not appropiate when indicating document edits, for that, use the del and ins elements, as appropiate.


- ```<samp>```
The samp HTML element is used to enclose inline text which represents sample (or quoted) output from a computer program. Its contents are typically rendered using the browser's default monospaced font (such as courier or lucida console).


- ```<small>```
This element represents side-comments and small print, like copyright and legal text, independent of its styled presentation. By default, it renders text within it one font-size smaller, such as from small to x-small.


- ```<span>```
The span HTML element is a generic inline container for phrasing content, which does not inherently represent anything. It can be used to group elements for styling purposes (using the class or id attributes) or because they share atribute values, such as lang. It should be used only when no other semantic element is appropiate. Span is very much like a div element, but div is a block-level element whereas a span is an inline element.

- ```<strong>```
The strong HTML element indicates that its contents have strong importante, seriousness or urgency. Browsers typically render the contents in bold type.


- ```<time>```
The time HTML element represents a specific period in time. It may include the datetime attribute to translate dates into machine-readable format, allowing for better search engine results or custom features such as reminders.

- ```<u>```
The u HTML element represents a span of inline text which should be rendered in a way that indicates that it has a non-textual annotation. This is rendered by default as a simple solid underline, but may be altered using CSS.


- ```<var>```
The var HTML element represents the name of a variable in a mathematical expression or a programming context. It's typically presented using an italicized version of the current typeface, although that behavior is browser-dependent.



## Image and multimedia.

- ```<area>```
The area HTML element defines an area inside an image map that has predefined clickable areas. An image map allows geometric areas on an image to be associated with Hyperlink.


- ```<audio>```
The audio HTML element is used to embed sound content in documents. It may contain one or more audio sources, represented using the src attribute or the source element: the browser will choose the most suitable one. It can also be the destination for streamed media, using a MediaStream.


- ```<img>```
This element embeds an image into the document.


- ```<map>```
This element is used with area elements to define an image map (a clickable link area).

- ```<track>```
The track HTML element is used as a child of the media elements, audio and vide. It lets you specify timed text tracks (or time-based data), for example to automatically handle subtitles. The tracks are formatted in webVTT form (.vtt files)- Web Video Text Tracks.

- ```<video>```
The video HTML element embeds a media player which supports video playback into the document. You can use video for audio content as well, but the audio element may provide a more appropiate user experience.


## Embedded content

In addition to regular multimedia contnet, HTML can include a variety of other content, even if it's not always easy to interact with.

- ```<embed>```
The embed HTML element embeds external content at the specified point in the document. This content is provided by an external application of other source of interactive content such as a browser plug-in.

- ```<iframe>```
The iframe HTML element represents a nested browsing content, embedding another HTML page into the current one.

- ```<object>```
The object HTML element represents an external resource, which can be treated as an image, a nested browsing context, or a resource to be handled by a plugin.

- ```<picture>```
The picture HTML element contains zero or more source elements and one img element to offer alternative versions of an image for different display/device scenarios.

- ```<source>```
The source HTML element specifies multiple media resources for the picture, the audio element, or the video element. It's a void element, meaning that it has no content and does not have a closing tag. It's commonly used to offer the same media content in multiple file formats in order to provide compatibility with a broad range of browsers given their differing support for image file formats and media file formats.

- ```<portal>```
This element enables the embedding of another HTML page into the current one for the purposes of allowing smoother navigation into new pages.