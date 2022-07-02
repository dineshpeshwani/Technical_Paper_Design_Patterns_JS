# Design patterns in js

## Abstracts

this paper is about Design Pattterns used in javascript. Design patterns in js are reusable solutions applied to commonly occurring problems in writing JavaScript web applications.It is quite appropriate to refer JavaScript design patterns as templates to provide solutions to problems.

## Table of Contents : 

    1. Introduction
    2. Requirement of Design Patterns
    3. Types of Desgin Patters
       3.1. Module Design Pattern.
       3.2. Constructor Design Pattern
       3.3. Observer Design Pattern.
       3.4. Prototype Design Pattern.
       3.5. Singleton Design Pattern.
    4. Conclusion
    5. References

## Introduction : 

    * Every developer strives to write maintainable, readable, and reusable code. Code structuring becomes more important as applications become larger. 
    * Design patterns prove crucial to solving this challenge - providing an organization structure for common issues in a particular circumstance.
    * They decrease the overall codebase by doing away with unnecessary repetitions, thus makes our code more robust than the ad-hoc solutions.


## Requirement of Design Patterns : 

    1. Solutions that work: 
       Because they are used by a lot of developers, you can be sure that they work. And not just that, but as the patterns have been used a lot of times, several optimizations were made.

    2. Easily reusable: 
       Design patterns are reusable by definition and even though they are very generic, they can be easily adapted to particular problems.

    3. They are expressive: 
       Design patterns can describe a complex solution in an elegant format.

    4. Reduce the need for refactoring: 
       When you write an application with design patterns in mind, it is easier to get to a clean code faster. This way we make less refactors. Specially in JavaScript, a language that allows for so many ways to write the same thing.

    5. Makes your code smaller: 
       As design patterns are usually optimized, they need less code to be implemented, and less code means less bugs.

## Types of Desgin Patters :

### Module Design Pattern : 

    * JavaScript modules are the most prevalently used design patterns for keeping particular pieces of code independent of other components. This provides loose coupling to support well-structured code.

    * For those that are familiar with object-oriented languages, modules are JavaScript “classes”. One of the many advantages of classes is encapsulation - protecting states and behaviors from being accessed from other classes. The module pattern allows for public and private (plus the lesser-know protected and privileged) access levels.

    * Modules should be Immediately-Invoked-Function-Expressions (IIFE) to allow for private scopes - that is, a closure that protect variables and methods (however, it will return an object instead of a function). This is what it looks like:

            (function() {
                // declare private variables and/or functions
            return {
               // declare public variables and/or functions
            }
            })();

### Constructor Design Pattern : 

    * This is a special method that is used to initialize the newly created objects once a memory is allocated. Since JavaScript is typically object-oriented, it deals with objects most, therefore I intend to delve in to object constructors. There are three ways to create new objects in JavaScript: 

        // This creates a new empty Object
        var newObject = {};
        // This creates a new empty Object
        var newObject = Object.create(Object.prototype);
        var newObject = newObject();

### Observer Design Pattern :

    * The observer design pattern is handy in a place where objects communicate with other sets of objects simultaneously. In this observer pattern, there is no unnecessary push and pull of events across the states, rather the modules involved only modify the current state of data.

        Example :

            function Observer() {
                this.observerContainer = [];
                }

                Observer.prototype.subscribe = function (element) {
                this.observerContainer.push(element);
                }

                // the following removes an element from the container

                Observer.prototype.unsubscribe = function (element) {

                const elementIndex = this.observerContainer.indexOf(element);
                if (elementIndex &gt; -1) {
                this.observerContainer.splice(elementIndex, 1);
                }
                }

                /**
                * we notify elements added to the container by calling
                * each subscribed components added to our container
                */
                Observer.prototype.notifyAll = function (element) {
                this.observerContainer.forEach(function (observerElement) {
                observerElement(element);
                });
            }

### Prototype Design Pattern :

    * The prototype pattern is based on prototypical inheritance whereby objects created to act as prototypes for other objects. In reality, prototypes act as a blueprint for each object constructor created.

    Example : 

        var myCar= {
            name:"Ford",
            brake:function(){
            console.log("Stop! I am applying brakes");
            }
            Panic : function (){
            console.log ( "wait. how do you stop thuis thing?")
            }
            }
            // use objec create to instansiate a new car
            var yourCar= object.create(myCar);
            //You can now see that one is a prototype of the other
            console.log (yourCar.name);]

### Singleton Design Pattern :

    * It is essential in a scenario where only one instance needs to be created, for example, a database connection. It is only possible to create an instance when the connection is closed or you make sure to close the open instance before opening a new one.  This pattern is also referred to as strict pattern, one drawback associated with this pattern is its daunting experience in testing because of its hidden dependencies objects which are not easily singled out for testing.

    Example : 

            function DatabaseConnection () {

                    let databaseInstance = null;

                    // tracks the number of instances created at a certain time
                    let count = 0;

                    function init() {
                    console.log(`Opening database #${count + 1}`);
                    //now perform operation
                    }
                    function createIntance() {
                    if(databaseInstance == null) {
                    databaseInstance = init();
                    }
                    return databaseInstance;
                    }
                    function closeIntance() {
                    console.log('closing database');
                    databaseInstance = null;
                    }
                    return {
                    open: createIntance,
                    close: closeIntance
                    }
                    }

                    const database = DatabseConnection();
                    database.open(); //Open database #1
                    database.open(); //Open database #1
                    database.open(); //Open database #1
                    database.close(); //close database

## Conclusion :

It is beneficial for JavaScript developers to use design patterns. Some major advantages of using design patterns include project maintainability and also cuts off unnecessary work on the development cycle. Even though JavaScript design patterns can provide solutions to complex problems, needless to say, rapid development and productivity, it is improper to conclude that these design patterns can replace the developers.

## References : 

* https://codesource.io/javascript-design-patterns/
* https://blog.bitsrc.io/my-9-favorite-design-patterns-in-javascript-9d2a09651d08
* https://www.digitalocean.com/community/tutorial_series/javascript-design-patterns