# Novicell Frontend

Novicell Default Frontend package is a framework for your frontend setup and a Gulp based boilerplate for optimizing your frontend flow. It includes a BEM'ified version of Bootstrap's bare necessities (LESS), for starting your new website's development.
When setup, it also helps you optimize images, combine SVGs to a sprite, compiling LESS to CSS and minifying Javascript.

### Table of content
* [Quick start](#quick-start)
* [Installation](#installation)
* [Setup](#setup)
* [What is GULP](#what-is-gulp)
* [How to use GULP](#how-to-use-gulp)
* [Tasks in this package](#tasks-in-this-package)
* [How to use SVG sprite sheet](#how-to-use-svg-sprite-sheet)
* [LESS components](#less-components)
  * [The grid](#the-grid)
  * [Buttons](#buttons)
  * [Forms](#forms)
  * [Tables](#tables)
* [JS components](#js-components)
  * [To be done](#to-be-done)
  * [Lazyload images](#lazyload-images)
* [Notes](#notes)
* [Requirements](#requirements)
* [License](#license)

## Quick start

Browse to your project folder and clone the repo `git clone https://github.com/novicell/novicell-frontend.git`. Then run `npm install` and then run `gulp` for the build proccess to start.


##  Installation

- Download and install Node.js v. 4.x.x (https://nodejs.org/download/)
- Download and install Git (http://git-scm.com/downloads)
  Remember to check "Git bash here" in context menu options

  To check if node is working, go to Gitbash / Terminal and type `node -v`
  If you get a version number, you'r good to go.

##  Setup

First navigate to your website and install novicell frontend package:

    cd "c:\Visual studio projects\project-name\Project.Website"
    npm install github:Novicell/novicell-frontend
    npm install


## What is GULP

GULP is a streaming build system - or short for:

"I'll take care of minifiyng the images, scripts, styles and icons
* now you just focus on doing what you do best: CODE!"

## How to use GULP

First navigate to your website

    cd c:\"Visual studio projects"\project-name\Project.Website

* To build whats already in there (runs the build task): `gulp`
* To never touch the cmd window again (runs the watch task): `gulp watch`
* To Stop/Restart GULP: `CTRl + c`

All tasks can be run like: `gulp <task name>`.

## Tasks in this package

The following tasks are available:

* build -	Runs all the tasks defined in: gulp-config.json > tasksToBuild
* clean -	Deletes the files/directories defined in: gulp-config.json > pathsToClean
* rebuild -	Runs the clean task, and then the build task.
* styles -	Minifies and bundles CSS files defined in: gulp-config.json > bundles > {bundleName} > styles
* scripts -	Minifies and bundles JS files defined in: gulp-config.json > bundles > {bundleName} > scripts
* images -	Minifies images defined in: gulp-config.json > bundles > {bundleName} > images
* icons -	Minifies and generates a svg sprite, from the icons defined in: gulp-config.json > bundles > {bundleName} > icons
* copy -	Copies the fonts defined in: gulp-config.json > bundles > {bundleName} > fonts
* hhtml - Looks through the html folder for `@@include`, to then partially replace them when compiling the html file
* watch

  * Runs the scripts, styles, images, icons and fonts task whenever a file has changed. The paths it listens on, is defined in the file gulp/config.json > watch.
  * Also it automatically refreshes your browser window, using livereload (port can be changed in gulp/config.json > livereload > port).

  Google Chrome Plugin: https://chrome.google.com/webstore/detail/livereload/jnihajbhpnppcggbcgedagnkighmdlei

  * Generates sourcemaps for CSS and JS.

NOTE: The distribution path for each task, can be defined in gulp/config.json - so can the basePath.

## How to use SVG sprite sheet

Use SVG's from the SVG sprite generated by GULP like the following. The `#icon-lock` is the ID of the current SVG in the sprite. This is based on the name of the original SVG in the `/images/icons/`-directory.
So ´/images/icons/lock.svg` are referenced like this:

```html
<svg class="icon icon-lock">
  <use xmlns:xlink="http://www.w3.org/1999/xlink" xlink:href="/dist/icons/icons.svg#icon-lock"></use>
</svg>
```

## LESS components
A basic variant of Bootstrap LESS, converted to BEM architecture and syntax for Novicell's projects.
There's a few basic setups that you will always need for all your projects. Buttons, Grid, Form elements, Tables. (Well, maybe you'll use tables).
There's also an example of a component and a view, just to show how the naming convention should be, as well as how you should both write and organize your LESS files.

### The grid
There's a grid based on the ideas behind Bootstrap.
You can use it as you normally would, but write it a bit differently.
```html
<div class="container">
    <div class="row">
        <div class="col--xs-12 col--ms-6 col--sm-5 col--md-4 col--lg-12"></div>
    </div>
</div>
```
Notice the double dash? `xs` or any other breakpoint is regarded as a modifier of the column.

### Buttons
There's some default styling for buttons as well, including two modifiers.
```html
<button class="button">Primary button</button>
<button class="button button--secondary">Secondary button</button>
<button class="button button--ghost">Ghost button</button>
```

### Forms
Default styling for form inputs. In regards to checkboxes and radiobuttons, refer to the `base.forms.less` file.
```html
<input type="text" class="input" placeholder="Default input">
```

### Tables
```html
<table class="table">
    etc...
</table>
```

## JS components

### To be done
- [ ] novicell.js
- [ ] novicell.visible.js
- [ ] novicell.debounce.js
- [ ] novicell.overlay.js
- [ ] novicell.embed.js
- [ ] novicell.cookieinfo.js

### Lazyload images
Include the `novicell.lazyloadResponsive.js` for lazyloading images.
You need to call images like this, and then the javascript will add querystrings for the [imageprocessor.web](http://imageprocessor.org/imageprocessor-web/) component. More `filters` and other settings can be found on the [imageprocessor documentation](http://imageprocessor.org/imageprocessor-web/imageprocessingmodule/filter/).


```html
<figure vocab="http://schema.org/" typeof="ImageObject"
  data-src="https://www.novicell.dk/media/3746/novicell_kopny.png"
  data-height-ratio="0.3"
  data-focalpoint="0,5,0,5"
  data-mode="crop"
  data-quality="75"
  data-is-background="true"
  data-parent="#parent"
  data-original-width="1337"
  data-filter="greyscale">
  <noscript class="responsiveLazyload">
      <img src="https://www.novicell.dk/media/3746/novicell_kopny.png"
      alt="Lazyload image demo"
      title="Lazyload image demo"
      property="contentUrl" />
  </noscript>
  <figcaption property="description">Lazyload image demo</figcaption>
</figure>
```
#### Description and rules
The original purpose of using the lazyloadResponsive.js is to always serve an optimal resized image depending on the user's viewport. Through time it has become a powerful script to manipulate images. There a several options you can set on your <figure>:
* data-src - the clean source of the image, without any parameters
* data-focalpoint - the value of the focalpoint. 
* data-mode - how to crop your image.
* data-quality - the quality of the image. (default: 80)
* data-is-background - if this is se no <img>-tag will be added, but the image will be added as a background on the data-parent NOTE: data-parent is required.
* data-parent - per default the size of the image will be determinated by the width of the <figure>. If a parent is specified it will use the size of this instead. NOTE: If a focalpoint is set, it only used the width of the parent.
* data-original-width - is used to set a max-width on the image return from the server to prevent a ugly upscaling of small images.
* data-filter - filters used by imageprocessor


#### When using Umbraco Default Package
When you are using the Novicell Umbraco Default Package, you can grab a lot of these values from the FocalPointItemModel itself. Listed below are the generated values:
* @Model.Image.GetFocalPoints() - returns the focalpoint set in the backend
* @Model.Image.GetOriginalHeightRatio() - returns the original height-ratio of the uploaded image. If you set a forced width and height in the backend, the ratio of these will overrule.
* @Model.Image.GetWidth() - returns the original width of the uploaded image. If a forced width is set, is will be overrules by that. 

Additional you can grab values as url, title and alt-text.


## Notes
* Added an additional breakpoint, medium-small, based on https://github.com/hesselberg/Bootstrap3-ms-breakpoint/


## Requirements
* None!


## License
The Novicell Frontend is licensed under the MIT license. (http://opensource.org/licenses/MIT)
