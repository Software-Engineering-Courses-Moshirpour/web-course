# CSS

CSS is responsible for the styling of a webpage. There are basically 3 ways to add CSS to webpages:

- External (also the most common one) is when you have a separate CSS file (or files). We link external CSS files to webpages inside the HTML `head` element.
  ```html
  <link rel="stylesheet" href="mystyle.css" />
  ```
- Internal is when styling happen inside HTML files (rather than separate files). It is also common to add interal CSS inside the HTML `head` element.
  ```css
  body {
    background-color: #f1f1f1;
  }
  p {
    text-align: center;
  }
  ```
- Inline is when we add styling directly to HTML elements.
  ```css
  <p style="text-align:center">This is a test</p>
  ```

In terms of priority, here is the order:

1. Inline
2. Internal
3. External

That means, in case we have External, Internal, and Inline styling for an element, Inline styles win. It's good practice to only stick with one method (Internal, External, or Inline) to avoid conflicts. Also, as mentioned above, External CSS is the most common approach, as it keeps our project clean and provides separation of concerns.

_Note: There is another way to add CSS to a webpage and that's called CSS in JavaScript. We will get to that later in the course!_

For more info about adding CSS to webpages, check out this [link](https://www.w3schools.com/css/css_howto.asp).

## Adding CSS to HTML Elements

In order to add styling to HTML elements, you first need to grab or specify that element. There are 3 main ways to do that:

- by tag name
- by tag id
- by tag class

Each of these methods have their use cases and based on different scenarios one of them would make more sense to use.

For example, if you need to apply the same style to every `<p></p>` element, choose styling by tag name:

```css
p {
  text-align: center;
  color: #444;
  padding: 10px 5px;
}
```

However, you may have a situation in which you need to apply these styles to a group of `<p></p>` elements, but not all of them. In this case, it makes more sense to use styling by class.

```html
<p class="center-aligned">...</p>
<p class="center-aligned">...</p>
<p class="center-aligned">...</p>
<p class="right-aligned">...</p>
<p class="right-aligned">...</p>
```

```css
p.center-aligned {
  text-align: center;
}
p.right-aligned {
  text-align: right;
}
```

Also, you will run into sitations where you only need to apply a set of styles to only one element. That's when styling by id would make more sense.

```html
<p class="special-p">...</p>
<p class="center-aligned">...</p>
<p class="right-aligned">...</p>
```

```css
p#special-p {
  color: blue;
}
```

## CSS Specifity

In case of conflicts, browsers adhere to a set of rules to find the winner. These rules are called Specifity. Basically, the more specific and detailed style wins the conflict. CSS specifity can get really complicated and there's actually a way to calculate the specifity of an style. Here's the simplified version of the rule (it could get more complicated that this):

> Start at 0, add 1000 for style attribute, add 100 for each ID, add 10 for each attribute, class or pseudo-class, add 1 for each element name or pseudo-element.

For instance, which style do you think wins the following conflict:

```css
div#some-id {
  color: black;
}
div.some-class {
  color: blue;
}
```

Since selecting an element by ID is more specific than selecting by class, the first style wins. In terms of actuall weight in numbers, the first one has the weight of 101 (one tag name and one id) and the second one 11 (one tag name and one class).

When two or more styles have the same weight or specifity, the last one wins.

```css
div.some-class {
  color: blue;
}
div.some-class {
  color: black;
}
```

Since the second style appears last, it will win the conflict.

For more infor on CSS Specifity, please check out this [page](https://www.w3schools.com/css/css_specificity.asp).

## CSS Examples

This [page](https://www.w3schools.com/css/css_specificity.asp) contains many examples on every CSS topic. You can run and edit the examples as well. If you don't have time, you can check out the first two, three examples in each section to get a sense of what they are about.

## CSS Frameworks

It usually takes a significant amount of time to write all the CSS of a website from scratch. That's why CSS frameworks are so popular nowadays. A CSS framework is a set of predefined styles ready to get applied to your HTML. Instead of writing your own CSS, you would simply assign predefined CSS classes from a framework.

Aside from the fact that you would save a huge amount of time by using a CSS framework, it would also make your website more robust, as CSS frameworks have been tested against all major browsers and do not contain common mistakes. More often than not, they are open source projects, which means there are houndreds, if not thousands of people contributing to these projects. So, it really makes sense to start with a CSS framework for your website.

Furthemore, the fact that most CSS frameworks are open source projects also means that you have complete control to change and modify the framework to your liking. Most CSS frameworks are written in Less or Sass and are highly organized and ready for modifications.

Among most popular CSS frameworks, here is a short list:

- [Bootstrap](https://getbootstrap.com/)
- [Bulma](https://bulma.io/)
- [Fundation](https://get.foundation/)
- [UIKit](https://getuikit.com/)
- [Materialize](https://materializecss.com/)

## Less and Sass

CSS doesn't quite seem like a programming language, as it lacks variables and functions and etc. Less and Sass are two main projects that aim to fix this problem.

Let's look at a scenario. Assume we have a CSS file containing these styles:

```css
p {
  color: #444;
  text-align: right;
}
h1,
h2 {
  color: #444;
  text-align: center;
}
aside {
  background-color: #444;
  float: right;
}
```

Now, let's imagine we've decided to change the color of our paragraphs and header elements from `#444` to `#666`. One way to do this is to use your editor's capabilities to replace `#444` with `#666`. But, note that we also have a `aside` element with the same color as its background which we do not want to change. This is of course a very short file and it's just a super simple example. But you get the idea. Even with your editor's capabilities, it's difficult to apply such changes, which by the way happens more than you think. Only if there was a way to assign use variables here. Well, that's why Less and Sass were created. Here's how we can re-write the same styles with Less:

```less
@text-color: #444;
@aside-bg-color: #444;
p {
  color: @text-color;
  text-align: right;
}
h1,
h2 {
  color: @text-color;
  text-align: center;
}
aside {
  background-color: @aside-bg-color;
  float: right;
}
```

Here, for changing the color of `p` and `h1, h2` we only need to change the value of `@text-color` variable:

```less
@text-color: #666;
```

More interestingly, we can separate our files and have a completely separate file for just our variables:

```less
@import "variables";
```

There are many more capabilities that come with Less. You can check out a lot examples on the official [website](http://lesscss.org/).

Sass is a lot like Less with minor differences. For instance, in order to define a variable in Sass, we would use the `$` sign instead of the `@` sign:

```css
$text-color: #444;
```

You can find many examples on the official [website](https://sass-lang.com/documentation/).

Most if not all CSS frameworks are written in one of these two languages. Because it would be so difficult to maintain a huge CSS project without the capabilities that these languages offer. For instance, [Bootstrap](https://getbootstrap.com/) uses Less, while [Bulma](https://bulma.io) uses Sass.

If you are looking for a good article explaining the differences between Sass and Less, take a look [here](https://css-tricks.com/sass-vs-less/).
