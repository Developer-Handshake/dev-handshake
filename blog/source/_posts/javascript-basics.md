---
title: Javascript Standards for Development
date: 2018-12-17 22:44:19
tags:
- javascript 
- es6 
- common js 
- object oriented programming
---
Javascript has undergone numerous changes since its inception in 1995. After being introduced as a complementary aspect of web development alongside HTML and CSS, Javascript engines are now found in a number of web technologies from server-side web servers and databases to full scale native mobile application development. We take a deeper dive into the growth of Javascript through the scope of CommonJS and ECMAScript 6. 

## Javascript: The Beginning and The Future 
![Diagram1](https://raw.githubusercontent.com/Developer-Handshake/Developer-Handshake.github.io/org-page/img-media/javascript.png)

After its origins from the NetScape architecture, JavaScript underwent a form of standardization in order to make it a more applicable scripting language for modern and future web technologies. This is known as the ECMAScript Standard, and **ECMAScript Version 6** -- or more commonly referred to as [ES6](http://es6-features.org/#Constants) -- is the current industry standard. 

_ES6_ introduces a number of new features and syntax for creating efficient and readable code such as arrow functions, template strings, class destruction, modules and more. 

```javascript 
const myFunc = greeting => {
    return 'Hello ${greeting}'; 
}

console.log(myFunc('World! This is ES6!')) // output => Hello World! This is ES6!
```
---
### ES6 and Modern Web Development 
There are a number of advantages that the ES6 standard has brought to javascript programming. Despite web browsers not having full feature support for ES6, the new Javascript standard is compatible with certain compilers that enable ES6 to be translated into ES5 when the web page or web application is rendered. 

#### Compilers to get you started
* [Babel](https://babeljs.io/) - Babel is a toolchain that is mainly used to convert ECMAScript 2015+ code into a backwards compatible version of JavaScript in current and older browsers or environments 
* [Sucrase](https://sucrase.io/) - Sucrase is an alternative to Babel that allows super-fast development builds. Instead of compiling a large range of JS features to be able to work in Internet Explorer, Sucrase assumes that you are developing with a recent browser or recent Node.js version, so it focuses on compiling non-standard language extensions 

![Diagram1](https://raw.githubusercontent.com/Developer-Handshake/Developer-Handshake.github.io/org-page/img-media/compiler.png)

#### Advantages for Web Development
**Default Function Parameters** 
The ES6 standard comes with functionality that allows developers to create modular environments for their code. For example the implementation of **Default Function Parameters** in the ES6 standard allows for formal parameters to be initialized with default values if no value or undefined is passed. Previously _default function parameters_ were employed as such: 

```javascript 
var link = function (height, color, url) {
    var height = height || 10
    var color = color || 'green'
    var url = url || 'developer-handshake.github.io'
    ...
} 
```

However certain values being passed through functions with this setup would result in error. Typically developers could handle these one-off-occurrences through logic loops, but now with ES6 a rational alternative has already been built into the scripting language. Simply declare your default parameters while implementing the function: 

```javascript 
var link = function(height = 10, color = 'green', url = 'developer-handshake.github.io') {
    ...
}
```

**Interpolation and Template Literals** 
ES6 also allows developers to employ the use of strings in their code in a more conducive and efficient manner. The improved standard makes it easier to define multi-line strings, interpolate variables and expressions in strings and create domain specific language with template tags. 

When utilizing template literals in ES6, you initialize them with the backtick. If the use of a multi-line string is required then you simply continue the string on a new line, there is no longer the requirement of having to initialize with a special character. 

```javascript 
// Template Literals in ES6 - multi-line strings 
var string = `this is an example of 
a multi line string using the ES6 standard` 

// The ES5 way of working with strings and expressions
var name = 'Your name is' + first + ' ' + last + '.'
var link = 'http://localhost:3000/api/message/' + id 

// The ES6 way of working with strings and expressions 
var name = 'Your name is ${first} ${last}' 
var link = 'http://localhost:3000/api/message/${id}' 
```

**Destructuring in ES6**
_Object Destructuring_ implies the breaking down of complex objects into simpler fragments, which can be used for _variable declaration_ or _variable assignment_. This functionality enables the developer to work with object literals on the left hand side of an assignment expression. Destructuring syntax also allows you to set default values upon implementation. When assigning a variable corresponding to a key that does not exist within the object the value `undefined` is used by default. This behavior can be altered by initializing the default values yourself. Applicable examples for the destructuring of objects can be seen below: 

```javascript 
// Object Destructuring in ES6
const student = {
    firstname: 'Glad',
    lastname: 'Egoge',
    country: 'Nigeria'
}; 

const { firstname, lastname, country } = student; 

console.log( firstname, lastname, country ) // => Glad Egoge Nigeria

const { firstname, lastname, country, age = 21 } = student; 

console.log( firstname, lastname, country, age ) // => Glad Egoge Nigeria 21 
```

**Arrow Functions** 
The ES5 syntax required developers to write out all aspects of a function's expression and statement. _Arrow Functions_ streamline the binding of `this` and defining parameters. Although arrow functions are applicable in a number of scenarios, they should not be used in favor of regular functions for the following scenarios: 
1. When working with object methods
2. When utilizing callback functions with dynamic context 
3. When it makes your code less readable 

```javascript 
// Arrow Function syntax in ES6 
const myFunc = (x, y) => { return x * y }; 

// Application of Arrow Function for variable assignment with array 
var ids = ['dfks123', 'fskd873']; 

var messages = ids.map(value => `ID is ${value}`); 
```

**Promises** 
_Promises_ and their usefulness were debated greatly with the previous ECMAScript standard. However in ES6, Promises are have been given a defined role. In comparison to the callback function, promises are defined as objects -- which store information about whether or not a specific event has occurred and said outcome. Promises are only created in asynchronous functions and then returned. When an event happens, the asynchronous function will update the promise to notify the external code sets. Promises, unlike callbacks, only represent one event that was either successful once or failed once. 

```javascript 
// Returning a promise which resolves after the specified interval  
function delay(interval) { 
    return new Promise(function(resolve) {
        setTimeout(resolve, interval)
    });
}

var oneSecondDelay = delay(1000); 
```

**Classes** 
A common methodology for employing Object Oriented Programming is the utilization of classes. Previous versions of Javascript have either completely ignored or provided a different implementation for classes. The keyword `class` was reserved in ES5 but did not provide the same functionality as you would see in Python, Java, etc. In Javascript instantiating a `class` creates an object that is linked to a _prototype_. Changes to that prototype propagate to the new object, even after instantiation. A simple Animal class implementation in ES6 should look something like this:

```javascript 
class Animal {
    constructor (name, fierce) {
        this.name = name; 
        this.fierce = fierce; 
    }

    get name() {
        return this._name; 
    }

    get fierce() {
        return `This animal is ${this._fierce ? 'fierce' : 'tame'}`; 
    }

    toString() {
        return `This is a ${this._fierce ? 'fierce' : 'tame'} ${this._name}`; 
    }
}

let Lion = new Animal('Lion', true);

console.log (Lion.fierce) // => This animal is fierce. 
console.log (Lion.toString()) // => This is a fierce Lion. 
```

Classes in Javascript come with a baseline set of properties. Class methods are non-enumerable. The `class` declaration sets the `enumerable` flag to `false` for all methods in the `prototype`. Classes also have a default `constructor() {}`. If there is no `constructor` in the `class` construct, then an empty function is generated. All Classes always `use strict`. All content inside the class construct is automatically in strict mode. 

**Modules in ES6** 
Traditionally Javascript has never really had native modules support. Some alternatives were developed as a workaround of sorts, but with the latest implementation of the ECMAScript standard there are now modules with the `import` and `export` operand. The main issue with ES6 Modules is the lack of support amongst common web browsers. At the time of writing, you will need to employ an npm package, [jspm](https://jspm.io/), in order to use the new ES6 modules in modern browsers. Other web technologies have taken hold of this functionality and provided an alternative for the yet supported ES6 modules. 

![Diagram3](https://raw.githubusercontent.com/Developer-Handshake/Developer-Handshake.github.io/org-page/img-media/module.png)

1. [RequireJS](https://requirejs.org/) - is a Javascript file and module loader. It is optimized for in-browser use, but it can be used in other Javascript environments. Using a module script loader like RequireJS will improve speed and quality of code  
2. [CommonJS](https://requirejs.org/docs/commonjs.html) - is the module specification standard used in NodeJS for working with modules. Modules allow developers to encapsulate all types of functionality and expose said functionality to other Javascript files, as libraries 

**CommonJS Modules** 
The [**CommonJS API**](http://www.commonjs.org/) is useful in defining APIs that handle many common application needs, ultimately providing a standard library as rich as those of _Python_, _Ruby_, and _Java_. The intention behind this technology is that an application developer will be able to write an application using the _CommonJS API_ and then run that application across different Javascript interpreters and host environments. With CommonJS-compliant systems, you can use Javascript to write: 
* Server-side Javascript applications 
* Command line tools
* Desktop GUI-Based applications 
* Hybrid applications 

With _CommonJS_ modules, every file explicitly states its dependencies,letting the tooling figure out what the ordering is. Using _CommonJS_ modules keeps developers from polluting the global namespace which enables engineers to now write and distribute high quality libraries with shared dependencies. Every _CommonJS_ modules is given two main globals: `module.exports` and `require`. 

```javascript 
// from foo.js 
module.exports = 'This is a string'; 

// from bar.js 
var foo = require('./foo');
assert.equal(foo, 'This is a string'); // => True 
```

There are developers that feel that the use of CommonJS is far more suited for sever-side applications as opposed to web applications. Many CommonJS APIs address server-oriented features that one would simply not be able to implement at a browser level in Javascript. However, it is useful to know how to structure CommonJS modules to be able to utilize them on numerous scenarios. CommonJS modules that have application on both client and server-side include validation, conversion, and templating engines. 

- [Jzbonner](https://github.com/Jzbonner) 🌐
