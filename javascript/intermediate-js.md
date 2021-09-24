## Functions and Variables

Two types of scope in JavaScript:
- Global Scope: Any code written directly in the file.
- Local Scope: Any code nested inside a method/function/loop etc. 

Inner scopes have access to the outer scope. The reverse is not true.

**Varibale Hoisting:** Variables declared with `var` are **hoisted** to the top of their scope. I.e., declaration is split from assignment and move up.

This: 

```javascript
console.log(x);
var x = 19;
var y = 21;
```

becomes:

```javascript
var x;
var y;
console.log(x); // prints `undefined`
x = 19;
y = 21;
```

**Function Hoisting:** _Function expressions_ are hoisted like variables. _Function declarations_ are hoisted in their entirety. The is no split in declaration and assignment. Function declarations are even hoisted higher than variables. 

```js

doSomething(); // Error - undefined at this point.
doaction();     // Works because of hoisting.

var doSomething() = function() {
    // This is hoisted
};

function doAction() {
    // This is not hoisted
}
```

## `let` and `const`

Variables declared with `let` are:
- Not hoisted: Can only be used after the line on which they are declared.
- Block-scoped: Unlike `var`, `let` variables are only available inside the scope in they are declared. E.g., `var` variables declared in a loop are available outside it.

`const` variables must be initialized where declared and cannot be reassigned.

TIP: `var` is obsolete, do not use again.
TIP: Use `const` whenever possible. 

_TODO: Read about callbacks and closures_

## Values vs References

Primitives: `Boolean`, `undefined`, `String`, `Number` and `null` are copied _by value_. This means when a variable of one of this type is assigned to another variable, A new independent copy of the value is creadted.

References: `Array`, `Object`, `Function` are copied by reference. I.e., many variables can control the same value.

_TODO: Read more about values and references in JS_

## Modern JavaScript features 

**Template literals** allow for evaluating variables inside string literals. They are written with backticks _``_, which are used for multiline strings. E.g:

```js
let str = `
    Hello ${name},

    How are you?
`;
```

**Arrow functions** are a cleaner way of writing callbacks. 

```js
const action = (a, b) => {
    const x = a + b
    return x;
};

const action2 = (a, b) => a + b;
```

**Methods** are functions attached to objects.

```js
const obj1 = {
    a,
    b,
    add = function() {
        return this.a + this.b;
    }
};
```

**Getters and setters** are created by placing `get` and `set` respectively, before a method name. The method can then be called without `()`.

```js
const obj1 = {
    a,
    b,
    get add = function() {
        return this.a - this.b;
    },
    set plus = function(name) {
        this.b = name;
    }
};

const y = obj1.add // Get
obj1.plus = 4;     // Set
```

**Array and object destructuring** is used to create new variables from elements of an array of fields of an object.

```js
const arr = [1, 3, 5];
const [a, b, c] = arr;

const obj = {
    a: 4,
    b: 5
};

const {x, y} = obj
```

_TODO: Read about `this` keyword in JS. And about object prototypes_



