## create an array
+ Arrays in JavaScript can work both as a queue and as a stack. They allow you to add/remove elements, both to/from the beginning or the end.
+ In computer science, the data structure that allows this, is called deque.
There are two syntaxes for creating an empty array:
```
let arr = new Array();
let arr = []; // Mostly we use this syntax.
```
+ `let arr = [ 'Apple', { name: 'John' }, true, function() { alert('hello'); }, ];` // “trailing comma” style

## Access elements
1. Using square bracket
```
arr[i], if i >= 0 and <arr.length;
arr[0]; // access first element.
arr[arr.length-1]; // access last element.
```
> [! Note]
>  we can't use -ve index in square bracket `arr[-1]; // undefine`. because the index in square brackets is treated literally.
+ for negative values of i, it steps back from the end of the array.
2. Using "at"
```
arr.at(0); // access first element.
arr.at(-1); // last element.
```

## Add element in an array
 ### 
```
arr.push("a"); //adds an element to the end and returns the new length of the array.
arr.pop(); //remove and return an element from the end, if array is empty returns "undefined".
```






