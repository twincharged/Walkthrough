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
