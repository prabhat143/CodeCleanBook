# Chapter 07 - Error Handling

Things can go wrong, we as programmers are responsible for making sure that our codes do what it needs to do and should be clear! 
Error handling is essential but if it obscures logic it's wrong.

### Use Exceptions Rather Than Return Codes

It is better to throw an exception.
- The calling code is cleaner.
- Its logic is not obscured by error handling.

Try to separate the algorithm from error handling:
```
public void sendShutDown() {
  try {
    tryToShutDown();
  } catch (DeviceShutDownError e) {
    logger.log(e);
}
private void tryToShutDown() throws DeviceShutDownError {
  // ..
}
```

### Write Your Try-Catch-Finally Statement First
Try blocks are like transactions => catch has to leave your program in a consistent state, no matter what happens in the try. 
Write a test that forces exceptions and adds behaviour to satisfy your test.


### Use Unchecked Exceptions
Your code would not compile if the signature doesn't match what your code does.
Some programming languages do not have it and you can build robust software with them.
Declaring the exception between you and the catch is an Open/Close Principle violation => a change at a low level can force changes on many higher levels.
Encapsulation is broken because all functions in the path of a throw must know about the details of that low-level exception.

### Provide Context with Exceptions
Pass enough information to be able to log the error in the catch. A stack trace won't tell you the intent of the operation that failed.

### Dene Exception Classes in Terms of a Caller’s Needs
Sometimes is very useful to write a simple wrapper that catches and translates exceptions from a third-party API => to minimize the dependencies upon it and you can move to another different library without much penalty.

### Dene the Normal Flow
SPECIAL CASE PATTERN [Fowler]: you create a class or configure an object so that it handles a special case for you => the client code does not have to deal with exceptional behaviour because is encapsulated.
Example:
```
try {
  MealExpenses expenses = expenseReportDAO.getMeals(employee.getID());
  m_total += expenses.getTotal();
} catch(MealExpensesNotFound e) {
  m_total += getMealPerDiem();
}
```
VS
```
MealExpenses expenses = expenseReportDAO.getMeals(employee.getID());
m_total += expenses.getTotal();
// the Exception is handled in the DAO and getMails returns
// PerDiemMealExpenses if an error is thrown...
public class PerDiemMealExpenses implements MealExpenses {
 public int getTotal() {
 // return the per diem default
 }
}
```

### Don’t Return Null
If you return null then you have to manage "the null" with if's...". 
When we return null we are creating work for ourselves.
You can return an empty list and clean up the code:
```
List<Employee> employees = getEmployees();
if (employees != null) {
  for(Employee e : employees) {
    totalPay += e.getPay();
} }
```
VS
```List<Employee> employees = getEmployees();
for(Employee e : employees) {
  totalPay += e.getPay();
}
//...
public List<Employee> getEmployees() {
  if( .. there are no employees .. )
     return Collections.emptyList();
}
```

### Don’t Pass Null
Returning null from methods is bad, but passing null into methods is worse
You have to deal with null, with if's or with assertions at the beginning asserts are good documentation). A null in an argument is an indication of a problem.

### Conclusion
Clean code is readable, but it must also be robust! These are not conflicting goals: error handling can be seen as a separate concern, independent of the main logic.










