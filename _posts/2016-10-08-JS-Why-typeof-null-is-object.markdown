---
published: true
layout: post
date: '2016-10-08 00:08:19 +0530'
categories: links
author: Ishwerdas
image: notes.jpg
permalink: /javascript/why-typeof-null-returns-object-the-history
comments: true
title: History behind typeof null equals object.
---

## Introduction

Javascript is undoubtedly bit weird at times. However for me, that's what makes it special. 
Javascript has 6 or 7 (depending upon how you count) primitive types. They are 

* string
* number
* boolean
* object
* symbol (new in es6)
* Null and undefined

Now if you have met javascript before, you know that her variables don't have a type. It's the value that has a type. To find that type we use `typeof`.


```
var u;
typeof u; //undefined

var a = "inder";
typeof a;  // string

var b =  true;
typeof b; //boolean
```

However if you run `typeof` on a null value, it returns `object`, something you won't expect from a primitive type.

```
var i = NULL;
typeof i; //object 
```

This is a **bug** that exists since the beginning of javascript. The reason that this bug exists is simple. Each javascript value has a type tag. First 1-3 bits of each value are reserved for it's type. The type tags for different types were as follows: -

* 000 - object
* 001 - int
* 010 - double
* 100 - string
* 110 - boolean


* To define **undefined** they used a special number 2 <sup>-30</sup> 
* To define **null** NULL pointer was used.

After the type tage folows the actual value. `typeof` got confused between zeros of null pointer and 000 tag of object and thus the bug. 

## Why isn't this bug removed?

It would have been removed in EcmaScript 6, but the proposal got rejected because of a lot of old javascript code that relies on it. So for now, we are stuck with it. 
