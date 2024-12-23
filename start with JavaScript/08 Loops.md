## 1. for loop
  Syntax: `for (initialization; condition; increment/decrement) { // code to be executed }`
```
const myArray = [10, 20, 30, 40, 50];
for (let i = 0; i < myArray.length; i++) {
  console.log(myArray[i]);
}
```
## 2. while loop
  Syntax: `while (condition) { // code to be executed }`
```
let counter = 0;
while (counter < 3) {
  console.log("Counter: " + counter);
  counter++;
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
