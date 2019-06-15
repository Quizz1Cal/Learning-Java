# Lecture Questions/Misc Notes
- Use hackerrank, codecademy, codesignal for practice problems
- Revise arrays, Comparable<T>
- PUBLIC AND STATIC ARE DEFAULT? (it was in a lecture)
- So local variables don't have defaults, but instance (class) variables do
- Use of random
- Slide 44 of Lecture 9 is still weird to me
- Slide 47 of Lec9: "Makes the subclass behaviour available when using variables of a superclass" what?
- Why is slide 13 Lec12 an interface and not an abstract?
- What the hell is slide 28 Lec12?
- Multiple associations Lec13 slide32
- Check my ANS for the Death Star Q 2017 Exam Q3
- Fairly certain null==null works but never use for class instances
- Clarify the points raised on last slide of Exceptions ('using exceptions' in particular)
- Lec 22 (Event-D-P) slide 43 - type inference for a generic method from what it's being assigned.
- Review `String.startsWith`, `s.getchar...`
- review Arrays methods: `Arrays.asList() etc.`

# OOP

## Four Principles

### Encapsulation
- The hiding of data implementation by use of access modifiers and getter/setters, for security and clean, scalable code. AKA Information hiding

### Data Abstraction
- Solving problems by creating abstract data types to represent problem components; achieved in OOP through classes, which represent data and actions. Bottom-up implementation

### Polymorphism
The ability to represent an object in many forms; subtype (overriding, substitution), ad hoc (overloading), parametric (generics)

### Inheritance

### Delegation???

## Other
[Programming to the interface - see the comments by Bill the Lizard](https://stackoverflow.com/questions/383947/what-does-it-mean-to-program-to-an-interface)

# Java Basics

## Syntax

Simple rules:
- Java is case-sensitive
- Identifiers must be unique within their scopes
- whitespace doesn't affect interpretations; semi-colon is necessary
- Cannot use keywords for identifiers; must start with alphabetical or underscrores
- Java entirely uses pointers
- Conflicting names --> preference is always given to local variables (e.g. arguments)
- A solution must have at least one main (LOWERCASE) method in order for it to run, but each class may have at most one main

Conventions:
- Verbose naming in camelCase
- Classes start with uppercase e.g. `class MyClass`
- Methods/variables start with lowercase e.g. `void doStuff(String withThis) {`
- Contants all uppercase e.g. `public static final String FIRSTNAME="Yo";`

### Common reserved characters:

```java
/* multiline comment
- // single line comment
- ; indicates end of statement
- "" used to start and end strings. NO SINGLE QUOTING FOR STRINGS
--- Use \" to include them in strings. Also \n, \t available
*/
```

### Arithmetic and Logic Operators
```java
// + concatenates string representations of objects
"1 + 1 = " + 1 + 1 // 1 + 1 = 11
"1 + 1 = " + (1 + 1) // 1 + 1 = 2. This is due to precedence of ()
null // "no object here"
true && !false // evaluates to true
1 || 0 // Error: logical operators only work on booleans
7 % 2 // modulus
```
Use same reiational operators as in C e.g. !=, >= etc.
Division is only floating point if one number involved is float/double
To compare floats/doubles, use the epsilon approach
++, --, +=, -=, \*= and /= are in Java

## Control flow
Use if, else if, else with {} just as in C
Use while, do and for loops identically to C
**Switch/case**:
```java
switch (variable) {
   case val:  // USING BREAKS TO STOP WARNINGS
   case val:
   default:
}
```
**Application: continuous input**
```java
// Continually request input from standard input that is an integer. Once a non-int is entered, it terminates
Scanner scanner = new Scanner(system.in);
while(scanner.hasNextInt()) {
}
```

**For**:
```java
for (int i = 1; i <= N, i++) {}
for (int x : array) {}
```


## Objects

**Definition**: a specific, concrete instance of a class. Contains state, or dynamic information.
**Instance**: an object that exists in your code

### General Features

**Instantiation**: To create an object of a class. All objects are null until this occurs.
- E.g. `Actor RDJ = new Actor(<args>); // the 'new' directs the JVm to allocate memory for it (instantiate it, give it address)

#### Inherited Object Methods
- `object.equals(object_2)` checks equality of objects (esp. strings)

#### Wrappers & Primitives
**Primitives**: boolean, byte, char, int, float, double, long & short
**Wrapper Class**: Boolean, Byte, Character, Integer, Float, Double, Long & Short

Some Wrapper Class methods:
- `Integer.rotate` to move bitstring
- `Integer.signum` for sign
- `Integer.Reverse()` to reverse bits
- `Integer.parseInt(str_literal)`
- `Character.isLowerCase(<char>)`
- `Character.isUpperCase(<char>)`
- `Character.getType(<char>) == Character.OTHER_PUNCTUATION, .DECIMAL_DIGIT_NUMBER, .LETTER_NUMBER`
- `Wrapper.parseWrapper(str_literal)` exists for all wrapper classes

**Boxing**: converting a primitive instance to wrapper class. *Unboxing* is the opposite
Manual examples:
- `Integer i1 = 10;`
- `Integer i1 = new Integer(10);`
- `int i1 = new Integer(10);`

**Casting**: not always necessary (e.g. int to float) but should specify regardless to prevent loss/clearly specify

### Strings
- IMMUTABLE VALUE (and hence can only be **replaced**, not modified)
   The JVM automatically checks if new string literals point to a pre-existing literal. Allowing
   modification of the base value would be difficult to detect/regulate - hence, immutability.
- As always, reference variables are mutable
- Can use + and += for concatentation
- Typical strings are constants, so declaring them in standard fashion --> s1 == s2 will typically return true
- Review control strings: %1$+020.2f
- However creating new instances with wrapper class (`s3 = new String("Hello")`) will make `"Hello" == s3` FALSE
- If going to compare strings, use `first_str.equals(other_str)`
- Character addition/subtraction works as it did in C

**Useful methods**: .length(), .toUpperCase(), .contains(substr), .indexOf(substr), .format(), .charAt(index), .substring(startIndex, lastExclIndex)
- .substring(a, b) attains slice from a to b-1; b presumed end if not included
```java
String new_str = "fun";
new_str = str.concat(" times"); // "fun" is lost but "fun times" is newly generated
```
- Stored in the "string constant pool"
- Use `String` class and double-quotation marks (note: this is marked `final`)

### Arrays
**Definitions**

Some text

```java
String[][] name = newString[ROWS][unfixed_cols]{items}
// You actually define the sub-arrays LATER (individually) (at which point size must be specified and EACH subarray must be defined like a proper array... but each of those entries can be any size)
// OR
String[] name = new String[size];
String line[] = file.nextLine().split(",");
String[] strings = {"str_1", "str_2"};
name = other_name
```

*NOTE THAT THIS IS AN ALIAS, AS ARE ANY VALUES THAT POINT TO NON-PRIMITIVES*

Useful attributes:
- array.length
- array.copyof(array, array_new_size)
- array.sort()

Use java.util.Arrays:
- Arrays.toString(nums) (allows Array printing)
- Arrays.binarySearch(arr, key)
- Arrays.sort(arr)
- Arrays.equals(arr1, arr2)

## Files, I/O *DO NOT NEED TO MEMORISE*

- *Command line*: `java Program_aka_arg_0 arg_1 arg_2 arg_3 // All strings`. Argugments have to be sent all at once!
- Use "" in command line if the name is extensive
- Easily access them with `args[0]` etc.

- *Scanner*
   ```java
   import java.util.Scanner;
   Scanner scanner_inst = new Scanner(System.in); // System.in is simply location from which to derive input
   String str = scanner.nextLine();
   // primitive ref = scanner.nextPrimitive();
   ```
- Important note: `\n` is a nasty character to remove. Use nextLine() frequently to skip across it, as other next will ignore it (whitespace)

- System.out.print(string) does NOT print whitespace, println DOES

- System.out.format() is equivalent to String.format() but prints it
- **Control string format**:
   - % to flag it
   - 1$ for argument specifier (use < without $ to take 'previous')
   - +0 for flags (a 0 here will pad with 0 rather than spaces)
   - 20 for width (n.b. - PRINTS YOUR THING FIRST, + LAST)
   - .10 for precision
   - f for type

### Files

NOTE: When reading csv files, split the words with String[] cols = `text.split(",")`


#### Method 1: BufferedReader
```
import java.io.FileReader; // Allows reading of chars; simple
import java.io.BufferedReader; // Allows reading of strings as well as characters; allows file manipulation
import java.io.IOException;
import java.io.FileWriter;
import java.io.PrintWriter;

try {
  BufferedReader br = new BufferedReader(new FileReader("test.txt"));
  PrintWriter pw = New PrintWriter(new FileWriter("test.txt", true)) { // Will auto-close file
    String text;
    while ((text = br.readLine()) != null) {
      //...
      pw.println(<stuff>)
      pw.format(<moar_stuff>)
    }
  }
} catch (Exception e) {
  e.printStackTrace();
}
```

#### Method 2: Scanner
```java
try(Scanner scanner = new Scanner(new FileReader("test.txt"));) {
  while (scanner.hasNextLine()) {//...
  }
}
```

## Classes

**Definition**: a unit of abstraction in OOP, represents a real world/problem world entity. A template for things/objects/datatypes that have common properties (attributes, methods).

**Constructors**: A method used to create and initialise an object. Typicallly invoked by 'new'. Have same name as a class. They do NOT return values ... explicitly (there is an output though). More than one is possible.
- 'Default constructor' is literally an empty constructor

**this**: a reference to a calling object (object that owns/is executing the method). Use to prevent name conflicts b/t class method arguments and class attributes

```java
// Example constructor
public <ClassName>(<type> firstAttr, <type> SecondAttr) {
   this.firstAttr = firstAttr;
   this.secondAttr = secondAttr;
} // NOTE THE LACK OF RETURN TYPE DECLARATION
```

### Some standard class methods

*equals*: `public boolean equals(<type> var) { // returns boolean of whether two objects are equal; you define equality`

```java
public boolean equals(Movie otherMovie) {
   return this.title.equals(otherMovie.title) && this.rating == otherMovie.rating;
}
```

*toString*: Returns string representation of an object. **Automatically called when objects acts like a string** e.g. printing

- You define what the string equivalent is with this function

- E.g. define toString as `return String.format("%ss are %s!", this.name, this.colour)`. Then `System.out.println(new Fruit("apple", "red"))` will print "apples are red!" without explicit reference to ToString

*finalize*: method called when objects are deleted. Use to clean up, record keep etc.

### Inheritance
**Definition**: A form of abstraction that permits "generalisation" of similar attributes/methods - pass on common features/behaviours to children.
- Characterised by "is a" relationship.
- REUSES code
- Everything inherits from Object and therefore has toString(), .equals(), .getClass() etc

#### Equality of classes/subclasses
- getClass returns calling object's class as an Object of type Class
- instanceof is an operator for instance1 instanceof instance2 --> boolean evaluation, True if inst1 is of type (or subclass of) inst2
- The object signature is boolean .equals(Object) so you need to include a getClass check in the overriding code
- In subclasses, just do a super.equals(other) call

**Superclass**: parent/base class.

**Subclass**: child/derived class that inherits/`extends` common attr/methods. Can extend behaviour as well. **Does NOT inherit private attr/methods**
- `final` PREVENTS INHERITING
- `extends` flags that you are inheriting from a class. You can only inherit from one class (explicitly).
- `super()` is used **AS THE FIRST STATEMENT** in a subclass constructor to invoke a superclass constructor, AND to get superclass methods (e.g. `super.superMethod()`)

**Shadowing**: When 2 or more variables are declared with *same name* in *overlapping scopes* e.g. subclass and superclass. AVOID AT ALL COSTS

### Abstract Classes
**Abstract**: Defines a superclass method that is common to subclasses but without implementation, with expectation that a subclass will override (define) functionality.
- Any class that is incomplete, i.e. a "general/incomplete concept" is also **abstract**. THEY CANNOT BE INSTANTIATED. Need not necessarily have abstract methods.
- Those that are fully defined are **concrete**

### Interfaces (NOT A CLASS)
**Definition**: `interface` declares a set of (implied `public static final`) constants and (implied) `public abstract` methods that define behaviour of an object. A "can do" relationship, called <...>able
- Cannot be instantiated
- Zero code UNLESS `default` used for a method
- `Implements` is used to flag that a class will take on the behaviours:
    - Abstract classes don't **have to** define it all
    - But any concrete class **has to**
- MULTIPLE IMPLEMENTATION possible, and extension of interfaces into other interfaces too
- *Inheritance* generalises shared properties, **similar classes**, "is a"
- *Interface* generalises shared behaviour, **potentially dissimilar classes**, "can do"
- *Callum's rule of thumbs*: If it feels like the only thing they have in common is that a) they're an object or b) the actual action, or you feel like the implementation would vary significantly each instance, then it's probably due cause for an interface
> From Oracle Documentation: "Implementing an interface allows a class to become more formal about the behaviour it promises to provide. Interfaces form a contract between the class and the outside world, and this contract is enforced at build time by the compiler."

#### Functional Interfaces and anonymous implementers
[Strong explanation on what anonymous implementers are/how](https://stackoverflow.com/questions/16750772/instantiating-interfaces-in-java/35708932)
**Functional interface**: Only has one (implied abstract) method.

#### Inbuilts
**Comparable<className>** is an interface (generic) that specifies behaviour for comparing objects of the same class via `public int compareTo(<className> object_or_any_subclass_of_className)` (-1,0,1) --> (< = >)
- This is then exploited by things like Arrays.sort()

### Polymorphism
**Definition**: The ability to use objects/methods in different ways.

- *Overriding*: Same method, varying forms dependent on class **SUBTYPE POLYMORPHISM**
  - ONLY CAN BE DONE BY A SUBCLASS.
  - Cannot change return type when overriding UNLESS it is subclass of super's return e.g. returns Piece in super but Rook when overriden
  - Cannot increase privacy but can decrease it
  - `final` PREVENTS OVERRIDING = 'a variable, method, or class can only be assigned, declared, defined ONCE'
- *Overloading*: Same method, varying signatures **AD-HOC POLYMORPHISM**
  - Can overload a superclass method in subclass.
  - Changing return type *alone* **DOES NOT COUNT AS OVERLOADING**
- *Substitution*: Use subclasses in place of superclasses **SUBTYPE P.**
  - **Upcasting**: A child is assigned to a variable of a superclass (ancestor class) e.g. `Robot robot = new AerialRobot()`
  - **Downcasting**: An ancestor class instance is assigned to a variable of subclass.
    - `Piece piece = new Rook()` is okay (upcasting)
    - `Rook rook =  new Piece()` is nonsensical UNLESS you plan on casting it (downcasting) via `Rook actual_rook = (Rook) rook;`
- *Generics*: Defining parametrised methods/classes **PARAMETRIC P.**

## Methods

### Signatures
`<privacy?> <static?> <return type> <method name>(<arguments>)` - defined by number and type of arguments, and function name.

## Static vs Instance
Advice: make all methods static, remove static only if method uses an instance variable.

**Static/Class Variables**: Property/attribute shared by all instances of a class. ONE COPY PER CLASS. Const or variable okay
- E.g. all `Students()` instances should have a `public static /*final? */ String SCHOOL_NAME`

**Instance Variables**: A variable/property/attribute that is unique to each class' instance. ONE COPY PER OBJECT
This means modification is possible independent of other instances.
- E.g. `public <type> varName = <value>`

**Class/Static Methods**: A method/action that can be called independent of any instance ("performed by a class"). Typically spits out a message. DOES NOT REFER TO any instance variables (as these are not instance-independent)
- E.g. `public static <return-type> methodName(<args>) {...`

**Instance Methods**: A method that each class' instances can use, but whose output could vary across each instance of an object due to different attribute/property values
- E.g. `public <return_type> methodName(<args>) {`...

## Privacy/Encapsulation

- *Information hiding*: Using privacy to hide details
- *Access control*: Preventing outside class from manipulating properties undesirably
- *Encapsulation*: Using privacy to restrict unwanted access to object values

The order of privacy from weakest to strongest (cumulative):
- **Private**: class methods. Typically apply to mutuable instance variables, some methods
- Default is **package** - additional access to classes in *same package*
- **Protected**: additional access to **subclasses** in *different packages*
- **Public**: available at all times in the application

Other definitions:
- **Getter/accessor**: method that returns instance variable
- **Setter/mutator**: method that modifies value of an instance variable
- **Privacy leak**: When a reference to an external variable is made available and hence undesired alteration possible
- **Deep copy**: when copying an object, copy references of objects inside it

### Mutability
- objects are mutable where instance variables can be changed post-initialisation
- Objects are immutable if NONE of its instance variables can be changed post-initialisation
- Classes are considered immutable if
   - a) all attributes are private (so cannot be modified directly)
   - b) only returns copies of mutable instance variables (ditto)
   - c) no setters (no indirect modification)
- *IDEA*: Use a COPY CONSTRUCTOR (e.g. `Actor(Actor actor)` to define a separate copy of an input, so that `new Actor(prev_actor)` does not alias)

- Use `final` flag to prevent change. Does not need to be assigned immediately, but can only be assigned once. CAPITALIZE ANY FINAL VARIABLES

## Generics
**Definition**: Allows parametrisation of data types to enable generic logic to be written that applies to any class type.
- `<T>` ==> T is a *type parameter/variable* (a placeholder) whose value is literally `String`, `Integer`, `Robot` etc. and Java directly substitutes whatever T is into each *placeholder*
  - This is the 'argument' representation, just use `T` in actual code

### Limitations
- CANNOT instantiate with a generic e.g. `new T()` not allowed
- CANNOT create arrays (size unknown) e.g. `new T[]` not allowed

### Comparable<T>
A non-generic `Comparable` functional interface exists with functional `public int compareTo(Object o)`; OTHERWISE this requires a typecheck (`instanceof`) and downcast `(Type)o` and returns ANOTHER flag (-2) if type inconsistent

### Comparator<T>
Used to sort 'by any mechanism desired' - abstraction of comparison.

```java
import java.util.Comparator;
class XComparator implements Comparator<Class> {
  public int compare(Class c1, Class c2) {
    if (c1.getX() < c2.getX()) return -1;
    if (c1.getX() > c2.getX()) return 1;
    else return 0;
  }
}
...
Collections.sort(ArrayList<Class>, new XComparator()); // Etc
```

### ArrayList<T>
- Useful, auto-expands but DOES NOT AUTO-SHRINK
- Cannot hold primitives (needs class name)
- Can sort if Comparable<T> implemented

```Java
import java.util.ArrayList;
import java.util.Collections;

ArrayList<String> array = new ArrayList<String>();  // This T can be excluded
array.add(new String(args));
array.add(new String(args));
array.toString();
for (String s: array) {
    // Stuff
}
Collections.sort(array);
```

### Generic Classes
**Definition**: A class that is defined with an arbitrary type for a field, parameter or return type.
- Use `<T>` after class name in definition heading
- Technically any non-keyword identifier ok but single-cap-letter conventional

Example 1: Basic class
```java

public class Sample<T1, T2> {
  public T1 first;
  public T2 second;

  public Sample(T1 first, T2 second) {
    this.first = first;
    this.second = second;
  }
}
...
Sample<Integer, String> pair = new Sample<Integer, String>(1, "Ayo");
```

Example 2: Bounds to types using Generic keyword
```Java
public class Generic<T extends Robot & Comparable<T> & List<T>> {  
}
```

### Generic Method
**Definition**: Method that accepts arguments/returns args of arbitrary type.
```java
/* A function with:
- Two generic types T and S (these are local to the method just like any arg)
- Outputs T
- Takes two arguments of type T and S respectively
*/
public <T,S> T genericMethod(T arg1, S arg2);
```

### Anonymous Inner Class
**Definition**: A class created 'on the fly' without a new file (or a class of which only one object is created).
```java
import java.util.Collections;
Collections.sort(list, new Comparator<Class> {
  //...(body of class definition)
})
```

## Exceptions

### Errors
**Syntax/syntactical Error**: Errors where written code is illegal - compiler/editor identified.

**Semantic Error**: Code runs to completion but has incorrect output/operation - software testing identified.

**Runtime Error**: Error that causes premature program crash/end - execution identified.
- E.g. dividing by zero, out of bounds index accessing (-1 or over capacity), etc.
- E.g. ArithmeticException, ArrayIndexOutOfBoundsException etc.

### Error Handling

**Defensive Programming**: To explicitly guard against dangerous/invalid conditions.
- CON: Explicit guarding, lack of a 'backup/alternative', poor abstraction
- PRO: Better than 'hoping for the best'

**Exception**: A) An error state created by a runtime error. B) An object created by Java to represent the encountered error.
- *Checked*: Inherited from Exception class, must be EXPLICITLY handled by programmer, otherwise a compiler error occurs.
> All checked exceptions must be handled with try/catch, OR declaring that such a method could throw the exception
- *Unchecked*: Inherited from Error class, can be IGNORED by programmer without defensive programming against them. They exist because they can be related to program logic, or are too numerous.  
> ALL RuntimeExceptions and all Errors are unchecked. This includes ArithmeticException - so the error is NOT flagged at compilation, only at runtime.
> [Here's the bottom line guideline: If a client can reasonably be expected to recover from an exception, make it a checked exception. If a client cannot do anything to recover from the exception, make it an unchecked exception.](https://docs.oracle.com/javase/tutorial/essential/exceptions/runtime.html)

**Exception Handling**: Code that actively protects your program in the event of exceptions.

Use this structure:
```Java
try {
  stuff;
} catch (<ExceptionClass> varName) {
  if_encountered e.g. varName.printStackTrace();
} ... as many catches as you want {
} finally {
  regardless, e.g. clean up;
}
```

### Throwing Exceptions

**throw**: To respond to an error state by creating an Exception object.
- Exception throwing = 'you create and throw the exception if criterion are met'
- Exception handling = 'programming what to do if exception(s) thrown at runtime'

**throws**: A method has the potential to throw, and does not 'deal with it' or it's response differs by application.

```Java
public method (args) throws PotentialException {
  ... code ...;
  if (testing) {
    throw new PotentialException(args_if_any);
  }
}
```

### Defining Exceptions

Exceptions have a constructor - subclasses should call the super but with an updated error message. This message is retrievable if the error is caught by `e.getMessage()`

```java
import java.lang.Exception;
class CustomException extends Exception {
  public CustomException (args?) {
    super("message which could include args as well");
  }
}
```

## Advanced Topics

### Enumerated Types
**enum**: A clas with a finite list of constants.
- Must list all values
- By default, static, and are accessed statically.
- `toString()` will print their name I THINK

### Variadic Parameters
**Variadic Method**: Methods with an unknown number of arguments. Use `...` to denote, and will IMPLICITLY convert arguments into an array.

### Functional Interface
**Functional Interface**: Interface with only one abstract method. Flagged as `@FunctionalInterface`
- E.g. `Predicate<T>` interface with `test (T t)` method.
- E.g. `UnaryOperator<T>` interface with `T apply (T t)` method.
- Most useful when combined with Lambda Expressions.

### Lambda Expressions (BRILLIANT)
**Lambda Expression**: Treats code as data that can be used as an object, e.g. instantiating an interface w/o implementation. Essentially, an 'instance' of a functional interface that allows us to treat the functionality of an interface as an object.
- E.g. `Predicate<Integer> p1 = i -> i > 0;` allows `p1.test(1)`
- E.g. `Predicate<Integer> p3 = p1.and(p_other)`
- Can have 0 or more arguments

#### Functional arguments
The important thing here is that any lambda expression is a 'substitute' for a unary operator.

##### Example 1
```java
public abstract class List<T> {
  public void replaceAll(UnaryOperator<T> operator);
}
```
...
```java
List<String> names = ...;
names.replaceAll(name -> name.toUpperCase());
```

##### Example 2
The use of LE can be done in place of anonymous classes, but are different.
```java
starWarsMovies.sort((m1, m2) -> m1.rating - m2.rating);
```

Is an alternative to (but 'not the same thing' as)
```java
SWM.sort(new Comparator<Movie> {
  public int compare(Movie m1, Movie m2) {
    return m1.rating - m2.rating;
  }
});
```

### Method References (BRILLIANT)

**Method Reference**: An object that stores a method; can take the place of a lambda expression IF that LE only calls a single method.
- E.g. `unaryoperator = names.replaceAll(String::toUpperCase)` beats `unaryoperator = names.replaceAll(name -> name.toUpperCase())`.
- Can be done for static, instance and constructor methods (String::new). Method arguments are IMPLIED.

### Streams
**Stream**: Series of elements given in sequence, that are automatically put through a pipeline of operations.
- Useful: `map`, `filter`, `limit` (# iterations), `collect` (into array/etc.), `reduce` (to a single value)
- Note `Collectors.toList()`, `Collectors.joining(", ")`
```java
list.stream()
      .filter(s -> s.length() > 5)
      .filter(...)
      .map(String::toUpperCase)
      .collect(Collectors.toList());
```

## Memory

Java has automatic memory allocation and management (the garbage collector):

- Objects are created in heap memory
- Stack memory is 'somewhat faster', heap is more flexible and always stores complex objects
- Automatic memory allocation
- Any object that still is referenced to by a variable will not be thrown out by garbage collection
   e.g. local variables within a method
   Can explicitly dereference with null e.g. `myvar = null;`
- Garbage decides when to throw out (destroy i.e. reclaim memory of) unreferenced objects

If no memory is available for a newly requested object, `OutOfMemoryError` is thrown.

- Can use `Runtime.maxMemory()` and `Runtime.totalMemory` to measure memory

# Class Reference

### java.lang.Math
- Math.abs(-1)
- Math.pow(value, power)
- Math.sin, asin, acos, ceil, floor, exp, min/max, pow etc.

#### java.util
- Scanner
```java
   import java.util.Scanner;
   Scanner scanner_inst = new Scanner(System.in);
   String str = scanner.nextLine();
   // primitive ref = scanner.nextPrimitive();
   ```
- Scanner.next, .nextLine, .nextInt, .nextDouble, .nextBoolean DOES NOT kill \n... ONLY NEXTLINE
- Scanner.hasNextXXX detects whether it can read XXX next
- Collections
  - Members:
    - ArrayList
    - HashSet (no dupes)
    - PriorityQueue (yeahhh)
    - TreeSet (fast lookup of uniques)
  - c.size()
  - c.contains(Object element)
  - c.add(E element)
  - c.remove(Object element)
  - for (T t: Collection<T>)
  - c.get(int index) // Abstract list and below
#### System.out
- println
- format(ctrl_str, primitives_and_literals) OR printf(ctrl_str, primitives_and_literals)
   "% then number$ then flags then width then .precision then type"
