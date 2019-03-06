Attempted use of git to learn and document java features

# Lecture Questions/Misc Notes
- Will learn git in OOSD a bit
- Brand new assignments, using graphics, some competitiveness
- Friday starts now so that GF does not impact
- Use grok to learn Java, use Eclipse after that (GROK = basic stuff)
- Launch into OOSD from the getgo, no intro to java first!
- Use hackerrank, codecademy, codesignal for practice problems
- He will use questions from the grok to test us in midsem

# Java Basics

## Syntax

Simple rules:
- Java is case-sensitive
- Identifiers must be unique within their scopes
- whitespace doesn't affect interpretations; semi-colon is necessary
- Cannot use keywords for identifiers; must start with alphabetical or underscrores
- Java entirely uses pointers
- Conflicting names --> preference is always given to local variables (e.g. arguments)

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

#### Arithmetic and Logic Operators
```java
// + concatenates string representations of objects
"1 + 1 = " + 1 + 1 // 1 + 1 = 11
"1 + 1 = " + (1 + 1) // 1 + 1 = 2. This is due to precedence of ()
null // "no object here"
1 && 0 // evaluates to 1
1 || 0 // evaluates to 1
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

### Getters & Setters

### Inheritance

### Abstract Classes

### Polymorphism

### Enums

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
