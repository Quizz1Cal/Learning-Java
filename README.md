# Lecture Questions/Misc Notes
- Will learn git in OOSD a bit
- Use hackerrank, codecademy, codesignal for practice problems
- He will use questions from the grok to test us in midsem
- PRACTICE READING IN CSV
- Okay so for a class with default attributes, can a subclass access?
- Slide 44 of Lecture 9 is still weird to me
- Slide 47 of Lec9: "Makes the subclass behaviour available when using variables of a superclass" what?

## Brief Slick Notes for Midsem
- Slick is a java graphics library built on top of *Light Weight Java Gaming Library* (LWJGL)
- *`init`*: initialises game, sets up objects that are needed to play
- *`update`*: performs computations for Objects
- *`delta`*: # ms since last frame
- *`render`*: Draws objects to screen AND THAT IS IT

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
- However creating new instances with wrapper class (`s3 = new String("Hello")`) will make `"Hello" == s3` FALSE
- If going to compare strings, use `first_str.equals(other_str)`
- Character addition/subtraction works as it did in C

**Useful methods**: .length(), .toUpperCase(), .contains(substr), .indexOf(substr), .format(), .charAt(index)
- .substring(a, b) attains slice from a to b-1; b presumed end if not included
```java
String new_str = "fun";
new_str = str.concat(" times"); // "fun" is lost but "fun times" is newly generated
```
- Stored in the "string constant pool"
- Use `String` class and double-quotation marks (note: this is marked `final`)

### Arrays
**Definitions**
1. ```java
String[][] name = newString[ROWS][unfixed_cols]{items}
// You actually define the sub-arrays LATER (individually) (at which point size must be specified and EACH subarray must be defined like a proper array... but each of those entries can be any size)
```
2. ```java
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

## Methods

### Overloading

### Interfaces

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
--> You define what the string equivalent is with this function
--> E.g. define toString as `return String.format("%ss are %s!", this.name, this.colour)`
--> then `System.out.println(new Fruit("apple", "red"))` will print "apples are red!" without explicit reference to ToString

*finalize*: method called when objects are deleted. Use to clean up, record keep etc.

### Inheritance
**Definition**: A form of abstraction that permits "generalisation" of similar attributes/methods - pass on common features/behaviours to children.
- Characterised by "is a" relationship.
- REUSES code

**Superclass**: parent/base class.
**Subclass**: child/derived class that inherits/`extends` common attr/methods. Can extend behaviour as well. **Does NOT inherit private attr/methods**
- `final` PREVENTS INHERITING
`extends` flags that you are inheriting from a class. You can only inherit from one class (explicitly).
`super` is used **AS THE FIRST STATEMENT** in a subclass constructor to invoke a superclass constructor, AND to get superclass methods (e.g. `super().superMethod()`)

**Shadowing**: When 2 or more variables are declared with *same name* in *overlapping scopes* e.g. subclass and superclass.
**Overriding**: Same name and signature, re-defined in subclass. ONLY CAN BE DONE BY A SUBCLASS.
- Cannot change return type when overriding UNLESS it is subclass of super's return e.g. returns Piece in super but Rook when overriden
- Cannot increase privacy but can decrease it
- `final` PREVENTS OVERRIDING = 'a variable, method, or class can only be assigned, declared, defined ONCE'
**Overloading**: Same name, different signature. Can overload a superclass method in subclass.

**Downcasting**: To treat ...
- `Piece piece = new Rook()` is okay
- `Rook rook =  new Piece()` is nonsensical UNLESS...

### Abstract Classes

### Polymorphism

## Methods

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
- Default: **package** - additional access to classes in same package
- **Protected**: additional access to subclasses that inherit from this class
- **Public**: available at all times in the application
- **Getter/accessor**: method that returns instance variable
- **Setter/mutator**: method that modifies value of an instance variable
- **Privacy leak**: When a refernce to an external variable is made available and hence undesired alteration possible
- **Deep copy**: when copying an object, copy references of objects inside it

### Mutability
- objects are mutable where instance variables can be changed post-initialisation
- Objects are immutable if NONE of its instance variables can be changed post-initialisation
- Classes are considered immutable if
   - a) all attributes are private (so cannot be modified directly)
   - b) only returns copies of mutable instance variables (ditto)
   - c) no setters (no indirect modification)
- *IDEA*: Use a COPY CONSTRUCTOR (e.g. `Actor(Actor actor)` to define a separate copy of an input, so that `new Actor(prev_actor)` does not alias)

- Use `final` flag to prevent change. Does not need to be assigned immediately, but can only be assigned once.
--> CAPITALIZE ANY FINAL VARIABLES

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

#### System.out
- println
- format(ctrl_str, primitives_and_literals) OR printf(ctrl_str, primitives_and_literals)
   "% then number$ then flags then width then .precision then type"
