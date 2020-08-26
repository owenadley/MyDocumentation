********************************
JavaScript
********************************

Vanilla JS
==================
Arrays
------------------
unshift(x)
^^^^^^^^^^^^^^^^^^^^^^^
Adds a new item to the beginning of the array and returns the new array length

push(x)
^^^^^^^^^^^^^^^^^^^^^^^
Adds a new item to the end of the array and returns the new array length

slice(start, end)
^^^^^^^^^^^^^^^^^^^^^^^^
Returns a new array composed of the items between indicies start and end

splice(start, end)
^^^^^^^^^^^^^^^^^^^^^^^
Removes the indicies of an array between start and end

join()
^^^^^^^^^^^^^^^^^^^^^^^
Returns all elements in an array as a single string

.. code-block:: javascript
    
    var fruits = ["Banana", "Orange", "Apple", "Mango"];
    var energy = fruits.join();
    // energy == "Banana,Orange,Apple,Mango"

The elements will be seperated by a specified seperator. By default this is a comma

every()
^^^^^^^^^^^^^^^^^^^^^^^
Tests whether all elements of an array pass the test implemented by the provided function. Returns boolean

.. code-block:: javascript
    
    const isBelowThreshold = (currentValue) => currentValue < 40;
    const array1 = [1, 30, 39, 29, 10, 13];

    console.log(array1.every(isBelowThreshold));
    // expected output: true

    // OR you can do it Inline

    console.log(array1.every((num) => num < 40))

The elements will be seperated by a specified seperator. By default this is a comma

for .. of
^^^^^^^^^^^^^^^^^^^^^^^
Used to iterate over the values in an iterable, this is not limited to arrays though

.. code-block:: javascript

    var arr = ["Owen", "Adley];
    for (str of arr) {
        console.log(str);
    }
    // Owen Adley

forEach
^^^^^^^^^^^^^^
ForEach is used to iterate through an array and applies some operation to every element of the array

map
^^^^^^^^^^^^^
Map is used to iterate through an array, apply some operation on every element and return a new array with the new elements.
Use this when you need to do an operation of each element of the array, but you keep the original array and store the operated values in a new array:

.. code-block:: javascript

    let sorted = strs.map(str => {
        return str.split('').sort().join('')
    })

sort
^^^^^^^^^^^^^^
Sorts the elements of an array in place and returns the sorted array


Strings
------------------

slice(start, end) OR slice(end)
^^^^^^^^^^^^^^^^^^^^^^^
Extracts depicted parts of the string and returns the extracted parts in a new string


split("")
^^^^^^^^^^^^^^^^^^^^^^^
Split a string into an array based on each occurance of the passed parameter

* Ex. "" would split each single char into its own index in the array

parseInt("40")
^^^^^^^^^^^^^^^^^^^^^^^
Parse a string and returns an integer

.. code-block:: javascript
    
    parseInt("40") // 40
    parseInt("40 20 34") //40
    parseInt("3.5") //3
    parseInt("3.7") //3
    parseInt("40 years") //40
    parseInt("He is 40 years") //NaN

concat(str)
^^^^^^^^^^^^^^^^^^^^^^^
Concats strings together

    .. code-block:: javascript
        
        let newStr = str1.concat(str2)
        let newStr = str1.concat(str2, str3, strn)


replace(id, new)
^^^^^^^^^^^^^^^^^^^
You can use the replace method to replace all matches of a specific pattern with something else. This returns a new string with the replacements.

    .. code-block:: javascript

        const str = "Hello World I Am Owen"
        // we can replace all the l's with P's
        const newStr = str.replace(/l/g, 'P')
        // newStr: HePPo WorPd I Am Owen

See the official docs for some more configurations and options when replacing elements:
`JS Replace Function <https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/replace>`_

includes(str)
^^^^^^^^^^^^^^^
The includes method returns a boolean indicating whether or not a string includes and specific substring

    .. code-block:: javascript

        var str = "I Am Owen"
        var n = str.includes("Owen")    // true

ES6+ (ECMAScript 6)
======================
Arrow Functions
-------------------------
Arrow functions are a new way to declare function with ES6. Declaring an arrow function will automatically bind the function to its parent.
The 'this' variable of the function will be the same as the 'this' of its surrounding code.

.. code-block:: javascript

    increment = (num) => {
        return num++;
    }

Classes
-------------------------
Classes are also new with ES6, and in fact are "special functions". However, unlike functions, classes are not hoisted.
Classes are primarily syntactical sugar over JS's existing prototype-based inheritance.

Template Strings
-----------------
A template string is declared using backticks and allows for interpolations and multi-line strings.

.. code-block:: javascript:

    `Hi my name is ${name}`
    
Promises
-------------------------
Promises represent a value that is available now, in the future, or never. You can use it by creating a new Promise object from the function which is operating asynchronously.

.. code-block:: javascript

    function timeout(duration = 0) {
        return new Promise((resolve, reject) => {
            setTimeout(resolve, duration);
        })
    }

    var p = timeout(1000).then(() => {
        return timeout(2000);
    }).then(() => {
        throw new Error("hmm");
    }).catch(err => {
        return Promise.all([timeout(100), timeout(200)]);
    })


Variable Definitions
-------------------------
let
^^^^^^^^^^^^^^^^^^^^^^^
Variable which is accessible from within the scope that it is declared only.

const
^^^^^^^^^^^^^^^^^^^^^^^
Variable decleration for an immutable value.


Import vs Require
-------------------------
import uses ES2015 Modules
require uses CommonJS Modules

Spread Operator (...)
------------------------
There are three places you can use spread:
* In function calls (when executing)

    For example, if you wanted to pass an array of numbers to a function which does not accept
    arrays, but only functions, we can use the spread operator:

    .. code-block:: javascript

        var array = [10, 20, 30]
        Math.min(10, 20, 30)    // 10
        Math.min(array)  // NaN
        Math.min(...array)  // 10

    You can think of it as literally 'spreading' the items of the array out into their own parts.
    This also works for strings since they are iterable:

    .. code-block:: javascript

        var str = "ABC"
        console.log(...str) // A B C

    In this case, we split the chars of the string into their own parts, and they are seperated by a space

* In an array literal (when you're making a new array)

    Probably the most common use case for the spread operator is for array literals.
    We can use it to take data from an array and create new arrays:

    .. code-block:: javascript

        const parents = ["Rob", "Sheryl"]
        const kids = ["Katelyn", "Owen"]

        const fullFam = [...parents, ...kids]   // ["Rob", "Sheryl", "Katelyn", "Owen"]

    It can also be used to copy an array.
    Since arrays are reference based, if we assign an array to a new variable and change that new varaible, the original array will also change.
    We can get around this by creating a copy using the object spread notation

    .. code-block:: javascript

    const original = ['hello', 'world'];
    const new = original
    new.push('again')
    // new and original now both contain the word 'again'
    const newtwo = [...original]
    newtwo.push('again')
    // now only newtwo contains the word 'again'


* In object literal (when you're making an object)

    The same as array literals, but using object notation rather than array notation ({} vs []).
    Example:

    .. code-block:: javascript

        const lion = {hasTail: true, legs: 4}
        const eagle = {canFly: true}

        const hybrid = {name: "Gryphon", ...lion, ...eagle}
        // hybrid = {canFly: true, hasTail: true, legs: 4, name: "Gryphon"}

A good example of the spread notation with regards to React is how you update the state.
For example, if we have an array of TODO objects in state, we dont want to mutate the state by using
push() or unshift(). We should make a copy of the TODO state, add the new TODO, then update the state
with the new TODO list.

    .. code-block:: JavaScript

        const todo = [{name: "Owen", completed: false, task:"Something"]

        function addToDo(newToDo) {
            return [...todo, {...newToDo, completed: false}]
        }



Types and Operators
======================
Dynamic Typing
-------------------------
You don't tell the JS engine what type of data a variable holds, it figures it out while your code is running. Unlike Java where you would declare type (ex. bool isTrue = false)

Primitive Types
-------------------------
A type of data that represents a single value. Not an object. There are six types in JS.

Undefined
^^^^^^^^^^^^^^^^^^^^^^^
undefined represents a lack of existence and is what the JS engine sets variables to intially. Do not set variables to undefined.

Null
^^^^^^^^^^^^^^^^^^^^^^^
null represents lack of existence but is not set by the JS engine. Set variables to null if you want them to equal nothing.

Boolean
^^^^^^^^^^^^^^^^^^^^^^^
true or false

Number
^^^^^^^^^^^^^^^^^^^^^^^
Floating point number (there's always some decimals). Unlike other programming languages, there is only one 'number' type.

String
^^^^^^^^^^^^^^^^^^^^^^^
A sequence of characters (both " and ' can be used)

Symbol - ES6+
^^^^^^^^^^^^^^^^^^^^^^^

Operators
-------------------------
A special function that is syntactically (written) differently. Generally operators take two parameters and return one result.

`Precedence & Assciatvity <https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence>`_

Operator Precedence
^^^^^^^^^^^^^^^^^^^^^^^
Which operator function gets called first (when there is more than one on the same line of code).
Functions are called in order of precedence (Higher precedence first).

Operator Associatvity
^^^^^^^^^^^^^^^^^^^^^^^
Which order operator function get called in: Left-to-Right or Right-to-Left.
When functions have the same precedence

Coercion
-------------------------
Converting a value from one type to another. This happens quite often in JS because it is dynamically typed.
Coercion will take place when using comparison operators. To avoid coercion, we can use strict equality and inequality.

.. code-block:: javascript

    3 == "3" //true
    3 === "3" //false - strict equality compares the object type

`Equality & Sameness table <https://developer.mozilla.org/en-US/docs/Web/JavaScript/Equality_comparisons_and_sameness>`_


Execution Contexts and Lexical Environments
=============================================
Syntax Parser
-------------------------
A program that reads your code and determines what it does and if its grammar (or syntax) is valid.
Your code isn't magic. Someone else wrote a program to translate it for the computer (compiler).

Lexical Environment
-------------------------
Where something wits physically in the code your write.
'Lexical' means 'having to do with words or grammar'. A lexical environment exits in programming languages in which where you write something is important.

Execution Context
-------------------------
A wrapper to help manage the code that is running.
There are lots of lexical environments. Which one is currently running is managed via execution contexts. It can contain things beyond what you've written in your code.

.. image:: img/jsexecutionenvironment.png
  :width: 400
  :alt: Execution Context

Creation & Hoisting
^^^^^^^^^^^^^^^^^^^^^^^
Execution Context is created in two phases:

1. Creation Phase
    * Global Object
    * 'this'
    * Outer Environment
    * Setup Memory Space for Variables (undefined) and Functions - "**Hoisting**"

        * A function and all its code is stored in memory
        * A variable is stored in memory, however the value is unknown and will be set to undefined

Single Threaded & Synchronous
------------------------------
Single Threaded:
   * One command at a time.
   * Under the hood of the browser, maybe not...

Synchronous:
    * One (line of code) at a time. And in order.

Asynchronous
-------------------------
More than one at a time. Some code intializes other code to run at the same time. Javascript is synchronous, so we need special implementation to handle this.
An event queue is created that stores notification of events that are happening. For example, Click. We can have an event listener to react to these accordingly.
This event queue gets looked at once the execution stack is empty, and then creates the execution context to react to the item in the event queue (ex. handleClick()).

Invocation
------------------------------
Running a function. In JS, by using parenthesis ()

Object
-------------------------
A collection of name value pairs (The simplest definition when talking about Javascript).

.. code-block:: javascript
    
    Address: {
        Street: 'Main',
        Number: 100,
        Apartment: {
            Floor: 3,
            Number: 301
        }
    }

Variable Environment
-------------------------
Where the variables live and how they relate to each other in memory.
Variables declared within a function live within the execution context of that function.

The Scope Chain
-------------------------
Each execution context has a reference to an Outer Environment. This outer environment is a reference to the Global Execution Context.
This means that a function can reference a variable if it is declared in the Global Execution Context, and not in its own execution context.

.. image:: img/jsscopechain.png
  :width: 400
  :alt: Scope Chain

However, if we have a function that is nested inside of another function, the outer reference then becomes the parent function of which it sits inside.

Scope
-------------------------
Where a varibale is available in your code. And, if it's truly the same variable, or a new copy.


Objects & Functions
=============================================
Function Expression
------------------------
A function expression is when you use the *function* keyword to define a function inside an expression.
• The function can then be passed around like a variable and invoked at any time (commonly used for callbacks).
• Unlike function declerations, function expressions are not hoisted.
• You can declare a function expression as an anonymous function or a named function.

Anonymous function expressions are sometimes referred to as **Inline Functions**.
However, there is no consensus or official JS documentation referring to *Inline Functions*, but if you hear the term, they are referring to an anonymous function expression.

Here is an example of an anonymous function expression (or an Inline Function as some would like to say):

.. code-block:: javascript

    let funExpression = function(name) {
        return 'Hello ' + name; 
    }

Here is an example of an named function expression:

.. code-block:: javascript

    let funExpression = function namedFunction(name) {
        return 'Hello ' + name;
    }

One of the benefits of using named function expressions is that if there is an error, the stack trace will contain the name of the function making it easier to find the origin.

for .. in
^^^^^^^^^^^^^^^^^^^^^^^
Used to iterate over the properties of an object.

.. code-block:: javascript
    let cars = {
        make: 'Honda',
        model: 'Civic',
        year: '2003'
    }

    for (key in cars) {
        console.log(key)
    }

    //make, model, year

Namespace
-------------------------
A container for variables and functions. Typically to keep variables and function with the same name seperate.
javascript does not have namespace, but we can fake it.

First Class Functions
-------------------------
Everything you can do with other types you can do with functions. Assign them to variables, pass the around, create them on the fly.

Expression
-------------------------
A unit of code that results in a value. It doesnt have to save a variable.

Passing by value vs. reference
--------------------------------
By value
^^^^^^^^^^
When a variable is passed by value, it creates a new space in memory for the variable.

.. code-block:: javascript
    
    var a = 3;
    var b;

    b = a;
    a = 2; 

    console.log(a); // 2
    console.log(b); // 3

By reference
^^^^^^^^^^^^^^
When a variable is passed by reference, the reference points to the same location in memory.


.. code-block:: javascript
    
    var c = { greeting: 'hi' };
    var d;

    d = c;
    c.greeting = 'hello';

    console.log(c); // { greeting: 'hello'}
    console.log(d); // { greeting: 'hello'}


Mutate
--------------------------------
To change something. "Immutable" means it can't be changed

Arguments
--------------------------------
The paramaters you pass to a function.
Javascript gives you a keyword of the same name which contains them all (arguments).

.. code-block:: javascript
    
    function a(fname, lname) {
        if (arguments.length === 0) {
            // nothing was passed to the function
        }
    }

Whitespace
--------------------------------
Invisible characters that create literal 'space' in your written code. -> Comments

Immediately Invoked Function Expressions (IIFE)s
---------------------------------------------------
Using a function expression, you can immediately invoke the function at runtime, at the point in the code where the function is defined.

.. code-block:: javascript
    
    var greeting = function(name) {
        console.log('Hello' + name);
    }(name);

    // OR

    (function(name) {
        var greeting = 'Hello';
        console.log(greeting + ' ' + name);
    }(firstname));

Closures
---------------------------------------------------
Any time a function is called it gets its own execution context, and any functions created inside of it will point to that execution contexts variables that were created.
Closure gives you access to an outer function’s scope from an inner function. In JavaScript, closures are created every time a function is created, at function creation time.

Callback Function
---------------------------------------------------
A function you give to another function, to be run when the other function is finished.
So the function you call, 'calls back' by calling the function you gave it when it finishes

call(), apply() and bind()
---------------------------------------------------
Used to indicate the 'this' context for a function.

.. code-block:: javascript
    
    var person = {
        fname: "Owen"
        getFirstName: function() {
            return fname;
        }
    }

    var logName = function(lname) {
        console.log(this.getFirstName() + ' ' + lname);
    }

    logName.call(person, "Owen");   // will point the 'this' variable to the person object.
    logName.apply(person, ["Owen"]);    // Same as above, except apply() takes an array of arguments 
    
    var logPersonName = logName.bind(person);   // bind will assign the 'this' variable but will not call the function until you invoke it yourself
    logPersonName("Owen");

    var person2 = {
        fname: "Owen"
    }

    // function borrowing
    // Since the objects have similar property names, we can 'borrow' the function declared in person to use for the person 2 object
    person.getFirstName.apply(person2);


Function Currying
---------------------------------------------------
Creating a copy of a function but with some preset parameters. Very useful in mathematical situations.

.. code-block:: javascript

    // function currying

    function multiply(a, b) {
        return a*b
    }
    var multipleByTwo = multiply.bind(this, 2); // this will permanetely set 'b' to 2 - default paramater
    console.log(multiplyByTwo(4));


Object-Oriented Javascript and Prototypal Inheritance
=======================================================
Inheritance
-------------------------
One object gets access to the properties and methods of another object.

Reflection
-------------------------
An object can look at itself, listing and changing its properties and methods.


Building Objects
=======================================================
Function Constructors
-------------------------
A normal function that is used to construct objects.
The 'this' variable points to a new empty object, and that object is returned from the function automatically.

Polyfill
-------------------------
Code that adds a feature which the enginer may lack (common for older browsers to create support for new feature)
