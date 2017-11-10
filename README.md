# JavaScript Style Guide

## 空隔包覆運算符號
Always put spaces around operators ( = + - * / ), and after commas:
```javascript=
var x = y + z;
var values = ["Volvo", "Saab", "Fiat"];
```
## 程式碼排縮
Always use 4 spaces for indentation of code blocks:
```javascript=
function toCelsius(fahrenheit) {
    return (5 / 9) * (fahrenheit - 32);
}
```
## statements規則
General rules for simple statements:

* Always end a simple statement with a semicolon.

```javascript=
var values = ["Volvo", "Saab", "Fiat"];

var person = {
    firstName: "John",
    lastName: "Doe",
    age: 50,
    eyeColor: "blue"
};
```

General rules for complex (compound) statements:

* Put the opening bracket at the end of the first line.
* Use one space before the opening bracket.
* Put the closing bracket on a new line, without leading spaces.
* Do not end a complex statement with a semicolon.

```javascript=
function toCelsius(fahrenheit) {
    return (5 / 9) * (fahrenheit - 32);
}
```
```javascript=
for (i = 0; i < 5; i++) {
    x += i;
}
```
```javascript=
if (time < 20) {
    greeting = "Good day";
} else {
    greeting = "Good evening";
}
```

## 物件規則
General rules for object definitions:

* Place the opening bracket on the same line as the object name.
* Use colon plus one space between each property and its value.
* Use quotes around string values, not around numeric values.
* Do not add a comma after the last property-value pair.
* Place the closing bracket on a new line, without leading spaces.
* Always end an object definition with a semicolon.
```javascript=
var person = {
    firstName: "John",
    lastName: "Doe",
    age: 50,
    eyeColor: "blue"
};
```
Short objects can be written compressed, on one line, using spaces only between properties, like this:
```javascript=
var person = {firstName:"John", lastName:"Doe", age:50, eyeColor:"blue"};
```
## 行數長度 < 80
For readability, avoid lines longer than 80 characters.

If a JavaScript statement does not fit on one line, the best place to break it, is after an operator or a comma.
```javascript=
document.getElementById("demo").innerHTML =
    "Hello Dolly.";
```
## 命名規則
Always use the same naming convention for all your code. For example:

* Variable and function names written as camelCase
* Global variables written in UPPERCASE (We don't, but it's quite common)
* Constants (like PI) written in UPPERCASE

Should you use hyp-hens, camelCase, or under_scores in variable names?

This is a question programmers often discuss. The answer depends on who you ask:

### Hyphens in HTML and CSS:

HTML5 attributes can start with data- (data-quantity, data-price).

CSS uses hyphens in property-names (font-size).

**Hyphens can be mistaken as subtraction attempts. Hyphens are not allowed in JavaScript names.**

### Underscores:

Many programmers prefer to use underscores (date_of_birth), especially in SQL databases.

Underscores are often used in PHP documentation.

### PascalCase:

PascalCase is often preferred by C programmers.

### camelCase:

camelCase is used by JavaScript itself, by jQuery, and other JavaScript libraries.

**Do not start names with a $ sign. It will put you in conflict with many JavaScript library names.**

## Loading JavaScript in HTML
Use simple syntax for loading external scripts (the type attribute is not necessary):
```javascript=
<script src="myscript.js"></script>
```
## Accessing HTML Elements
A consequence of using "untidy" HTML styles, might result in JavaScript errors.

These two JavaScript statements will produce different results:
```javascript=
var obj = getElementById("Demo")

var obj = getElementById("demo")
```
If possible, use the same naming convention (as JavaScript) in HTML.

## File Extensions
HTML files should have a .html extension (not .htm).

CSS files should have a .css extension.

JavaScript files should have a .js extension.

## Use Lower Case File Names
Most web servers (Apache, Unix) are case sensitive about file names:

london.jpg cannot be accessed as London.jpg.

Other web servers (Microsoft, IIS) are not case sensitive:

london.jpg can be accessed as London.jpg or london.jpg.

If you use a mix of upper and lower case, you have to be extremely consistent.

If you move from a case insensitive, to a case sensitive server, even small errors can break your web site.

To avoid these problems, always use lower case file names (if possible).


**Avoid global variables,  avoid new,  avoid  ==,  avoid eval()**

## Avoid Global Variables
Minimize the use of global variables.

This includes all data types, objects, and functions.

Global variables and functions can be overwritten by other scripts.

Use local variables instead, and learn how to use closures.

## Always Declare Local Variables
All variables used in a function should be declared as local variables.

Local variables must be declared with the var keyword, otherwise they will become global variables.

**Strict mode does not allow undeclared variables.**

## 變數放在上面
It is a good coding practice to put all declarations at the top of each script or function.

This will:

* Give cleaner code
* Provide a single place to look for local variables
* Make it easier to avoid unwanted (implied) global variables
* Reduce the possibility of unwanted re-declarations
```javascript=
// Declare at the beginning
var firstName, lastName, price, discount, fullPrice;


// Use later
firstName = "John";
lastName = "Doe";

price = 19.90;
discount = 0.10;

fullPrice = price * 100 / discount;
This also goes for loop variables:
```
This also goes for loop variables:

```javascript=
// Declare at the beginning
var i;

// Use later
for (i = 0; i < 5; i++) {
```
## 不要宣告 Number, String, 或是 Boolean 物件
Always treat numbers, strings, or booleans as primitive values. Not as objects.

## 不要使用 new Object()
Use {} instead of new Object()
Use "" instead of new String()
Use 0 instead of new Number()
Use false instead of new Boolean()
Use [] instead of new Array()
Use /()/ instead of new RegExp()
Use function (){} instead of new Function()

```javascript=
var x1 = {};           // new object
var x2 = "";           // new primitive string
var x3 = 0;            // new primitive number
var x4 = false;        // new primitive boolean
var x5 = [];           // new array object
var x6 = /()/;         // new regexp object
var x7 = function(){}; // new function object
```
## Beware of Automatic Type Conversions
Beware that numbers can accidentally be converted to strings or NaN (Not a Number).
```javascript=
var x = 5 + 7;       // x.valueOf() is 12,  typeof x is a number
var x = 5 + "7";     // x.valueOf() is 57,  typeof x is a string
var x = "5" + 7;     // x.valueOf() is 57,  typeof x is a string
var x = 5 - 7;       // x.valueOf() is -2,  typeof x is a number
var x = 5 - "7";     // x.valueOf() is -2,  typeof x is a number
var x = "5" - 7;     // x.valueOf() is -2,  typeof x is a number
var x = 5 - "x";     // x.valueOf() is NaN, typeof x is a number
```

## 使用 === 比較
The == comparison operator always converts (to matching types) before comparison.

The === operator forces comparison of values and type:
```javascript=
0 == "";        // true
1 == "1";       // true
1 == true;      // true

0 === "";       // false
1 === "1";      // false
1 === true;     // false
```
## 預設參數值
If a function is called with a missing argument, the value of the missing argument is set to undefined.

Undefined values can break your code. It is a good habit to assign default values to arguments.

```javascript=
function myFunction(x, y) {
    if (y === undefined) {
        y = 0;
    }
}
```

## 使用default完結switch
Always end your switch statements with a default. Even if you think there is no need for it.
```javascript=
switch (new Date().getDay()) {
    case 0:
        day = "Sunday";
        break;
    case 1:
        day = "Monday";
        break;
    case 2:
        day = "Tuesday";
        break;
    case 3:
        day = "Wednesday";
        break;
    case 4:
        day = "Thursday";
        break;
    case 5:
        day = "Friday";
        break;
    case 6:
        day = "Saturday";
        break;
    default:
        day = "Unknown";
}
```

## 避免使用 eval()
The eval() function is used to run text as code. In almost all cases, it should not be necessary to use it.

Because it allows arbitrary code to be run, it also represents a security problem.
