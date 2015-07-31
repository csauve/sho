# Sho
A command-line tool for creating simple, self-contained HTML slideshows from Markdown documents. Use horizontal rules to separate slides:
```md
# Title Page Header
## A subheader

---

### Slide 1 Header
Bacon ipsum dolor amet [frankfurter brisket](www.example.com).
* jowl ham hock hamburger
* kielbasa shank short ribs

Short loin `spare ribs` pork doner venison.
```
![sho slides example 1](http://csauve.github.io/sho/examples/example-1.png)

## Features
* Comes pre-styled so you can concentrate on content
* [CommonMark](http://commonmark.org/) support with sensible defaults
* Code highlighting with [highlight.js](https://highlightjs.org)
* Arrow-key navigation
* Slide progress bar
* Can watch your source file for continuous editing
* Generated HTML has no external dependencies
* Text scales down for low resolution projectors and screens
* Supports background images and colours
* Included CSS for left/right floating images

## Getting Started
Requires [Node.js](https://nodejs.org/download/) to install and run:
```sh
$ npm install -g sho

# generates slides.html if slides.md is present
$ sho
# generates presentation.html
$ sho presentation.md
# or specify both paths
$ sho input.md output.html
# you can also watch files
$ sho presentation.md --watch
```
Just open the HTML file in your favourite browser and you're ready to go!

## Helpers
CommonMark allows the [inclusion of HTML tags](http://spec.commonmark.org/0.21/#html-blocks) in your markdown. Sho's stylesheet has some special classes and IDs can be used to customize your slides:

![sho slides example 1](http://csauve.github.io/sho/examples/example-2.png)

### Backgrounds
To include a **background image in all slides**, add an `img` tag with `id="background"` anywhere in your Markdown document. The `src` should be relative to the destination HTML file:
```md
<img id="background" src="images/background.jpg"/>

# Title Page
etc...
```

To include a **background image in one slide**, add an `img` tag with `class="background"` inside the slide you want affected. This background will override an all-pages background.
```md
---

<img id="background" src="images/slide5-bg.jpg"/>
### Slide 5
etc...

---
```

For a **solid colour background**, a styled span with `class="background"` or `id="background"` will behave the same way:
```md
<span id="background" style="background: #380b35"/>
# All slides are purple by default

---

<span class="background" style="background: green"/>
### Slide 1
This slide is green.
```

### Formatting
To **center-align** text, wrap it in a `class="center"` div. Don't forget to [pad inner Markdown with blank lines](http://spec.commonmark.org/0.21/#example-120):
```md
<div class="center">

by [@Author](www.author.example.io)

</div>
```

You can **left/right float images** by adding the corresponding class to an `img` tag:
```md
<img src="images/example.jpg" class="right"/>
```

## API
This module can programmatically transform Markdown files. Install the module non-globally:
```sh
npm install sho
```

Then require and call Sho:
```js
var sho = require("sho");
sho("~/docs/input.md", "~/docs/output.html");
```

## Alternatives
Sho is pretty minimal and might not fit your needs. It is inspired by [Cleaver](https://github.com/jdan/cleaver) and [reveal.js](http://lab.hakim.se/reveal-js/#/).

## Contributing
1. Fork this repo
2. Clone your fork
3. Install dependencies with `npm install`
4. Hack away!
5. Use `npm link` to test your edited Sho on the command-line
6. Commit and push changes to your fork
7. Create a pull request describing the change

License: MIT