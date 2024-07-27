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
###	let
  -	are block scoped
  -	can be updated, but not be re-declare once created.
  -	It stores undefined if not initialized.
###	Const
  -	Neither updated nor re-declared once created.
  -	Must be initialized with a value.
```
Console.log(x);   Console.log(x);
                  Var x = 10;	
// Error          // x has not defined	"Undefined" due to hoisting //	
```
