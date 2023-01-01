# Chapter 03 - Functions

Functions are the first line of organization in any program.

### Small!

First: they should be small. Second: they should be smaller than that.

Functions should hardly ever be 20 lines long. Functions should be transparently obvious. Each function tells a story.
Each function leads you to the next thing in a compelling order.


### Blocks and Indenting

The blocks within if, else, while, etc. statements should be one line long, probably will be a function call. This function call can have a nice and descriptive name
The indent level of a function should not be greater than one or two.


### Do One Thing
```
FUNCTIONS SHOULD DO ONE THING. THEY SHOULD DO IT WELL. THEY SHOULD DO IT ONLY
```

A function do one thing though it contains calls to other functions. But those functions should be always one level below the stated name of the function.
We create functions to decompose a larger concept (the name of the function) into a set of steps at the next level of abstraction.


### Sections within Functions
A function that is divided into sections will be probably doing more than one thing.


### One Level of Abstraction per Function
Don't mix levels of abstraction in a function. It gets harder to tell whether a particular expression is important or small detail.


### Reading Code from Top to Bottom: The Stepdown Rule
Write code like a top-down set of TO-paragraphs where each paragraph provides further instructions on the one before it. TO build the page we include setups then include the test page. TO include setups we include the suite setup if this is a suite. TO include the suite setup...


### Switch Statements
Switch statements always do N things.
Use them to create polymorphic objects. Abstract Factory pattern.

### Use Descriptive Names
You know that you are working with clean code when each routine turns out to be pretty much as you expected.
Use descriptive names. A long descriptive name is better than a short enigmatic one and better than a long descriptive comment. Be consistent with your names, try always to use the same verbs, nouns, etc.
includeSetupAndTeardownPages, includeSetupPages, includeSetupPage...

### Function Arguments
- Zero arguments (niladic)
- One argument (monadic)
- Two arguments (dydadic)
- ~Three arguments (triadic)~
- ~Four arguments~
..
Zero arguments > One argument > Two arguments
Avoid output arguments, they are not easy to understand.


### Common Monadic Forms

- Asking a question about that argument.boolean fileExists("miFile")
- Operating on that argument, transforming and returning InputStream fileOpen("miFile")
- Events to alter the state of the system.

Try to avoid other forms.


### Flag Arguments
Flag arguments (true|false) are ugly. Functions with that do one thing if it is true and another thing if is false. Split the function in two: render(boolean isSuite) => renderForSuite() , renderForSingleTest()

### Dyadic Functions
They are harder to understand than monadic functions. assertEquals(expected, actual) ... it would take practice to remember which order to put the arguments in.


### Triads
They are harder to understand than dyadic functions. assertEquals(msg, expected, actual) ... now the msg seems to be the expected value.

### Argument Objects
When a function needs to have more than two or three arguments some of these arguments should be wrapped into a class of their own. makeCir cle(double x, double y, double radius) => makeCircle(Point center, double radius);


### Argument Lists
The function that takes argument lists can be monads, dyads or even triads: void monad(String... args); void dyad(String name, String... args); void triad(String name, int count, String... args)


### Verbs and Keywords
We can encode the name of the arguments into the function name: assertEquals => assertExpectedEqualsActual
And we can do more meaning to the argument: write(name) => writeField(name)


### Have No Side Effects
Functions should not do things that you don't expect. i.e: checkPassword(login, password) => inside initializes the user session...initializing the user session should be its own function.


### Output Arguments
The should be avoided with OOP. If you see appendFooter(s), is s being appended to something, or are you appending something to s? void appendFooter(StringBuffer report); => report.appendFooter();


### Command Query Separation
Functions should either do something or answer something, but not both. attributeExists and setAttribute should be different functions. Avoid things like setAndCheckIfExists


### Prefer Exceptions to Returning Error Codes
Error codes violate Command Query Separation.
Exceptions can help to separate the happy path code from the error path and that helps to simplify.


### Extract Try/Catch Blocks
Try/catch's are ugly. It is better to extract try and catch methods.


### Error Handling Is One Thing
Methods with try/catch should only have this structure and nothing more.


### The Error.java Dependency Magnet
Error codes are usually in classes like Error.java (with constants). Avoid that, it is a dependency magnet (it is everywhere) and nobody wants to add new errors or change it because you have to recompile/deploy everything. Instead, the tendency will be to re-use error codes for uses they aren't intended for.
Use Exceptions instead of Error codes.


### Don’t Repeat Yourself
Duplication may be the root of all evil in software.


### Structured Programming
Things like "there should only be one return statement" is unnecessary when you create small functions.


### How Do You Write Functions Like This?
- Write ugly and long functions with a long list of arguments.
- You need to have unit tests that cover all that functions.
- Then you can massage and refine that code. You can break everything in classes and keep your test passing.


### Conclusion
Functions are the verbs and classes are the nouns of the language of our system.
Your real goal is to tell the story of the System. You have to write functions that help you to tell that story.


