# Objects
+ Ihere are eight data types in JavaScript. Seven of them are called “primitive”, 
because their values contain only a single thing (be it a string or a number or whatever).
+ In contrast, objects are used to store keyed collections of various data and more complex entities.
+ In JavaScript, An object can be created with figure brackets {…} with an optional list of properties.
  ```
    let user = {     // an object created with property
    name: "John",  // by key "name" store value "John"
    age: 30        // by key "age" store value 30
    "likes birds": true,  // multiword property name must be quoted
    };
  ```
+ A property is a “key: value” pair, where key is a string (also called a “property name”), and value can be anything.
+ An empty object (“empty cabinet”) can be created using one of two syntaxes:
  ```
    let user = new Object(); // "object constructor" syntax
    let user = {};  // "object literal" syntax
  ```

The value can be of any type. Let’s add a boolean one:

user.isAdmin = true;
> [!NOTE]
> To remove a property, we can use the delete operator: `delete user.age;`

> [!TIP]
> The last property in the list may end with a comma:
> That is called a “trailing” or “hanging” comma. Makes it easier to add/remove/move around properties, because all lines become alike.

## Square brackets
+ For multiword properties, the dot access doesn’t work:
> [!CAUTION]
> `user.likes birds = true;` // this would give a syntax error
+ The dot requires the key to be a valid variable identifier. That implies: contains no spaces, doesn’t start with a digit and doesn’t include special characters ($ and _ are allowed).
+ There’s an alternative “square bracket notation” that works with any string:

let user = {};
1. set
  user["likes birds"] = true;
2. get
  alert(user["likes birds"]); // true
3. delete
  delete user["likes birds"];
+ Now everything is fine. Please note that the string inside the brackets is properly quoted (any type of quotes will do).
+ Square brackets also provide a way to obtain the property name as the result of any expression :
  ```
    let key = "likes birds";
    user[key] = true;
    // same as user["likes birds"] = true;
  ```
+ Here, the variable key may be calculated at run-time or depend on the user input. And then we use it to access the property. That gives us a great deal of flexibility.
  ```
    let key = prompt("What do you want to know about the user?", "name");
    // access by variable
    alert( user[key] ); // John (if enter "name")
    // The dot notation cannot be used in a similar way:
    let key = "name";
    alert( user.key ) // undefined
  ```
## Computed properties
+ We can use square brackets in an object literal, when creating an object. That’s called computed properties.
  ```
    let fruit = prompt("Which fruit to buy?", "apple");
    let bag = {
      [fruit]: 5, // the name of the property is taken from the variable fruit
    };
    alert( bag.apple ); // 5 if fruit="apple"
    let bag = {
    [fruit + 'Computers']: 5 // bag.appleComputers = 5
    };
  ```
+ The meaning of a computed property is simple: [fruit] means that the property name should be taken from fruit.
+ Square brackets are much more powerful than dot notation. They allow any property names and variables. But they are also more cumbersome to write.

## Property value shorthand
In real code, we often use existing variables as values for property names.
  ```
    function makeUser(name, age) {
      return {
        name: name,
        age: age,
        // ...other properties
      };
    }
    let user = makeUser("John", 30);
    alert(user.name); // John
  ```
+ In the example above, properties have the same names as variables. The use-case of making a property from a variable is so common, that there’s a special property value shorthand to make it shorter.
+ Instead of name:name we can just write name, like this:
    ```
    function makeUser(name, age) {
      return {
        name, // same as name: name
        age,  // same as age: age( We can use both normal properties and shorthands in the same object: like age: 30)
        // ...
      };
    }
  ```
## Property names limitations
+ As we already know, a variable cannot have a name equal to one of the language-reserved words like “for”, “let”, “return” etc.
+ But for an object property, there’s no such restriction:
  ```
    // these properties are all right
    let obj = {
      for: 1,
      let: 2,
      return: 3
    };
  ```
+ Other types are automatically converted to strings.
+ For instance, a number 0 becomes a string "0" when used as a property key:
  ```
    let obj = {
    0: "test" // same as "0": "test"
    };
    alert( obj["0"] ); // test
    alert( obj[0] ); // test (same property)
  ```
+ There’s a minor gotcha with a special property named __proto__. We can’t set it to a non-object value:
  ```
    let obj = {};
    obj.__proto__ = 5; // assign a number
    alert(obj.__proto__); // [object Object] - the value is an object, didn't work as intended
  ```
Reading a non-existing property just returns undefined.

let user = {};

alert( user.noSuchProperty === undefined ); // true means "no such property"
There’s also a special operator "in" for that.

The syntax is:

"key" in object
For instance:

let user = { name: "John", age: 30 };

alert( "age" in user ); // true, user.age exists
alert( "blabla" in user ); // false, user.blabla doesn't exist
Please note that on the left side of in there must be a property name. That’s usually a quoted string.

If we omit quotes, that means a variable should contain the actual name to be tested. For instance:

let user = { age: 30 };

let key = "age";
alert( key in user ); // true, property "age" exists
Why does the in operator exist? Isn’t it enough to compare against undefined?

Well, most of the time the comparison with undefined works fine. But there’s a special case when it fails, but "in" works correctly.

It’s when an object property exists, but stores undefined:

let obj = {
  test: undefined
};

alert( obj.test ); // it's undefined, so - no such property?

alert( "test" in obj ); // true, the property does exist!
In the code above, the property obj.test technically exists. So the in operator works right.

Situations like this happen very rarely, because undefined should not be explicitly assigned. We mostly use null for “unknown” or “empty” values. So the in operator is an exotic guest in the code.

The "for..in" loop
To walk over all keys of an object, there exists a special form of the loop: for..in. This is a completely different thing from the for(;;) construct that we studied before.

The syntax:

for (key in object) {
  // executes the body for each key among object properties
}
For instance, let’s output all properties of user:

let user = {
  name: "John",
  age: 30,
  isAdmin: true
};

for (let key in user) {
  // keys
  alert( key );  // name, age, isAdmin
  // values for the keys
  alert( user[key] ); // John, 30, true
}
Note that all “for” constructs allow us to declare the looping variable inside the loop, like let key here.

Also, we could use another variable name here instead of key. For instance, "for (let prop in obj)" is also widely used.

Ordered like an object
Are objects ordered? In other words, if we loop over an object, do we get all properties in the same order they were added? Can we rely on this?

The short answer is: “ordered in a special fashion”: integer properties are sorted, others appear in creation order. The details follow.

As an example, let’s consider an object with the phone codes:

let codes = {
  "49": "Germany",
  "41": "Switzerland",
  "44": "Great Britain",
  // ..,
  "1": "USA"
};

for (let code in codes) {
  alert(code); // 1, 41, 44, 49
}
The object may be used to suggest a list of options to the user. If we’re making a site mainly for a German audience then we probably want 49 to be the first.

But if we run the code, we see a totally different picture:

USA (1) goes first
then Switzerland (41) and so on.
The phone codes go in the ascending sorted order, because they are integers. So we see 1, 41, 44, 49.

Integer properties? What’s that?
The “integer property” term here means a string that can be converted to-and-from an integer without a change.

So, "49" is an integer property name, because when it’s transformed to an integer number and back, it’s still the same. But "+49" and "1.2" are not:

// Number(...) explicitly converts to a number
// Math.trunc is a built-in function that removes the decimal part
alert( String(Math.trunc(Number("49"))) ); // "49", same, integer property
alert( String(Math.trunc(Number("+49"))) ); // "49", not same "+49" ⇒ not integer property
alert( String(Math.trunc(Number("1.2"))) ); // "1", not same "1.2" ⇒ not integer property
…On the other hand, if the keys are non-integer, then they are listed in the creation order, for instance:

let user = {
  name: "John",
  surname: "Smith"
};
user.age = 25; // add one more

// non-integer properties are listed in the creation order
for (let prop in user) {
  alert( prop ); // name, surname, age
}
So, to fix the issue with the phone codes, we can “cheat” by making the codes non-integer. Adding a plus "+" sign before each code is enough.

Like this:

let codes = {
  "+49": "Germany",
  "+41": "Switzerland",
  "+44": "Great Britain",
  // ..,
  "+1": "USA"
};

for (let code in codes) {
  alert( +code ); // 49, 41, 44, 1
}
Now it works as intended.

Summary
Objects are associative arrays with several special features.

They store properties (key-value pairs), where:

Property keys must be strings or symbols (usually strings).
Values can be of any type.
To access a property, we can use:

The dot notation: obj.property.
Square brackets notation obj["property"]. Square brackets allow taking the key from a variable, like obj[varWithKey].
Additional operators:

To delete a property: delete obj.prop.
To check if a property with the given key exists: "key" in obj.
To iterate over an object: for (let key in obj) loop.
What we’ve studied in this chapter is called a “plain object”, or just Object.

There are many other kinds of objects in JavaScript:

Array to store ordered data collections,
Date to store the information about the date and time,
Error to store the information about an error.
…And so on.
They have their special features that we’ll study later. Sometimes people say something like “Array type” or “Date type”, but formally they are not types of their own, but belong to a single “object” data type. And they extend it in various ways.

Objects in JavaScript are very powerful. Here we’ve just scratched the surface of a topic that is really huge. We’ll be closely working with objects and learning more about them in further parts of the tutorial.

Tasks
Hello, object
importance: 5
Write the code, one line for each action:

Create an empty object user.
Add the property name with the value John.
Add the property surname with the value Smith.
Change the value of the name to Pete.
Remove the property name from the object.
solution
Check for emptiness
importance: 5
Write the function isEmpty(obj) which returns true if the object has no properties, false otherwise.

Should work like that:

let schedule = {};

alert( isEmpty(schedule) ); // true

schedule["8:30"] = "get up";

alert( isEmpty(schedule) ); // false
Open a sandbox with tests.

solution
Sum object properties
importance: 5
We have an object storing salaries of our team:

let salaries = {
  John: 100,
  Ann: 160,
  Pete: 130
}
Write the code to sum all salaries and store in the variable sum. Should be 390 in the example above.

If salaries is empty, then the result must be 0.

solution
Multiply numeric property values by 2
importance: 3
Create a function multiplyNumeric(obj) that multiplies all numeric property values of obj by 2.

For instance:

// before the call
let menu = {
  width: 200,
  height: 300,
  title: "My menu"
};

multiplyNumeric(menu);

// after the call
menu = {
  width: 400,
  height: 600,
  title: "My menu"
};
Please note that multiplyNumeric does not need to return anything. It should modify the object in-place.

P.S. Use typeof to check for a number here.

Open a sandbox with tests.

solution
