## 1.Simple function
```

function myFun(unlimited_parameters<optional>){ there is no any return type
  // code
} we could have any number of parameters.
eg. function myFun(){}; // without parameter
    function myFun(parameter1, parameter2){}// this function accepting two parameters.

myFun; // reference of function
myFun(); // excution
const result = myFun();
```
## 2. expression function
```
const add = function(num){
  return num+1;
}
```
## 3. Arrow function
```
const print = (parameter<optional>) => {
  console.log("Hello Arrow Function");
}
print();
const add = () => a+b; // one liner, it returns sum of a and b.
```
### This Keyword

```
const obj = {
  value: 10,
regular : function(){
    console.log(this.value); // 'this' refers to the 'obj' output is 10.
  },
  arrow : () =>{
    console.log(this.value); // 'this' refers to the global object (window in browsers) or undefined in strict mode, output is undefined.
  },
  regularFunction: function() {
    setTimeout(function() {
      console.log(this.value); // 'this' inside setTimeout refers to the global object (window in browsers) or undefined in strict mode
    }, 1000);
  },
  arrowFunction: function() {
    setTimeout(() => {
      console.log(this.value); // 'this' inside setTimeout refers to the 'obj' because arrow function does not bind its own this
    }, 1000);
  },
};

obj.regularFunction(); // Output: undefined (or a value from the global scope if not in strict mode)
obj.arrowFunction(); // Output: 10
```

## 4. High order function
+ High order fn => functions take functions as arguments (callbacks) or return functions. 
+ A callback function is a function that is passed as an argument to another function (often a higher-order function) and is executed after the outer function has finished its work.  It's a way to handle asynchronous operations or to customize the behavior of a function.
```
function operate(func, a, b) {
  return func(a, b);
}

function add(a, b) {
  return a + b;
}

const result = operate(add, 5, 3); // result is 8
```
+ `operate` is high order fn and `add` is callback fn
## 5. IIFE
+ Immediately Invoked Function Expressions(IIFE)
+ This function runs as soon as it is defined.
+ If we have multiple IIFE use comma(,) between them.
+ first enclosing bracket is definition, second enclosing bracket is execution of same function.
+ It helps to avoid polluting the global namespace.
```
(function () {
  // …
})();

(() => {
  // …
})();

(async () => {
  // …
})();
```
+ Parameter - when we write definition of function, the variable we use to take value is called parameters.
+ Argument - When we call a function, the value we pass is called arguments
## Hoisting
+ we can call(execute) a simple function before its definition, it is called hoisting.
+ It does not work in expression fn or arrow function, since JS run all simple function first, then other stuff.
## Accepting Infinite Arguments
### 'arguments' keyword
+ Every function except arrow have build in arguments keyword which contains all the parameters passed to this function, it does matter we have used variable to catch parameter, arguments object also catch all the parameters.
```
function add(){ // we do not write 'arguments' keyword as argument of function.
  console.log(arguments); // [3, 4, 5, 'er', [1, 2, 3]]
  console.log(arguments[arguments.length-1][2]; // 2
}
arr = [1, 2, 3];
add(3, 4, 5, 'er', arr);
```
### Rest Parameter
+ accepting multiple values using one variable in function
+ It works in all function either simple or arrow function.
```
function add(...number){
  let result = 0;
  number.forEach(element =>{
   result += element
  });
  return result;
}
console.log(add(1, 2, 3, 4, 5, 6, 7) // 28
function add(number1, number2, ... number) // number1->1, number2->2, number->[3, 4, 5, 6, 7]
```
| Feature	| arguments Keyword	| Rest Parameters (...) |
|----------|----------|----------|
| Type	| Array-like object	| True Array |
| Methods	| No direct array methods (needs conversion) except length and index based access | All array methods available directly |
| Arrow Functions |	Not available	| Available |
## spread operator(...array/set/object/etc)
+ The spread operator (...) is a modern syntax (introduced in ES6) that allows an iterable (like an array, string, or Set) to be expanded into its individual elements.
+ When we use the spread operator to copy an array or an object, it performs a shallow copy.
  + For primitive values (like numbers, strings, booleans), the spread operator copies the actual value.
  + For non-primitive values (like nested objects or arrays), the spread operator copies the reference to that nested value.
```
const originalArray = [1, 2, 3]; // array
const copiedArray = [...originalArray];

const defaults = { theme: 'dark', notifications: true };
const userSettings = { notifications: false, language: 'en' };
const finalSettings = { ...defaults, ...userSettings, debugMode: true }; // object

functionName(...iterable) // In function calls:
```
## Shallow Copy
+  shallow copy creates a new object or array, but it only copies the top-level elements or properties. If the original object or array contains nested objects or arrays, the shallow copy will not create new copies of these nested structures. Instead, it will copy their references.
+  Implication: If you modify a nested object or array within the shallow copy, the original object/array will also be affected because both the original and the copy are pointing to the same underlying nested data in memory.

## Deep Copy
+ creates a completely new object or array and recursively duplicates all levels of the original structure, including all nested objects and arrays.
+ The deep copy is entirely independent of the original. Changes made to any part of the deep copy (even nested elements) will not affect the original object or array.
+ For a true **deep copy** (where all nested structures are also duplicated), you would typically use methods like `JSON.parse(JSON.stringify(obj))` (with limitations) or a dedicated deep-cloning library, or the modern `structuredClone()` API.
