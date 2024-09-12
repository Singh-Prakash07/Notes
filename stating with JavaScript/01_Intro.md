  -Dynamic typed language
  -Means we need not to define data type of variables
## Three ways to run JS
1. In HTML
  - In same HTML file
```
Writing JS within HTML file	External Linking     // linking external JS file in HTML 
<body>                      
  // html statement
<script>
  // JS statements
</script>
</body>
```
- linking external JS file in HTML 
```	
 <head>
   <script src =” file_path.js”>
   </script>
   <title>
   </title>
</head>
<body>
```

2.	In Node JS complier
3.	In browser's console
## Use of var, let, const
###	var
  -	globally scoped
  -	can be updated and re-declare anywhere
  -	It stores undefined if not initialized.
  -	try to not use var in js
###	let
  -	are block scoped
  -	can be updated, but not be re-declare once created.
  -	It stores undefined if not initialized.
###	Const
  -	Neither updated nor re-declared once created.
  -	Must be initialized with a value.
  -	mostly we use const type variable
```
Console.log(x);    // Error   Console.log(x); // undefined
                              Var x = 10;	    // due to hoisting, later we talk about hoisting	
```

## checking equality
  1. Strict Equality (===)
       - Compares both the value and the type of the operands.
         ```
         console.log(5 === 5); // true
         console.log(5 === "5"); // false (different types
         ```
  3. Loose Equality (==)
      - Compares the values of the operands, but performs type coercion if necessary.
        ```
        console.log(5 == "5"); // true (type coercion)
        console.log(true == 1); // true (type coercion)
        ```
### All operators are same as in java
```
'Prakash'+34; // 'Prakash34'  (String)
'23'+5;       //  '235'       (string)
'45'*2;       //  90          (Number)
'Prakash'*5   // Error
'ab'*'cd'     // NaN 
```
## Ternary Operator
```
const age = 20;
age >= 18 ? console.log('Yes') : console.log('No');
result  --> No

let result = age >= 45 ? 'Yes' : 'No';
// result = 'No'
result = age>45 ? console.log('yes') : console.log('no'); // no
// result = undefined
```


















































