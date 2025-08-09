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
## Access elements
1. Using square bracket
```
arr[i], if i >= 0 and <arr.length;
arr[0]; // access first element.
arr[arr.length-1]; // access last element.
```
> [!Note]
>  we can't use -ve index in square bracket `arr[-1]; // undefine`. because the index in square brackets is treated literally.
+ for negative values of i, it steps back from the end of the array.
2. Using "at"
```
arr.at(0); // access first element.
arr.at(-1); // last element.
```

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
```
for (let i = 0; i < arr.length; i++) {
  alert( arr[i] );
}

for (let fruit of fruits) {
  alert( fruit );
}

for (let key in arr) { // we shouldn’t use for..in for arrays, since it use in object and it is slow
  alert( arr[key] ); 
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
## Some more about methods

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

### Some Static methods
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
### 1. forEach
+ it didn't return anything, instead excute fn on each element of array.
```
const arr = [1, 2, 3];
arr.forEach((val) => console.log(val));   // 1  2  3
function print(n){
 console.log(n);
}
arr.forEach(print)  // 1  2   3
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
### 3. filter
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
### 4. reduce
+ The `reduce()` method executes a **reducer function** on each element of the array, resulting in a single output value.
```
[1, 2, 3, 4].reduce((accumulator, currentValue) => accumulator + currentValue, 0)
```
+ accumulator stores the running total (starts at 0), and currentValue is the current element.  The function returns the updated total, which becomes the next accumulator.
+ The final result is 10.










