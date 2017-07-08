---
published: true
layout: post
title:  "Beginner's Guide to CSS Grids"
date:   2017-07-08 00:08:19 +0530
categories: css
author: Ishwerdas
image: grids.jpg
permalink: "/css/:title.html"
comments: true
---
Hey,

How are you? 

You know what, I am a big fan of Richard Fyenman's technique  of reducing everything to freshman level. I believe as he did, that if you are unable to explain a concept in simplest words you don't really understand it. 

Addition of Grids in CSS spec is something that would change every course that's taught on web development. CSS Grids is relatively new but as fundamental a concept as say box model. So let's try teaching it without assuming any CSS expertise from audience.

## What are grids?

Grid in its most simplest terms is rows and columns. Horizontal and vertical lines that divide the page, canvas or in our context screen into equal boxes. Grids provide rhythm to our design. Human mind loves symmetry, so when it sees symmetry it likes symmetry and hence finds a symmetric design aesthetically pleasing a.k.a good looking.

 You can [learn more about grids here](https://webdesign.tutsplus.com/articles/a-comprehensive-introduction-to-grids-in-web-design--cms-26521)

## Before Grids were introduced into CSS

In the ancient times (a year ago) we did not have grids in CSS. In the pre-historic times (couple of years ago) we had to rely on 3rd party grid frameworks for building grid based layouts. These frameworks bloated our markup (html) or added extra burden on the site. Then came the [flexbox](https://scotch.io/tutorials/a-visual-guide-to-css3-flexbox-properties). It somewhat allowed us to have grids but that was more of a hack than a solution. Using flexbox as a grid layout can be arguably considered as an improper use of flexbox. Well, we don't have to argue on that anymore because we have grids built in CSS Now.

## Shut up! and show me how

### Step 1: Make a container
Before you can add rows and columns, you need a container to contain those rows and columns. You do that by adding `display:grid` to your container element.

```
<main class="container">
  <div class='cell'> 1 </div>
  <div class='cell'> 2 </div>
  <div class='cell'> 3 </div>
  <div class='cell'> 4 </div>
  <div class='cell'> 5 </div>
  <div class='cell'> 6 </div>
  <div class='cell'> 7 </div>
  <div class='cell'> 8 </div>
  <div class='cell'> 9 </div>
  <div class='cell'> 10 </div>
  <div class='cell'> 11 </div>
  <div class='cell'> 12 </div>
  <div class='cell'> 13 </div>
  <div class='cell'> 14 </div>
  <div class='cell'> 15 </div>
  <div class='cell'> 16 </div>
</main>
```

```
.container {
    display:grid;
  }
```
<p data-height="265" data-theme-id="dark" data-slug-hash="rwZXoe" data-default-tab="result" data-user="inderpreetsingh" data-embed-version="2" data-pen-title="Beginner's Guide to CSS Grids - Step 1" class="codepen">See the Pen <a href="https://codepen.io/inderpreetsingh/pen/rwZXoe/">Beginner's Guide to CSS Grids - Step 1</a> by Inder Singh (<a href="https://codepen.io/inderpreetsingh">@inderpreetsingh</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>

### Step 2: Create Rows and Columns
Now we have grid, let's tell it the number and size of columns.

```
.container {
  display:grid;
  
  /* Create 4 columns of 100px each */
  grid-template-columns:100px 100px 100px 100px;
  
}
```
So as its obvious from the code, you use `grid-template-columns` to create columns and the extra columns (5 - 16) automatically gets arranged into rows. Pretty neat, eh? 

This property of CSS grids to automatically create rows for you when you don't explicitly define those rows in your css, that's called **implicit grid**. Not just rows, implicit grid can also add implicit columns for you. By default the property `grid-auto-flow` is `row`, however if you change it to `column` instead of creating implicit rows it would create implicit columns. 

In contrast, the grid that we define in css that's **explicit grid**. 

Let's add the rows now , **explicitly**.

```
.container {
  display:grid;
  grid-template-columns:100px 100px 100px 100px;

  /* Create 4 rows, first one with height of 50px 
   * & rest of them adjusting their height to content 
   */
  grid-template-rows: 50px auto 100px;  
  
```
<p data-height="265" data-theme-id="dark" data-slug-hash="owPKKp" data-default-tab="result" data-user="inderpreetsingh" data-embed-version="2" data-pen-title="Beginner's Guide to CSS Grids - Step 2.1" class="codepen">See the Pen <a href="https://codepen.io/inderpreetsingh/pen/owPKKp/">Beginner's Guide to CSS Grids - Step 2.1</a> by Inder Singh (<a href="https://codepen.io/inderpreetsingh">@inderpreetsingh</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>

Just like `grid-template-columns` , `grid-template-rows` add explicit rows to grid. The auto value makes it adjust the height of content. Still cells 14 - 16 are in an implicit row. There's a way you can target implicit rows in css called `grid-auto-rows`. Let's try that.

```
.container {
  display:grid;
  grid-template-columns:100px 100px 100px 100px;
  grid-template-rows: 50px auto 100px;  
  
  grid-auto-rows: 150px;
  
```
<p data-height="265" data-theme-id="dark" data-slug-hash="YQOmmL" data-default-tab="result" data-user="inderpreetsingh" data-embed-version="2" data-pen-title="Beginner's Guide to CSS Grids - Step 2.2" class="codepen">See the Pen <a href="https://codepen.io/inderpreetsingh/pen/YQOmmL/">Beginner's Guide to CSS Grids - Step 2.2</a> by Inder Singh (<a href="https://codepen.io/inderpreetsingh">@inderpreetsingh</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>

### Step 3: Add Gutter
Beside rows and columns, most grids have third thing called gutters. Gutters are the gap between 2 adjacent rows or 2 adjacent columns.

`grid-column-gap` and `grid-row-gap` to the rescue.

```
.container {
  display:grid;
  grid-template-columns:100px 100px 100px 100px;
  grid-template-rows: 50px auto 100px;  
  grid-auto-rows: 150px;
  
  grid-column-gap:20px;
  grid-row-gap:20px;
```
If you want same gap on rows as in columns, there's a shorthand that you can use called `grid-gap`.

```
.container {
  display:grid;
  grid-template-columns:100px 100px 100px 100px;
  grid-template-rows: 50px auto 100px;  
  grid-auto-rows: 150px;
  
  grid-gap:20px;
```
<p data-height="265" data-theme-id="dark" data-slug-hash="qjJWWP" data-default-tab="result" data-user="inderpreetsingh" data-embed-version="2" data-pen-title="Beginner's Guide to CSS Grids - Step 3" class="codepen">See the Pen <a href="https://codepen.io/inderpreetsingh/pen/qjJWWP/">Beginner's Guide to CSS Grids - Step 3</a> by Inder Singh (<a href="https://codepen.io/inderpreetsingh">@inderpreetsingh</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>
By this knowledge you can create a basic grid, and using media queries even a flexible grid for yourself. However that's just surface of what grids have to offer. There are whole bunch of [other properties](https://css-tricks.com/snippets/css/complete-guide-grid/) that you can use to manipulate grids. If time allowed, I will create more posts about it and link them down under.