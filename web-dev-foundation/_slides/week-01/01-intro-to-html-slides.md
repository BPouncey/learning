---
layout: slidedeck
title: Intro to HTML Slides
---

{% highlight html %}
name: inverse
layout: true
class: center, middle, inverse

---

# Intro to HTML

.title-logo[![Red logo](../../public/img/red-logo-white.svg)]

---
layout: false

# Agenda

1. What is HTML?
2. Elements & Attributes
3. Creating a Webpage
4. Doctypes and Comments
5. Structural Tags
6. Semantic Tags

---
template: inverse

# What is the Web?

---
class: center, middle

![HTTP request diagram](/public/img/slide-assets/http-request-diagram.svg)

---
template: inverse

# What is HTML?

---
class: center, middle

### What does "HTML" mean?

HTML stands for **HyperText Markup Language**.

It helps us describe the structure of webpage, and its connections with other webpages.

---

# HTML Defined

**HyperText** is a system of clickable text links that let you view information in a non‐linear way.

Hypertext also relates to **hyperlinks**, which applies to media and non‐text links, such as images or buttons.

Links don’t necessarily always get you to another page, a hyperlink can also be set-up to run a script that can play a video or sound, or make something happen dynamically.

---
class: center, middle

.inline-images[
   ![Traditional documents](/public/img/slide-assets/html-traditional-doc.svg)
]

---
class: center, middle

.inline-images[
   ![HyperText documents](/public/img/slide-assets/html-hypertext-doc.svg)
]

---

# HTML Defined

A **markup language** provides a set of rules for how we use characters and symbols (knowns as **tags** or **elements** in HTML) to annotate text to provide information about its structure or presentation.

HTML simply tells our browser how to structure the text and media on a webpage.

---

# HTML Defined

But not all markup is created equal!

In HTML, we will see two different kinds of markup:

1. **Structural** markup
2. **Semantic** markup

*More on both of those in a minute...*

---
template: inverse

# Elements & Attributes

---
class: center, middle

.inline-images[
   ![HTML element structure](/public/img/slide-assets/html-tag-structure.svg)
]

---

# Using HTML Elements

HTML elements are surrounded with angle brackets so the browser know how to distinguish them from the text that we actually see on a webpage.

Based on what the browser sees in the angle brackets, it knows how to render the structural format of the page.

HTML elements are often interchangeably called **tags**.

*Let's dive in and see how it works...*

---

# A Basic Element

If we wanted to markup a paragraph in HTML, our code would look like this:

```html
<p>The quick brown fox jumps over the lazy dog.</p>
```

Notice that the text is wrapped in `<p>` tags, and the closing tag contains a `/` after the opening angle bracket.

---

# A Basic Element

And if we want to add a second paragraph, we'll enclose its text inside of its own set of `p` tags:

```html
<p>The quick brown fox jumps over the lazy dog.</p>
<p>Grumpy wizards make toxic brew for the evil Queen and Jack.</p>
```

---

# Adding Attributes

An **attribute** is a bit of information we add inside the element's opening tag.

They are made up of two parts, a **name** and a **value** that are separated by an equal sign:

```html
<p lang="fr">Bonjour mes amis!</p>
```

HTML offers many different attributes. Some can be used **globally** on any element, but many are **element-specific**.

---

# Nesting Elements

We can also **nest** our tags in HTML. For example, to add emphasis to our paragraph text we can use the `<em>` tags.

```html
<p><em>The quick brown fox jumps over the lazy dog.</em></p>
```

Think of nested tags like Russian *Matryoshka* dolls.

---

background-image: url(/public/img/slide-assets/russian-nesting-dolls.jpg)

.footnote.white[
   Image Credit: [Bradley Davis](https://www.flickr.com/photos/backpackphotography/2318055128/)
]

---

# Escape Characters

Some characters are reserved for HTML so we need to use **special codes** to represent them in our document.

For example, if we want to use curly double quotes around text, we would use these codes:

```html
<p>&#8220;Off with her head!&#8221; the Queen shouted at the top of her voice. Nobody moved.</p>
```

Codes can also be used to represent symbols like &copy; or &trade;.

You can find HTML codes for many characters on **[copypastecharacter.com](http://copypastecharacter.com/)**.

---
template: inverse

# Creating a Webpage

---
class: center, middle

### What makes a webpage?

To create a basic webpage, we need three things: a code editor, a file with a `.html` extension, a handful of HTML elements inside it that are common to all webpages.

---

# Code Editors

Any program that edits plain text files can be used as a code editor (e.g. Notepad on Windows or TextEdit on a Mac).

But programs that are specially designed for editing code offer extra features like **syntax highlighting**.

Some good (free) code editor options include:

- **[VS Code](https://www.visualstudio.com/en-us/products/code-vs.aspx)**
- **[Atom](https://atom.io/)**
- **[Sublime Text](http://www.sublimetext.com/)**

---

# Building Blocks

Virtually all websites share the same basic structure. They contain a `<head>` and a `<body>`, and those two elements are wrapped in `<html>` tags:

```html
<html>
   <head>
      <title>This is the Page Title</title>
   </head>
   <body>
      <p>This is a paragraph.</p>
   </body>
</html>
```

Let's copy that HTML into a code editor, save the file as `index.html`, and open it in a web browser.

---
class: center, middle

### Why call it index.html?

When you name a file `index.html` (most) web servers will automatically know that this is the homepage.

---

# One Folder = One Site

Before long, you're going to want to add additional pages to your site, or other files (like images).

To keep all of those HTML files and your other webpage assets organized, you'll want to set up a folder somewhere on your computer.

We call this the **root folder** of your project. You can name it anything you'd like and it can contain any number of sub‐folders to further organize your files.

---
class: center, middle

.inline-images[
   ![Root folders](/public/img/slide-assets/html-folder-structure.png)
]

---

# Organizing Your Files

You'll want to put some thought in ahead of time to decide how you want to organize your **sub-folders** and **files**.

This is especially important for your media files, so you don't end up with *broken media* links later...

.inline-images[
   ![Broken image link](/public/img/slide-assets/broken-image-link.jpg)
]

---

#  New Site = New Folder

You'll also want to create a new `root folder` for each *different* website that you build:

.inline-images[
   ![Root folders](/public/img/slide-assets/html-multiple-sites.svg)
]

---

# File/Folder Naming Tips

Use these sanity-saving tips to name your folders and files:

- Stick to lowercase consistently
- Don't use spaces in your file names, instead use hyphens or underscores to separate words
- Don't use special characters in your file names
- Choose logical and descriptive names for files and folders

---

# Exercise 1

Your turn! Time to create your first webpage.

First things first...you need to pick a code editor to download and install it (if you haven't done so already).

Next create a root folder somewhere on your computer and save a new file called `index.html`.

Then open that folder and create a simple webpage containing `<html>`, `<head>`, `<title>`, and `<body>` tags, then add a few paragraphs of text.

Lastly, save and view your new website in a browser.

---
template: inverse

# Doctypes & Comments

---

# A Little Bit of History

Doctypes have a long and complicated history on the web.

The important thing to know is that the doctype declaration is not an HTML tag, but rather tells the browser which version of HTML the webpage uses.

---

# Then & Now...

**XHTML:**

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN" "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
```

**HTML5:**

```html
<!DOCTYPE html>
```

---

# Where Does It Go?

Doctype declarations go at the top of your `.html` files:

```html
<!DOCTYPE html>
<html>
   <head>
      <title>This is the Page Title</title>
   </head>
   <body>
      <p>This is a paragraph.</p>
   </body>
</html>
```

---

# Meta Tags

In addition to adding a doctype, there's other information we can add to the `<head>` of our document using `meta` tags to help with rendering and describing our webpage:

```html
<!DOCTYPE html>
<html>
   <head>
      <meta charset="utf-8">
      <title>This is the Page Title</title>

      <meta name="description" content="A most excellent website">
      <meta name="author" content="RED Academy">
   </head>
   <body>
      <p>This is a paragraph.</p>
   </body>
</html>
```

---

# Comments

Similar to the doctype declaration, comments aren't HTML elements per se.

Adding comments to our HTML is a good practice to help us **document** our code for ourselves and others.

```html
<!-- This text will not be visible in the browser window. -->
<p>The quick brown fox jumps over the lazy dog.</p>

<!-- <p>We can comment-out elements to temporarily hide them.</p> -->
```

---
template: inverse

# Structural Tags

---

# Headings

We've already seen the `<p>` element in action, now let's take a look at headings.

In HTML, you can denote 6 different levels of headings with markup like so:

```html
<h1>Heading 1</h1>
<h2>Heading 2</h2>
<h3>Heading 3</h3>
<h4>Heading 4</h4>
<h5>Heading 5</h5>
<h6>Heading 6</h6>
```

---

# Lists

In HTML we can create both **ordered** and **unordered** lists:

```html
<ol>
   <li>Mix ingredients</li>
   <li>Put cake in oven</li>
</ol>
```

```html
<ul>
   <li>Apples</li>
   <li>Oranges</li>
</ul>
```

We can also create something called a [definition list](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/dl) in HTML, but those are a bit advanced.

---

# Whitespace

We can create whitespace in HTML using line breaks:

```html
<h1>Stopping by Woods on a Snowy Evening</h1>
<p>Whose woods these are I think I know.<br />His house is in the village though...</p>
```

Or horizontal rules:

```html
<p>This paragraph talks about a specific topic.</p>
<hr />
<p>This paragraph shifts to a different topic.</p>
```

Notice something special about these elements? They don't contain any text, and are represented by a single, self-closing tag. These are called **empty elements**.

---

# Divs

You'll likely also run into a structural element called a `<div>`:

```html
<div>
   <p>The quick brown fox jumps over the lazy dog.</p>
</div>
```

A `<div>` element is mostly used for flowing content, but with HTML5 we now have more semantic structural elements...

---
class: center, middle

.inline-images[
   ![HTML5 example layout](/public/img/slide-assets/html5-semantic-tags.png)
]

---

# HTML5 Goodies

So an HTML5 webpage might look a little something like this:

```html
<header>
   <h1>Article Title</h1>
</header>
<article>
   <section>
      <p>The paragraph goes here...</p>
   </secton>
   <aside>
      <p>"The aside goes here..."</p>
   </aside>
</article>
<footer>
   &copy; 2015.
</footer>
```

---

# Exercise 2

Try marking up this block text as instructed. If you haven't created a Codepen account yet, do that right now and complete this exercise by clicking "Edit on Codepen", and create a "Fork" of the pen to save your answer to your account.

<iframe height='268' scrolling='no' src='//codepen.io/redacademy/embed/WvjrrR/?height=268&theme-id=0&default-tab=html' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/redacademy/pen/WvjrrR/'>WvjrrR</a> by RED Academy (<a href='http://codepen.io/redacademy'>@redacademy</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

---
template: inverse

# Semantic Tags

---
class: center, middle

### Structural vs. Semantic?

Semantic elements don't affect the structure of a webpage, but they do add extra information about its content

---

# Strong & Emphasis

The `<strong>` tag indicates that the text contained within is of strong importance:

```html
<p><strong>Warning!</strong> This is extremely dangerous.</p>
```

A browser will display this text as bold by default.

The `<em>` tag indicates a subtle shift in meaning of the text:

```html
<p>The most important thing is <em>that you do not quit!</em></p>
```

A browser will display this text as italicized by default.

---
template: inverse

# Last but not least...

---

# Link Elements

Links are the lifeblood of the web, so let's take a look at how we make one:

```html
<p>The <a href="https://developer.mozilla.org/en-US/" target="_blank">
Mozilla Developer Network</a> is a great resource!</p>
```

**Note** that any text contained within the `<a>` tags will be linked to the page inside the quotes of the `href` attribute. The `target` attribute is typically used to call a new window or tab to open for external links. Internal links don't need the `target` attribute.

---

# Link Elements

Links can also be **relative** to the root folder of your website:

```html
<a href="about.html">About Us</a>
```

And if a page is in a sub-folder:

```html
<a href="sub_pages/about.html">About Us</a>
```

---

# Link Elements

Links can point to email addresses too if we add `mailto:` at the front of the `href` value followed by an email address:

```html
<a href="mailto:mandi@redacademy.com">Email Mandi</a>
```

When a user click this link, it will open their default email application with the email address in the "To:" line.

---

# Image Elements

And of course, images!

```html
<img src="images/grump-cat.jpg" alt="Grumpy Cat scowls furiously" />
```

An `<img>` element has two important attributes:

- `src` tells the browser where to find the image
- `alt` provides a description of the image so the content can be understood by screenreader software and search engines

---

# Image Elements

We can also specify `title`, `width`, and `height` attributes:

```html
<img src="images/grump-cat.jpg" alt="Grumpy Cat scowls furiously again" title="The Grumpiest Cat on the Web" width="480" height="320" />
```

The `title` of the image will appear as a tooltip in most browsers when you hover over it.

---

# Exercise 3

Now try using an assortment of structural and semantic tags:

<iframe height='268' scrolling='no' src='//codepen.io/redacademy/embed/VLbemJ/?height=268&theme-id=0&default-tab=html' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='http://codepen.io/redacademy/pen/VLbemJ/'>VLbemJ</a> by RED Academy (<a href='http://codepen.io/redacademy'>@redacademy</a>) on <a href='http://codepen.io'>CodePen</a>.
</iframe>

---

# Exercise 4

Let's dive right in and start thinking about how we might tackle the first project's design comp to convert it into semantically-appropriate HTML elements.

Jot some idea out on your own, then you'll pair up to discuss your approach with a partner. Based on this discussion, is there anything you'd revise in your approach?

Finally, you and your partner will share your insights with the class.

---

# What We've Learned

- What HTML is and it's basic elements
- How to create a webpage on your computer
- The difference between structural and semantic elements
- New HTML5 elements
- How to create links and add images

---

template: inverse

# Questions?

{% endhighlight %}
