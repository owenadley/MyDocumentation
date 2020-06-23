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

The elements will be seperated by a specified seperator. By default this is a comma

Strings
------------------
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

ES6+ (ECMAScript 6)
======================
Variable Definitions
-------------------------
let - ES6+
^^^^^^^^^^^^^^^^^^^^^^^
Variable which is accessible from within the scope that it is declared only.

var 
^^^^^^^^^^^^^^^^^^^^^^^
Variable decleration which is accessible globally or anywhere within the function.

const
^^^^^^^^^^^^^^^^^^^^^^^
Variable decleration for an immutable value.

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
Any time a function is called it gets its own execution context, and any functions created inside of it will point to that execution context.
Closure gives you access to an outer function’s scope from an inner function. In JavaScript, closures are created every time a function is created, at function creation time.



React
==================
ComponentLifeCycle
-------------------------
In order from first to last:

1. componentWillMount
    * Immediately before initial rendering

2. componentDidMount
    * Immediately after initial rendering

3. componentWillRecieveProps
    * When component recieved new props (ex. new props due to parent state change)

4. shouldComponentUpdate
    * Before rendering, after recieving new props or state. Can return false to prevent rerendering

5. componentWillUpdate
    * Before rendering, after receiving new props or state

6. componentDidUpdate
    * After component's update are flushed to DOM

7. componentWillUnMount
    * Immediately before removing component from DOM

Error Boundaries
-------------------------
`Error Boundaries <https://reactjs.org/docs/error-boundaries.html>`_

Runtime errors during rendering will break the app, we can prevent this using error boundaries.
Consists of two lifecycle methods:

* static getDerivedStateFromError(error)

    * Used to render a fallback UI after an error is thrown
    * Can set error state to true and conditionally render a specific UI

* componentDidCatch(error, info)

    * Used to log the error and information

Create an ErrorBoundary component which has the two lifecycle methods above. You can then wrap any
component in this ErrorBoundary component if you wish to enable the error boundaries for it.

Redux State Management
-------------------------
A popular state management library that keeps all state information in a central location called a 'store'.
Redux models the applications state as a single JS Object

Action
    
    * A POJO that must have a key called 'type' and a string value
    * Can have any number of additional keys

Reducer

    * A function that accepts the state and an action and returns a new state

Store

    * One bug POJO that represents the entire state of the application

Vue
==================

Polymer
==================

D3
==================