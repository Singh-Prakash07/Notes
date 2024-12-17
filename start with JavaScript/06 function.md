## 1.Simple function
```

function myFun(unlimited_parameters<optional>){ there is no any return type
  // code
} we could any number of parameters.
eg. function myFun(){}; // without parameter
    function myFun(parameter1, parameter2){}// this function accepting two parameters.

myFun; // reference of function
myFun(); // excution
const result = myFun();
```
## 2. expression function
```
const add = function(num){
  return num+1;
}
```
## 3. Arrow function

```
const obj = {
  value: 10,
  regularFunction: function() {
    setTimeout(function() {
      console.log(this.value); // 'this' inside setTimeout refers to the global object (window in browsers) or undefined in strict mode
    }, 1000);
  },
  arrowFunction: function() {
    setTimeout(() => {
      console.log(this.value); // 'this' inside setTimeout refers to the 'obj' because arrow function does not bind its own this
    }, 1000);
  },
};

obj.regularFunction(); // Output: undefined (or a value from the global scope if not in strict mode)
obj.arrowFunction(); // Output: 10
```
+ Parameter - when we write definition of function, the variable we use to take value is called parameters.
+ Argument - When we call a function, the value we pass is called arguments

## Accepting Infinite Arguments
```
function add(){
  console.log(arguments); // [3, 4, 5, 'er', [1, 2, 3]]
  console.log(arguments[arguments.length-1][2]; // 2
}
arr = [1, 2, 3];
add(3, 4, 5, 'er', arr);
```
### Rest operator 
+ accepting multiple values using one variable in function
+ It works in all function either simple or arrow function.
```
function add(...number){
  let result = 0;
  number.forEach(element =>{
   result += element
  });
  return result;
}
console.log(add(1, 2, 3, 4, 5, 6, 7) // 28
function add(number1, number2, ... number) // number1->1, number2->2, number->[3, 4, 5, 6, 7]
```
###
