# string to number
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
# number to string
```
  let score = 5;
  score.toString();  // "5"
```
#  string and number to boolean
```
"" ----> false
0 -----> false
"pk" --> true
5 -----> true
null --> false
undefined-> false
```

# Heap and stack Memory
+ Primitive type stored in Stack memory.( variable contains actual value)
+ Non-Primitive type stored in heap memory.( variable contains reference of value(or object, array).

