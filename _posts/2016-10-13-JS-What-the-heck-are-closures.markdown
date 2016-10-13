---
published: true
layout: post
date: '2016-10-08 00:08:19 +0530'
categories: javascript
author: Ishwerdas
image: closures.jpg
permalink: /javascript/what-are-closures
comments: true
title: What are closures?.
---

**Work in progress**

Javascript is weirdly awesome.Closures in javascript are one of those things that would make your brain swoon over its weirdness, over it's mild yet intriguing complexity. Closure is a way to remember function's variables even after that function has finished running.

Let's get into code

```
function greet(greeting) {

  function noun(name) {
    return greeting + "  " + name +"!";
  }

  return noun;
}
```

Now the `noun` that's returned from `greet` is said to have closure over variable `greeting`. In simple terms it will remember whatever we pass as `greeting` to `greet(greeting)`. Let's clarify that with an example.

```
/**
the noun that's returned from greet remembers the greeting that we pass to greet. 
We are storing that noun inside different variables here.
*/
var helloGreet = greet('hello');
var holaGreet = greet('hola');

/**
Now helloGreet and holaGreet are kind of noun functions in disguise. 
So we can pass them their intended argument a.k.a the variable `name` to it.
*/

helloGreet('inder'); // hello inder
holaGreet('gaurav'); // hola gaurav
```

A bit confusing isn't it?

It's supposed to be. Don't worry practice them a bit, and stay tuned for more explanation.
