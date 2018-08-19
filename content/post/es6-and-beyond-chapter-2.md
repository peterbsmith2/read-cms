+++
chapter = "Syntax"
title = "YOU DON'T KNOW JAVASCRIPT"
subtitle = "ES6 AND BEYOND"
author = "KYLE SIMPSON"
chapter_number = 2
amazon = "https://www.amazon.com/You-Dont-Know-JS-Beyond/dp/1491904240/ref=sr_1_1?s=books&ie=UTF8&qid=1487530921&sr=1-1&keywords=es6+and+beyond"
github = "https://github.com/getify/You-Dont-Know-JS/blob/master/es6%20&%20beyond/README.md#you-dont-know-js-es6--beyond"
books=["YOU DON'T KNOW JAVASCRIPT"]
+++

## Quotes

### `let` Declarations

Pg. 8
> However, we can now create declarations that are bound to any block, called (unsurprisingly) block scoping. This means all we need is a pair of { .. } to create a scope. Instead of using var, which always declares variables attached to the enclosing function (or global, if top level) scope, use let:

```javascript
var a = 2;

{
    let a = 3;
    console.log( a );   // 3
}

console.log( a );       // 2
```

Pg. 9-10: 
> Unlike traditional var-declared variables, which are attached to the entire enclosing function scope regardless of where they appear, let declarations attach to the block scope but are not initialized until they appear in the block.
  
Pg. 10:
> ...I insist that let declarations should all be at the top of their scope.


### `const` Declarations

Pg. 12: 
> There's one other form of block-scoped declaration to consider: the const, which creates constants.
>
> What exactly is a constant? It's a variable that's read-only after its initial value is set.

### Spread / Rest


Pg. 13, Spreading: 
```javascript
function foo(x,y,z) {
    console.log( x, y, z );
}

foo( ...[1,2,3] );              // 1 2 3
```
(above reaplces pre-ES6 `foo.apply(null, [1,2,3]);`)  
  
Pg. 13, Gathering:  
```javascript
var a = [2,3,4];
var b = [ 1, ...a, 5 ];

console.log( b );                   // [1,2,3,4,5]
```
  
### Default Parameter Values

Pg. 16-17
```javascript
function foo(x = 11, y = 31) {
    console.log( x + y );
}

foo();                  // 42
foo( 5, 6 );            // 11
foo( 0, 42 );           // 42

foo( 5 );               // 36
foo( 5, undefined );    // 36 <-- `undefined` is missing
foo( 5, null );         // 5  <-- null coerces to `0`

foo( undefined, 6 );    // 17 <-- `undefined` is missing
foo( null, 6 );         // 6  <-- null coerces to `0`
```

### Default Value Expressions
(skipped)

### Destructuring

Pg. 19, Arrays:
```javascript
function foo() {
    return [1,2,3];
}

var tmp = foo(),
    a = tmp[0], b = tmp[1], c = tmp[2];

console.log( a, b, c );             // 1 2 3
```
Pg. 19, Objects:
```javascript
function bar() {
    return {
        x: 4,
        y: 5,
        z: 6
    };
}

var tmp = bar(),
    x = tmp.x, y = tmp.y, z = tmp.z;

console.log( x, y, z );             // 4 5 6
```
Pg. 20, Simplifying Above Examples:
```javascript
var [ a, b, c ] = foo();
var { x: x, y: y, z: z } = bar();

console.log( a, b, c );             // 1 2 3
console.log( x, y, z );             // 4 5 6
```

### Object Property Assignment Pattern
(skipped)


### Computed Property Names
Pg. 38
```javascript
var prefix = "user_";

var o = {
baz: function(..){ .. },
     [ prefix + "foo" ]: function(..){ .. },
     [ prefix + "bar" ]: function(..){ .. }
     ..
};
```

```javascript
var o = {
  ["f" + "oo"]() { .. }   // computed concise method
  *["b" + "ar"]() { .. }  // computed concise generator
};
```