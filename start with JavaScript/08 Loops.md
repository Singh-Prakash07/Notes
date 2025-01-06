| Loop Type | Arrays (Iterable) | Strings (Iterable) | Objects (Non-Iterable, Enumerable) | Maps/Sets (Iterable) |
|---|---|---|---|---|
| **for** | Yes | Yes (by index) | Yes (by index using Object.keys()) | Yes (by index) |
| **for...in** | Yes (but not recommended for order-dependent iteration) | Yes (iterates over indices) | Yes (iterates over keys) | No (use for...of) |
| **for...of** | Yes | Yes | No (unless converted to an iterable) | Yes |


## 1. for loop
  Syntax: `for (initialization; condition; increment/decrement) { // code to be executed }`
### String, Array
```
const myString = "Hello, world!";

// Using a traditional for loop
for (let i = 0; i < myString.length; i++) {
  console.log(myString[i]); // Output: Each character of the string
}
```
### Object
```
const person = { name: "Alice", age: 30 };
for (let i = 0; i < Object.keys(person).length; i++) {
  const key = Object.keys(person)[i];
  console.log(key, person[key]); 
}
```
### Map
```
const myMap = new Map([["a", 1], ["b", 2]]);
for (let i = 0; i < myMap.size; i++) {
  const key = Array.from(myMap.keys())[i];
  console.log(key, myMap.get(key)); 
}
```
## 2. do...while loop
Syntax: do { // code to be executed } while (condition);
```
let i = 0;
do {
  console.log("Value of i: " + i);
  i++;
} while (i < 5);
```
## 3. for...in loop

## 4. for...of loop
Syntax: for (value of iterable) { // code to be executed }
 Iterates over iterable objects (arrays, strings, maps, sets, etc.), accessing the values directly.
