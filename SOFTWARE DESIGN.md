# Unified Modelling Language

**Definition**: A graphical ML that can be used to represent object-oriented ANALYSIS, DESIGN and IMPLEMENTATION (ADI)

### Design algorithm
1. Identify classes (nouns)
2. Identify class relationships ('is-a', 'can-do', 'has-a')
3. Refine classes/relationships
4. Develop a class diagram
5. Represent using accepted notation

## Basic representation features
- Classes consist of a name, **NON-CLASS** attributes (`privacy attribute: type = default`) and methods (`privacy method(p_type: parameter): return type`)
    - *Classes that are in the UML diagram that are associated with a class are NOT mentioned as attributes*
- Multiplicity: [10], [1..10], [1..\*], [\*], [0..1, 3..4, 6..\*]
- Privacy flags: `- ~ # +` for private, package, protected and public (NOTE: Slowly increases from 'flat' to 'plus')
- Abstract: italicised text
- Static: underlined entire line
- Interface: include `<<interface>>` just above name
- final/constant/construtor???
- NOTE: All inheritance/interface must 'come down the same line'

## Relationships

### Association
**Definition**: `has-a` relationship of containment; one class contains another class as an attribute.

**Self-association**: Contains/refers to an instance of it's own class.

**Visual format**: solid line between classes.
- Can label in middle with name, and at either end with role (e.g. `employee`, `employer`)
- No arrow: bidirectional containment (e.g. cells have prisoners and prisoners cells)
- Arrow: unidirectional; points to what is contained.

#### Subtypes of Association APPARENTLY NOT NEED TO KNOW
**Aggregation**: Both parties can exist independently, e.g. a duck and pond.
- **Visual format**: Uses a white diamond that 'points' towards the dominant. E.g. C has an address D...?

**Composition**: One class cannot exist without the other, e.g. a uni and a department.
- **Visual format**: Uses a black diamond that 'points' towards the dominant

### Generalisation (Inheritance)
**Definition**: An inheritance relationship.

**Visual format**: a white, triangular arrow with solid line. It points to the ancestor

### Realization (Interfaces)
**Definition**: An interface (can-do) relationship.

**Visual format**: a white, triangular arrow but dotted line. It points to the interface/dominant.

### Dependency
**Definition**: A weak relationship between classes implying that a change to one may impact the other.

**Visual format**: A dotted arrow (white) pointing to the dominant (who would influence the other)

# Design Patterns

**Definition**: A description of a solution to a recurrent problem in software design; published solution that allows streamline solutions without 'reinventing the wheel'.

## Features of a Pattern
- *Intent*: Goal, why it exists
- *Motivation*: Scenario highlighting a need for it.
- *Applicability*: General situations where you can use it
- *Structure*: Graphical representations (e.g. UML)
- *Participants*: List of classes/objects and their roles
- *Collaboration*: How objects in pattern interact.  **Code example of how it's used**
- *Consequences*: A description of results/side effects/tradeoffs
- *Implementation*: Example of solving a problem **Code example of implementation**
- *Known Uses*: Specific, real-world examples

### Singleton

- Note the PRIVATE CONSTRUCTOR

#### Features
- *Intent*: Ensure a class has only one instance, provide a global point of access to it.
- *Motivation*: There are cases where only one instance must be enforced with easy access to it.
- *Applicability*: Use when a single instance is required.
- *Structure*: ![alt text](LINK TO IMAGE "Singleton Structure")
- *Participants*: Singleton class.
- *Collaboration*: `X = S.getInstance()` and `Y = S.getInstance()`
- *Consequences*: Inappropriate use could result in bad design.
- *Implementation*: ![alt text](LINK TO IMAGE "Singleton Implementation")
- *Known Uses*: `CacheManager`, `PrinterSpooler`

### Template

- Note the use of `protected` in the code

#### Features
- *Intent*: Define a family of encapsulated, interchangeable algorithms ... through inheritance.
- *Motivation*: Build generic, extendable, reusable components.
- *Applicability*: Implementing invariant parts of an algorithm ONCE in an *abstract class*, allowing subclass(es) to implement the variant aspects (hook methods, underlying data structures, etc.)
- *Structure*: ![alt text](LINK TO IMAGE "Template Structure")
- *Participants*: GenericAlgorithmClass (abstract), ConcreteAlgorithm subclasses
- *Collaboration*: GenericClass implements algorithm but delegates structure-specific methods such as `swap` or `lastItem` to abstract methods. A subclass will then amongst other things, implement these abstract methods, hence 'finalising' the algorithm.
- *Consequences*: All algorithms must use the same interface (strong dependency, prevents re-use of generic methods defined in subclass of the template).
- *Implementation*: ![alt text](LINK TO IMAGE "Template Implementation?")
- *Known Uses*: Generic sorting algorithm in GenericClass, specific implementation of data structure and manipulations (DoubleSorter, IntSorter) in subclasses, that typically are not used elsewhere...?

### Strategy

#### Features..?
- *Intent*: Define a family of encapulsated, interchangeable algorithms ... through delegation.
- *Motivation*: Build generic, extendable, reusable components.
- *Applicability*: Implementing invariant parts of an algorithm ONCE (*concretely*), delegating all domain-specific aspects to an interface. An *associated Handle that implements the interface* implements the variant aspects (hook methods, underlying data structures, etc.)
- *Structure*: ![alt text](LINK TO IMAGE "Strategy Structure")
- *Participants*: ConcreteAlgorithmS class (`Context`), AlgorithmHandle interface (`Strategy`), HandleImplementer implementations of the interface (`ConcreteStrategy#`)
- *Collaboration*: `Context` fully defines the algorithm, delegates domain-specific operations to a concrete implementer of the Strategy.
- EXTRA DETAIL FOR ME: `Strategy` outlines the methods that a `Context` requires (e.g. `swap`, `setArray`, etc.). A `ConcreteStrategy` implements these methods for a specific domain (e.g. integers, doubles, texts, robots).
- *Consequences*: There is still a strong dependency on the interface, however now function implementations can be used in other contexts as they are not constrained to a algorithm-specific class (this is comparing to Strategy Pattern of course).
- *Implementation*: ![alt text](LINK TO IMAGE "Template Structure")
- *Known Uses*: Re-use of a sorting algorithm (e.g. BubbleSort) with multiple data structures that require/have use elsewhere in the code.

### Factory

**Definition**: A general technique for manufacturing objects.

**Product**: An abstract class that generalises the objects being created.

**Creator**: An abstract class that generalises objects that consume/produce products.

#### Features
- *Intent*: To generalise object creation.
- *Motivation*: Loading player objects when a game loads - players are used elsewhere in the code, and are not just a property of a 'spawn point', for example. Without this method, these sister classes would *repeat code, be poorly abstracted, and be rigid/fragile.*
- *Applicability*: When sister classes depend on/create similar objects (i.e. many things use it and create it)
- *Structure*: ![alt text](LINK TO IMAGE "Factory Structure")
- *Participants*: Abstract `Creator`, Concrete `Creator#`, Abstract `Product` and concrete `Product#`.
- *Collaboration*:
  - THEM: Concrete creators invoke the factoryMethod to produce their desired product.
  - Elaborated description for ME: `Creator` actually 'does the creation' in its concrete methods and stores the created Products, but delegates `how to create` to subclasses who choose what product subclass they create (the `factoryMethod`; usually just a `return new SpecificProduct()` call).
- *Consequences*: Object creation in superclass is **decoupled** from specific object required.
- *Implementation*: ![alt text](LINK TO IMAGE "Factory Implementation")???
- *Known Uses*:

### Observer

**Subject**: An important object whose state/change influences the decisions/actions of other classes.

**Observer**: An object that monitors the subject's state/change in order to respond/update its own.

#### Features
- *Intent*: To decouple the subject and its observers through use of publish-subscribe communication.
- *Motivation*: Use of a single object to manage a many-to-one dependency is inflexible, as it commits/couples the subject to the dependents - harder to implement, test and maintain.
- *Applicability*: Where there are many-to-one dependencies on a single object, whose state impacts the many.
- *Structure*: ![alt text](LINK TO IMAGE "Observer Structure")
- *Participants*: An abstract `Observer` class (who can `notify()`), `ConcreteObserver#` who defines/inherits how to `notify()`, and a concrete `Subject` who tracks the registered/unregistered observers and thus notifies all subscribers when necessary.
- *Collaboration*: A subject stores any subscribed observer instances and can add to/unsubscribe these observers. The subject when requested will notify() all subscribed observers.
- *Consequences*: Automatic notification, decouples subject and observer, allows event-driven programming, clearer responsibilities, allows extension (event-handling etc.)
- *Implementation*: CAN BE ABSTRACT CLASSES OR INTERFACES.
- *Known Uses*: Project 2 (the World is a subject, and Sprites/Camera observers of it; the Pylon is also a Subject)

# Software Testing and Design

## Documentation

Commenting:
- Follow Conventions
- Intended for yourself and other developers
- Really code should be self-documenting (readable without extra documentation)
- Comments should 'piece together' if all the code disappeared
- Attach to blocks of code
- Placement should be ABOVE code

### Javadoc
**Definition**: A special comment that can be compiled to HTML. Should document how to use and interact with classes, packages, methods and attributes.
- Uses *tags* `@param`, `@return` for generating specific documentation

## Design

### Symptoms of Poor Design
- Rigidity: Hard to modify; changes in one class/method cascade to others
- Fragility: Modification breaks supposedly unrelated parts
- Immobility: Cannot be decomposed into reusable modules
- Viscosity: Writing 'hacks' to preserve the design
- Complexity: Premature optimisation, un-necessary clever code
- Repetition: "Cut and Paste" code writing
- Opacity: Convoluted logic, hard to follow

### GRASP
**Definition**: A series of guidelines for assigning responsibility to classes in OOD: how to break problem down into modules with clear purpose.
- General, Responsibility, Assignment, Software, Patterns/principles
- *Cohesion*: Classes solve clear, focused problems. Aim for MAXIMUM cohesion.
- *Coupling*: Degree of interaction b/t classes, their methods, or variables. Aim for MINIMUM coupling
- *Open-Closed Principle*: Classes are open to extension, but closed to modification - a change of functionality means inheritance, not alteration to base class.
- Encapsulation, Abstraction, Polymorphism
- *Delegation*: Keeping classes focused by passing work to other classes. Computations are performed IN THE CLASS with MAXIMAL RELEVANT INFORMATION.

## Software Testing
*Unit*: Small, well-defined component of a s/w system with one, or small # of, responsibilities.
*Unit Test*: Verifying a unit's operation by testing a single-use case (I/O), intending it to fail.
- IDEA: When it comes to 'valid input' - does it to ALL the right things it is meant to? (e.g. change the board, change the right position, use the correct char, return true etc.)
- Easier to test units if components of a unit are further broken down to their simplest case via ABSTRACTION
*Unit Testing*: Identifying s/w bugs by subjecting every unit to a suite of tests.
*Manual Testing*: To test code manually, ad-hoc (with the con of not reaching all edge-cases and poor scalability)
*Automated Testing*: To test code with automated, purpose built s/w. Faster, more reliable, less human reliant.

### TestCase
*TestCase class*: Class dedicated to testing a single unit. Flag with `@Test` and title `testFUNC/testCLASS etc.`
*TestRunner class*: Class dedicated to executing tests on a unit.

```java
import static org.junit.Assert.*;
import org.junit.Test;

public class BoardTest {
    @Test
    public void testBoard() {
        Board board = new Board();
        assertEquals(board.cellIsEmpty(0, 0), true);
    }
    @Test
    public void testValidMove() {
        Board board = new Board();
        Move move = new Move(0, 0);
        assertEquals(board.isValidMove(move), true);
    }
}
```

### Software Testing Jobs
**Software QA**: Actively works to improve the development process/lifecycle. Directs software testers to conduct tests, primarily to prevent bugs.

## Event-Driven Programming
**State**: properties that defne an object/device, e.g. `active` or not.

**Event**: Created when a state is altered.

**Callback**: A method trigged by an event.

**Event-Driven Programming**: To use events and callbacks to control a program's execution flow.
- Better encapsulation of classes
- Easily add/remove behaviour to classes
- Easily add/remove additional responses
- E.g. GUIs, WebDev, Embedded Systems/Hardware

**Sequential Programming**: A program 'run' top to bottom, starting at a `main` method and concluding at its end.
- Static programs
- Constant logic
- Similar execution each time

**Polling/Sampling**: Relies on program actively enquiring about an object's state etc.
- Lot of waiting
- Lots of asking
- Same order, every time
- Cannot escape methods to deal with urgent events

### Asynchronous Programming

**Interrupt**: A signal generated by hardware/software indicating an event that needs immediate CPU attention.

**Interrupt Service Routine**: Event-handling code 'at a very low level' to respond to interrupt signals.
- Exception/error handling
- Activating a sleeping process/task
- Device drivers (mouse, keyboard)

#### Example ISR

```java
public class DistanceSensor {
    public void detectCollision() {
        ... if (danger) mainThread.interrupt();
    }
}
```

### Game Design

#### Inheritance-Based

The pitfall of a typical inheritance approach is it doesn't allow for dynamic behaviour choice. E.g. monsters that are sometimes passive and sometimes aggressive. 

#### Composition-Based (Entity-Component approach)
To break down the functionality of each object into its components, and so entities = a composition (sum) of components. This principle is a response to the large, complex inheritance hierarchies.

> Entity: Contains a list of Components; can have components added.
> Component: abstract class of abstract functionality. Can be enabled/disabled, updated, and rendered. Contains a reference to the containing Entity to allow access to its member variables/other components.
> After defining concrete components such as 'Aggressor', 'Image', create `Entity monster = new Entity(); monster.add(new Image(monster)); monster.add(new Aggressor(monster));`. 
> Also require a `<T extends Component> T getComponent()` method for Entity (which requires a `ClassCastException ignored catch` if `return (T) c` doesn't work)
> This allows reuse, easy on/off activation (prevents convoluted inheritance/interface fixes)
