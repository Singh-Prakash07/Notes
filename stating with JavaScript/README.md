  -Loosely typed language
  -Means we need not to define data type of variables
## Two ways to run JS
### In HTML
  - Writing JS within HTML file	External Linking
        
```
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

-	In Node JS complier
## Use of var, let, const
###	var
  -	globally scoped
  -	can be updated and re-declare anywhere
  -	It stores undefined if not initialized.
###	let
  -	are block scoped
  -	can be updated, but not be re-declare once created.
  -	It stores undefined if not initialized.
###	Const
  -	Neither updated nor re-declared once created.
  -	Must be initialized with a value.
```
Console.log(x);    // Error   Console.log(x); // undefined
                              Var x = 10;	    // due to hoisting, later we talk about hoisting	
```
## Data type
  - we use typeof to get data type of a variable ex--> ` console.log(typeof 123) // number`
  - JavaScript has 8 datatypes
  - String       // "Yellow" , 23+"volvo", `js evaluates from left to right.`
    - 16+4+ "volvo" `20volvo` // "volvo" +16 + 4 `volvo164` // 4* "volvo" `NaN`
  - Number       // 16, 6.7
  - Bigint       // 
  - Boolean      // true, false
  - Undefined    //
  - Null         //
  - Symbol       //
  - Object       // `const person = {firstName: "John", lastName: "Doe"};`


























































