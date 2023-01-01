# Chapter 02 - Meaningful Names

### Introduction

Names are everywhere in software: variables, functions, args, classes, packages, files...


### Use Intention-Revealing Names
The name should answer all the big questions:
```
Why does it exist?
What does it do?
How it is used? Avoid using this like:
```
Avoid using this like:
```
int d; // elapsed time in days!
```

Instead of that use a name that specifies what is being measured and it's unit:
```
int elapsedTimeInDays;
```

Choosing names that reveal intent can make it much easier to understand and change code. This is helpful to others as well as your future self. What is the purpose of this code?
From this:
```
public List<int[]> getThem() {
List<int[]> list1 = new ArrayList<int[]>(); for (int[] x : theList)
if (x[0] == 4)
list1.add(x);
return list1;
}
```

We can improve it only with revealing naming:
```
public List<int[]> getFlaggedCells() {
List<int[]> flaggedCells = new ArrayList<int[]>(); for (int[] cell : gameBoard)
if (cell[STATUS_VALUE] == FLAGGED)
flaggedCells.add(cell); return flaggedCells;
}
```

And it is still better with a Cell class:
```
public List<Cell> getFlaggedCells() {
List<Cell> flaggedCells = new ArrayList<Cell>(); for (Cell cell : gameBoard)
if (cell.isFlagged())
flaggedCells.add(cell); return flaggedCells;
}
```
 
 

### Avoid Disinformation

If you want to name a group of accounts use accounts to try to avoid an account list (maybe its type is not a List). Beware of using names that are very similar XYZFooBarClassForBlabla and XYZFooBarClassForBlablable. Using lower case l (looks like 1) and uppercase O (looks like 0) is also unhelpful.


Make Meaningful Distinctions

Do not use number-series naming: a1, a2, ... aN
```
public static void copyChars(char a1[], char a2[]) { for (int i = 0; i < a1.length; i++) {
a2[i] = a1[i];
}
}
```

This would be much better with source and destination as argument names. 

Avoid Noise words (Info, Data, a, an, the, variable, table, String):
  ProductInfo and ProductData are more or less the same. 
  Is name string better than name? No.
  
  
The same for methods, what I should do?: getActiveAccount() getActiveAccounts() getActiveAccountInfo().


### Use Pronounceable Names

If you can't pronounce it you can't discuss it without sounding like an idiot. Example:
 ```
// generation date, year, months, day, hour, minute, and second class DtaRcrd102 {
private Date genymdhms;
/* ... */
}

// better:
class Customer {
private Date generationTimestamp;
/* ... */
}
```

Use Searchable Names

Single-letter names and numeric constants are not easy to locate across a body of text. i.e.:
```
for (int j=0; j<34; j++) {
s += (t[j]*4)/5;
}
```

It's better when has searchable names:
```
int realDaysPerIdealDay = 4; const int WORK_DAYS_PER_WEEK = 5; int sum = 0;
for (int j=0; j < NUMBER_OF_TASKS; j++) {
int realTaskDays = taskEstimate[j] * realDaysPerIdealDay; int realTaskWeeks = (realdays / WORK_DAYS_PER_WEEK);
sum += realTaskWeeks;
}
```

Avoid Encodings

Don't use symbols or emojis.

Hungarian Notation, Member Prexes

Old examples from Fortran, BASIC. No longer likely to be applicable. 

### Important screenshot:
 ![alt text](https://github.com/prabhat143/CodeCleanBook/blob/main/Images/Picture2.png)
 
Interfaces and Implementations

Leave interfaces unadorned (i.e. plain without encodings);
So [ ShapeFactory (as interface) and ShapeFactoryImplementation (for concrete implementation) ] are better than [ IShapeFactory (for interface) and ShapeFactory (for concrete implementation) ].

An example is Java List interface.


### Avoid Mental Mapping
Just because you can remember that this means that doesn't mean you should write your code that way.
One difference between a smart programmer and a professional programmer is that the professional understands that clarity is king. Professionals use their powers for good and write code that others can understand.


### Class Names
A class name should be a noun, not a verb. Avoid words like Manager, Processor, Data, or Info. Good names could be Customer, WikiPage, Account, and AddressParser.


### Method Names
Methods should have verb or verb phrase names like postPayment, deletePage, save...
When constructors are overloaded use static factory methods with names that describe the arguments:

better than

Don’t Be Cute

Don't use slang!: whack() instead of kill() Say what you mean. Mean what you say.
 
### Pick One Word per Concept
If you choose get() use it always (instead of fetch, retrieve, etc.)

### Don’t Pun
Avoid using the same word for two purposes (add() method could mean different things in different classes...)
Make your code as easy as possible to understand.


### Use Solution Domain Names
Use pattern names: Factory, Visitor, Decorator, etc. The people who read your code will be programmers so if there is a commonly understood term, it's ok to use it.

### Use Problem Domain Names
And you could ask a domain expert if you have doubts when there is no 'programmer way' to define something. I.e. the term you use is familiar to people in the project, company, etc.

### Add Meaningful Context
Variables usually don't have a meaning by themselves. You will need context. Names like: firstName, lastName, street, postalCode, etc. Are names from an address. If you have problems with the context you can add a prefix: addrFirstName, addrLastName, etc. But It would be better if you put them into a class Address => you will have a great context. When a method has a lot of variables with an unclear context you can try to break it into smaller functions.

### Don’t Add Gratuitous Context
Don't use prefixes in all your classes/methods to say that they belong to a specific context. Gas Station Deluxe => GSD and then you have: GSDAccountAddress... it is not a good name.
Shorter names are generally better than longer ones.
