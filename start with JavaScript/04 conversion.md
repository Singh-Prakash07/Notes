## string to number
+ we always use captalize name like class_name to convert in differnet data types. 
```
  let score = " 55";  // string
  let valueInNumber = Number(score)  // Number and its value is 55
```
>[!CAUTION]
>But what if given string does not contains a number, then it always converted into number but is value is NaN or something else, we need take care about it.
  ```
  let score = "33abc";
  let valueInNumber = Number(score);   // typeof gives Number  but its value is NaN.
  null --> converted to   0.
  undefined -----> NaN
  boolean
  true      ------> 1
  false      -----> 0
  ```
## number to string
```
  let score = 5;
  Console.log(String(score)); // "5", It handles null and undefined value as 'null', 'undefined'.
  score.toString();  // "5", throw typeError for null and undefined value.
  score.toString(2); // "101" convert and store in binary string.
  Console.log(""+score); // "5", null+5 = 5, undefined+5 = NaN.
```
## string and number to boolean
```
"" ----> false
0 -----> false
"pk" --> true
5 -----> true
null --> false
undefined-> false
```

## Heap and stack Memory
+ Primitive type stored in Stack memory.( variable contains actual value)
+ Non-Primitive type stored in heap memory.( variable contains reference of value(or object, array).

## Control Flow

### Nullish Coalescing Operator(??)
+ This operator check for null or undefined values in a variable.
+ it returns its right-hand side operand when its left-hand side operand is null or undefined, and otherwise returns its left-hand side operand.
```
const baz = 0 ?? 42; // 0
const baz = null ?? 'prakash'; // 'prakash'
const baz = undefined ?? 42; // 42
const baz = null ?? 42 ?? undefined; // 42
const baz = null ?? undefined; // undefined
const baz =  undefined ?? null; // null
```
### Ternary Operator
+ It is the only JS operator that takes three operands: a condition followed by a question mark (?), then an expression to execute if the condition is truthy followed by a colon (:), and finally the expression to execute if the condition is falsy.
```
let value = check ? 10 : 20   // if check is true, 10 assign to value else 20 assign.
```
### do.. while loop
```
do{
}while(condition);
```
