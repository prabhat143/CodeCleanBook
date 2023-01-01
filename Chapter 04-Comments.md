# Chapter 04 - Comments

### Introduction
If we were expressive enough in our programming language we would not need comments. Comments are always failures. Express yourself in code instead!
Code changes and evolves...the comments don't always get moved or updated with code changes!


### Comments Do Not Make Up for Bad Code
"Ooh, I would better comment that!" => No! It would be better to clean it!


### Explain Yourself in Code
This:
```
// Check to see if the employee is eligible for full benefits if (employee.flags && HOURLY_FLAG) && (employee.age >65)) {
```

vs:
```
// Check to see if the employee is eligible for full benefits if (employee.isEligibleForFullBenefits())
```

=> Create a function that says the same thing as the comment you want to write
 
### Good Comments
The only truly good comment is the comment you found a way not to write.

### Legal Comments
Put all the terms and conditions into an external document.

### Informative Comments
Useful information about the implementation and take decisions.

### Explanation of Intent
Take care that there is no better way, and then take even more care than they are accurate.

### Clarication
If you do it take care that there is no better way and they are accurate.

### Warning of Consequences
Warn other programmers about certain consequences: Maybe a test that lasts a lot of => try to use @Ignore
Something that is not thread-safe and you have to use "new" each time.

### TODO Comments
It is not an excuse to leave bad code in the system.
You do not want your code to be littered with TODOS => san them regularly and eliminate the ones you can.

### Amplication
If something is very very important you can amplify it.

### Javadocs in Public APIs
If you are writing a public API => write good docs for it. (but they can lie as any other kind of comment).


### Bad Comments
Most comments fall into this category.

### Mumbling
Is a catch block empty with a comment => was the author trying to tell himself to come later to do it? Any comment that forces you to look in another module to know the meaning is wrong.

### Redundant Comments
Less information than the code.
It is not easier to read than the code. It is less precise

### Misleading Comments Mandated Comments
A rule that says that every function/property/variable must have a Javadoc is stupid
You will finally get things like @param author The author

### Journal Comments
We have source control now => they should be completely removed.

### Noise Comments
Auto-generated or very obvious comments that are nothing but noise.

### Scary Noise
Maybe with copy/paste errors... are they a bug?

### Don’t Use a Comment When You Can Use a Function or a Variable
Consider the following stretch of code:
```
// does the module from the global list <mod> depend on the
// subsystem we are part of?
if (smodule.getDependSubsystems().contains(subSysMod.getSubSystem()))
```

This could be rephrased without the comment as
```
ArrayList moduleDependees = smodule.getDependSubsystems(); String ourSubSystem = subSysMod.getSubSystem();
if (moduleDependees.contains(ourSubSystem))
```


### Position Markers
Things like:
```
// Actions ////////////////////////////////////////////////
```

Noise is obvious and usually ignored... do not use banners

### Closing Brace Comments
Might leave a comment to mark which braces close which part of the function. Better to write shorter functions without so much nesting.

### Attributions and Bylines
Added by:... SCMs are a better place for this.

### Commented-Out Code
Trust in SCM's... delete the code.

### HTML Comments
HTML in source code comments is an abomination: it makes them hard to read.

### Nonlocal Information
The comment should describe the code it appears near.
Too Much Information Inobvious Connection

Maybe the comment needs its explanation...

### Function Headers
Short functions do not need much description. We prefer well-chosen names to a comment header.

