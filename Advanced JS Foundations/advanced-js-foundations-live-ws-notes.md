## Summary:

It is intended to go over some JS fundamentals that are not normally taught or learned because they are hard to grasp. It is intended for any level of developer. For those just starting and wanting to go to the next level and it will serve as are fresher for mid-senior devs.

## Goal of this course:

Have clarity about the things they use every day. (“You’re already doing this stuff, you just don’t know what’s going on below the surface”.

So go over things that I already know but have a deeper understanding of what it is and how it works. 

1. Answer “What is a closure”
2. Explain Recursion
3. Explain const/let/var
4. Use Date & Math objects correctly
5. Understand strict mode
6. Difference between implicit & explicit coercion
7. Understand prototypes more in depth
8. Understand the `this` keyword
9. Understanding of the primitive types

Coercion in coding: **Many programming languages support the conversion of a value into another of a different data type. This kind of type conversions can be implicitly or explicitly made. Implicit conversion, which is also called coercion, is automatically done.**

Key things for me: Most everything to be honest. I know a good bit about `const/let/var` so I'm not too worried about that. But most everything else I've heard of/used but don't understand to a great depth. 

## [Github Prep](https://www.notion.so/egghead/Lucas-notes-for-Advanced-JS-Foundations-Live-Workshop-b53e9ede3da34064954051469d05a8f2#fca5a0f143b04a4fb7c463eb0c3c48bd):

Just downloaded the repo. 

There wasn't really any prep to do for this workshop. The only thing I could think of was maybe doing some research beforehand on some of the key points he was teaching on. 

## Post Workshop Notes:

The chat interaction was great! I only had a couple of questions that I threw out that I needed answering. Those were posted in my notes down below. Tyler did a great job of answering most questions. 

I feel like paying a little more attention to the chat as things came up to answer questions would be a better way of doing things rather than waiting till he is done with the lesson or halfway through the lessons to answer. If there was a key part of the lesson that someone didn't understand, asked in the chat and one of us was unable to help them, the user may not understand what was being taught in the lesson. (just my opinion). 

For this W.S. there wasn't much coding to do. I liked the examples that were given to try and test how well we were learning and following along. There were a few in there that did a good job of tripping me up and rethinking how I knew the material. 
It was difficult for me to take my own notes. I found about halfway through, 95% of my notes were just copy/paste what he had in his repo. I feel like that was just the nature of this kind of W.S. 

## Next Time:

Not gonna lie, for these long 4.5 hour workshops, it can get hard to pay attention. I found myself getting distracted and had to pull my attention back to the W.S. I need to find a way to be able to pay more attention and not get distracted as easily. More coffee?? 

For a W.S. that has basically all of the notes already written out, maybe not clone the repo so that I have to write everything out in my own words/take pictures more/write my own code examples. I feel like I would be able to get much more useful notes out of it. I don't feel like my notes were very useful for this workshop. 

## Live Workshop Notes:

Not really required to be a dev. Just being able to use it is enough, but we will be focusing on exactly what these all mean. Helps with debugging and give more depth in how to use these things correctly. 

### Lesson 01 - Primitive Types, the what, how, and why

What is a `type`? Types are a way of organizing data that has similar values. 

Primitive types: data that is not an object, has no methods, cannot be mutated. 

These types are: string, number, bigint, boolean, null, undefined, and symbol

Q. What is a `bigint`?? How does it differ to a regular `int`? 

A. BigInts can use all operators that numbers can use though it is not strictly equal to a `Number`, but "loosely so".

bigint is written out like: `42n` with this `n` character. 

`NaN` is a number. 

Data types are functions, arrays, maps, objects. They have methods and can be mutated. 

Example
```js
let obj = { a: 1 }

function addTwo(obj) {
  obj.a = 2
}

addTwo(obj)
```

If we console.log `obj`, it returns `2`. 

But if we do this with a primitive type: 

```js
let num = 1

function addTwo(num) {
  num = num + 2
  console.log(num)
}

addTwo(num)
```

Now if we console.log `num`, we get `1`. 

Q. But I can dot into prototype methods on strings??

A. Auto-boxing. This is the boxing, or wrapping, of value types in objects when they are treated like objects. Behind the scenes, a temporary object is created for the duration of the use of the value type instance.

```js
const str = 'foo'
console.log(typeof str)
console.log(str.length)
```

If we `.` onto a string, string is being wrapped into an object and given a `length` value. 

```js
const wrapperString = new String('foo')

console.log(typeof wrapperString)

console.log(wrapperString)

console.log(wrapperString[0])

console.log(Object.getPrototypeOf(wrapperString) === String.prototype)
```

Tagging on `new String` to our `wrapperString`, it is now an object. 

`console.log(Object.getPrototypeOf(wrapperString) === String.prototype)` will equal to true. 

The best thing is to usually let JS to autobox instead of doing it yourself. 

`Should try to use the literal syntax for everything.. You can use it on RegExp, Error.. and Date (no literal)`

GOTCHAS: 
```js
const foo = false
const bar = new Boolean(false)

foo === bar // false

typeof bar // "object"
```

Comparing object and primitive types. They are not the same. 
```js
const baz = false
const buzz = Boolean(false)

baz === buzz // true

typeof buzz // "boolean"
```

You have the primitive value of `buzz`. Since we aren't using the `new` keyword, we aren't creating an object. 

### Lesson 02 - How prototypal inheritance works in JS & Create objects with the `new` keyword

What is a prototype?? 

- The fundamental way inheritance works in JavaScript.

- Prototypes are objects. It is the linking of objects

- OO languages work through classes, a parent to child relationship. Typically with classes you use the `new` keyword to create a copy of that blueprint code (class)

- Prototypes is the linkeage between objects through properties. Or commonly called the prototype chain.

- When accessing a property, it looks at each object level one at a time until it finds it or returns `null`. So you can "replace" the `.toString()` found on the global `Object.prototype.toString` by giving your object the same property name.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/979c53f8-abef-4ce3-8b53-9010e46251e3/Screen_Shot_2019-10-24_at_9.25.27_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/979c53f8-abef-4ce3-8b53-9010e46251e3/Screen_Shot_2019-10-24_at_9.25.27_AM.png)

This is a `dunder proto`. 

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5b2b34dc-b5df-4e56-b4f2-995a9a4120b4/Screen_Shot_2019-10-24_at_9.25.53_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5b2b34dc-b5df-4e56-b4f2-995a9a4120b4/Screen_Shot_2019-10-24_at_9.25.53_AM.png)

A literal object, is automatically connecting it through the dunder proto. The same thing happens in arrays. 

What is the connection between `.prototype` and `__proto__`.? Functions have a `.prototype` property that points to an object with a constructor property, and a `__proto__` property.

```js
function a() {
  return 'hello'
}

console.log(a.prototype)


```
![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/787495b3-cd32-471e-95c5-b1237bab834b/Screen_Shot_2019-10-24_at_9.31.08_AM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/787495b3-cd32-471e-95c5-b1237bab834b/Screen_Shot_2019-10-24_at_9.31.08_AM.png)

First step is understanding the what the global Functions and Prototypes are: `Array`, `Object`, `Number`, `String`.

These all have `prototype` .

*dunder* is *double underscore*. 

### Understanding the `new` keyword

Does main three things: Creates a new object, connects new object's `__proto__` to function's `.prototype`, `this` used within called function points to new object created. (Fourth is it returns `this` which is that new object)

1. Creates new object:
```js
*function* a() {

return 'hello'

}

*const* b = new a()

*console*.log(b) // { }
```

2. Connects new object's `__proto__` to function's `.protoype`

```js
*function* A() {

return 'hello'

}

*A*.prototype.name = 'world'

*const* b = new A()

*console*.log(b) // A{}

*console*.log(b.name) // world
```

3. `this` used within called function points to new object created
```js
*function* A() {

this.name = 'hello'

}

*const* b = new A()

*console*.log(b) // a{name: 'hello'

*console*.log(b.name) // { }
```

For fun: 
```js
function A() {
  this.name = 'hello'
}

A.prototype.name = 'world'

const b = new A()

console.log(b) // A { name: 'hello' }

console.log(b.name) // hello
```

### Loops with Prototypes

- Loops can behave differently when objects have chained prototype objects.

- The for...in statement iterates over all non-Symbol, enumerable properties of an object.

```js
const obj = {
  firstName: 'Tyler',
  lastName: 'Clark'
}

let n = 0
for (let property in obj) {
  n++
}
console.log(n) // 2
```

vs.

```js
const obj = {
  firstName: 'Tyler',
  lastName: 'Clark'
}

const protoObj = {
  hair: 'Brown'
}

Object.setPrototypeOf(obj, protoObj)

let n = 0
for (let property in obj) {
  n++
}
console.log(n) // 2
```

In order to avoid this situation, you need to add a check

```js
const obj = {
  firstName: 'Tyler',
  lastName: 'Clark'
}

const protoObj = {
  lastName: 'Brown'
}

Object.setPrototypeOf(obj, protoObj)

let n = 0
for (let property in obj) {
  if (obj.hasOwnProperty(property)) {
    n++
  }
}
console.log(n) // 2
```

In order to avoid this situation, you need to add a check

```js
const obj = {
  firstName: 'Tyler',
  lastName: 'Clark'
}

const protoObj = {
  lastName: 'Brown'
}

Object.setPrototypeOf(obj, protoObj)

let n = 0
for (let property in obj) {
  if (obj.hasOwnProperty(property)) {
    n++
  }
}
console.log(n) // 2
```

`Object.create` creates a object and gives the ability to point another object to be the new object's prototype.

```js
const house = {
  houseColor(color) {
    console.log(`${color} is a good color`)
  }
}

const myHouse = Object.create(house) // { }

myHouse.houseColor('blue') // blue is a good color
```

`object.create` is the third way to do this. You don't HAVE to use `new`.

Its recommended to NOT use the `new` keyword. Use `object.create`, `.create` or `setPrototypeOf`.

### Lesson 3 - Understanding implicit vs explicit coercion

Conversion from one type to another type. 

Think of it as `conversion`. changing types from primitive to primitive or object to primitive. 

To understand your code, you have to learn to interpret code like JS. 

Coercion happens more than you think. its unavoidable. but doesn't have to be a black box. see below

A couple prototypes have a `.toString()` for converting it to a string primitive. 

Work around for sting is to object is `JSON.parse` and `JSON.stringify`.

Implicit Coercion:

Abstracts away the lower details to provide more focus for the developer. Are the explicit coercion distracting to the reader? Example: Template strings

```js
const someNumber = 2
const str = `Hello, I have ${someNumber} eyes`
```

Putting a number into a string. 

For JS to be able to understand and do this: 

- *First* JS will do is call the .valueOf function on the wrapper object prototype chain to determine it's primitive value.
- Afterwards it will coerce the type into the similar type to complete the operation.
- Using prototype methods on primitive... Boxing is implicit coercion
- Overload operators like the `+`
- Truthy & Falsy checks

```js
const arr = []

if (arr.length) {
  // do something while arr.length is truthy?
  // vs. do something while arr.length > 0?
}
```
== (Using valueOf on prototype to determine what type it is. Then calls needed method to coerce into right type for comparison.. which then runs same algorithm as ===)

Explicit Coercion: 

Using the native functions (String, Boolean, Number)

    const someNumber = 2
    const str = `Hello, I have ${String(someNumber)} eyes`

to-string coercion

- String(val)
- .toString()
- Using the `+` operator
```js
const num = (1).toString()
// "1"
// the parenthesis around the 1 are necessary for grouping.
// this is both implicit and explicit coersion

const arr = [1, 2, 3].toString()

// "1, 2, 3"

const obj = { a: 1 }.toString()

// "[object Object]"

const stringNumber = 2 + ''

// '2'
```

Common Gotchas: 

```js
const nestedArr = [[], [], []].toString()
// ",,"
// this is just three empty strings instead of arrays
// this is also truthy

const arrEmpty = [null, undefined].toString()
// ","
// this will return two empty strings
```

To-number() has a lot of the same issues as well. 

- `Number(val)`
- `parseInt(val)`
- `parseFloat(val)`
```js
const empty = Number('') // 0
// empty string gets turned into a 0

const notANumber = Number('.') // NaN
// '.' cannot be a number
```

Why? 

```js
const zeroDot = Number('0.') // 0

const falses = Number(false) // 0
// instead of returning NaN, it returns a 0

const trues = Number(true) // 1

const nulls = Number(null) // 0

const undef = Number(undefined) // NaN

const arr = Number(['']) // 0
// array with nothing will return a 0

const arrValue = Number([1, 2]) // NaN
// but if there are multiple numbers, it will return NaN
```

to-boolean is the easiest to remember. 

- Looks to see if value is falsy or truthy
- `Boolean(val)`
- Comparing the value `==` or `===`

Falsy: `""`, `0`, `-0`, `null`, `NaN`, `false`, `undefined` 

Truthy: ....everything else.

### Lesson 4 - Reference execution with the `this` keyword

`this` value changes. It's not always the same. 

Simply put, `this` **references the execution context of a function's call**. Which is determined how the function was called and in non–strict mode, is always a reference to an object.

Can be different depending on how the function is called... In other words you cannot look at a function and know what the this context will be. You have to see how the function is called at runtime. (Whenever you write a function, `this` is not static.)

Important to understand how functions are invoked... Functions can be invoked with `()` individually (implicit binding), methods like `call` (explicit binding), or the `new` keyword.

Understanding how functions are executed is the first step. 

### Implicit Binding

Option 1: _Context object_: where `this` is probably intended to be the object the function lives on:

- From mdn: "When a function is called as a method of an object, its this is set to the object the method is called on."

```js
const person = {
  firstName: 'tyler',
  getName() {
    return `${this.firstName} is my first name`
  }
}

person.getName() // 'tyler is my first name'
```

Is the function invoked? Yes. What is the context? The context is `person`. `this` context of `firstName`. `this` is person. `person.firstName` is basically the same thing. 

Q. Why use `this` at all then? Seems like it is just confusing things. 

A. REUSABILITY! Leaving it as `this` instead of `person`, you can reuse this function elsewhere and won't have to worry about changing things. 

```js
const person = {
  value: {
    firstName: 'tyler',
    getName() {
      return `${this.firstName} is my first name`
    }
  }
}

person.value.getName() // 'tyler is my first name'
```

`firstName` is inside of the same object, that is why this example above works. 

- Invoking `()` individually: _Default binding_ where it is called with a context and `this` defaults to the global

- Behaves differently depending on `strict mode` or `non-strict mode`

```js
var firstName = 'tyler'

function getName() {
  return `${this.firstName} is my first name`
}

getName() // 'tyler is my first name'
```

Functions automatically get added to the global object when they are created. Only works with `var` since `var` can be changed where `const` cannot. 

Look at call site of function, where is it actually called?

```js
const person = {
  firstName: 'tyler',
  getName() {
    console.log(`${this.firstName} is my first name`)
  }
}

window.setInterval(person.getName, 3000) // "undefined is my first name"
```

Why is the `setInterval` messing with things? 

The function isn't being invoked!!! `setInterval` is calling the function in a new context. 

Example 2: 

```js
const person = {
  firstName: 'tyler',
  getName() {
    return `${this.firstName} is my first name`
  }
}

const anotherPerson = {}

anotherPerson.getName = person.getName

anotherPerson.getName() // "undefined is my first name"
```

Where is `getName` being invoked? The context is to the left of the `.`. It doesn't have access to `firstName`. `anotherPerson` becomes the value of `this`. `firstName: 'tyler',` would have to be added to `anotherPerson` to be able to make this code work. 

Explicit binding: apply, call, bind: Takes a parameter which assigns the `this` context explicitly.

```js
const person = {
  firstName: 'tyler'
}

function getName() {
  return `${this.firstName} is my first name`
}

getName.call(person) // 'tyler is my first name'
```

Arrow functions: 

- Arrow functions have no concept of `this`. If you use a `this` inside of a arrow function it will act like any other variable. It will lexically resolve to the enclosing scope looking for a this.
- It's not a fix all solution for our troubles with `this`

```js
const person = {
  firstName: 'tyler',
  getName: () => {
    console.log(`${this.firstName} is my first name`)
  }
}

window.setInterval(person.getName, 3000) // "undefined is my first name"

person.getName() // "undefined is my first name"
```

First need to understand lexical scoping. Lexical scoping references the parent function context / scope. This is the enclosing function or the window. Object curly bracket's do not represent "scope". We are looking for function curlys for scope.

```js
const person = {
  firstName: 'tyler',
  getName: () => {
    return function() {
      console.log(`${this.firstName} is my first name`)
    }
  }
}

window.setInterval(person.getName(), 3000) // "undefined is my first name"
```

wrong: 

```js
const person = {
  firstName: 'tyler',
  getName() {
    window.setInterval(function() {
      console.log(`${this.firstName} is my first name`)
    }, 3000)
  }
}

person.getName() // "undefined is my first name"
```

wrong: 

```js
const person = {
  firstName: 'tyler',
  getName: () => {
    window.setInterval(function() {
      console.log(`${this.firstName} is my first name`)
    }, 3000)
  }
}

person.getName() // "undefined is my first name"
```

answer: 

```js
const person = {
  firstName: 'tyler',
  getName() {
    window.setInterval(() => {
      console.log(`${this.firstName} is my first name`)
    }, 3000)
  }
}

person.getName() // "tyler is my first name"
```

`this` references `getName`. `this` is treated like a `variable`. 

Arrow function gotchas: 

- Cannot self reference with recursion.
- Do not have a name, it is anonymous (unless assigned to a variable)
- Cannot be used with the `new` keyword
- `call` or `apply` first param for `this` is ignored

`this` and prototypes (dunder prototype is the chain of prototypes)

- Works similar to looking up properties on an context object. `this` will step through the prototype chain looking for a property... because prototypes are just objects.
- getters and setters

```js
const proto = {
  get myName() {
    return this.firstName
  }
}

const person = Object.create(proto) // { }
// creates a new object

person.firstName = 'tyler' // { firstName: 'tyler' }
// person is now { firstName: 'tyler' }

console.log(person.myName) // 'tyler'
// first looks at person, myName isnt there. It works its way up the tree till it finds myName
```

### Lesson 5 - Understand lexical vs. dynamic scope & Hoisting variables with const, let, var & Immediately invoked function (IIFE)

- Contains any assignments of variables and functions. Cannot access "buckets" inward, just outward.
- Many will say "best practice" is to make private as much as you can. This mediates naming collisions and it is prevented from being used elsewhere. Lots of public variables couples functionality and makes it difficult to refactor.

### Lexical Scope

- Think of lexical related to "author" time or at "compile time" or "fixed". It is not decided on when or how the code is executed ("runtime").
- Other languages have dynamic scoping. Think the opposite of lexical, it's at "runtime". A function references scoped variables at execution. This does not work in JS, however we have the `this` keyword that gives us that dynamic scoping.

var, let, const:

- `var` declarations are processed before any code is executed. It's scope is its **current execution context**.
- Re-declaring it without a value, will not lose it's initial value.
- It's declaration is equal to `undefined` and hoisted to the top of it's execution context.

```js
var firstName = 'tyler'

function x() {
  var firstName = 'clark'
  console.log(firstName) // 'clark'
}

console.log(firstName) // 'tyler'
```

This focus' on scope. `var` in the first function = `'clark'`. 

Any assignment without a variable statement puts it on the global object, regardless of it's execution context

```js
function x() {
  firstName = 'clark'
  console.log(firstName) // 'clark'
}
x()

console.log(firstName) // 'clark'
```

`let` vs `var`

- `let` is different from `var` as it's scope is blocked (statement or expression).
- `let` does not create properties on the window object like `var`.
- `let` is only initialized to value when the parser evaluates it. In other words it is not hoisted to top of scope with initial value of `undefined` like `var`.
- Re-declartion of `let` throws an SyntaxError, unlike `var`

```js
var firstName = 'tyler'

{
  var firstName = 'clark'
  console.log(firstName) // clark
}

console.log(firstName) // clark
```

vs

```js
let firstName = 'tyler'

{
  let firstName = 'clark'
  console.log(firstName) // clark
}

console.log(firstName) // tyler
```

`let` does 'block scope' where `var` does not. 

const: 

- `const` very similar to `let`.
- Blocked scoped as well
- Major difference between it and `let` is as mdn states: `The value of a constant can't be changed through reassignment, and it can't be redeclared`
- Gotcha: Does not do deep equals on object types. Like mutating values in an array or object

Scope example: 

```js
const firstName = 'tyler'

{
  const firstName = 'clark'
  console.log(firstName) // clark
}

console.log(firstName) // tyler
```

`const` also does block scoping. 

### Let and Const gotcha: Temporal dead zone

- Because let and const do not start with an initial value hoisted to the top, if you trying to access it before it is initialized with result in a reference error.
- From MDN: "The variable is in a "temporal dead zone" from the start of the block until the initialization is processed."

[egghead.io tweet on variables](https://twitter.com/eggheadio/status/783723540029681665)

### Lesson 6 - Use the ES6 class keyword

- Simply just syntactic sugar over functions and the prototype chain.
- Can be a class declaration and class expression like functions.
- Unlike functions, classes are not hoisted
- Has many keywords specific to `class`, however it is still just sugar over functions and prototypes.

## Had something come up so I missed a good bit of the last couple lessons.