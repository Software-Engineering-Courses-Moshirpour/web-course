# HTML

## Overview

On a webpage, we have three different "languages": HTML, CSS, and JavaScript.

HTML defines the content of a webpage. CSS defines the layout and styling (like color and font size). JavaScript provides interactivity (like the reaction of a webpage when you click a button).

HTML is a declarative language. There's no logic. It's just for declaring the different pieces of content on a webpage:

- This is an image
- That's a paragraph
- Those are checkboxes

HTML uses tags to declare content. Most tags (not all) are a pair of opening and closign tags. Take the paragraph tag as an example: opening tag `<p>` and closing tag `</p>`. Here's how to declare a paragraph in HTML:

`<p>This is a paragraph</p>`

Tags can be nested:

`<p>This is <strong>important</strong></p>`

A webpage is just a hierarchy of HTML tags, all within `<html></html>`. This hierarchy makes a tree that is called Document Object Model or DOM. DOM becomes important in writing CSS and JavaScript. The way we structure our content using HTML tags can make it more or less efficient when it comes to the performance of executing CSS or JavaScript code. They also have a direct effect on how good our website will appear on search engines, something known as Search Engine Optimization or SEO.

<br/>

<div style="text-align: center">
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/5/5a/DOM-model.svg/1200px-DOM-model.svg.png" alt="drawing" width="400"/>
</div>
<br>
<br>

In a nutshell, HTML provides meaning to our content. Take the following piece from the New York Times, for instance:

> **Alzheimer’s Prediction May Be Found in Writing Tests**

> IBM researchers trained artificial intelligence to pick up hints of changes in language ahead of the onset of neurological diseases.

Here's how we can give meaning to it with HTML tags:

```html
<article>
  <h1>Alzheimer’s Prediction May Be Found in Writing Tests</h1>
  <p>
    IBM researchers trained artificial intelligence to pick up hints of changes
    in language ahead of the onset of neurological diseases.
  </p>
</article>
```

Using CodePen, you can easily start writing HTML, CSS, and JavaScript without any setup on your system. Go to this [link](https://codepen.io/masoudkarimif/pen/ExNjPGZ) to find the above example in CodePen.

---

## Comments

Anything between `<!--` and `-->` will be considered as a comment and will not show up on the page. Bundler tools, such as Webpack, are smart enough to remove your comments to prepare your application for production. We will see this in action when we get to the React part of the course. However, removing comments is perhaps the simplest thing that tools like Webpack do. You can learn more about Webpack [here](https://webpack.js.org/).

```html
<!--This is a comment-->
```

---

## Inline and Block Elements

A block-level element, like `<div></div>` takes up the full width of the page and has top and bottom margins. An inline element, like `<span></span>`, on the other hand, does not start on a new line and only takes up as much width as necessary.

You will find an example on CodePen [here](https://codepen.io/masoudkarimif/pen/xxROjXQ?editors=1000). Also, here's a [link](https://www.w3schools.com/html/html_blocks.asp) for more information.

We may put inline elements inside other inline elements or block elements. But we don't put block elements inside inline elements.

---

## Browser Developer Tools

All major browsers provide developer tools that help you test and debug your application. We will see the value of these tools when we get to the CSS and JavaScript part of the course. [Here](https://www.youtube.com/watch?v=x4q86IjJFag&ab_channel=TraversyMedia) you can find a crash course on the Google Chrome Developer Tools (51 mins).

---

## HTML Attributes

HTML elements can accept multiple attributes. This is how we add an attribute to an HTML element:

```html
<p attribute-name="attribute-value">...</p>
```

There are two kinds of attributes:

**Global** attributes are the ones that can be added to any element. Examples of Global attributes are the `id` and `class` attribute. These attributes become crucial when we get to the CSS and JavaScript part of the course.

There are also attributes that only apply to certain elements. For example, the `href` attribute applies to the `<a>` or Anchor element. You will find more information about HTML attributes [here](https://www.w3schools.com/html/html_attributes.asp).

---

## Relative vs Absolute Links

When it comes to linking a file or a page on your website, there are usually two ways to do it:

**Relative** paths start from your current location, whereas **Absolute** paths are the full URL of a file. When possible, it is recommended to use Relative paths as they are more reliable and there's less chance they may break in production. You will find more information [here](https://www.w3schools.com/html/html_filepaths.asp).

---

## Images

We can define images and illustrations using the `<figure></figure>` element. It also gives us the ability to add a caption.

```html
<figure>
  <img src="PATH_TO_THE_IMAGE" alt="ALTERNATE_TEXT" />
  <figcaption>Figure Caption</figcaption>
</figure>
```

The `alt` attribute will show up if for any reason the browser cannot show the image. For instance, if the file path is wrong or there is a problem with the connection. You will find more information [here](https://www.w3schools.com/tags/tag_figure.asp).

Note that for the `src` attribute, you can use both relative (if the file is on your servers) and absolute paths, as discussed before.

---

## Generic Elements

It's a very good practice to find an appropriate HTML tag for your content. If you are writing a paragraph, it's best to use the `<p></p>` element, for instance; and if the paragraph is part of an article, it's best to put it inside the `<article></article>` tag. These so called semantic elements help your website to become more optimized when it comes to search engines.

However, in case you don't come up with an appropriate elemenet, you can use the generic elements. For block-level elements, you can use the `<div></div>` element, and for inline elements, you can use the `<span></span>` element.

---

## Head of the Document

In an HTML document, the `<head></head>` element is where you provide metadata about your page and link your external files such as CSS and JavaScript. The content of the `<head></head>` element does not show up on the page. The most important elements that go inside the `head` are:

- `<title>` for declaring the title of the page. This title will show up on the tab of the browser
- `<meta>` for providing metadata about the page. These data are used by search engines
- `<link>` for linking external CSS files to your page
- `<script>` for linking JavaScript (internal or external) to the page

You will find more information about the `head` element and what usually goes in there [here](https://www.w3schools.com/tags/tag_head.asp).

---

## Forms

Forms are the main way to get data from users. HTML provides a broad range of elements and attributes when it comes to form. You will examples about these elements [here](https://www.w3schools.com/tags/tag_form.asp).

Before the advent of AJAX (Asynchronous JavaScript And XML), people needed to send from data to another page (or the sample page), which would force the browser to redirect (or refresh) the page. That's what the `action` attribute of a form is about. The data will be sent to whatever address you put as `action`. This approach is not considered best practice anymore. Nowadays, we send asynchronous calls (usually via REST API) and update the page without a refresh and redirect. Just think about web applications you use every day. Most, if not all of them must be using the same approach. Think of liking a post on Facebook. Does the browser redirect you to another page or reload your feed? No. You just wait a few moment for the data to be sent to the backend, and will see the result afterward. That is considered best practice today and we will talk about that when we get to the JavaScript part of the course.

You will find more information about AJAX [here](https://www.w3schools.com/js/js_ajax_intro.asp).

---

## Tables

We use tables only when we want to show tabular data. That might seem like a given, but there was a time when people would use tables for designing the layout of a page. That is no longer the case. We design the layout using CSS which we will discuss in a later session. Declaring a table in HTML is fairly easy. Here's an [example](https://codepen.io/masoudkarimif/pen/YzpWjWe?editors=1000) on CodePen. You will find more information and examples [here](https://www.w3schools.com/tags/tag_table.asp).

---

## Additional Resources:

- [W3School](https://www.w3schools.com/html/default.asp)
- [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/HTML)
- [StackOverflow](https://stackoverflow.com/questions/tagged/html)
