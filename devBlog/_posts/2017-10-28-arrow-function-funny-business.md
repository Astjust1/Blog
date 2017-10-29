---
layout: post
title: "Arrow function funny business"
blog: dev
date: 2017-10-28
categories: javaScript es6 misc
show: true
permalink: /devBlog/:title.html
---
# Arrow Functions are fun #

With the introduction of ES6 comes a wonderful take on functions using '=>' or the fat arrow instead of the function keyword.

Here's some quick examples:

```javascript
//Normal Declaration
function(x,y){
    return x + y;
}
//Arrow
(x,y) => x+y;

```

```javascript
//Normal
function sum(x+y){
    return x+y;
}
//Arrow
let sum = (x,y) => x+y;
```

All of these have the same effect really. Personally, one of the top benefits that I get from this is just saved time. Anonymous functions are used very heavily when using javascript. Having to constantly write out ```function``` every time I want to provide callback functionality was in hindsight kind of unnecessary. So I welcome them with open arms.

## On to the funny business ##

So there is one main difference between the two types of function declarations. Arrow functions do not have their own ```this``` value. They take the ```this``` value from the enclosing execution context, while functions declared with the ```function``` keyword work as expected.

I came across this while writing some code for a personal project. While working with authenticating different types of user models, I realized that the logic was context agnostic. Meaning that I could write a utility function to just have the logic in one place and use the ```this``` keyword as a reference for the specific model to be authenticated.

Here's a small sample of the code that I originally wrote:

```javascript
//Util.js
module.exports.authenticate = (email,password,cb){
    this.findOne({email:email})
    .exec((err,user)=>{
        //compare passwords and return results
    });
}

//In my schema

UserSchema.statics.authenticate = Util.authenticate;
```

Now while running my model tests this was failing. The error said something along the lines of ```this``` not being a model. Now at first, I was all sorts of confused. "That doesn't make any sense" in a simplistic view of my understanding the scope of ```this``` was defined by the function, which would let me build what I'm trying to. But a quick bit of Google-Fu proved me wrong. ***ARROW FUNCTIONS DON'T DEFINE THEIR OWN ```this```!!!*** In a sense. What they do is take the value from the enclosing lexical context instead of how the function is being called.

So in my case, I was using the dynamic binding of ```this``` to my advantage by making the assumption that; since the call would be coming from a model, that would be what ```this``` would be bound to.

Unfortunately for me, JavaScript has a tendency to be the Wild West. And I need to look more in depth when using new language features. Learn from my mistakes people!!