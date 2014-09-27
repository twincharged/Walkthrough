Walkthrough
===========

Walkthrough for installing and using some packages


## Node.js

Node.js is a technology that allows you to run JavaScript on the server. You'll need it to install many libraries and frameworks. Install Node.js for your Windows machine here: http://nodejs.org/download/ . Node.js will come with something called NPM. NPM is a "package manager". This means that it will help you download, update, and keep track of all of the free, open source JS packages that are registered with it, which is about 100,000.

When Node is done installing open your powershell and type `npm install -g jade` and `npm install -g stylus`. This is how you will be using NPM to install packages of your choosing in the future. You type `npm install [your package name]`. The `-g` means that it will install the package globally, meaning you can access it from anywhere in your system. Here's NPM's website: https://www.npmjs.org. You can look up any/all packages there (or on GitHub since they're all there also).


## Jade

Jade is epic. It's a preprocessor. A preprocessor means that it will give you extra facilities to use and it will translate down into a language (in Jade's case it translates to HTML). Jade aims to help you easily build more maintainable, intelligent, and beautiful HTML. Here's a rundown of its main features.

Jade code:

```jade
doctype html
html(lang="en")
  head
    title Modules
    meta(name="viewport" content="width=device-width, initial-scale=1")
    link(href="./css/demo.css" rel="stylesheet")
    script(src="./js/index.js")
  body
    section#intro
      .container
        .row
          .col-md-12
            .dashed
              | This is my new HTML page!
        .row
          .col-md-6
            a.box.outer(href="#") Outer
          .col-md-6
            a.box.target(href="#") Target
```
And here's the equivalent HTML it compiles to:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Modules</title>
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link href="./css/demo.css" rel="stylesheet">
    <script src="./js/index.js"></script>
  </head>
  <body>
    <section id="intro">
      <div class="container">
        <div class="row">
          <div class="col-md-12">
            <div class="dashed">This is my new HTML page!</div>
          </div>
        </div>
        <div class="row">
          <div class="col-md-6"><a href="#" class="box outer">Outer</a></div>
          <div class="col-md-6"><a href="#" class="box target">Target</a></div>
        </div>
      </div>
    </section>
  </body>
</html>
```

There's two huge syntax differences. Jade lets you forgo the angle brackets and makes you instead use parenthesis to surround the element's attributes.
Example:

```jade
link(href="./css/demo.css" rel="stylesheet")
```
versus
```html
<link href="./css/demo.css" rel="stylesheet">
```

The second difference is that Jade allows you to skip all closing tags if you use indentation instead. This is the same concept as CoffeeScript and Stylus (which are also preprocessors). Example:
```jade
html(lang="en")
  head
    title Modules
  body
    p Hello!
```
versus
```html
<html lang="en">
  <head>
    <title>Modules</title>
  </head>
  <body>
    <p>Hello!</p>
  </body>
</html>
```
There are a couple more important things. Ids and classes are different. In Jade, you should use ids and classes like you would in css (with the #hash and the .dot). Example:
```jade
section#intro.background-black
  p.large-text.centered Jade is awesome!
```
versus
```html
<section id="intro" class="background-black">
  <p class="large-text centered">Jade is awesome!</p>
</section>
```
One more quick thing that is optional, but generally considered good practice: you don't have to type `div` tags. This is because they're the most common tag. Example:
```jade
#main-box.background-red
  p Cool, huh?
  
// is the same as this:

div#main-box.background-red
  p Cool, huh?
```
versus the compiled html
```html
<div id="main-box" class="background-red">
  <p>Cool, huh?</p>
</div>
```

When ou create your first Jade file, you compile it using the NPM package you downloaded. Just go to the powershell and type `jade [your file name].jade` and it will create the equivalent HTML file in the same directory as the Jade file that you just compiled. As far as Jade sublime syntax highlighting goes, you can download it by going into Sublime and hitting `ctrl`+ `shift` + ` p` and start typing `install` in the prompt. Select the box that says "Package control: install package". You will be given another prompt. Type in "jade" and select the package by davidrios. If the syntax of your Jade file doesn't automatically update, go to the bottom right of sublime and select Jade (not the python version) from the list. More Jade info here: http://jade-lang.com/


## Stylus

Stylus shares a lot of the same principles as Jade. Aka:
```sass
body
  font: 12px Helvetica, Arial, sans-serif
  color: #333

a.button
  border-radius: 5px
```
compiles to
```css
body {
  font: 12px Helvetica, Arial, sans-serif;
  color: #333;
}
a.button {
  border-radius: 5px;
}
```
You can forgo typing the semicolons and braces by using indentation. You can also forget the colons, but don't. It just makes it confusing without them. There are three more really important things with Stylus that you'll use often: nesting, variables, and mixins.

Variables are the simplest. You just assign any css value you want to a variable. Example:
```sass
$main-color = #777
$main-fonts = Helvetica, Arial, sans-serif

// and use them like this:

body
  color: $main-color
  font-family: $main-fonts
```

Nesting is very useful for organization and logic. Example:
```sass
section#intro
  background: #555
  & .main-box
    color: #999
    &:hover
      color: #111


// is equivalent to this:

section#intro
  background: #555

section#intro .main-box
    color: #999

section#intro .main-box:hover
    color: #111
```

To use, you just indent the specific css sub-classes (like `.main-box` and `.main-box:hover` in this case) under the parent element (`section#into`) and use the `&` sign to reference the parent element. This means that, in the example above, the first `&` sign references the `section#intro` and the second, more indented `&` sign references `section#intro .main-box`.

Mixins are fairly easy to understand. Just think of them as reusable chunks of code. Example:

```sass
placement(tp, rt, bm, lt)
  top: tp
  right: rt
  bottom: bm
  left: lt

section#intro
  color: #333
  placement(5px, 10px, 5px, 10px)

// will create this:

section#intro
  color: #333
  top: 5px
  right: 10px
  bottom: 5px
  left: 10px
```

It's like calling a JS function, but it'll place everything in the function body inside whatever element it is called.
