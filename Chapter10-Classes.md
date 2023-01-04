# Chapter 10 - Classes

Classes belong to higher levels of code organization.


### Class Organization
Like a newspaper article:
- public static constants 
- private static variables 
- private instance variables 
- public functions
- private functions

### Encapsulation
Utility functions should be private but could be protected to be accesible by tests in the same package.

### Classes Should Be Small!
... and then should be smaller than that!.
With functions, we count lines, with classes we count responsibilities.
Too many responsibilities => God class.
Avoid including words like 'Processor, Manager, Super' in class names => aggregation of responsibilities. Class description in 25 words without "if", "and", "our", "but"...

### The Single Responsibility Principle
Classes should have one responsibility--one reason to change.

Too many of us think that we are done once the program works. We move on to the next problem rather than going back and breaking the
classes into decoupled units with single responsibilities.

We have to organize system complexity. A developer should know where to look to find things and need only understand the directly affected complexity at any given time.

We want systems composed of many small classes. Single responsibility and single reason to change. They collaborate with a few others to achieve the desired system behaviour.

### Cohesion
The small number of instance variables => each method manipulates one or more of those variables. => more variables manipulate => the more cohesive a method is.

A class in which each variable is used by each method is maximally cohesive.

Maintaining Cohesion Results in Many Small Classes

When classes lose cohesion split them!

Breaking a large function into many smaller functions often gives us the opportunity to split several smaller classes out as well => better organization and more transparent structure.

Do it with tests => write a test suit that verified the precise behaviour of the first version. Then tiny little changes, one at a time to get the desired result.

### Organizing for Change
Open-Closed Principle => Our classes should be open for extension but closed for modification. 
Allow new functionality via subclassing.

We incorporate new features by extending the system, not by making modifications to existing code.

### Isolating from Change
Dependency Inversion Principle (DIP) => Classes should depend upon abstractions, not on concrete details.
