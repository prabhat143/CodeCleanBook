# Chapter 05 - Formatting

We want people to perceive that professionals have been at work... not to see a scrambled mass of code that looks like it was written by a bevvy of drunken sailors.

#### You should take care your code is nicely formatted
In a team: define a single set of formatting rules that everybody should comply with.

### The Purpose of Formatting
Code formatting is about communication. Readability of code.

### Vertical Formatting
Small files are easier to understand than large files.
It is possible to build a significant system(JUnit, tomcat, ant, fitness) with files between 200-500 lines.

### The Newspaper Metaphor
#### We would like a source file to be like a newspaper article:
- At the top, you expect a headline
- The first paragraph gives you a synopsis of the whole story. 
- As you continue down the details increase

In a source file: high-level concepts and algorithms => lowest level functions and details

### Vertical Openness Between Concepts
- line => expression or clause.
- group of lines => complete thought. 
- thoughts are separated with blank lines.

### Vertical Density
Useless comments in class's properties make the class more difficult to read it. Example
```
public class ReporterConfig {
 /**
 * The class name of the reporter listener
 */
 private String m_className;
 /**
 * The properties of the reporter listener
 */
 private List<Property> m_properties = new ArrayList<Property>();
 public void addProperty(Property property) {
   m_properties.add(property);
}
```
```
public class ReporterConfig {
 private String m_className;
 private List<Property> m_properties = new ArrayList<Property>();
 public void addProperty(Property property) {
   m_properties.add(property);
}
```

### Vertical Distance
#### Variable declaration:
Variables should be declared as close to their usage as possible Our functions are short -> local variables at the top. Control variables for loops => declare them within the loop statement

#### Instance variables
Should be declared at the top of the class. Everybody should know where to go to see the declarations.

#### Dependent functions
If one function calls another they should be vertically close, and the caller should be above the callee if it is possible.

#### Conceptual Affinity
Group of functions performing a similar operation. They share a common naming scheme and perform variations of the same task. We want them to be close together.

### Vertical Ordering
Downward direction => flow from high level to low level

### Horizontal Formatting
Programmers clearly prefer short lines. Keep your lines short! Limit 120 characters You should never have to scroll to the right

### Horizontal Openness and Density
We use white spaces in:
- Operators to accentuate them.
- Arguments in function calls and definitions (after the comma).

Don't put white spaces between the function's name and the opening parenthesis => They are closely related 
Example:
```
public class Quadratic {
 public static double root1(double a, double b, double c) {
   double determinant = determinant(a, b, c);
   return (-b + Math.sqrt(determinant)) / (2*a);
 }
 public static double root2(int a, int b, int c) {
   double determinant = determinant(a, b, c);
   return (-b - Math.sqrt(determinant)) / (2*a);
}
 private static double determinant(double a, double b, double c) {
  return b*b - 4*a*c;
} }
```

### Horizontal Alignment
Horizontal alignment is not useful:
- You read down the list of variable names without looking at their types.
- You look down the list of values without ever seeing the assignment operator. 
- Automatic reformatting tools usually eliminate it. 

Example:
```
public class FitNesseExpediter implements ResponseSender
{
  private    Socket        socket;
  private    InputStrea    input;
  public FitNesseExpediter(Socket          s,
                           FitNesseContext context) throws Exception
  {
    this.context = context;
    input =        s.getInputStream();
} }
```

```
public class FitNesseExpediter implements ResponseSender
{
  private Socket socket;
  private InputStream input;
  public FitNesseExpediter(Socket s, FitNesseContext context) throws
Exception {
    this.context = context;
    input = s.getInputStream();
  }
}
```

### Indentation
#### Without indentation, programs would be virtually unreadable by humans
Try to avoid breaking rules by collapsing everything in one line with short ifs, loops, and functions.

### Dummy Scopes
If the body of a while/for is a dummy make the body indented and surrounded by braces.

### Team Rules
Every programmer has his own favourite formatting rules, but if he works in a team, the team rules
