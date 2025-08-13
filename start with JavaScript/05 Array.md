## create an array
+ Array is also an Object, so all methods work 
+ Arrays in JavaScript can work both as a queue and as a stack. They allow you to add/remove elements, both to/from the beginning or the end.
+ In computer science, the data structure that allows this, is called deque.
There are two syntaxes for creating an empty array:
```
let arr = new Array();
let arr = new Array(5);  // creates an array of length 5.
const arr = new Array(1, 2, 3,, 4, 5); // [1, 2, 3, 4, 5]
let arr = []; // Mostly we use this syntax.
let arr = [ 'Apple', { name: 'John' }, true, function() { alert('hello'); }, ]; // “trailing comma” style
```
## copy array
1. Spread Syntax (...)
+ The spread syntax is a modern and concise way to create a shallow copy of an array.
```
let sparseArray = [1, , 3]; // Index 1 is empty
let copiedSparse = [...sparseArray];
console.log(copiedSparse); // [1, empty, 3]
```
2. Array.prototype.slice()
+ The slice() method returns a shallow copy of a portion of an array into a new array object. When called without any arguments, it copies the entire array.
```
let sparseArray = [1, , 3];
let copiedSparse = sparseArray.slice();
console.log(copiedSparse); // [1, empty, 3]
```
3. Array.from()
+ This static method creates a new, shallow-copied array from an array-like or iterable object.
+ Array.from() handles sparse arrays by treating the empty slots as undefined and explicitly adding undefined to the new array.
```
let sparseArray = [1, , 3];
let copiedSparse = Array.from(sparseArray);
console.log(copiedSparse); // [1, undefined, 3]
```
4. for loop

## Access elements
1. Using square bracket
```
arr[i], if i >= 0 and <arr.length;
arr[0]; // access first element.
arr[arr.length-1]; // access last element.
```
> [!Note]
>  we can't use -ve index in square bracket `arr[-1]; // undefine`. because the index in square brackets is treated literally. we have "at" if we wise to use -ve indx.
2. Using "at"
```
arr.at(0); // access first element.
arr.at(-1); // last element.
```
+ for negative values of i, it steps back from the end of the array.

## Add element in an array
 ### Using push/pop
```
// we use this method with stack
arr.push("a"); //adds an element to the end and returns the new length of the array.
arr.pop(); //remove and return an element from the end, if array is empty returns "undefined".
```
### Using shift/unshift
```
arr.shift() ); // get an element from the beginning, advancing the queue, so that the 2nd element becomes the 1st.
arr.unshift('Apple'); // Add the element to the beginning of the array, advancing the queue, so that the 1nd element becomes the 2st and returns new length of array.

```
+ Methods push/pop run fast, while shift/unshift are slow.
## Loops
1. for 
```
for (let i = 0; i < arr.length; i++) {
  alert( arr[i] );
}
```
2. for... of
+ The for...of loop is designed to iterate over the values of an iterable object. This includes built-in iterables like Array, Map, Set, String, and others.
> [!Caution]
> It doesn't work on plain objects because they are not iterable by default. You would have to get the object's keys first (e.g., using Object.keys()) and then iterate over them.
```
const myString = "hello";
for (const char of myString) {
  console.log(char); // Prints: "h", "e", "l", "l", "o"
}
```
3. for...in
+ The for...in loop is designed to iterate over all enumerable properties of an object. This means it will loop through the property keys (or names) of the object, including those on the object's prototype chain.
> [!Caution]
> It's generally not recommended for iterating over arrays because the order of properties is not guaranteed, and it can also iterate over unwanted properties from the prototype chain.
```
for (let key in arr) { // we shouldn’t use for..in for arrays, since it use in object and it is slow
  alert( arr[key] ); 
}

const myObject = { a: 1, b: 2, c: 3 };
for (const key in myObject) {
  console.log(key); // Prints: "a", "b", "c"
  console.log(myObject[key]); // Prints: 1, 2, 3
}

const myArray = [10, 20, 30];
myArray.customProperty = 'hello';
for (const index in myArray) {
  console.log(index); // Prints: "0", "1", "2", "customProperty"
}
```
## Comparision (==)
+ Two objects are equal == only if they’re references to the same object.
```
[] == []; // false
[0] == [0]; // false
0 == [] ; // true
'0' == []; // false
0 == ''; // true, as '' becomes converted to number 0
'0' == ''; // false, no type conversion, different strings
```
## methods
1. Mutating Methods
   
### Array methods and empty slots
+ Array methods have different behaviors when encountering empty slots in sparse arrays.
+ methds like concat filter(), forEach(), indexOf(), map(), reverse(), slice(), sort(), and splice(), etc don't visit empty slots at all.
+ entries(), fill(), find(), findIndex(), includes(), join(), keys(), toLocaleString(), toSorted(), etc do not treat empty slots specially.
  
### Copying methods and mutating methods
 + Some methods do not mutate the existing array that the method was called on, but instead return a new array eg. toReversed(), toSorted(), etc.
 + Mutating methos are push(), pop(), sort(), splice(), etc.
 + An easy way to change a mutating method into a non-mutating alternative is to use the spread syntax or slice() to create a copy first.

## Some More Methods
+ `const arr = [1, 2, 3, 4, 5]`
+ `arr.includes(4)` // true  -->return true if 4 exits in array else false.
+ `arr.indexOf(4)` // 3  -->return the first index of 4, return -1 if 4 not exits in array.
+ `arr.join()` // "1,2,3,4,5" , it return string joining all element of array.
+ `arr.join("-")` //'1-2-3-4-5'
+ `arr.slice(1, 3)` //`[2, 3]` returns a new array including index 1 to 2. without changing original array.
+ `arr.splice(1, 3)` // `[2, 3, 4]` it return a new array including index 1 to 3. but removes these element from original array.
+ `const newArr = arr1.concate(arr2)` // it merge both elements of both array and returns a new array.
+  we have a better way to merge more than one arrays using spread operator.
+  `const newArr = [...arr1, ...arr2, ...arr3]`// so on.
+ `arr.flat(Infinity)` // to reduce 2D-3D or more into 1D array.
## some advance js concept
3 Prototype Methods 
+ The methods I previously discussed (like map(), push(), filter()) are all prototype methods. This means they are defined on the Array.prototype object. When you create an array, for example, let myArray = [1, 2, 3], myArray doesn't have its own map function. Instead, it inherits it from Array.prototype. This is how all arrays can access the same set of methods without each array needing its own copy, which saves memory.
```
let arr = [1, 2, 3];
console.log(arr.__proto__ === Array.prototype); // true
console.log(arr.hasOwnProperty('map')); // false, because it's inherited
```
2. Some Static methods
 + Static methods are methods that belong to the Array class itself, not to an instance of an array. You call them directly on the Array constructor, like Array.isArray(), not on a variable holding an array. They are often utility functions that don't need to operate on an existing array.
1. `Arrays.sort(arr)` // It basically sort an array in ascending order.
2. from()
```
Array.from(arrayLike)
Array.from(arrayLike, mapFn)
Array.from(arrayLike, mapFn, thisArg)
console.log(Array.from('foo')); // ["f", "o", "o"]
console.log(Array.from([1, 2, 3], (x) => x + x));// [2, 4, 6]
```
3. `Array.isArray(arr)` // return true/false
4. `Array.of('foo', 2, 'bar', true); // ["foo", 2, "bar", true]`
5. Suppose we have 4-5 variable and want to create an array. `Array.of(element1, element2, /* …, */ elementN)`
6. etc..

## Arrays High Order Function
1. forEach
+ it didn't return anything, instead excute fn on each element of array.
+ forEach() is non-mutating. It doesn't change the original array.
+ Using forEach itself does not inherently mutate the array on which it is called. forEach is a loop that iterates through each element of an array and executes a callback function for each one. The key point is that it's what you do inside the callback function that determines if the original array is mutated.
### forEach Without Mutation (Non-Mutating)
+ In this case, the forEach loop simply reads the values of the array. The callback function doesn't modify the original array.
```
const numbers = [1, 2, 3];
// This forEach loop doesn't change the 'numbers' array.
// It just logs the values and performs a calculation on a copy.
numbers.forEach((num) => {
  const doubledNum = num * 2;
  console.log(doubledNum);
});
console.log(numbers); // Output: [1, 2, 3] - The original array is unchanged.
```
### forEach with Mutation (Mutating)
+ Here, the callback function explicitly modifies the original array. The forEach loop is still just iterating, but the code inside the loop is directly changing the array's contents.
```
const numbers = [1, 2, 3];

// This forEach loop mutates the original array.
numbers.forEach((num, index, arr) => {
  // `arr` is a reference to the original 'numbers' array.
  // We are directly modifying the element at the current index.
  arr[index] = num * 2;
});

console.log(numbers); // Output: [2, 4, 6] - The original array has been mutated.
```
### 2. map
+ When we need to create a new modify array from existing one.
+ It returns new array and does not modigy original array.
+ Syntax
```
array.map(callback(currentValue, index, array), thisArg)
        
callback: A function to execute on each element. It can take up to three arguments:
currentValue: The current element being processed in the array.
index (optional): The index of the current element being processed.
array (optional): The array `map()` was called upon.
thisArg (optional): Value to use as `this` when executing `callback`.
```
+ Example :
```
const arr1 = new Array(5).fill(0).map((_, i) => i + 1); // arr1 = [1, 2, 3, 4, 5]
```
+ the underscore _ is a common convention in JavaScript to indicate a function parameter that is intentionally ignored. It's a placeholder for an argument that the developer doesn't need or plan to use.
+ The first parameter, _, corresponds to the currentValue from the array (which is 0 in every iteration). The developer doesn't need this value, so they use _ as a clear signal to others reading the code that it's being ignored.
+ The second parameter, i, corresponds to the index of the current element being processed (0, then 1, then 2, etc.). This is the value the developer actually wants to use. 
+ The expression i + 1 returns the index plus one.
```
const newArr = arr.map(val => val*2);   // 2  4  6
```
### Why map() is a better choice for creating a new array
+ f your goal is to create a new array with modified elements without changing the original, you should use the map() method instead. map() is designed specifically for this purpose and is also non-mutating.
### filter
+ It return new array after filtering existing array.
+ Syntax
```
array.reduce(callback(accumulator, currentValue, index, array), initialValue);

accumulator: The value returned from the last callback execution. For the first iteration, it's              the `initialValue` you provide (or the first element of the array).
currentValue: The current element being processed.
index (optional): The index of the current element.
array (optional): The array `reduce()` was called upon.
```
```
const newArr = arr.filter((val) => val % 2 == 0); // an array of even numbers only.
```
### reduce
+ The `reduce()` method executes a **reducer function** on each element of the array, resulting in a single output value.
```
[1, 2, 3, 4].reduce((accumulator, currentValue) => accumulator + currentValue, 0)
```
+ accumulator stores the running total (starts at 0), and currentValue is the current element.  The function returns the updated total, which becomes the next accumulator.
+ The final result is 10.

