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


