---
published: true
layout: post
date: '2016-3-22 00:08:19 +0530'
categories: links
author: Ishwerdas
image: notes.jpg
permalink: /javascript/data-structures-using-javascript-arrays.html
comments: true
title: Arrays Using Javascript
---
# Data Structures using Javascript - Arrays 
## Arrays 

In programming we have something called variables. You can think of a variable as a named box and you can put stuff in it. Sometimes we need to put a bunch of related boxes in a bigger box, that's where arrays come into scene. 

Arrays can also be thought of as list containing homogenous list items. By homogenous I mean, of the same [datatype](https://developer.mozilla.org/en/docs/Web/JavaScript/Data_structures "datatype"). 

###Create a new array
Creating an array is simple. Syntax is almost similar to that of creating a variable, just that a list of comma separated items are enlosed in square brackets `[  ]`

```
var cars = ['lambohrgini' , 'audi' , 'mercedes' , 'datsun'];
var years = [1990, 1992, 1985, 1984, 1947] ;
```

You can also create array using `new Array()` method. To do that

```
var arr = new Array(1,2,3,4);
```

###Accessing a particular element of array (index)
Each element of array has an index. The indices start from 0.  You can access each element of array using arrayname followed by it's index in square brackets.
```
var cars = ['lambohrgini' , 'audi' , 'mercedes' , 'datsun'];
var years = [1990, 1992, 1985, 1984, 1947] ;
alert(cars[0]); // will alert lambohrgini
alert(cars[2]); // will alert mercedes
```
In javascript we can have named indices too, which is discussed later.

There are three basic operations that one can perform on array
- **Traversing** an array
- **Insert** an element into array
- **Remove** an element from array

###Traversing an array 
Traversing an array means, visiting each element of array one by one and then performing a certain operation on it. 

We need to use a loop to access each element of array. There are [bunch of loops](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Loops_and_iteration "bunch of loops") in Javascript, we will be using basic `for loop` for traversing. For loops exists in almost all the high level languages, so you can make use of this guide even if you are not that into Javascript. 

```
var friends = ['jane', 'mary', 'valerie', 'stephanie', 'carol']
for(i = 0; i < 5; i++) {
    alert(friends[i]); 
}
```

What for loops does is, it initializes a variable named `i` to `0`, and as long as `i` is less than five `< 5` , it keeps increasing it by 1 `i++`. This way the statement inside for loop runs 5 times, showing each element of array in a popup. 

This syntax is fine when we know the legnth of array (5 here) .In case the length of array is changing or we are not yet sure about how many elements we would put in it, then we can use a special javascript method called `.length` to access the length of array.

```
var friends = ['jane', 'mary', 'valerie', 'stephanie', 'carol'];

for(i = 0; i < friends.length; i++) {
    alert(friends[i]); 
}
```

Another simpler way to traverse arrays in javascript is to use [for .. in ](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Loops_and_iteration#for...in_statement "for .. in ")loop.

```
var friends = ['jane', 'mary', 'valerie', 'stephanie', 'carol']

for(i in friends) {
    alert(friends[i]); 
}
```

###Insert an element at end or array
Inserting an element at end of array is the simplest. Just find the length of array. Now you should note here that length of array is always one greater than highest index. So in following array
```
var arr = [45,46,47,48,49];
```
Highest index value is 4, as `arr[4]` is `49` but `arr.length` is `5` as there are 5 elements in array. So if we want to add an element at end of this array, we need to do it at `arr[5]` which can also be written as `arr[arr.length]`. So to insert an element at end of array, allw we have to do is :-

```
var arr = [45,46,47,48,49];
arr[arr.length] = 50; // which is same ass arr[5] = 50;

alert(arr); // will show 45,46,47,48,49,50 
```
The above funciton was a bit general that can be used in any other programming language. A more javascript-ish way is to use `.push()` method.

```
var arr = [45,46,47,48,49];
arr.push(50);

alert(arr); // will show 45,46,47,48,49,50 
```																					

###Insert an element at any index
Inserting an element at beginning or mid of array is a tiny bit tricky. Because say if you want to add an element at 3rd index , then you have to move all the elements that come after 3rd element one index ahead.

Let's first setup our array and variables. We need an array, a new value to be inserted into that array, and a position at which the array will be inserted. 

```
var fruits = ['apple','orange', 'kiwi', 'banana', 'mango'];
var newValue = 'pear';
var insPos = 2; 
//we will add a new fruit (pear) at fruits[2], a.k.a in place of 'kiwi'
```

Now we need to know the highest index value of an array. As discussed earlier array.length is always 1 greater than highest index value. We can also say that highest index value is 1 less than length of an array.

```
var fruits = ['apple','orange', 'kiwi', 'banana', 'mango'];
var newValue = 'pear';
var insPos = 2; //insert Position
//we will add a new fruit (pear) at fruits[2], a.k.a in place of 'kiwi'

highestIndex = fruits.length - 1;
```

Our array and all other variables are now prepared. Next step would be to move each element after `insPos` one index ahead.We start from last element of array and move upwards till insert position.
```
for(i = highestIndex; i >=insPos; i--){
    fruits[i+1] = fruits[i];
}
```
Now only thing left is to insert element at required position.

```
    fruits[insPos] = newValue;
```
The complete code now looks like.
```
var fruits = ['apple','orange', 'kiwi', 'banana', 'mango'];
var newValue = 'pear';
var insPos = 2; 
//we will add a new fruit (pear) at fruits[2], a.k.a in place of 'kiwi'

highestIndex = fruits.length - 1;

for(i = highestIndex; i >=insPos; i--){
    fruits[i+1] = fruits[i];
}

fruits[i] = newValue;
alert(fruits);
```
Hurray! now we have inserted an element into array.

###Removing an element from end of array. 
I have been unable to find a general way to remove an element from array in javascript. If you know one, let me know in comments or you can also send a PR to this article. So we are going to use Javascript's `.pop()` method. 

```
var arr = [45,46,47,48,49];
arr.pop();

alert(arr); // will show 45,46,47,48 
```		

###Removing an element from any index.
For removing an element from a certain index we will use `.splice()` method of javascript. Which removes the array at an index with single line of code. If that function was not available we would have deleted an array item from the array and then moved all the next elements one index value back. But as I don't know a general method of deleting some variable or array element in javascript, I will use built-in method splice to have same effect.

```
var arr = [45,46,47,48,49];
var remPos = 2;
arr.splice(remPos, 1);

alert(arr); // will show 45,46,48,49 
```
So that completes guide to a very basic data structure called arrays. Array is a data structure that we will use to create other complex datastructures like matrices and graphs and so on. Stay tuned...
