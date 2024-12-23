| Loop Type | Arrays (Iterable) | Strings (Iterable) | Objects (Non-Iterable, Enumerable) | Maps/Sets (Iterable) |
|---|---|---|---|---|
| **for** | Yes | Yes (by index) | Yes (by index using Object.keys()) | Yes (by index) |
| **while** | Yes | Yes (by index) | Yes (using conditions based on properties) | Yes (using iterators) |
| **do...while** | Yes | Yes (by index) | Yes (using conditions based on properties) | Yes (using iterators) |
| **for...in** | Yes (but not recommended for order-dependent iteration) | Yes (iterates over indices) | Yes (iterates over keys) | No (use for...of) |
| **for...of** | Yes | Yes | No (unless converted to an iterable) | Yes |


## 1. for loop
  Syntax: `for (initialization; condition; increment/decrement) { // code to be executed }`
```
const myString = "Hello, world!";

// Using a traditional for loop
for (let i = 0; i < myString.length; i++) {
  console.log(myString[i]); // Output: Each character of the string
}
```
## 2. while loop
  Syntax: `while (condition) { // code to be executed }`
```
const myArray = [10, 20, 30, 40, 50];
let index = 0;
while (index < myArray.length) {
  console.log(myArray[index); // print all element of array
  index++;
}
```
## 3. do...while loop
Syntax: do { // code to be executed } while (condition);
```
let i = 0;
do {
  console.log("Value of i: " + i);
  i++;
} while (i < 5);
```
## 4. for...in loop

## 5. for...of loop
Syntax: for (value of iterable) { // code to be executed }
 Iterates over iterable objects (arrays, strings, maps, sets, etc.), accessing the values directly.
