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
let
^^^^^^^^^^^^^^^^^^^^^^^
Variable which is accessible from within the scope that it is declared only.

var 
^^^^^^^^^^^^^^^^^^^^^^^
Variable decleration which is accessible globally or anywhere within the function.

const
^^^^^^^^^^^^^^^^^^^^^^^
Variable decleration for an immutable value

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

.. image:: ../img/jsexecutioncontext.png
  :width: 400
  :alt: Execution Context

Creation & Hoisting
^^^^^^^^^^^^^^^^^^^^^^^
Execution Context is created in two phases:

1. Phase 1 - Creation Phase
    * Global Object
    * 'this'
    * Outer Environment
    * Setup Memory Space for Variables (undefined) and Functions - "**Hoisting**

        * A function and all its code is stored in memory
        * A variable is stored in memory, however the value is unknown and will be set to undefined

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