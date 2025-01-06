
+ Objects: for...in (with hasOwnProperty() for own properties)
+ Maps: for...of (iterates over key-value pairs)
+ Sets: for...of (iterates over values)

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
### Set
```
const mySet = new Set([1, 2, 3]);
const setArray = Array.from(mySet); 

for (let i = 0; i < setArray.length; i++) {
  console.log(setArray[i]); 
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
### String
```
const str = "hello";
for (let i in str) {
  console.log(str[i]); // Iterates over indices
}
```
### Array (Not recommended) 
```
const numbers = [1, 2, 3];
for (let i in numbers) {
  console.log(numbers[i]); // Order might not be preserved
}
```
### Object
```
const person = { name: "Alice", age: 30 };
for (const key in person) {
  console.log(key, person[key]);
}
for (const key in person) {
    if (person.hasOwnProperty(key)) {
        console.log(key, person[key]);
    }
}
```

## 4. for...of loop
Syntax: for (value of iterable) { // code to be executed }
 Iterates over iterable objects (arrays, strings, maps, sets, etc.), accessing the values directly.
### String
```
const str = "hello";
for (const char of str) {
  console.log(char);
}
```
### Array
```
const numbers = [1, 2, 3];
for (const number of numbers) {
  console.log(number);
}
```
### Object (Not directly iterable)
```
// Convert Object to an array of entries
const person = { name: "Alice", age: 30 };
const entries = Object.entries(person);
for (const [key, value] of entries) {
  console.log(key, value);
}
```
### Map
```
const myMap = new Map([["a", 1], ["b", 2]]);
for (const [key, value] of myMap) {
  console.log(key, value);
}
```
### Set
```
const mySet = new Set([1, 2, 3]);
for (const item of mySet) {
  console.log(item);
}
```
