Attempted use of git to learn and document java features

Further Research:
- FOUNDATIONS OF PROGRAMMING: Object-Oriented Design
- UP TO LEC 4

# Java Basics

## Syntax

Simple rules:
- Java is case-sensitive
- Identifiers must be unique within their scopes
- whitespace doesn't affect interpretations; semi-colon is necessary
- Cannot use keywords for identifiers; must start with alphabetical or underscrores

Conventions:
- Classes start with uppercase e.g. `class MyClass`
- Methods/variables start with lowercase e.g. `void doStuff(String withThis) {`	
- Contants all uppercase e.g. `public static final String FIRSTNAME="Yo";`

#### Common reserved characters:

```java
/* multiline comment
- // single line comment
- ; indicates end of statement
- "" used to start and end strings. NO SINGLE QUOTING FOR STRINGS
--- Use \" to include them in strings. Also \n, \t available
*/
```

#### Operators
```java
// + concatenates string representations of objects
"1 + 1 = " + 1 + 1 // 1 + 1 = 11
"1 + 1 = " + (1 + 1) // 1 + 1 = 2. This is due to precedence of ()

```

## Objects

### General

#### Inherited Object Methods
- `object.equals(object_2)` checks equality of objects (esp. strings)

#### Wrappers & Primitives
*Primitives*: boolean, byte, char, int, float, double, long & short
*Wrapper Class*: Boolean, Byte, Character, Integer, Float, Double, Long & Short

Apply wrapper classes to parsing:
- `parseInt(str_literal)` or `parseDouble(str_literal)`
*Boxing*: converting a primitive instance to wrapper class. *Unboxing* is the opposite 

### Strings
- IMMUTABLE VALUE (and hence can only be replaced, not modified)
   The JVM automatically checks if new string literals point to a pre-existing literal. Allowing
   modification of the base value would be difficult to detect/regulate - hence, immutability.
- As always, reference variables are mutuable
```java
String new_str = "fun";
new_str = str.concat(" times"); // "fun" is lost but "fun times" is newly generated
```
- Stored in the "string constant pool"
- Use `String` class and double-quotation marks (note: this is marked `final`)

### Arrays

### Lambda Expressions

### Mutability
- objects are mutable where instance variables can be changed post-initialisation
- Classes are considered immutable if
   - a) all attributes are private (so cannot be modified directly)
   - b) only returns copies of mutable instance variables (ditto)
   - c) no setters (no indirect modification)

## Files, I/O

- *Command line*: `java Program_aka_arg_0 arg_1 arg_2 arg_3 // All strings`
- *Scanner*
   ```java
   import java.util.Scanner;
   Scanner scanner_inst = new Scanner(System.in);
   String str = scanner.nextLine();
   // primitive ref = scanner.nextPrimitive();
   ```

## Methods

### Overloading

### Method Reference

### Streams

### Variadic Parameters

### Interfaces

## Classes

### Constructors

### Getters & Setters

### Inheritance

### Abstract Classes

### Polymorphism

### Enums

## Methods

## Static vs Instance

### Static Variables

Shared by all instances of a class (e.g. all `Students()` instances should 
have a `public static /*final? */ String SCHOOL_NAME`

### Static Methods

A method that can be called independent of any instance. Typically spits out
a message. Should not ask for any instance variables

### Instance Variables

A variable/property/attribute that is unique to each class' instance
This means modification is possible independent of other instances.

### Instance Methods

A method that each object can use, but whose output could vary 
across each instance of an object due to different attribute/property values

## Scope

## Access Modifiers

The order of privacy from weakest to strongest (cumulative):
- **Private**: class methods. Typically apply to mutuable instance variables, some methods
- Default: additional access to classes in same package
- **Protected**: additional access to subclasses that inherit from this class
- **Public**: available at all times in the application

## Generics

## Error Handling (Exceptions)

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

### System

#### System.util
- Scanner
```java
   import java.util.Scanner;
   Scanner scanner_inst = new Scanner(System.in);
   String str = scanner.nextLine();
   // primitive ref = scanner.nextPrimitive();
   ```

#### System.out

- println
- format(ctrl_str, primitives_and_literals);
   "% then number$ then flags then width then .precision then type"
