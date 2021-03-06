# Intro to HTML & the DOM

## Table of Contents
* [Learning Objectives](#learning-objectives)
* [Preparation](#preparation)
* [Differentation between HTML and DOM](#differentation-between-html-and-dom)
* [Introduction to HTML tags](#introduction-to-html-tags)
* [Creating a table in HTML](#creating-a-table-in-html)
* [Google Chrome Developer Tools](#google-chrome-developer-tools)
* [HTML 5 Tags](#html-5-tags)
* [Other Topics](#other-topics)
* [Additional Resources](#additional-resources)
* [Exercise #1](#exercise-#1)
* [Exercise #2](#exercise-#2)


## Learning Objectives
* Build a simple web page using HTML
* Explain the various parts of an HTML document, including:
  - the `<head>` and `<body>` tags
  - container elements such as `<div>`, `<header>`, `<footer>`, `<section>`, and `<article>`
  - common elements such as `<h1>`, `<h2>`, `<p>`, `<ul>`, and `<li>`
* Explain the difference between _HTML_ and the _DOM_

## Preparation
- Pre-work and About Me page completion

## Hook (5m)
This morning we are going to take a look at the DOM and how we can use the Chrome Dev Tools to manipulate it. This afternoon we will look at more advanced ways to perform DOM manipulation using Javascript.

<details>
<summary>To start, can someone describe the difference between HTML and the DOM in their own words?</summary>
The DOM (Document Object Model) is the browser's intrepretation of the HTML. Your browser creates objects out of the HTML elements.

examples: 

- skeleton => HTML, body => DOM
- song chords, lyrics => HTML, recorded song => DOM
- recipe ingredients => HTML, finished dish => DOM

</details>


**WE DO:** Goto [Kickass App](http://kickassapp.com/) and use it. What is happening?


We're gonna get into DOM manipulation later in the week, but to demonstrate the difference between an _HTML_ document and the _DOM_ that is created from the _HTML_ document, let's go to the [Jezebel](http://jezebel.com/) web site and play around with some headlines.

Using the Chrome DevTools Inspector, alter something on the page.


**YOU DO** Go to [Atlanta Craigslist](https://atlanta.craigslist.org/) and try running the following `javascript` DOM manipulation code in the JavaScript console:

```javascript
document.getElementById('logo').children[0].text = 'MarensList';
document.getElementsByClassName('ban')[0].children[0].text = 'WDI Rocks!'
```

Questions:

<details>
<summary>Did I just hack Craigslist?</summary>
No. We manipulated the DOM, or what existed in the browser's memory.
</details>
<details>
<summary>What happens if I refresh the page?</summary>
All of your changes will disappear.  
</details>
<details>
<summary>What are we actually changing - the HTML or the DOM?</summary>
You are changing the DOM.  The developers at Craigslist will not be worried that their site is now called 'MarensList'.
</details>

<br />

---

## **YOU DO**
- 5 min - Read this article on the difference between HTML and the DOM from [CSS Tricks](https://css-tricks.com/dom/) 
- 5 min - Pair and Share - discuss what you learned with your partner
- 5 min - Ask each group for something they learned in the article

<br />

---

## Let's Differentiate between HTML and the DOM

* **HTML**: the language we use to create an HTML Page/Document
* **DOM**: the Document Object Model, i.e. the in-memory representation of the HTML page, that is created every time the browser _renders_ the HTML document.

**Note**: the _DOM_ can be _manipulated_ via _JavaScript_ code.  And we will discuss this in further detail next week.

<br />

### What is HTML?
**HTML** stands for "Hyper Text Markup Language". It is not a general purpose programming language like *JavaScript* or _Ruby_ but rather a **markup language**, i.e. a language for representing structured text.

To create any website, you need HTML, CSS and JavaScript.  While CSS provides the style and color for a site, and JavaScript allows interaction with the end user, HTML creates the skeleton of a website. It is the *structured content*.

![Anatomy of an HTML Document](images/anatomy-of-an-html-doc.jpg)

The `<head>` section is for metadata, which gives the browser information about the site.  Inside of the head, we would add the title of our website- which is what you see in the browser tab, any link tags to css pages.     

The `<body>` section is for the visible content on a web page.  As well as our JavaScript `<script>` tags.

```html
<!doctype html>
<html>
  <head>
    <!-- document metadata goes here. -->
  </head>
  <body>
    <!-- document contents go here. -->
  </body>
</html>
```

<br />

### What is the DOM?

- A browser receives a page as HTML and creates a **Document Object Model** (a.k.a. the DOM tree) that it stores in memory.  The DOM defines a standard for accessing your HTML document.

![DOM Tree](images/dom_tree.gif)

- The DOM is a **tree-like structure** or data structure, similar to an outline, that consists of parent and child nodes that represent each element on our site.
- The DOM has properties (a value that you can get or set), methods (an action that you can do) and events (what happens when a user interacts with the page- by clicking on a button or mousing over an element).
- The DOM defines each HTML **element** is an object. These objects may be accessed and modified, using properties and methods, in order to change them.

- In the console, type `document.` and check out the available methods.
- In the console, type `document.title`.
<details>
<summary>What do you expect to see?</summary>
The `document.title` is going to output the title of the website, or what you see in your browser tab.
</details>
- In the console, type `document.body.children[5]`.
<details>
<summary>What do you expect to see?</summary>
This statement will highlight the main content div, and we can click through and highlight other content from there.
</details>


#### **WE DO**
- Go to Jezebel.
- In the console, type `document.getElementsByClassName('headline')[0];`
  - We will discuss this more later, but getElementsByClassName, returns an array/list of items with that class.  Arrays are zero-indexed, which means that they start with zero, so we need to add that number in square brackets to highligh the first title. 
  - This will highlight the first news title on the page.
- Update that title to have the id="first-title"
  - The funny thing is that Jezebel doesn't really use ids, so in order to access and Id, we need to take the initiative to add it ourselves.
- In the console, type `document.getElementById('first-title');`
  - This statement will also highlight the first news title on the page, but in a different way.

- As with our earlier Jezebel example, you can change the HTML in the inspector but when you re-render the page, the changes are gone. Try `document.write('WDI Rocks!!!')`. (Traditionally, you only use document.write for testing purposes because you don't have any control over where it renders on the page, and it overwrites everything else).

<br />

## What is the Window Object?

- The **Window Object** represents the window that is open in the browser.
- The location property is the URL of the page.
- In the console, type `window.` and check out the available methods.
<details>
<summary>Do you recognize any of these methods?</summary>
`alert()` will alert a message to the user.
`focus()` will set the focus/cursor in an input box- this is helpful with forms. 
`prompt()` displays a dialogue box to the user.
`setInterval()` calls a function or expression at specified intervals (in milliseconds).
`setTimeOut()` calls a function or expression after a certain amount of time (in milliseconds).
</details>
- In the console, type `window.location`.
<details>
<summary>What do you expect to see?</summary>
`window.location.href` returns the href (URL) of the current page
`window.location.hostname` returns the domain name of the web host
`window.location.pathname` returns the path and filename of the current page
`window.location.protocol` returns the web protocol used (http: or https:)
`window.location.assign` loads a new document
</details>
- In the console, type `window.document.write('Hello')`.
<details>
<summary>Knowing what happened before, what do you expect this statement to do?</summary>
It will write over everything that exists on the webpage with the string 'Hello'.  Notice that this is similar to `document.write`.  The only difference is that we added `window.` in front of that statement.  `Document`, returns the document object for the window.  Often, the `window.` is left off of window object methods.
</details>

<br />

## Introduction to HTML tags

## Describe the content of a tag - (5m)

Between the opening and closing tags, we insert the text or "content" of a tag.  

The final result would look like this: `<example-tag>Content Goes in here</example-tag>`.  

Tags can also be placed within other tags:

```html
<outer-tag>
  <inner-tag></inner-tag>
</outer-tag>
```

Note that when placing a tag inside another tag, you should indent the new tag to show that it is a child of its parent tag.

##### Example of an Anchor tag containing an Image tag

```html
<a href="www.w3.org" target="_blank">
  <img src="http://www.misiide.net/images/2013/03/Tim-Berners-Lee.jpg" alt="A picture of Tim Berners-Lee!" />
</a>
```

#####QUESTION
<details>
<summary>Can anyone explain the HTML above?</summary>
    The `href` attribute above makes the image of Sir Timothy John Berners-Lee "clickable" and redirects the user to the W3 website.
</details>

<details>
<summary>What is the importance of the 'alt' attribute?</summary>
    The `alt` attribute tells screen readers about the image displayed.
</details>

<details>
<summary>Who is Sir Timothy John Berners-Lee?</summary>
Sir Timothy John Berners-Lee invented the World Wide Web in 1989.  He founded and Directs the World Wide Consortium (W3C) which oversees the continued development of the web. He also founded the World Wide Web Foundation whose mission is for the WWW to serve Humanity through improvement and availability, and he co-founded the Open Data Institute in London.
</details>

<br />

![We Do](http://i.imgur.com/6Kce0ca.png)

#####WE DO - (10m)

As a quick review, I will give you some examples of broken HTML and you tell me what's wrong with them. 

[HTML Fixit](https://github.com/ATL-WDI-Curriculum/atl-wdi-9/blob/master/unit_01/w02d01/instructor_notes/html_fixit.md)

<hr>

<br />

![We Do](http://i.imgur.com/6Kce0ca.png)

# WE DO - CODE ALONG -  90 min 

## Common Tags

In general, we don't create our own tags.  Instead there are a set of pre-defined tags with functionality already associated with them.

### Initializing a page

Every site should start with:

```html
<!DOCTYPE html>
<html>
  <head>
    <title></title>
  </head>
  <body></body>
</html>
```

1. The DOCTYPE tag is special and doesn't get closed.  It also is the only tag that can have non-alpha-numeric (letters/numbers) values in it.
1. html: shows where the html begins
1. head: contains content specifically for the browser, not the user, to see (e.g.- meta tags, google analytics scripts). 

  - The `head` section is important for search engines, as it helps provide additional information about the website. Anything within the opening and closing `<head>` tags will **NOT** be displayed on the page.

  - The `<head>` tags are placed right after the opening `<html>` tag, and before the opening `<body>` tag.

1. body: contains all the content that the user will see when viewing the html in a web browser like Chrome, Firefox, etc.

1. title: This is what shows up in your browser tab.

** These are the 4 pairs of tags: html, head, title and body that are mandatory for every web page.

<br />

### Meta Tags

| Element        | Description                                               |
|:-------------- |:--------------------------------------------------------- |
| `<link>`       | used to load a CSS file - it is self closing. |
| `<script>`     | used to load a JavaScript file or for embedding JavaScript code. |

**Although any script tags should really be at the bottom of your html page**
<details>
<summary>Does anyone know why?</summary>
If your `<script>` tags are placed in the `<head>` of your document, your html will wait to render until the javaScript has been loaded.  Therefore, it is best to place it at just before your closing body tag.
</details>

<br />

**YOU DO**

1. Create the initial structure of the page
    - `cd ~/dev`
    - `mkdir html_css_intro`
    - `cd` into the folder
    - `touch index.html`
    - `subl .`
    - Create the basic html structure
2. Add the meta tags for external `css` and `javascript` files.
    - `<link rel="stylehseet" type="text/css" href="main.css" />`
    - `<script src="main.js"></script>`

---

**YOU DO - (2m)**

I want you to put every html tag you can think of into Slack with a description. Don't worry about duplicates and don't overthink it. Just type them in there!

For example: `<p></p>` - paragraph tag, block element, used for basic text on a page

---

<br />

### Basic Tags

1. h1, h2, h3, h4, h5, h6
  - These are headers.  Imagine you are giving a lecture and you would like to create an outline.  Headers will help a computer/programmer figure out what are the title, sub sections, sub-sub sections, etc. of your outline.  The allude to importance on an html page.
  - The lower the number, the more important the header is.  h1 tags are generally the title of the page.  h2 denote a section, and so on.
1. p
  - These are paragraphs

### Specific Structural Elements

Of course a website is more than just headers and paragraphs.  It has many sections to it that a normal outline doesn't.  Here are some of the more common tags we use to give structure to the page"

See also [HTML5 New Elements](http://www.w3schools.com/html/html5_new_elements.asp)

1. header
  - could contain elements like a logo and a nav bar.  Perhaps the title of the page too?
1. footer
  - could contain disclaimers, copyrights, and less important links (privacy, terms and conditions, legal, etc).
1. main
  - the bulk of your site goes in here
1. section
  - within some of the tags listed above, there can be different sections.  Use this tag to block off those sections.
1. nav
  - this will hold navigation links
1. article
  - if you're writing a blog, or have a page with many self contained sections, you might think about using the article tag
1. aside
  - this is for tangential material.  Sidebars, inserts, etc.

<br />

**YOU DO**

In the `index.html` file you created earlier...

1. Add a `header` tag for your post WDI plans
2. Add `title` tags and empty `nav` tags inside the `body` 
3. Add a `main` section
4. Add a `footer` section with your name

---

<br />

### Generic Structure

Sometimes we need a tag that doesn't quite fit into any of the previously defined categories.  If this is the case, we can use one of two generic tags

1. div
  - used to block out chunks of content
1. span
  - use inline, to separate out small bits of content (e.g. letters, words, sentences, etc)

### Elements

Some elements are not structural, but will make the content display differently

1. ul/ol/li
  - creates a list, either unordered (ul) or ordered (ol)
  - inside each `ul` or `ol` is a set of `li` list item elements.

### Styled Text 
1. em
  - this will emphasize a chunk of text, usually making it italicized
  - best practice- use **em** instead of **i**
1. strong
  - this will emphasize a chunk of text, usually making it bold.
  - best practice- use **strong** instead of *b*

  > NOTE: It is usually better to avoid these tags as it is better to use CSS for styling content.

  - We use strong and em because screen readers will say what is inside of these tags with a strong or emphasized voice.
  
<br />

**YOU DO**

In the `index.html` file you created earlier...

1. Add a `ul` with 4 `li` tags to your `nav`
2. Add styled text tags to some piece of content
3. Add a `span` tag to a small piece of content

--- 

<br />

### Decorative Elements

Some elements do not contain content and instead are purely for decoration.  Elements that do not contain content are written like so `<no-content-tag/>`.  Note there is no closing tag and the slash comes before the final `>`

1. hr
  - horizontal rule, `<hr>` creates a divider
1. br
  - break, `<br />`, starts a new line in a chunk of text.

---

<br />

## Describe what attributes do

We can add more meaning to a tag by adding "attributes" to it.  It looks like `<some-tag my-attribute="attribute-value"><some-tag>` or `<self-closing-tag attribute="value"/>`.  Again, in general, we don't create our own attributes, but instead choose from predefined ones that have specific functionality depending on what tag they're attached to.

| HTML          |  Example                              |
|:-------------:|:------------------------------------- |
| attribute     | `<a href="www.google.com">Google</a>` |

<br />

**QUESTION:** What are some attributes that we add to HTML tags?

<br />

## Common tags with attributes

1. a
  - Anchor tag.  Creates a clickable link to another page.  Uses the `href` attribute to do so
  - example: `<a href="http://www.google.com">This link will go to Google</a>`
  - note that the actual URL (location) of the page is hidden, and that only the content is shown.
1. img
  - self closing, but contains a `src` attribute with is the URL for the image
  - example: `<img src="https://www.google.com/images/branding/googlelogo/2x/googlelogo_color_272x92dp.png" alt="google logo"/>`
1. video
  - like `img` but links to a video
  - example: `<video src="http://www.w3schools.com/html/mov_bbb.mp4"/>`
  - also has attributes like `autoplay`, `controls`, `loop`
1. audio
  - like `img` and `video`
  - example: `<audio controls="true" src="http://www.w3schools.com/tags/horse.mp3" />`

<br />

**YOU DO**

In the `index.html` file you created earlier...

1. Add a link to your GitHub repo in the `footer` section of your page.
2. Add an image to your page

<br />

---

## Describe what Semantic HTML means

The most important thing to remember is that these tags and attributes are supposed to give structure and meaning your content, not appearance.  Sometimes you might want the title of the page to be smaller than the titles of the sub sections.  You should still use the tag that conveys the proper meaning, even if it doesn't look right.  You mainly need to focus on this because of screen readers, so that they can understand the importance of the tags/flow of your page.

<br />

**YOU DO**

Go to this [HTML Practice Exercise](https://github.com/ATL-WDI-Exercises/html-dom/blob/master/html_practice_exercise.md) and follow the instructions to build a basic webpage in 15 minutes. Based on the screenshots of your sites, sent to me in slack, I will then choose a student to demo what they have built.

<br />

---

## Review Questions (10m)

1. Why should we use the `<strong>` tag instead of the `<b>` tag?
2. What does Accessibility mean?

<br />

---

![Imgur](http://i.imgur.com/WzTTdIe.jpg)

## Exercise #1

Using HTML tags only (don't worry about CSS), use the starter code below to recreate the Document Outline for the following website:

[How We Use Energy](http://needtoknow.nas.edu/energy/energy-use/)

* [Starter Code](https://github.com/ATL-WDI-Exercises/html-dom/blob/master/energy_dom_outline/energy_document_outline.html)
* [Finished Code](https://github.com/ATL-WDI-Exercises/html-dom/blob/master/energy_dom_outline/energy_document_outline_fin.html)

## Exercise #2

Clone your HTML/DOM repo and work on the [Busy Hands](https://github.com/ATL-WDI-Exercises/busy-hands) exercise.

---

## HTML Cheatsheet

![Anatomy of an HTML Document](images/html-cheat-sheet-v1.png)

---

## Google Chrome Developer Tools

Let us have a quick first look at **Chrome Developer Tools**. Available as a console in Google Chrome, it allows us to get a lot of information about the page we are on, providing a detailed look into the HTML structure of the page as well as the CSS styling, among other things.

In Chrome, you can access it with:
  - `Cmd + Alt + i` on a Mac
  - `Ctrl + Shift + C` or `F12` on Windows or Linux
  - or right-click on the browser and click on the "Inspect element" option

As of now, let's mainly look at the "Elements" tab -> This tab is a very powerful way to look at the page structure, and locate specific elements within the page as well as view their styles.

You can gain some useful information on all of the elements by looking at the data on the right column of the console, most notably the CSS properties that are currently applied to the elements. You can change them/"live" update them to play around with different styles. These changes, however, only apply to the page that is displayed, you are only updating the DOM - they will not save to your CSS file unless you manually add them, and they will disappear on the next page reload.

We will play with this functionality more when we dig deeper into CSS.

---

## HTML 5 Tags

See [HTML5 New Elements](http://www.w3schools.com/html/html5_new_elements.asp)

---

## Other Topics

For information on accessibility and search engine optimization, see [Accessibility and SEO](accessibility-and-seo.md).

For information on HTML5 Boilerplate, see [HTML5 Boilerplate](html5-boilerplate.md).

---

## Additional Resources

* [Online HTML live editor](https://thimble.webmaker.org/en-US/projects/wrangler/)
* [HTML element reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Element)
* [HTML Elements by Category](http://www.w3schools.com/tags/ref_byfunc.asp)
* [HTML5 element reference](https://developer.mozilla.org/en/docs/Web/Guide/HTML/HTML5/HTML5_element_list)
* [Tim Berners-Lee](http://www.w3.org/People/Berners-Lee)
* [Evolution of the Web - Great Link](http://www.evolutionoftheweb.com/)
* [Stack Overflow: What is the difference between Section and Div](http://stackoverflow.com/questions/6939864/what-is-the-difference-between-section-and-div)
* [HTML5 Doctor](http://html5doctor.com/)
* [HTML5 Validator](http://html5.validator.nu/)
* [Semantic HTML](http://en.wikipedia.org/wiki/Semantic_HTML)
* [CSS Tricks](https://css-tricks.com/dom/)

---
