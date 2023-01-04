# Chapter 06 - Objects and Data Structures

We keep our variables private. Nobody depends on them. Freedom to change their type of implementation. If you don't need them don't expose them to public getters and setters!

### Data Abstraction
Hiding implementation is about abstractions.

A class does not simply push its variables out through getters and setters. Rather it exposes abstract interfaces that allow its users to manipulate the essence of the data, without having to know its implementation.

Concrete Point
```
public class Point {
 public double x;
 public double y;
}
```

Abstract Point
```
public interface Point {
 double getX();
 double getY();
 void setCartesian(double x, double y);
 double getR();
 double getTheta();
 void setPolar(double r, double theta);
}
```

Abstract point it's hiding its implementation. The methods enforce an access policy => read coordinates independently but write them together.

Concrete Vehicle

```
public interface Vehicle {
 double getFuelTankCapacityInGallons();
 double getGallonsOfGasoline();
}
```

Abstract Vehicle

```
public interface Vehicle {
 double getPercentFuelRemaining();
}
```
Abstract vehicle doesn't expose the details of the data.

The worst option is to blithely add getters and setters

### Data/Object Anti-Symmetry
Objects vs Data structures
- Objects hide their data behind abstractions and expose functions that operate on that data.
- Data structures expose their data and have no meaningful functions.

OO code vs Procedural code
- OO code makes it easy to add new classes without changing existing functions
- Procedural code makes it easy to add new functions without changing the existing data structures. 
- OO code makes it hard to add new functions because all the classes must change.
- Procedural code makes it hard to add new data structures because all the functions must change.

Sometimes you need data structures and sometimes you need objects!

### The Law of Demeter
talk to friends, not to strangers

- C
- An object created by f
- An object passed as an argument to f
- An object held in an instance variable of C

Avoid this (called train wreck):
```
final String outputDir = ctxt.getOptions().getScratchDir().
getAbsolutePath
```

Try to split them:
```
Options opts = ctxt.getOptions();
File scratchDir = opts.getScratchDir();
final String outputDir = scratchDir.getAbsolutePath();
```

Train Wrecks
=> bunch of coupled train cars! Is this a violation of Demeter's Law? it depends...
- if context, options and scratchDir are objects is a clear violation of the Law. 
- if they are data structures with no behaviour Demeter's Law does not apply.

If it was a data structure you could use it this way:
```
final String outputDir = ctxt.options.scratchDir.absolutePath;
```

### Hybrids
Public fields + methods => Avoid creating them. Worst of both worlds: hard to add new functions and hard to add new data structures.

### Hiding Structure
You could think of these options:
```
ctxt.getAbsolutePathOfScratchDirectoryOption();
```

=> explosion of methods in ctxt object or
```
ctx.getScratchDirectoryOption().getAbsolutePath()
```
=> it returns a data structure, not an object.

Neither option feels good.
You tell an object to do something you should not be asking it about its internals Why do you want to know the absolute path?.. to create something:
```
BufferedOutputStream bos = ctxt.createScratchFileStream(classFileName);
```
=> ctxt hides its internals and we are not violating Demeters' Law.

### Data Transfer Objects
Structures to communicate with databases, parsing messages from sockets...
You usually use Beans => private properties with setters and getters. It is ok for OO purists but has no other benefits.

### The Law of Demeter
There is a well-known heuristic called the Law of Demeter that says a module should not know about the innards of the objects it manipulates. As we saw in the last section, objects hide their data and expose operations. This means that an object should not expose its internal structure through accessors because to do so is to expose, rather than to hide, its internal structure.

### Conclusion
Objects expose behavior and hide data. This makes it easy to add new kinds of objects without changing existing behaviors. It also makes it hard to add new behaviors to existing objects. Data structures expose data and have no significant behavior. This makes it easy to add new behaviors to existing data structures but makes it hard to add new data structures to existing functions.
In any given system we will sometimes want the flexibility to add new data types, and so we prefer objects for that part of the system. Other times we will want the flexibility to add new behaviors, and so in that part of the system we prefer data types and procedures. Good software developers understand these issues without prejudice and choose the approach that is best for the job at hand.



