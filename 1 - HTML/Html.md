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


