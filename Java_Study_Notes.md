# Java Study Notes - Complete Guide

**Focus: Exam Preparation & Key Concepts**  
**Total Modules:** 16 + 11 Tutorial Labs  
**Total Topics:** UML Diagrams (Use Case & Class) + All Java Concepts  
**Last Updated:** March 1, 2026

---

## Table of Contents

1. [UML Diagrams](#uml-diagrams)
   - [Use Case Diagrams](#use-case-diagrams)
   - [Class Diagrams](#class-diagrams)
2. [Tutorial Lab Exercises](#tutorial-lab-exercises)
3. [Module 1: Basic Java Concepts](#module-1-basic-java-concepts)
4. [Module 2: OOP Fundamentals](#module-2-oop-fundamentals)
5. [Module 3: GUI Programming](#module-3-gui-programming)
6. [Module 4: Advanced OOP](#module-4-advanced-oop)
7. [Module 5: Specialized Topics](#module-5-specialized-topics)
8. [Module 6: Advanced Projects](#module-6-advanced-projects)
9. [Quick Reference Cheat Sheet](#quick-reference-cheat-sheet)
10. [Common Exam Questions](#common-exam-questions)

---

## UML Diagrams

### Use Case Diagrams

#### 🔑 What is a Use Case Diagram?

- Used for describing a set of user scenarios
- Shows relationships between actors and use cases in a system
- Used for capturing user requirements
- Works like a contract between end user and software developers

#### 🔑 Key Elements

**1. Actors**
- A role that a user plays with respect to the system
- Includes:
  - Human users
  - Other systems (external systems needing information)
  - Inanimate physical objects (e.g., robot)
- Examples: Customer, Clerk, Maintenance Man, Administrator
- **Must be named as singular** (e.g., "student" NOT "students")

**2. Use Cases**
- A set of scenarios that describe an interaction between a user and a system
- **MUST begin with a VERB** (e.g., generate report, withdraw cash, place a call)
- Sequence of use cases shows timing of events/operations
- Examples: Cancel Room, Print Receipt, Transfer Funds

**3. System Boundary**
- Rectangle representing the boundary between actors and the system
- Shows which functionality is inside the system scope

#### 🔑 Types of Relationships

**1. Association**
- Communication between an actor and a use case
- Represented by a **solid line**
- No arrow head needed

**2. Generalization**
- Relationship between one general use case and a special use case
- Used for defining special alternatives
- Represented by a line with a **triangular arrow head pointing toward the parent use case**
- Example: Special payment methods inheriting from general payment use case

**3. Include (<<include>>)**

**Symbol:** Dotted line labeled `<<include>>`
**Direction:** Arrow points from **base use case** to **included use case**

**When to Use:**
- When a chunk of behavior is similar across more than one use case
- Use "include" instead of copying the description

**Key Characteristics:**
- Behavior of included use case is part of base use case
- Base use case is **incomplete without** the included use case
- Included use case is **not optional** - it's **mandatory**

**Example:**
```
Withdraw Cash  ----<<include>>----  Print Receipt
Transfer Funds  ----<<include>>----  Print Receipt
```

**4. Extend (<<extend>>)**

**Symbol:** Dotted line labeled `<<extend>>`
**Direction:** Arrow points toward the **base use case**
**Requirements:** Base use case declares "extension points"

**When to Use:**
- When a use case adds optional behavior to another use case
- When behavior is triggered conditionally

**Key Characteristics:**
- Extending use case adds behavior to base use case
- Extending use case is **dependent on** base use case
- Extending use case is **usually optional** or triggered conditionally
- Base use case must be **meaningful on its own**
- Base use case should be **independent** and not rely on extending use case

**Example:**
```
Send Message  ----<<extend>>----  Place a Call
(when user selects message option)
```

#### 🔑 Include vs Extend Comparison

| Aspect | <<include>> | <<extend>> |
|--------|-------------|-----------|
| Purpose | Reuse common behavior | Add optional behavior |
| Mandatory? | Yes (required) | No (optional) |
| Dependency | Base depends on included | Extending depends on base |
| Base completeness | Incomplete without included | Meaningful on its own |
| Arrow direction | Base → Included | Extending → Base |

#### 🔑 Guidelines and Best Practices

1. **Use Case MUST always begin with a verb** (e.g., "generate report" not "report")
2. **Avoid showing communication between actors**
3. **Actors should be named as singular** (e.g., "student" NOT "students")
4. **Do NOT show workflow** in a use case diagram; only depict system functionality
5. **Avoid showing include and extends** as much as possible unless necessary
6. **KISS – Keep It Small and Simple**

#### 🔑 Use Case Specification Format

- **Use Case**: Name of the use case
- **Brief Description**: What the use case does
- **Actors**: Who participates
- **Preconditions**: What must be true before use case starts
- **Main Flow**: Step-by-step normal sequence
- **Alternative Flows**: Alternative scenarios and exceptions

#### 🔑 Example: ATM System

**Actors:**
- Customer
- Maintenance Man

**Use Cases:**
- Withdraw Cash
- Print Receipt
- Pay Bills
- Transfer Funds
- Restock Paper

**Relationships:**
```
Customer  ----  Withdraw Cash
Withdraw Cash  ----<<include>>----  Print Receipt
Customer  ----  Transfer Funds
Transfer Funds  ----<<include>>----  Print Receipt
Maintenance Man  ----  Restock Paper
```

#### 📝 Exam Points

- Know when to use <<include>> vs <<extend>>
- Remember use cases must start with verbs
- Understand actors represent roles, not specific people
- Know association vs generalization vs include vs extend
- Remember: Include = mandatory, Extend = optional

---

### Class Diagrams

#### 🔑 What is a Class Diagram?

- Used for describing **structure and behavior** in the use cases
- Provides a conceptual model of the system in terms of **entities and their relationships**
- Used for requirement capture, end-user interaction
- Detailed class diagrams are used by developers
- Models the **static structure** of a system
- Shows relationships between classes, objects, attributes, and operations

#### 🔑 Class Structure

```
+-------------------+
|    Class Name     |
+-------------------+
| - privateAttr     |
| # protectedAttr   |
| + publicAttr      |
+-------------------+
| + publicMethod()  |
| # protectedMethod()|
| - privateMethod() |
+-------------------+
```

#### 🔑 Visibility Modifiers

| Symbol | Modifier | Visibility |
|--------|----------|------------|
| `+` | `public` | Visible to any class |
| `-` | `private` | Visible only to own class |
| `#` | `protected` | Visible to own and child classes |
| `~` | `default` | Visible to classes in same package |

#### 🔑 Attributes Format

`Visibility attributeName : DataType`

**Examples:**
- `+ Age : Integer`
- `- Weight : Float`
- `# Name : String`
- `+ isActive : Boolean`

#### 🔑 Methods Format

`Visibility methodName(parameters) : ReturnType`

**Examples:**
- `+ Get_Name() : String`
- `# Set_Name(String) : void`
- `~ Speak(String) : void`
- `+ Calculate(int x, int y) : double`

#### 🔑 Types of Relationships

**1. Association**

**Purpose:** Represents relationship between instances of classes
**Symbol:** Solid line
**Components:**
- Role names (e.g., "enrolls", "teaches")
- Multiplicity (e.g., 1, *, 0..1, 1..*)
- Navigability (unidirectional, bidirectional)

**Examples:**
```
Student 1 -------- * Course
           enrolls

Student 1 ---- 1..* Lecturer
         teaches
```

**2. Aggregation**

**Purpose:** Shows that a class **CAN BE PART OF** another class
**Symbol:** Hollow diamond on container side
**Type:** Container-Containee relationship
**Independence:** Containee **can exist independently** of the container

**Key Characteristics:**
- May form "part of" the aggregate
- May not be essential to it
- Can exist independent of the aggregate
- Multiple owners possible
- Parts can outlive container

**Examples:**
- Bag of Apples (apples can exist without bag)
- Restaurant has Customers (customers exist without restaurant)
- Car has Tyres (tyres can exist without car)
- Department has Employees

**Notation:**
```
◇-------------------  Container
                     |
                     | 1
                     |
                     | *
                     |
                Containee
```

**3. Composition**

**Purpose:** Shows that a class **BELONGS TO** another class
**Symbol:** Filled diamond on whole side
**Type:** Whole-Part relationship
**Independence:** Part **cannot exist independently** of the whole

**Key Characteristics:**
- Components have only one owner
- Components cannot exist independent of their owner
- Components live or die with their owner
- Parts cannot outlive container

**Examples:**
- Human Body has Kidneys (kidneys can't exist without body)
- Book has Pages (pages can't exist without book)
- Automobile has Engine and Transmission
- House has Rooms

**Notation:**
```
◆-------------------  Whole
                     |
                     | 1
                     |
                     | *
                     |
                     Part
```

**4. Aggregation vs Composition**

| Aspect | Aggregation | Composition |
|--------|-------------|-------------|
| Strength | Weaker | Stronger |
| Independence | Parts can exist independently | Parts cannot exist independently |
| Ownership | Multiple owners possible | Single owner only |
| Lifecycle | Parts can outlive container | Parts die with container |
| Diamond | Hollow (◇) | Filled (◆) |
| Example | Bag of Apples | Book with Pages |
| Relationship | "has-a" (weak) | "owns-a" (strong) |

**5. Generalization (Inheritance)**

**Purpose:** Expresses **parent/child relationship** among related classes
**Symbol:** Solid line with **hollow triangular arrow pointing to parent**
**Keywords:** `extends` in Java

**Key Characteristics:**
- Child Class CAN inherit attributes and methods of Parent Class
- Parent Class CANNOT inherit attributes and methods of Child Class
- Child Class inherits **PUBLIC and PROTECTED** attributes and methods
- Child Class **WILL NOT inherit PRIVATE** attributes and methods
- Used for abstracting details in several layers

**Examples:**
```
Customer
  /   \
CorporateCustomer  PersonalCustomer

Employee
  /   \
Faculty   Staff
 /   \
FullTime  PartTime
```

**Notation:**
```
Child  ----△----  Parent
```

**6. Realization**

**Purpose:** Relationship between an interface and a class that implements it
**Symbol:** Dashed line with hollow triangular arrow pointing to interface
**Keywords:** `implements` in Java
**Requirement:** Class must implement all methods defined in the interface

**Example:**
```
Circle  ----▱----  Shape
```

**7. Dependency**

**Purpose:** One class depends on another (uses it)
**Symbol:** Dashed line with open arrow
**Type:** Weakest relationship type
**Usage:** Temporary relationships, method parameters

#### 🔑 Multiplicity Indicators

| Notation | Meaning | Example |
|----------|---------|---------|
| `1` | Exactly one | One student has one student ID |
| `*` or `0..*` | Zero or more | Department has 0+ employees |
| `1..*` | One or more | Student must take 1+ courses |
| `0..1` | Zero or one | Person can have 0 or 1 spouse |
| `m..n` | Between m and n | Classroom has 20-40 students |
| `n` | Specific number | Car has exactly 4 tyres |

#### 🔑 Example: Complete Class Diagram

```
+-----------+    1..*    +----------+    1    +------------+
|  Customer |-----------|   Order   |--------| OrderLine  |
+-----------+            +----------+        +------------+
| -name     |            |-dateRcvd |        |-quantity   |
| -address  |            |-isPrepaid|        |-price      |
| +credit() |            |-number   |        |-satisfied  |
+-----------+            +---------+        +------------+
     ^                                       1    *
     |                                            |
  --|--------------------------------------------|--
     |                                            |
+-------------+                             +------------+
|CorporateCust|                             |  Product   |
+-------------+                             +------------+
|-contactName |                             |-name       |
|-creditRating|                             |-price      |
|-creditLimit |                             |-description|
|+remind()    |                             |+getDetails()|
|+billForMonth()|                          +------------+
+-------------+

Relationships:
- Customer 1..* ---- 1 Order (Association)
- Order 1 ---- * OrderLine (Composition)
- OrderLine * ---- 1 Product (Association)
- CorporateCustomer --|> Customer (Generalization)
```

#### 🔑 Constraints

- Written inside braces `{ }`
- Specify conditions or rules
- Example: `{if Order.customer.creditRating is "poor", then Order.isPrepaid must be true}`

#### 📝 Exam Points

- Know difference between aggregation and composition (lifecycle dependency)
- Understand multiplicity notation
- Remember visibility symbols
- Know when to use generalization vs association
- Understand composition = strong ownership, aggregation = weak ownership
- Know that generalization uses `extends`, realization uses `implements`

---

## Tutorial Lab Exercises

### Lab 1 – Introduction to Java Programming

**Main Topic:** Basic Java program structure and compilation

**Key Exercises:**
- Create, compile, and run a basic Java program (Welcome.java)
- Understand Java case sensitivity (main vs Main, Welcome vs welcome)
- Understand project structure in NetBeans IDE
- Difference between "Run Project" and "Run File"

**Exam Focus:**
- Java program structure (class, main method)
- Compilation (javac) and execution (java) commands
- Case sensitivity in Java
- IDE project structure understanding

---

### Lab 2 – Primitive Data Types and Operations

**Main Topic:** Data types, operators, input/output, control structures

**Key Exercises:**
- Use Scanner class for user input
- Temperature conversion (Fahrenheit to Celsius)
- Cylinder volume calculation
- Sum digits of an integer
- Uppercase to lowercase letter conversion
- ASCII code to character conversion
- Days in month calculation (leap year handling)
- Grading system with marks to grade mapping
- Array sum using for-each loop
- Tuition calculation with 5% annual increase over 10 years
- Loop control with do-while
- Future investment value calculation

**Exam Focus:**
- Scanner class usage for input
- Data type conversions
- Control structures (if-else, for, while, do-while)
- Array operations
- Mathematical formulas implementation

---

### Lab 3 – Objects and Classes

**Main Topic:** Classes, objects, constructors, getters/setters, static members

**Key Exercises:**
- Account class (UML-based) with withdraw/deposit methods
- Rectangle class with static color variable
- Fan class with constants (1=slow, 2=medium, 3=fast)
- GregorianCalendar API usage
- Time class using System.currentTimeMillis()
- Array of Time objects with toString method

**Exam Focus:**
- Class structure (attributes, methods, constructors)
- Getters and setters
- Static variables
- Object instantiation
- Java API usage (GregorianCalendar)
- Time-related programming

---

### Lab 4 – UML Modeling (Use Case Diagrams)

**Main Topic:** Use case modeling concepts

**Key Exercises:**
- Explain UML elements in a given use case diagram
- Purpose of use case modeling
- When to use <<include>> and <<extend>>
- Create use case diagram for alarm clock application
  - Display time, set hours/minutes, 12/24 hour display
  - Set one or two alarms
  - Alarm actions: sound, turn off, snooze (after pre-adjustable time)
  - Auto turn off after 2 minutes

**Exam Focus:**
- Use case diagram components
- <<include>> vs <<extend>> relationships
- Identifying actors and use cases from requirements

---

### Lab 5 – Class Diagram

**Main Topic:** Class diagrams, relationships, UML notation

**Key Exercises:**
- Draw class diagram with attributes, operations, relationships, multiplicity
- APComp scenario: Departments, offices, headquarters, managers, employees
- Analyze Java code to draw class diagram (Driver + StringContainer)
- Collector scenario: Collector → Collections (1+) → Items (2+)
- AsiaMax Airline Flight Ticket Booking System (FTBS):
  - **Task 1:** Create use case diagram
  - **Task 2:** Create class diagram with generalization and composition/aggregation
  - Actors: Administrative Clerk, Manager
  - Functions: Register customer, update/search details, book tickets, generate reports
  - Reports: monthly sales, detail customers, peak season ticket sales
  - Login required for all users

**Exam Focus:**
- Class diagram from requirements/code
- Relationships: Association, Generalization, Composition, Aggregation
- Multiplicity notation (1, *, 0..1, 1..*, etc.)
- Real-world scenario analysis

---

### Lab 6 – Inheritance and Polymorphism

**Main Topic:** Inheritance, subclasses, polymorphism, interfaces

**Key Exercises:**
- Account hierarchy: Checking (with overdraft) and Savings (no overdraft)
- Person hierarchy: Person → Employee → Faculty/Staff → FullTime/PartTime
  - Person: name, address, phone, email
  - Student: status (freshman, sophomore, junior, senior - use Enum)
  - Employee: office, salary, date-hired (MyDate class)
  - Faculty: office hours, rank
  - Staff: title, override toString
  - FullTime: fixed salary, PartTime: hourly salary
- GeometricObject implementing Comparable interface
  - Create max() method in GeometricObject
  - Find larger of two circles/cylinders
- ComparableCylinder implementing Comparable based on volume
- Colorable interface with Square class implementation
  - Square extends GeometricObject and implements Colorable
  - howToColor() method

**Exam Focus:**
- Inheritance hierarchy design
- Abstract classes vs concrete classes
- Interface implementation
- Comparable interface and compareTo()
- Polymorphism through method overriding
- Enum usage

---

### Lab 7 – Abstract Class and Interfaces

**Main Topic:** Abstract classes, interfaces, multiple inheritance through interfaces

**Key Exercises:**
- Employee salary system:
  - FullTime: monthly payment, 40 hours/week
  - PartTime: hourly payment, ≤6 hours/week
  - Assistant: not payable, 2 hours/week
- Movable interface with MovablePoint and MovableCircle
- Lab 6 Q2 modification with Resizable interface
  - ResizeableCircle class
  - TestResizableCircle program

**Exam Focus:**
- Abstract classes vs interfaces
- When to use abstract classes
- When to use interfaces
- Multiple inheritance through interfaces

---

### Lab 8 – Java GUI Development

**Main Topic:** Swing components, event handling

**Key Exercises:**
- Login form with username, password, login button, message box
- Radio buttons for background color selection (red, yellow, white, gray, green)
- Simple calculator (add, subtract, multiply, divide)
- Miles/kilometers converter with Enter key event
- Future value calculator with investment amount, interest rate, years
- JFrame form with JLabel, JTextField, JButton, JTable
  - Add: Insert row to JTable
  - Edit: Modify record in JTable
  - Delete: Remove record from JTable

**Exam Focus:**
- JFrame creation
- Swing components (JButton, JTextField, JLabel, JRadioButton, JTable)
- Event handling (ActionListener)
- JTable with DefaultTableModel
- GUI layout and components

---

### Lab 9 – File Input/Output & Exception Handling

**Main Topic:** Text file I/O, exception handling

**Key Exercises:**
- Exception handling: ArrayIndexOutOfBoundsException
- Write array to file, read back from file
- Count characters, words, lines in a file
- Read scores from file, calculate total and average
- Create ints.txt with 100 random integers, read and sort
- Loan class with IllegalArgumentException:
  - Throw if loanAmount, annualInterestRate, or numberOfYears ≤ 0

**Exam Focus:**
- try-catch blocks
- Exception types (checked vs unchecked)
- File I/O with IOException handling
- Reading/writing text files
- Scanner for file reading
- StringTokenizer usage
- Custom exception throwing

---

### Lab 10 – Object Input/Output

**Main Topic:** Binary file I/O, serialization

**Key Exercises:**
- Create binaryint.dat with 100 random integers (append mode)
- Read binaryint.dat and calculate total
- Write array (1,2,3,4,5), Date object, double 5.5 to objfile.dat
- Loan class implementing Serializable
- Create 5 Loan objects, store in loanobj.dat

**Exam Focus:**
- Binary I/O vs Text I/O
- FileOutputStream, DataOutputStream
- FileInputStream, DataInputStream
- Serialization (Serializable interface)
- ObjectOutputStream, ObjectInputStream
- Reading/writing objects to files

---

### Lab 11 – Coursework Discussion

**Main Topic:** OOP concepts review, UML diagrams

**Key Topics:**
- **Object/Class:** Java class for business domain, object instantiation
- **Inheritance:** General class to specific class
- **Encapsulation:** Data hiding (private keyword, get/set methods)
- **Abstraction:** Abstract class and abstract methods implemented by subclasses
- **Polymorphism:** Overriding and overloading methods
- **Use Case Diagram:** Actors, use cases, system boundary, association, <<include>>, <<extend>>
- **Class Diagram:**
  - Logical class (single responsibility principle)
  - Class relationships: Association, Generalization, Aggregation, Composition, Realization, Dependency
  - Data properties and operations
  - Designed for software implementation

**Exam Focus:**
- All OOP concepts (encapsulation, inheritance, polymorphism, abstraction)
- UML diagram interpretation
- Class diagram relationships
- Business domain modeling

---

## Module 1: Basic Java Concepts

### Week 01: Operators and Data Types

#### 🔑 Key Concepts to Remember

**Primitive Data Types (8 types):**
- **Integer:** `byte` (8-bit), `short` (16-bit), `int` (32-bit), `long` (64-bit)
- **Floating-point:** `float` (32-bit), `double` (64-bit)
- **Character:** `char` (16-bit Unicode)
- **Boolean:** `boolean` (true/false)

**Memory Range:**
- byte: -128 to 127
- short: -32,768 to 32,767
- int: -2³¹ to 2³¹-1 (≈ ±2 billion)
- long: -2⁶³ to 2⁶³-1 (≈ ±9 quintillion)

**Operator Categories:**
1. **Unary:** `++`, `--`, `!`, `~`
2. **Binary:** `+`, `-`, `*`, `/`, `%`
3. **Ternary:** `condition ? value1 : value2`
4. **Relational:** `==`, `!=`, `<`, `>`, `<=`, `>=`
5. **Logical:** `&&`, `||`, `!`, `&`, `|`
6. **Bitwise:** `&`, `|`, `^`, `~`, `<<`, `>>`, `>>>`

#### ⚠️ Common Mistakes to Avoid

1. **String comparison with `==`:**
   - ❌ `if (str1 == str2)` - Compares references
   - ✅ `if (str1.equals(str2))` - Compares values

2. **Integer division:**
   - `5 / 2 = 2` (not 2.5) - Use `5.0 / 2 = 2.5`

3. **Prefix vs Postfix:**
   - `++x`: Increment first, then use
   - `x++`: Use first, then increment

4. **Short-circuit evaluation:**
   - `&&` and `||` short-circuit (second operand may not execute)
   - `&` and `|` always evaluate both operands

#### 📝 Exam Points

- Know which operators have higher precedence
- Understand type promotion and casting
- Know when to use short-circuit vs non-short-circuit operators
- Remember: `char` is numeric type, can be used in arithmetic
- Bitwise operations are important for low-level programming

---

### Week 02: Object-Oriented Programming Basics

#### 🔑 Key Concepts to Remember

**Pass-by-Value (CRITICAL!):**
- Java ALWAYS passes by value
- **Primitives:** Copy of the value
- **Objects:** Copy of the reference (NOT the object itself)
- Can modify object state through reference
- Cannot change what object a variable refers to

**Object vs Primitive:**
- Primitive: Stored on stack, holds actual value
- Object: Stored on heap, reference on stack

**Object Lifecycle:**
1. **Creation:** `new ClassName()`
2. **Use:** Access fields and methods
3. **Garbage Collection:** When no references exist

#### ⚠️ Common Mistakes to Avoid

1. **Assuming objects pass by reference:**
   ```java
   void changeName(Student s) {
       s = new Student("New"); // Doesn't affect caller!
   }
   ```

2. **Not initializing object references:**
   - Uninitialized reference = `null`
   - NullPointerException if used

#### 📝 Exam Points

- Be able to trace pass-by-value scenarios
- Understand when methods can/cannot modify original data
- Know difference between `=` assignment and parameter passing

---

### Lab 02: Basic Programming Exercises

#### 🔑 Algorithms to Remember

**Sum of Digits:**
```
1. Initialize sum = 0
2. While number > 0:
   - Extract last digit: digit = number % 10
   - Add to sum: sum += digit
   - Remove last digit: number /= 10
3. Return sum
```

**Grading Scale:**
- 90-100: A
- 80-89: B
- 70-79: C
- 60-69: D
- 0-59: F

**Array Operations:**
- Initialize: `int[] arr = new int[10];`
- Access: `arr[index]` (0-based)
- Length: `arr.length` (not a method!)
- Enhanced for-loop: `for (int x : arr)`

#### 📝 Exam Points

- Know algorithm for sum of digits
- Understand array indexing (0 to length-1)
- Remember `Math.random()` returns [0.0, 1.0)
- Know how to generate random number in range: `(int)(Math.random() * range) + min`

---

## Module 2: OOP Fundamentals

### Lecture 03: Packages and Access Modifiers

#### 🔑 Access Modifier Visibility Table

| Modifier | Same Class | Same Package | Subclass | World |
|----------|------------|--------------|----------|-------|
| `public` | ✓ | ✓ | ✓ | ✓ |
| `protected` | ✓ | ✓ | ✓ | ✗ |
| default (no modifier) | ✓ | ✓ | ✗ | ✗ |
| `private` | ✓ | ✗ | ✗ | ✗ |

**Key Rules:**
- Use most restrictive modifier possible
- `private`: Internal implementation details
- `protected`: For subclass access
- `public`: API that others need

#### 📝 Exam Points

- Know which modifier allows what access
- Understand `protected` allows subclass access in different package
- Remember: Private members NOT inherited

---

### Week 04: Encapsulation and Inheritance

#### 🔑 Encapsulation Principles

**Why Encapsulate?**
- Hide internal state
- Control access to data
- Validate data in setters
- Maintain invariants

**Best Practices:**
```java
private int age;

public void setAge(int age) {
    if (age > 0 && age < 150) {
        this.age = age;
    }
}
```

#### 🔑 Inheritance Key Points

**`extends` keyword:**
- Single inheritance only (Java doesn't support multiple)
- Subclass inherits all non-private members
- Private members NOT inherited (but exist in superclass)

**`super` keyword:**
- `super()`: Call superclass constructor
- `super.method()`: Call superclass method
- `super.field`: Access superclass field

**Method Overriding:**
- Same method signature as superclass
- Use `@Override` annotation (catches errors)
- Return type can be covariant (same or subclass)

**Constructor Rules:**
1. First statement: `super()` (implicit if not written)
2. If explicit `super()` call, must be first statement
3. No-arg constructor needed for implicit `super()` call

#### ⚠️ Common Mistakes

1. **Forgetting `@Override`:**
   ```java
   public void display() { ... }  // Typo in method name
   // Should be: @Override public void display()
   ```

2. **Calling `super()` after other code:**
   ```java
   public Child() {
       int x = 5;  // ERROR! super() must be first
       super();
   }
   ```

#### 📝 Exam Points

- Know difference between overloading and overriding
- Understand constructor chaining
- Know which members are inherited
- Remember: Can't override private methods (not accessible)

---

### Lab 03: Account Class Evolution

#### 🔑 Static vs Instance Members

**Static:**
- Belongs to class, not objects
- One copy shared by all instances
- Accessed via class name: `ClassName.staticMethod()`
- Can't access instance members directly

**Instance:**
- Belongs to each object
- Each object has its own copy
- Accessed via object reference: `object.instanceMethod()`

**Static Initializer:**
```java
static {
    // Runs once when class loads
    System.out.println("Class loaded");
}
```

#### 🔑 `toString()` Override

**Purpose:** Provide meaningful string representation
**Called automatically:** When object is printed
**Best Practice:** Include all important fields

```java
@Override
public String toString() {
    return "Student[name=" + name + ", id=" + id + "]";
}
```

#### 🔑 Enum

**Benefits:**
- Type-safe constants
- Can have fields, methods, constructors
- Prevents invalid values

```java
enum Velocity {
    SLOW(1), MEDIUM(2), FAST(3);
    private final int value;
    Velocity(int value) { this.value = value; }
}
```

#### 📝 Exam Points

- Know when to use static vs instance
- Understand enum advantages over int constants
- Remember `toString()` called automatically by `print()`

---

## Module 3: GUI Programming

### Lab 07: GUI Components and Event Handling

#### 🔑 GUI Component Hierarchy

```
Component (abstract)
├── Container
│   ├── Window
│   │   └── Frame
│   └── Panel
└── Button, Label, TextField, etc.
```

#### 🔑 Essential Components

| Component | Purpose | Key Methods |
|-----------|---------|-------------|
| `JFrame` | Main window | `setSize()`, `setVisible()`, `setTitle()` |
| `JPanel` | Container for grouping | `add()`, `setLayout()` |
| `JButton` | Clickable button | `addActionListener()` |
| `JLabel` | Display text/image | `setText()`, `setText()` |
| `JTextField` | Single-line input | `getText()`, `setText()` |
| `JRadioButton` | Single selection | `ButtonGroup` to group |
| `JCheckBox` | Toggle option | `isSelected()`, `setSelected()` |
| `JTextArea` | Multi-line text | `getText()`, `append()` |

#### 🔑 Layout Managers

**BorderLayout:** 5 regions
```java
frame.add(component, BorderLayout.NORTH);  // or SOUTH, EAST, WEST, CENTER
```

**GridLayout:** Grid of equal cells
```java
panel.setLayout(new GridLayout(rows, cols));
```

**FlowLayout:** Left-to-right flow
```java
panel.setLayout(new FlowLayout());
```

#### 🔑 Event Handling

**ActionListener:** Button clicks, menu selections
```java
button.addActionListener(e -> {
    // Handle click
});
```

**ItemListener:** Checkbox/radio button state changes
```java
checkbox.addItemListener(e -> {
    // Handle state change
});
```

**MouseListener:** Mouse interactions
```java
component.addMouseListener(new MouseListener() {
    public void mouseClicked(MouseEvent e) { }
    public void mousePressed(MouseEvent e) { }
    public void mouseReleased(MouseEvent e) { }
    public void mouseEntered(MouseEvent e) { }
    public void mouseExited(MouseEvent e) { }
});
```

#### 🔑 GUI Creation Pattern

```java
1. Create JFrame
2. Set size and location
3. Set layout manager
4. Create components
5. Add event listeners
6. Add components to frame
7. Make visible (last step!)
```

#### 🔑 Color Management

**RGB Color Model:**
- Each component: 0-255
- `new Color(red, green, blue)`
- Primary colors can be mixed

**Color Combinations:**
- RED + GREEN = YELLOW
- RED + BLUE = MAGENTA
- GREEN + BLUE = CYAN
- All three = WHITE
- None = BLACK

#### 🔑 JOptionPane for Dialogs

**Message Dialog:**
```java
JOptionPane.showMessageDialog(frame, "Message");
```

**Confirm Dialog:**
```java
int result = JOptionPane.showConfirmDialog(frame, "Continue?");
// Returns: YES_OPTION, NO_OPTION, CANCEL_OPTION
```

**Input Dialog:**
```java
String input = JOptionPane.showInputDialog(frame, "Enter value:");
```

#### ⚠️ Common Mistakes

1. **Adding components after setVisible():**
   ```java
   frame.setVisible(true);
   frame.add(button);  // Won't show properly
   ```

2. **Not using ButtonGroup for radio buttons:**
   ```java
   JRadioButton r1 = new JRadioButton("A");
   JRadioButton r2 = new JRadioButton("B");
   // Can select both! Need ButtonGroup
   ```

3. **Mixing AWT and Swing:**
   - Use Swing components (prefixed with 'J')
   - Don't mix with AWT components

#### 📝 Exam Points

- Know component hierarchy
- Understand layout managers
- Remember event listener interfaces
- Know when to use JOptionPane
- Understand ButtonGroup purpose

---

## Module 4: Advanced OOP

### Week 08: Polymorphism

#### 🔑 Types of Polymorphism

**1. Compile-time (Overloading):**
```java
void display(int x) { }
void display(String s) { }
// Method selected at compile time based on parameters
```

**2. Runtime (Overriding):**
```java
class Parent { void show() { } }
class Child extends Parent { @Override void show() { } }
// Method selected at runtime based on actual object type
```

**3. Type Promotion:**
```java
int x = 10;
long y = x;  // Automatic promotion
```

#### 🔑 Upcasting vs Downcasting

**Upcasting (Always Safe):**
```java
Child child = new Child();
Parent parent = child;  // Upcast
parent.show();  // Calls Child.show() (if overridden)
```

**Downcasting (Needs instanceof):**
```java
Parent parent = new Child();
if (parent instanceof Child) {
    Child child = (Child) parent;  // Safe downcast
    child.childMethod();
}
```

**Rule:**
- Upcasting loses access to subclass-specific methods
- Downcasting requires runtime type check

#### 🔑 `instanceof` Operator

**Purpose:** Check if object is instance of class
**Returns:** `true` or `false`

```java
if (obj instanceof String) {
    String s = (String) obj;
}
```

**Usage:**
- Before downcasting
- In polymorphic code
- For type checking

#### 📝 Exam Points

- Understand method selection at compile vs runtime
- Know when to use instanceof
- Remember: Upcasting always safe, downcasting risky
- Be able to trace polymorphic method calls

---

### Week 09: Abstract Classes and Interfaces

#### 🔑 Abstract Classes

**Characteristics:**
- Cannot be instantiated
- Can have abstract and concrete methods
- Can have instance variables
- Single inheritance

**Rules:**
```java
public abstract class Shape {
    private String color;  // Instance variable OK
    
    public abstract double calculateArea();  // Abstract method
    
    public void display() {  // Concrete method
        System.out.println("Color: " + color);
    }
}
```

**When to Use:**
- Define common behavior
- Provide partial implementation
- Share code among subclasses

#### 🔑 Interfaces

**Characteristics:**
- All methods are abstract (Java 8+ allows default)
- All fields are `public static final` (constants)
- Multiple inheritance
- Define contracts

**Rules:**
```java
public interface Drawable {
    double PI = 3.14159;  // public static final
    
    void draw();  // public abstract
    
    default void print() {  // Java 8+ default method
        System.out.println("Printing...");
    }
}
```

**When to Use:**
- Define contract without implementation
- Multiple inheritance
- Unrelated classes need same behavior

#### 🔑 Abstract Class vs Interface

| Feature | Abstract Class | Interface |
|---------|----------------|-----------|
| Multiple inheritance | No | Yes |
| Instance variables | Yes | No (only constants) |
| Concrete methods | Yes | Yes (default) |
| Constructor | Yes | No |
| Purpose | Share code | Define contract |

#### 🔑 Interface Inheritance

```java
interface A { void methodA(); }
interface B extends A { void methodB(); }  // Interface extends interface

class C implements B {
    public void methodA() { }
    public void methodB() { }
}
```

#### 📝 Exam Points

- Know difference between abstract class and interface
- Understand when to use each
- Remember: Interface can extend multiple interfaces
- Class can implement multiple interfaces

---

### Lab 08: String and Array Utilities

#### 🔑 String Methods (Important!)

| Method | Purpose | Example |
|--------|---------|---------|
| `length()` | Number of characters | `"hello".length()` → 5 |
| `charAt(index)` | Character at position | `"hello".charAt(0)` → 'h' |
| `substring(start, end)` | Portion of string | `"hello".substring(1,4)` → "ell" |
| `toUpperCase()` | Convert to uppercase | `"hello".toUpperCase()` → "HELLO" |
| `toLowerCase()` | Convert to lowercase | `"HELLO".toLowerCase()` → "hello" |
| `equals(str)` | Compare values | `"a".equals("a")` → true |
| `equalsIgnoreCase(str)` | Case-insensitive compare | `"A".equalsIgnoreCase("a")` → true |
| `contains(str)` | Check if substring exists | `"hello".contains("ell")` → true |
| `replace(old, new)` | Replace substrings | `"hello".replace("l", "L")` → "heLLo" |
| `split(regex)` | Split into array | `"a,b,c".split(",")` → ["a","b","c"] |
| `trim()` | Remove whitespace | `"  hi  ".trim()` → "hi" |

#### 🔑 Arrays Utility Class

| Method | Purpose |
|--------|---------|
| `Arrays.sort(arr)` | Sort array (ascending) |
| `Arrays.binarySearch(arr, key)` | Search sorted array |
| `Arrays.equals(arr1, arr2)` | Compare arrays |
| `Arrays.fill(arr, value)` | Fill with value |
| `Arrays.toString(arr)` | Convert to string |

#### 🔑 File Reading Patterns

**Scanner (Recommended):**
```java
Scanner scanner = new Scanner(new File("file.txt"));
while (scanner.hasNextLine()) {
    String line = scanner.nextLine();
    // Process line
}
scanner.close();
```

**StringTokenizer (Legacy):**
```java
StringTokenizer st = new StringTokenizer(str, ",");
while (st.hasMoreTokens()) {
    String token = st.nextToken();
}
```

**String.split():**
```java
String[] tokens = str.split(",");
for (String token : tokens) {
    // Process token
}
```

#### 📝 Exam Points

- Know important String methods
- Understand Arrays utility methods
- Remember binary search requires sorted array
- Know difference between Scanner and StringTokenizer

---

## Module 5: Specialized Topics

### Week 10: Exception Handling

#### 🔑 Exception Hierarchy

```
Throwable
├── Error (serious problems, don't catch)
└── Exception
    ├── RuntimeException (unchecked)
    │   ├── NullPointerException
    │   ├── ArrayIndexOutOfBoundsException
    │   └── ArithmeticException
    └── Checked Exceptions
        ├── IOException
        ├── SQLException
        └── FileNotFoundException
```

#### 🔑 Checked vs Unchecked

**Checked:**
- Must be declared or caught
- Compiler enforces handling
- Example: `IOException`, `SQLException`

**Unchecked:**
- Don't need to catch
- Subclass of `RuntimeException`
- Example: `NullPointerException`, `ArithmeticException`

#### 🔑 Try-Catch-Finally

```java
try {
    // Code that might throw exception
} catch (SpecificException e) {
    // Handle specific exception
} catch (AnotherException e) {
    // Handle another exception
} finally {
    // Always executes (cleanup)
}
```

**Key Points:**
- `finally` always executes (even if exception)
- `finally` executes even if `return` statement
- Multiple catch blocks: specific before general

#### 🔑 Throwing Exceptions

**Declare:**
```java
public void readFile() throws IOException {
    // Method might throw IOException
}
```

**Throw:**
```java
public void setAge(int age) {
    if (age < 0) {
        throw new IllegalArgumentException("Age cannot be negative");
    }
}
```

**Custom Exception:**
```java
public class NotEnoughMoneyException extends Exception {
    public NotEnoughMoneyException(String message) {
        super(message);
    }
}
```

#### 🔑 Common Exceptions

| Exception | Cause | How to Fix |
|-----------|-------|------------|
| `NullPointerException` | Accessing null object | Check for null before use |
| `ArrayIndexOutOfBoundsException` | Invalid array index | Check array bounds |
| `NumberFormatException` | Invalid number format | Use try-catch or validate |
| `ArithmeticException` | Divide by zero | Check divisor |
| `ClassCastException` | Invalid casting | Use instanceof |

#### ⚠️ Common Mistakes

1. **Catching Exception too broadly:**
   ```java
   catch (Exception e) { }  // Too general!
   // Catch specific exceptions
   ```

2. **Empty catch block:**
   ```java
   catch (Exception e) { }  // Swallows errors!
   // At least log the error
   ```

3. **Not closing resources:**
   ```java
   Scanner s = new Scanner(file);
   // If exception, file not closed!
   // Use try-with-resources
   ```

#### 📝 Exam Points

- Know exception hierarchy
- Understand checked vs unchecked
- Remember `finally` always executes
- Know when to use `throws` vs `throw`

---

### Week 12: Binary I/O and Serialization

#### 🔑 Serialization

**Purpose:** Save object state to file
**Requirement:** Implement `Serializable` interface

```java
public class Student implements Serializable {
    private String name;
    private transient int password;  // Not serialized
}
```

**Key Points:**
- `Serializable` is marker interface (no methods)
- `transient` fields not serialized
- Objects must be serializable (all fields)

#### 🔑 Writing Objects

```java
ObjectOutputStream oos = new ObjectOutputStream(
    new FileOutputStream("file.dat"));
oos.writeObject(student);
oos.close();
```

#### 🔑 Reading Objects

```java
ObjectInputStream ois = new ObjectInputStream(
    new FileInputStream("file.dat"));
Student student = (Student) ois.readObject();
ois.close();
```

**Note:** Need to cast to correct type

#### 🔑 When to Use Serialization

- Save object state
- Send objects over network
- Deep copy objects
- Session management

#### 📝 Exam Points

- Understand `Serializable` is marker interface
- Know `transient` keyword
- Remember serialization is binary (not human-readable)
- Understand need for casting when reading

---

### Lab 10: Account Inheritance System

#### 🔑 Inheritance Pattern

```java
public abstract class Account {
    protected String accountNumber;
    protected double balance;
    
    public abstract void withdraw(double amount);
    
    public void deposit(double amount) {
        balance += amount;
    }
}
```

#### 🔑 Overriding for Specialized Behavior

```java
public class SavingsAccount extends Account {
    @Override
    public void withdraw(double amount) {
        if (amount <= balance) {
            balance -= amount;
        }
    }
}

public class CheckingAccount extends Account {
    private double overdraftLimit;
    
    @Override
    public void withdraw(double amount) {
        if (amount <= balance + overdraftLimit) {
            balance -= amount;
        }
    }
}
```

#### 📝 Exam Points

- Understand abstract class pattern
- Know how inheritance enables specialization
- Remember `protected` for subclass access

---

### Lab 12: Employee Management System

#### 🔑 Interface Pattern

```java
public interface Payable {
    double getSalary();
    String getName();
}
```

#### 🔑 Multiple Implementations

```java
public class FullTimeEmployee implements Payable {
    private double monthlySalary;
    
    public double getSalary() {
        return monthlySalary;
    }
}

public class PartTimeEmployee implements Payable {
    private double hourlyRate;
    private double hoursWorked;
    
    public double getSalary() {
        return hourlyRate * hoursWorked;
    }
}
```

#### 🔑 Polymorphism with Interface

```java
Payable[] employees = {new FullTimeEmployee(), new PartTimeEmployee()};

for (Payable emp : employees) {
    System.out.println(emp.getName() + ": " + emp.getSalary());
}
```

#### 📝 Exam Points

- Understand interface as contract
- Know how to implement multiple interfaces
- Remember polymorphism with interfaces

---

## Module 6: Advanced Projects

### Class Diagram: UML Relationships

#### 🔑 Relationship Types

**Association:**
- "Uses" relationship
- Weak connection
- Objects can exist independently
- Example: Student and Course

**Aggregation:**
- "Has-a" relationship
- Ownership, but independent lifecycle
- Example: Department and Employees

**Composition:**
- Strong "has-a" relationship
- Dependent lifecycle
- Child cannot exist without parent
- Example: Car and Engine

#### 🔑 UML Notation

| Relationship | Symbol | Example |
|--------------|--------|---------|
| Association | Solid line | Student — Course |
| Aggregation | Empty diamond | Department ◇— Employee |
| Composition | Filled diamond | Car ♦— Engine |
| Inheritance | Empty triangle | Dog ▲— Animal |
| Implementation | Dashed triangle | Circle ▱— Shape |

#### 📝 Exam Points

- Know difference between relationship types
- Understand lifecycle implications
- Remember: Composition = strong ownership

---

## Quick Reference Cheat Sheet

### Data Types

| Type | Size | Range | Default |
|------|------|-------|---------|
| `byte` | 8 bits | -128 to 127 | 0 |
| `short` | 16 bits | -32,768 to 32,767 | 0 |
| `int` | 32 bits | -2³¹ to 2³¹-1 | 0 |
| `long` | 64 bits | -2⁶³ to 2⁶³-1 | 0L |
| `float` | 32 bits | ±3.4e38 | 0.0f |
| `double` | 64 bits | ±1.8e308 | 0.0 |
| `char` | 16 bits | 0 to 65,535 | '\u0000' |
| `boolean` | 1 bit | true, false | false |

### Operator Precedence (Highest to Lowest)

1. `()`, `[]`, `.`
2. `++`, `--`, `!`, `~`
3. `*`, `/`, `%`
4. `+`, `-`
5. `<<`, `>>`, `>>>`
6. `<`, `>`, `<=`, `>=`, `instanceof`
7. `==`, `!=`
8. `&`
9. `^`
10. `|`
11. `&&`
12. `||`
13. `?:` (ternary)
14. `=`, `+=`, `-=`, `*=`, `/=`, `%=`

### Access Modifiers

| Modifier | Class | Package | Subclass | World |
|----------|-------|---------|----------|-------|
| `public` | ✓ | ✓ | ✓ | ✓ |
| `protected` | ✓ | ✓ | ✓ | ✗ |
| default | ✓ | ✓ | ✗ | ✗ |
| `private` | ✓ | ✗ | ✗ | ✗ |

### UML Visibility Symbols

| Symbol | Modifier | Visibility |
|--------|----------|------------|
| `+` | `public` | Visible to any class |
| `-` | `private` | Visible only to own class |
| `#` | `protected` | Visible to own and child classes |
| `~` | `default` | Visible to classes in same package |

### UML Multiplicity Notation

| Notation | Meaning | Example |
|----------|---------|---------|
| `1` | Exactly one | One student has one student ID |
| `*` or `0..*` | Zero or more | Department has 0+ employees |
| `1..*` | One or more | Student must take 1+ courses |
| `0..1` | Zero or one | Person can have 0 or 1 spouse |
| `m..n` | Between m and n | Classroom has 20-40 students |
| `n` | Specific number | Car has exactly 4 tyres |

### Use Case Diagram Relationships

| Relationship | Symbol | Purpose |
|--------------|--------|---------|
| Association | Solid line | Actor interacts with use case |
| Generalization | Line with △ | Special use case inherits from general |
| Include | Dotted line <<include>> | Mandatory reuse of use case |
| Extend | Dotted line <<extend>> | Optional extension of use case |

### Class Diagram Relationships

| Relationship | Symbol | Diamond | Java Keyword | Lifecycle |
|--------------|--------|---------|--------------|-----------|
| Association | Solid line | None | - | Independent |
| Aggregation | Solid line | Hollow (◇) | - | Independent |
| Composition | Solid line | Filled (◆) | - | Dependent |
| Generalization | Solid line with △ | None | `extends` | Independent |
| Realization | Dashed line with ▱ | None | `implements` | Independent |
| Dependency | Dashed line | None | - | Independent |

### Aggregation vs Composition

| Aspect | Aggregation | Composition |
|--------|-------------|-------------|
| Diamond | Hollow (◇) | Filled (◆) |
| Strength | Weak (has-a) | Strong (owns-a) |
| Independence | Parts can exist independently | Parts cannot exist independently |
| Ownership | Multiple owners possible | Single owner only |
| Lifecycle | Parts can outlive container | Parts die with container |
| Example | Bag of Apples | Book with Pages |
| Relationship | "can be part of" | "belongs to" |

### String vs StringBuilder

| Feature | String | StringBuilder |
|---------|--------|---------------|
| Immutable | Yes | No |
| Thread-safe | Yes | No |
| Performance | Slow for concatenation | Fast for concatenation |
| Usage | Constant strings | Dynamic strings |

### Collection Framework

| Interface | Implementation | Ordered | Duplicates | Null Values |
|-----------|----------------|---------|------------|------------|
| `List` | `ArrayList` | Yes | Yes | Yes |
| `List` | `LinkedList` | Yes | Yes | Yes |
| `Set` | `HashSet` | No | No | One null |
| `Set` | `TreeSet` | Yes (sorted) | No | No |
| `Map` | `HashMap` | No | No (keys) | One null key |
| `Map` | `TreeMap` | Yes (sorted) | No (keys) | No null key |

### Common Exceptions

| Exception | Cause | Prevention |
|-----------|-------|------------|
| `NullPointerException` | Null reference | Check for null |
| `ArrayIndexOutOfBoundsException` | Invalid index | Validate index |
| `ClassCastException` | Invalid cast | Use instanceof |
| `NumberFormatException` | Invalid number format | Try-catch or validate |
| `IllegalArgumentException` | Invalid argument | Validate input |
| `ArithmeticException` | Math error (e.g., /0) | Check divisor |
| `FileNotFoundException` | File not found | Check file exists |
| `IOException` | I/O error | Use try-catch |

### GUI Components Quick Reference

```java
// JFrame
JFrame frame = new JFrame("Title");
frame.setSize(400, 300);
frame.setLocationRelativeTo(null);
frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
frame.setLayout(new BorderLayout());
frame.setVisible(true);

// Button
JButton button = new JButton("Click");
button.addActionListener(e -> {
    // Handle click
});

// Label
JLabel label = new JLabel("Text");

// TextField
JTextField field = new JTextField(20);
String text = field.getText();

// Radio Buttons
JRadioButton rb1 = new JRadioButton("Option 1");
JRadioButton rb2 = new JRadioButton("Option 2");
ButtonGroup group = new ButtonGroup();
group.add(rb1);
group.add(rb2);

// Checkbox
JCheckBox cb = new JCheckBox("Check me");
boolean checked = cb.isSelected();

// JOptionPane
JOptionPane.showMessageDialog(frame, "Message");
String input = JOptionPane.showInputDialog(frame, "Input:");
int result = JOptionPane.showConfirmDialog(frame, "Confirm?");
```

### File I/O Patterns

```java
// Reading text file
try (Scanner scanner = new Scanner(new File("file.txt"))) {
    while (scanner.hasNextLine()) {
        String line = scanner.nextLine();
    }
} catch (IOException e) {
    e.printStackTrace();
}

// Writing text file
try (PrintWriter writer = new PrintWriter(new FileWriter("file.txt"))) {
    writer.println("Line 1");
    writer.println("Line 2");
} catch (IOException e) {
    e.printStackTrace();
}

// Serialization (write)
try (ObjectOutputStream oos = new ObjectOutputStream(
        new FileOutputStream("file.dat"))) {
    oos.writeObject(object);
} catch (IOException e) {
    e.printStackTrace();
}

// Serialization (read)
try (ObjectInputStream ois = new ObjectInputStream(
        new FileInputStream("file.dat"))) {
    Object obj = ois.readObject();
    MyClass obj = (MyClass) obj;
} catch (IOException | ClassNotFoundException e) {
    e.printStackTrace();
}
```

---

## Common Exam Questions

### Question 1: Use Case Diagram - Include vs Extend

**Q:** When should you use <<include>> vs <<extend>> in a use case diagram?

**A:**
- **<<include>>:** Use when a use case always needs another use case (mandatory)
  - Example: "Withdraw Cash" includes "Print Receipt" - every withdrawal needs a receipt
  - Arrow points from base to included use case
  - Base is incomplete without included use case

- **<<extend>>:** Use when a use case optionally adds behavior to another (optional/conditional)
  - Example: "Send SMS" extends "Place Call" when user chooses to send message instead
  - Arrow points from extending to base use case
  - Base is meaningful on its own

---

### Question 2: Class Diagram - Aggregation vs Composition

**Q:** What is the difference between aggregation and composition? Give examples.

**A:**

**Aggregation (◇ - hollow diamond):**
- "has-a" relationship (weak)
- Parts can exist independently of the whole
- Multiple owners possible
- Parts can outlive container
- Example: Bag of Apples (apples exist without bag)

**Composition (◆ - filled diamond):**
- "owns-a" relationship (strong)
- Parts cannot exist independently of the whole
- Single owner only
- Parts die with container
- Example: Book with Pages (pages cannot exist without book)

**Key Difference:** Lifecycle dependency - composition parts depend on container, aggregation parts don't.

---

### Question 3: Class Diagram - Multiplicity

**Q:** What do these multiplicity notations mean?
- 1
- *
- 0..1
- 1..*
- 2..5

**A:**
- `1`: Exactly one
- `*`: Zero or more (0..*)
- `0..1`: Zero or one (optional)
- `1..*`: One or more (at least one)
- `2..5`: Between 2 and 5 (inclusive)

---

### Question 4: UML to Java - Generalization

**Q:** Convert this UML relationship to Java code:
```
Customer
  /   \
CorporateCustomer  PersonalCustomer
```

**A:**
```java
public class Customer {
    private String name;
    private String address;
    // getters and setters
}

public class CorporateCustomer extends Customer {
    private String contactName;
    private double creditLimit;
    // additional methods
}

public class PersonalCustomer extends Customer {
    private String creditCardNumber;
    // additional methods
}
```

**Key Points:**
- Use `extends` keyword
- Inherits public/protected members
- Private members not inherited

---

### Question 5: UML to Java - Realization

**Q:** Convert this UML relationship to Java code:
```
Shape  ----▱----  Circle
```

**A:**
```java
public interface Shape {
    double calculateArea();
    void draw();
}

public class Circle implements Shape {
    private double radius;
    
    public Circle(double radius) {
        this.radius = radius;
    }
    
    @Override
    public double calculateArea() {
        return Math.PI * radius * radius;
    }
    
    @Override
    public void draw() {
        System.out.println("Drawing circle with radius " + radius);
    }
}
```

**Key Points:**
- Use `implements` keyword
- Class must implement all interface methods
- Can implement multiple interfaces

---

### Question 6: Identify Relationship Type

**Q:** Identify the relationship type for each scenario:
1. Student enrolls in Course
2. Human Body has Kidneys
3. Employee works for Department
4. Car has Engine
5. Bag contains Apples

**A:**
1. **Association** - Student and Course are independent
2. **Composition** - Kidneys cannot exist without Body (filled diamond)
3. **Aggregation** - Employee can work for different departments or none (hollow diamond)
4. **Composition** - Engine cannot exist without Car (filled diamond)
5. **Aggregation** - Apples can exist without Bag (hollow diamond)

---

### Question 7: Pass-by-Value

**Q:** What does this code print?
```java
public class Test {
    public static void main(String[] args) {
        StringBuilder sb = new StringBuilder("Hello");
        change(sb);
        System.out.println(sb);
    }
    
    static void change(StringBuilder s) {
        s = new StringBuilder("World");
    }
}
```

**A:** "Hello"
**Explanation:** Java passes by value. The reference `s` is copied, and reassigning it doesn't affect the original `sb`.

---

### Question 2: Method Overriding

**Q:** Which method is called?
```java
class Parent {
    void show() { System.out.println("Parent"); }
}

class Child extends Parent {
    @Override
    void show() { System.out.println("Child"); }
}

public class Test {
    public static void main(String[] args) {
        Parent p = new Child();
        p.show();
    }
}
```

**A:** "Child"
**Explanation:** Runtime polymorphism. The actual object type determines which method is called.

---

### Question 3: String Comparison

**Q:** What is the output?
```java
String s1 = new String("Hello");
String s2 = new String("Hello");
System.out.println(s1 == s2);
System.out.println(s1.equals(s2));
```

**A:**
```
false
true
```
**Explanation:** `==` compares references (different objects), `equals()` compares values.

---

### Question 4: Array Index

**Q:** What happens?
```java
int[] arr = {1, 2, 3};
System.out.println(arr[3]);
```

**A:** `ArrayIndexOutOfBoundsException`
**Explanation:** Arrays are 0-indexed, so valid indices are 0-2.

---

### Question 5: Static vs Instance

**Q:** What is the output?
```java
class Counter {
    static int count = 0;
    
    Counter() {
        count++;
    }
}

public class Test {
    public static void main(String[] args) {
        Counter c1 = new Counter();
        Counter c2 = new Counter();
        System.out.println(Counter.count);
    }
}
```

**A:** 2
**Explanation:** Static variable is shared among all instances. Each constructor increments it.

---

### Question 6: Exception Handling

**Q:** What is printed?
```java
public class Test {
    public static void main(String[] args) {
        try {
            System.out.println(1);
            int x = 10 / 0;
            System.out.println(2);
        } catch (ArithmeticException e) {
            System.out.println(3);
        } finally {
            System.out.println(4);
        }
        System.out.println(5);
    }
}
```

**A:** 1 3 4 5
**Explanation:** Exception occurs at division, catch handles it, finally always executes.

---

### Question 7: Inheritance and Constructors

**Q:** What is printed?
```java
class Parent {
    Parent() {
        System.out.println("Parent");
    }
}

class Child extends Parent {
    Child() {
        System.out.println("Child");
    }
}

public class Test {
    public static void main(String[] args) {
        new Child();
    }
}
```

**A:**
```
Parent
Child
```
**Explanation:** Superclass constructor called first (implicit `super()`).

---

### Question 8: instanceof

**Q:** What is the output?
```java
class Parent {}
class Child extends Parent {}

public class Test {
    public static void main(String[] args) {
        Parent p = new Child();
        Child c = new Child();
        
        System.out.println(p instanceof Parent);
        System.out.println(p instanceof Child);
        System.out.println(c instanceof Parent);
        System.out.println(c instanceof Child);
    }
}
```

**A:**
```
true
true
true
true
```
**Explanation:** `instanceof` checks actual object type, not reference type.

---

### Question 9: Integer Division

**Q:** What is the result?
```java
int x = 5 / 2;
double y = 5.0 / 2;
```

**A:**
```
x = 2
y = 2.5
```
**Explanation:** Integer division truncates. Use double for precise division.

---

### Question 10: Abstract Classes

**Q:** Can you create an object of this class?
```java
public abstract class Shape {
    public abstract double calculateArea();
}
```

**A:** No
**Explanation:** Abstract classes cannot be instantiated. You must create a concrete subclass.

---

## Final Exam Preparation Checklist

### ✅ UML Diagrams (HIGH PRIORITY - 40-50% of exam)
- [ ] Understand use case diagram components (actors, use cases, system boundary)
- [ ] Know when to use <<include>> vs <<extend>>
- [ ] Remember use cases MUST begin with verbs
- [ ] Understand class diagram elements (classes, attributes, methods)
- [ ] Know visibility symbols (+, -, #, ~)
- [ ] Understand multiplicity notation (1, *, 0..1, 1..*, m..n)
- [ ] Know difference between aggregation and composition
- [ ] Understand relationship types and their symbols
- [ ] Be able to draw diagrams from requirements
- [ ] Be able to convert diagrams to Java code

### ✅ Tutorial Lab Exercises
- [ ] **Lab 1:** Java program structure, compilation, case sensitivity
- [ ] **Lab 2:** Data types, operators, Scanner, control structures, arrays
- [ ] **Lab 3:** Classes, objects, constructors, getters/setters, static members
- [ ] **Lab 4:** Use case diagrams, <<include>> vs <<extend>>
- [ ] **Lab 5:** Class diagrams, relationships, multiplicity
- [ ] **Lab 6:** Inheritance, polymorphism, interfaces, Comparable
- [ ] **Lab 7:** Abstract classes vs interfaces, multiple inheritance
- [ ] **Lab 8:** GUI components, event handling, JTable
- [ ] **Lab 9:** File I/O, exception handling, Scanner
- [ ] **Lab 10:** Binary I/O, serialization, ObjectOutputStream
- [ ] **Lab 11:** OOP concepts review, UML diagrams

### ✅ Fundamentals
- [ ] Know all primitive data types and their sizes
- [ ] Understand operator precedence
- [ ] Know type promotion and casting rules
- [ ] Understand pass-by-value (primitives vs objects)
- [ ] Know when to use `==` vs `equals()`

### ✅ OOP Concepts
- [ ] Understand encapsulation and access modifiers
- [ ] Know inheritance rules and `super` keyword
- [ ] Understand method overriding vs overloading
- [ ] Know polymorphism (runtime vs compile-time)
- [ ] Understand upcasting and downcasting
- [ ] Know when to use abstract classes vs interfaces

### ✅ Arrays and Collections
- [ ] Know array indexing (0 to length-1)
- [ ] Understand enhanced for-loop
- [ ] Know Arrays utility methods
- [ ] Understand common collection classes

### ✅ Exception Handling
- [ ] Know exception hierarchy
- [ ] Understand checked vs unchecked exceptions
- [ ] Know try-catch-finally behavior
- [ ] Understand when to use `throws` vs `throw`

### ✅ GUI Programming
- [ ] Know common Swing components
- [ ] Understand layout managers
- [ ] Know event listener interfaces
- [ ] Understand ButtonGroup for radio buttons
- [ ] Know JOptionPane usage

### ✅ I/O and Serialization
- [ ] Understand file reading patterns
- [ ] Know serialization requirements
- [ ] Understand `transient` keyword
- [ ] Know when to use serialization

### ✅ Best Practices
- [ ] Know naming conventions
- [ ] Understand when to use static vs instance
- [ ] Know how to override `toString()`
- [ ] Understand enum advantages
- [ ] Know when to use encapsulation

---

## Study Tips

1. **Practice Coding:** Don't just read - write code!
2. **Understand, Don't Memorize:** Focus on "why" not just "what"
3. **Trace Code:** Walk through code line by line
4. **Write Examples:** Create your own examples for concepts
5. **Review Common Mistakes:** Learn from typical errors
6. **Use Diagrams:** Draw UML for OOP concepts
7. **Teach Others:** Explaining helps you understand better

### 🎯 UML Diagram Tips (CRITICAL for Exam)
1. **Memorize Symbols:** Know all relationship symbols (◇, ◆, ▷, ▱, etc.)
2. **Practice Drawing:** Draw use case and class diagrams from scenarios
3. **Understand Multiplicity:** Know 1, *, 0..1, 1..*, m..n
4. **Distinguish Include vs Extend:** Include = mandatory, Extend = optional
5. **Distinguish Aggregation vs Composition:** Aggregation = independent, Composition = dependent
6. **Convert Both Ways:** Practice diagrams → Java code AND Java code → diagrams
7. **Remember Visibility:** + (public), - (private), # (protected), ~ (default)

### 📝 Tutorial Lab Tips
1. **Focus on Labs 4-7:** These contain UML diagrams and OOP fundamentals
2. **Practice All 11 Labs:** Each lab has unique concepts
3. **Understand Requirements:** Read carefully before drawing diagrams
4. **Identify Actors:** Find all external entities interacting with system
5. **Identify Use Cases:** Find all system functions (MUST start with verbs)
6. **Identify Relationships:** Determine relationships between classes
7. **Check Multiplicity:** Determine how many objects relate to each other

### 📚 Exam Day Strategy
1. **Prioritize Diagram Questions:** These are worth 40-50% of marks
2. **Read Requirements Carefully:** Don't miss any details
3. **Draw Neat Diagrams:** Clear labels and proper symbols
4. **Show Your Work:** Explain your reasoning for relationships
5. **Time Management:** Don't spend too long on one question
6. **Review:** Check for missing elements in diagrams

---

**Good luck with your studies! 📚✨**

---

*This study guide covers all 16 modules, 11 tutorial labs, UML diagrams, and exam-focused content.*