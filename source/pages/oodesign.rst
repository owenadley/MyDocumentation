********************************
Object Oriented Design
********************************

Four Principles of OO Design
==============================

Encapsulation
------------------
Restricting access to data by using public and private classes and methods. This often looks like using getters and setter to access a private variable inside a public class.

Abstraction
------------------
Having information tied to a model or something rather than the instance of it. For example, a genralized interface Person may have core information about the person: name, age, sex, etc. Various classes who would require this information can then implement the Person class.
Ex, class Student implements Person, class Professor implements person, etc.

Polymorphism
------------------
Where an object can take many forms. Ex, a piece of furniture could be a chair, table or bed. Any code written in the parent class can be used for the childern. Ex. for public class Furniture, public class Chair extends Furniture.
The idea is that Chair and Desk can both extend Furniture, and each can have their own setColor(color) method which allows for those classes to "take their own form"

Inheritance
------------------
An object has an "is a" relationship with another object. For example, an armchair "is a" chair. This can look like a subclass reusing code from its parent. Also done by extending the parent class.


Design Patterns
==============================
Constructor Patterns
----------------------
Abstract Factory
^^^^^^^^^^^^^^^^^^^^^^^
Builder
^^^^^^^^^^^^^^^^^^^^^^^
Factory Method
^^^^^^^^^^^^^^^^^^^^^^^
Used to create an instance of one or many derived classes

Object Pool
^^^^^^^^^^^^^^^^^^^^^^^
Prototype
^^^^^^^^^^^^^^^^^^^^^^^
A fully initalized instance to be cloned. The class will implement cloneable

Singleton
^^^^^^^^^^^^^^^^^^^^^^^

Structural Patterns
----------------------
Adapter
^^^^^^^^^^^^^^^^^^^^^^^
Bridge
^^^^^^^^^^^^^^^^^^^^^^^
Composite
^^^^^^^^^^^^^^^^^^^^^^^
Decorator
^^^^^^^^^^^^^^^^^^^^^^^
Facade
^^^^^^^^^^^^^^^^^^^^^^^
Flyweight
^^^^^^^^^^^^^^^^^^^^^^^
Private Class Data
^^^^^^^^^^^^^^^^^^^^^^^
Proxy
^^^^^^^^^^^^^^^^^^^^^^^

Behavioral Patterns
----------------------
Chain of responsibility
^^^^^^^^^^^^^^^^^^^^^^^
Command
^^^^^^^^^^^^^^^^^^^^^^^
Interpreter
^^^^^^^^^^^^^^^^^^^^^^^
Iterator
^^^^^^^^^^^^^^^^^^^^^^^
Mediator
^^^^^^^^^^^^^^^^^^^^^^^
Memento
^^^^^^^^^^^^^^^^^^^^^^^
Null Object
^^^^^^^^^^^^^^^^^^^^^^^
Observer
^^^^^^^^^^^^^^^^^^^^^^^
Observer will listen for specific state updates on a particular class. It will then process state change to notify certain classes of this change. 

State
^^^^^^^^^^^^^^^^^^^^^^^
Strategy
^^^^^^^^^^^^^^^^^^^^^^^
Template Method
^^^^^^^^^^^^^^^^^^^^^^^
Visitor
^^^^^^^^^^^^^^^^^^^^^^^