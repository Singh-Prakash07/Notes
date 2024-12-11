## create an array
+ Array is also an Object, so all methods work 
+ Arrays in JavaScript can work both as a queue and as a stack. They allow you to add/remove elements, both to/from the beginning or the end.
+ In computer science, the data structure that allows this, is called deque.
There are two syntaxes for creating an empty array:
```
let arr = new Array();
let arr = new Array(5);  // creates an array of length 5.
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

for (let key in arr) { // we shouldn’t use for..in for arrays, since it use in object
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











