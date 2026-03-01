# Java Programming Complete Study Guide

**Course:** Object-Oriented Programming with Java  
**Date:** March 1, 2026  
**Total Coverage:** 19 Sessions (10 Labs + 9 Lectures)

---

## 📚 Table of Contents

### Part 1: Fundamentals & Basics
1. [Java Language Basics](#1-java-language-basics)
2. [Control Flow & Arrays](#2-control-flow--arrays)
3. [Classes & Objects](#3-classes--objects)

### Part 2: Object-Oriented Programming
4. [Encapsulation](#4-encapsulation)
5. [Inheritance](#5-inheritance)
6. [Polymorphism](#6-polymorphism)
7. [Abstract Classes & Interfaces](#7-abstract-classes--interfaces)

### Part 3: Advanced Topics
8. [Exception Handling](#8-exception-handling)
9. [File I/O & Serialization](#9-file-io--serialization)
10. [GUI Programming](#10-gui-programming)

### Part 4: Real-World Projects
11. [Condominium Management System](#11-condominium-management-system)
12. [User Management System](#12-user-management-system)

---

## PART 1: FUNDAMENTALS & BASICS

---

## 1. Java Language Basics

### 1.1 Primitive Data Types

| Type | Size | Range | Default | Example |
|------|------|-------|---------|---------|
| **byte** | 8 bits | -128 to 127 | 0 | `byte b = 10;` |
| **short** | 16 bits | -32,768 to 32,767 | 0 | `short s = 1000;` |
| **int** | 32 bits | -2³¹ to 2³¹-1 | 0 | `int i = 100000;` |
| **long** | 64 bits | -2⁶³ to 2⁶³-1 | 0L | `long l = 100000L;` |
| **float** | 32 bits | ±3.4×10³⁸ | 0.0f | `float f = 3.14f;` |
| **double** | 64 bits | ±1.8×10³⁰⁸ | 0.0 | `double d = 3.14;` |
| **char** | 16 bits | 0 to 65,535 | '\u0000' | `char c = 'A';` |
| **boolean** | 1 bit | true/false | false | `boolean b = true;` |

### 1.2 Operators

#### Arithmetic Operators
```java
int a = 10, b = 3;
a + b;   // 13 (addition)
a - b;   // 7  (subtraction)
a * b;   // 30 (multiplication)
a / b;   // 3  (integer division)
a % b;   // 1  (remainder/modulus)
```

#### Increment/Decrement
```java
int x = 5;
x++;     // Post-increment: returns 5, then x becomes 6
++x;     // Pre-increment: x becomes 6, then returns 6
x--;     // Post-decrement: returns 6, then x becomes 5
--x;     // Pre-decrement: x becomes 5, then returns 5
```

#### Relational Operators
```java
int a = 5, b = 10;
a == b;  // false (equal)
a != b;  // true  (not equal)
a < b;   // true  (less than)
a > b;   // false (greater than)
a <= b;  // true  (less than or equal)
a >= b;  // false (greater than or equal)
```

#### Logical Operators
```java
boolean x = true, y = false;
x && y;  // false (AND - short-circuit)
x || y;  // true  (OR - short-circuit)
!x;      // false (NOT)
x & y;   // false (AND - evaluates both)
x | y;   // true  (OR - evaluates both)
```

#### Bitwise Operators
```java
int a = 5;  // Binary: 0101
int b = 3;  // Binary: 0011

a & b;   // 1  (0101 & 0011 = 0001)
a | b;   // 7  (0101 | 0011 = 0111)
a ^ b;   // 6  (0101 ^ 0011 = 0111)
~a;      // -6 (bitwise complement)
a << 1;  // 10 (left shift by 1)
a >> 1;  // 2  (right shift by 1)
```

#### Ternary Operator
```java
int age = 20;
String status = (age >= 18) ? "Adult" : "Minor";
// Result: "Adult"
```

### 1.3 Type Conversion

#### Widening (Implicit)
```java
int i = 100;
double d = i;      // int automatically converted to double
```

#### Narrowing (Explicit)
```java
double d = 10.5;
int i = (int)d;    // 10 (decimal part truncated)
```

#### String to Number
```java
String str = "123";
int num = Integer.parseInt(str);
double dnum = Double.parseDouble(str);
```

### 1.4 Input/Output

#### Console I/O with Scanner
```java
import java.util.Scanner;

Scanner input = new Scanner(System.in);

System.out.print("Enter name: ");
String name = input.nextLine();

System.out.print("Enter age: ");
int age = input.nextInt();

System.out.println("Hello " + name + ", you are " + age + " years old.");
input.close();
```

#### Dialog I/O with JOptionPane
```java
import javax.swing.JOptionPane;

String name = JOptionPane.showInputDialog(null, "Enter your name:");
JOptionPane.showMessageDialog(null, "Hello " + name + "!");
```

---

## 2. Control Flow & Arrays

### 2.1 Conditional Statements

#### if-else
```java
int score = 85;

if (score >= 90) {
    System.out.println("Grade: A");
} else if (score >= 80) {
    System.out.println("Grade: B");
} else if (score >= 70) {
    System.out.println("Grade: C");
} else {
    System.out.println("Grade: F");
}
```

#### switch-case
```java
int day = 3;
String dayName;

switch (day) {
    case 1: dayName = "Monday"; break;
    case 2: dayName = "Tuesday"; break;
    case 3: dayName = "Wednesday"; break;
    case 4: dayName = "Thursday"; break;
    case 5: dayName = "Friday"; break;
    default: dayName = "Weekend"; break;
}
```

### 2.2 Loops

#### for Loop
```java
// Known number of iterations
for (int i = 0; i < 10; i++) {
    System.out.println("Iteration: " + i);
}
```

#### while Loop
```java
// Unknown iterations, checks condition first
int i = 0;
while (i < 10) {
    System.out.println("Iteration: " + i);
    i++;
}
```

#### do-while Loop
```java
// At least one iteration
int i = 0;
do {
    System.out.println("Iteration: " + i);
    i++;
} while (i < 10);
```

#### Enhanced for Loop (for-each)
```java
int[] numbers = {1, 2, 3, 4, 5};
for (int num : numbers) {
    System.out.println(num);
}
```

### 2.3 Arrays

#### Array Declaration & Initialization
```java
// Method 1: Declare and initialize
int[] numbers = {1, 2, 3, 4, 5};

// Method 2: Declare with size
int[] numbers = new int[5];
numbers[0] = 1;
numbers[1] = 2;
// ...

// Method 3: Declare and allocate
int[] numbers = new int[]{1, 2, 3, 4, 5};
```

#### Array Operations
```java
int[] arr = {5, 2, 8, 1, 9};

// Get length
int length = arr.length;  // 5

// Access element
int first = arr[0];       // 5
int last = arr[arr.length - 1];  // 9

// Sort array
Arrays.sort(arr);         // [1, 2, 5, 8, 9]

// Find sum
int sum = 0;
for (int num : arr) {
    sum += num;
}

// Find max/min
int max = arr[0];
int min = arr[0];
for (int num : arr) {
    if (num > max) max = num;
    if (num < min) min = num;
}
```

### 2.4 Common Algorithms

#### Sum of Digits
```java
int number = 1234;
int sum = 0;

while (number != 0) {
    int digit = number % 10;  // Extract last digit
    sum += digit;             // Add to sum
    number /= 10;             // Remove last digit
}
// Result: sum = 10
```

#### Generate Random Numbers
```java
// Random number between 1 and 100
int random = (int)(Math.random() * 100) + 1;

// Using Random class
import java.util.Random;
Random rand = new Random();
int random = rand.nextInt(100) + 1;
```

---

## 3. Classes & Objects

### 3.1 Class Definition

```java
public class Car {
    // Instance variables (fields)
    private String brand;
    private String model;
    private int year;
    
    // Constructor
    public Car(String brand, String model, int year) {
        this.brand = brand;
        this.model = model;
        this.year = year;
    }
    
    // Methods
    public void start() {
        System.out.println(brand + " " + model + " is starting...");
    }
    
    public void drive() {
        System.out.println("Driving " + brand + " " + model);
    }
    
    // Getters and Setters
    public String getBrand() {
        return brand;
    }
    
    public void setBrand(String brand) {
        this.brand = brand;
    }
    
    // Override toString()
    @Override
    public String toString() {
        return brand + " " + model + " (" + year + ")";
    }
}
```

### 3.2 Creating Objects

```java
public class Main {
    public static void main(String[] args) {
        // Create objects
        Car car1 = new Car("Toyota", "Camry", 2023);
        Car car2 = new Car("Honda", "Civic", 2024);
        
        // Use objects
        car1.start();
        car1.drive();
        
        // Access properties
        System.out.println(car1.getBrand());  // Toyota
        System.out.println(car2.toString());  // Honda Civic (2024)
    }
}
```

### 3.3 Access Modifiers

| Modifier | Class | Package | Subclass | World |
|----------|-------|---------|----------|-------|
| `private` | ✓ | ✗ | ✗ | ✗ |
| (default) | ✓ | ✓ | ✗ | ✗ |
| `protected` | ✓ | ✓ | ✓ | ✗ |
| `public` | ✓ | ✓ | ✓ | ✓ |

### 3.4 Static Members

```java
public class Account {
    private int id;
    private double balance;
    private static double interestRate = 0.03;  // Shared among all instances
    private static int totalAccounts = 0;       // Counter
    
    public Account(int id, double balance) {
        this.id = id;
        this.balance = balance;
        totalAccounts++;  // Increment counter
    }
    
    // Static method
    public static void setInterestRate(double rate) {
        interestRate = rate;
    }
    
    public static int getTotalAccounts() {
        return totalAccounts;
    }
}
```

### 3.5 Enumerations

```java
public enum Velocity {
    STOPPED(0, "Stopped"),
    SLOW(1, "Slow"),
    MEDIUM(2, "Medium"),
    FAST(3, "Fast");
    
    private final int speedValue;
    private final String description;
    
    Velocity(int speedValue, String description) {
        this.speedValue = speedValue;
        this.description = description;
    }
    
    public int getSpeedValue() {
        return speedValue;
    }
    
    public String getDescription() {
        return description;
    }
}

// Usage
Velocity speed = Velocity.FAST;
System.out.println(speed.getDescription());  // Fast
```

---

## PART 2: OBJECT-ORIENTED PROGRAMMING

---

## 4. Encapsulation

### 4.1 What is Encapsulation?

Encapsulation is the bundling of data and methods that operate on that data within a single unit (class), and restricting direct access to some of an object's components.

### 4.2 Encapsulated Class Example

```java
public class BankAccount {
    // Private fields (hidden from outside)
    private String accountNumber;
    private double balance;
    private String ownerName;
    
    // Constructor
    public BankAccount(String accountNumber, String ownerName, double initialBalance) {
        this.accountNumber = accountNumber;
        this.ownerName = ownerName;
        this.balance = initialBalance;
    }
    
    // Public getters (read access)
    public String getAccountNumber() {
        return accountNumber;
    }
    
    public double getBalance() {
        return balance;
    }
    
    public String getOwnerName() {
        return ownerName;
    }
    
    // Public setters (write access with validation)
    public void setOwnerName(String ownerName) {
        if (ownerName != null && !ownerName.isEmpty()) {
            this.ownerName = ownerName;
        }
    }
    
    // Business methods (control how data is modified)
    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            System.out.println("Deposited: RM" + amount);
        } else {
            System.out.println("Invalid deposit amount");
        }
    }
    
    public void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
            System.out.println("Withdrew: RM" + amount);
        } else {
            System.out.println("Insufficient funds or invalid amount");
        }
    }
    
    @Override
    public String toString() {
        return String.format("Account: %s, Owner: %s, Balance: RM%.2f",
                           accountNumber, ownerName, balance);
    }
}
```

### 4.3 Benefits of Encapsulation

1. **Data Hiding:** Internal representation is hidden
2. **Control:** Control over how data is accessed and modified
3. **Flexibility:** Can change implementation without affecting users
4. **Maintainability:** Easier to debug and maintain

---

## 5. Inheritance

### 5.1 What is Inheritance?

Inheritance allows a class to acquire properties and methods of another class. It promotes code reuse and establishes a parent-child relationship.

### 5.2 Inheritance Example

```java
// Base class (Parent)
public class Animal {
    protected String name;
    protected int age;
    
    public Animal(String name, int age) {
        this.name = name;
        this.age = age;
    }
    
    public void eat() {
        System.out.println(name + " is eating.");
    }
    
    public void sleep() {
        System.out.println(name + " is sleeping.");
    }
    
    public void makeSound() {
        System.out.println(name + " makes a sound.");
    }
}

// Derived class (Child)
public class Dog extends Animal {
    private String breed;
    
    public Dog(String name, int age, String breed) {
        super(name, age);  // Call parent constructor
        this.breed = breed;
    }
    
    // Override parent method
    @Override
    public void makeSound() {
        System.out.println(name + " barks: Woof! Woof!");
    }
    
    // New method specific to Dog
    public void fetch() {
        System.out.println(name + " is fetching the ball!");
    }
    
    public String getBreed() {
        return breed;
    }
}

// Another derived class
public class Cat extends Animal {
    private boolean isIndoor;
    
    public Cat(String name, int age, boolean isIndoor) {
        super(name, age);
        this.isIndoor = isIndoor;
    }
    
    @Override
    public void makeSound() {
        System.out.println(name + " meows: Meow!");
    }
    
    public void scratch() {
        System.out.println(name + " is scratching!");
    }
}
```

### 5.3 Using Inheritance

```java
public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog("Buddy", 3, "Golden Retriever");
        Cat cat = new Cat("Whiskers", 2, true);
        
        // Inherited methods
        dog.eat();
        cat.sleep();
        
        // Overridden methods
        dog.makeSound();  // Buddy barks: Woof! Woof!
        cat.makeSound();  // Whiskers meows: Meow!
        
        // Specific methods
        dog.fetch();
        cat.scratch();
        
        // Access parent fields
        System.out.println(dog.name + " is " + dog.age + " years old");
    }
}
```

### 5.4 Method Overriding Rules

1. Method name must be the same
2. Parameters must be the same
3. Return type must be same or covariant
4. Access modifier must be same or less restrictive
5. Cannot override static methods
6. Use `@Override` annotation

### 5.5 The `super` Keyword

```java
public class Child extends Parent {
    public Child() {
        super();  // Call parent's no-arg constructor
    }
    
    @Override
    public void method() {
        super.method();  // Call parent's method
        // Add child-specific behavior
    }
    
    public void accessParentField() {
        int value = super.parentField;  // Access parent's field
    }
}
```

### 5.6 Types of Inheritance

```
Single Inheritance:
    Animal → Dog

Multilevel Inheritance:
    Animal → Dog → Bulldog

Hierarchical Inheritance:
        Animal
         /    \
       Dog    Cat

Multiple Inheritance (NOT supported in Java for classes):
    Parent1  Parent2
         \    /
          Child
```

---

## 6. Polymorphism

### 6.1 What is Polymorphism?

Polymorphism allows objects of different types to be treated as objects of a common type. It enables one interface to have multiple implementations.

### 6.2 Compile-Time Polymorphism (Method Overloading)

```java
public class Calculator {
    // Same method name, different parameters
    public int add(int a, int b) {
        return a + b;
    }
    
    public double add(double a, double b) {
        return a + b;
    }
    
    public int add(int a, int b, int c) {
        return a + b + c;
    }
    
    public String add(String a, String b) {
        return a + b;
    }
}

// Usage
Calculator calc = new Calculator();
System.out.println(calc.add(5, 3));           // 8
System.out.println(calc.add(5.5, 3.5));       // 9.0
System.out.println(calc.add(5, 3, 2));        // 10
System.out.println(calc.add("Hello", "World"));  // HelloWorld
```

### 6.3 Runtime Polymorphism (Method Overriding)

```java
public class Animal {
    public void makeSound() {
        System.out.println("Animal makes a sound");
    }
}

public class Dog extends Animal {
    @Override
    public void makeSound() {
        System.out.println("Dog barks");
    }
}

public class Cat extends Animal {
    @Override
    public void makeSound() {
        System.out.println("Cat meows");
    }
}

// Usage - Dynamic Method Dispatch
Animal myAnimal;

myAnimal = new Dog();
myAnimal.makeSound();  // Output: Dog barks

myAnimal = new Cat();
myAnimal.makeSound();  // Output: Cat meows
```

### 6.4 Type Casting

#### Upcasting (Implicit)
```java
Dog dog = new Dog();
Animal animal = dog;  // Upcasting (always safe)
animal.makeSound();   // Calls Dog's makeSound()
```

#### Downcasting (Explicit)
```java
Animal animal = new Dog();
Dog dog = (Dog)animal;  // Downcasting (may throw ClassCastException)
dog.makeSound();
dog.fetch();           // Dog-specific method

// Safe downcasting with instanceof
if (animal instanceof Dog) {
    Dog dog = (Dog)animal;
    dog.fetch();
}
```

### 6.5 The `instanceof` Operator

```java
Animal animal = new Dog();

if (animal instanceof Dog) {
    System.out.println("It's a Dog!");
    Dog dog = (Dog)animal;
    dog.fetch();
} else if (animal instanceof Cat) {
    System.out.println("It's a Cat!");
}
```

---

## 7. Abstract Classes & Interfaces

### 7.1 Abstract Classes

An abstract class cannot be instantiated and may contain abstract methods (methods without implementation).

```java
public abstract class Shape {
    protected String color;
    protected boolean filled;
    
    public Shape() {
        color = "white";
        filled = false;
    }
    
    public Shape(String color, boolean filled) {
        this.color = color;
        this.filled = filled;
    }
    
    // Concrete methods
    public String getColor() {
        return color;
    }
    
    public void setColor(String color) {
        this.color = color;
    }
    
    // Abstract methods (must be implemented by subclasses)
    public abstract double getArea();
    public abstract double getPerimeter();
}

// Concrete subclass
public class Circle extends Shape {
    private double radius;
    
    public Circle(double radius) {
        this.radius = radius;
    }
    
    @Override
    public double getArea() {
        return Math.PI * radius * radius;
    }
    
    @Override
    public double getPerimeter() {
        return 2 * Math.PI * radius;
    }
}

// Cannot instantiate abstract class
// Shape shape = new Shape();  // ERROR!
Shape circle = new Circle(5);  // OK
```

### 7.2 Interfaces

An interface is a contract that specifies what a class must do, but not how it does it.

```java
// Interface definition
public interface Drawable {
    void draw();
    void resize(double factor);
    
    // Constants are public, static, final by default
    double MAX_SIZE = 100.0;
    
    // Default method (Java 8+)
    default void reset() {
        System.out.println("Resetting to default size");
    }
}

// Implementing interface
public class Rectangle implements Drawable {
    private double width, height;
    
    public Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }
    
    @Override
    public void draw() {
        System.out.println("Drawing rectangle: " + width + "x" + height);
    }
    
    @Override
    public void resize(double factor) {
        width *= factor;
        height *= factor;
        System.out.println("Resized by factor: " + factor);
    }
}
```

### 7.3 Multiple Interface Implementation

```java
public interface Flyable {
    void fly();
}

public interface Swimmable {
    void swim();
}

public class Duck implements Flyable, Swimmable {
    @Override
    public void fly() {
        System.out.println("Duck is flying");
    }
    
    @Override
    public void swim() {
        System.out.println("Duck is swimming");
    }
}
```

### 7.4 Interface Inheritance

```java
public interface Animal {
    void eat();
}

public interface Mammal extends Animal {
    void giveBirth();
}

public class Dog implements Mammal {
    @Override
    public void eat() {
        System.out.println("Dog is eating");
    }
    
    @Override
    public void giveBirth() {
        System.out.println("Dog is giving birth");
    }
}
```

### 7.5 Abstract Class vs Interface

| Feature | Abstract Class | Interface |
|---------|----------------|-----------|
| Can have instance fields | Yes | No (only constants) |
| Can have constructors | Yes | No |
| Can have concrete methods | Yes | Only default methods (Java 8+) |
| Multiple inheritance | No | Yes |
| Purpose | Share code | Define contract |

---

## PART 3: ADVANCED TOPICS

---

## 8. Exception Handling

### 8.1 Exception Hierarchy

```
Throwable
├── Error (serious problems, not recoverable)
│   ├── OutOfMemoryError
│   └── StackOverflowError
└── Exception (recoverable problems)
    ├── IOException
    │   └── FileNotFoundException
    ├── RuntimeException (unchecked)
    │   ├── ArithmeticException
    │   ├── NullPointerException
    │   ├── ArrayIndexOutOfBoundsException
    │   └── NumberFormatException
    └── Other checked exceptions
```

### 8.2 Try-Catch Block

```java
try {
    // Code that may throw an exception
    int result = 10 / 0;  // ArithmeticException
} catch (ArithmeticException e) {
    // Handle specific exception
    System.out.println("Cannot divide by zero!");
} catch (Exception e) {
    // Handle general exception
    System.out.println("An error occurred: " + e.getMessage());
}
```

### 8.3 Finally Block

```java
try {
    // Code that may throw exception
    int[] arr = new int[5];
    arr[10] = 100;
} catch (ArrayIndexOutOfBoundsException e) {
    System.out.println("Array index out of bounds");
} finally {
    // Always executes, regardless of exception
    System.out.println("Finally block executes");
}
```

### 8.4 Multiple Catch Blocks

```java
try {
    String[] data = {"123", "abc", "456"};
    for (String s : data) {
        int num = Integer.parseInt(s);
        System.out.println("Number: " + num);
    }
} catch (NumberFormatException e) {
    System.out.println("Invalid number format");
} catch (ArrayIndexOutOfBoundsException e) {
    System.out.println("Array index out of bounds");
} catch (Exception e) {
    System.out.println("General exception: " + e.getMessage());
}
```

### 8.5 Throws Keyword

```java
public class Account {
    private double balance;
    
    public void withdraw(double amount) throws InsufficientFundsException {
        if (amount > balance) {
            throw new InsufficientFundsException(balance, amount);
        }
        balance -= amount;
    }
}
```

### 8.6 Custom Exception

```java
// Custom exception class
public class InsufficientFundsException extends Exception {
    private double balance;
    private double amount;
    
    public InsufficientFundsException(double balance, double amount) {
        super("Insufficient funds: Balance=" + balance + ", Requested=" + amount);
        this.balance = balance;
        this.amount = amount;
    }
    
    public double getBalance() {
        return balance;
    }
    
    public double getAmount() {
        return amount;
    }
}

// Using custom exception
public class Main {
    public static void main(String[] args) {
        Account account = new Account(1000);
        
        try {
            account.withdraw(1500);  // Throws InsufficientFundsException
        } catch (InsufficientFundsException e) {
            System.out.println("Error: " + e.getMessage());
        }
    }
}
```

### 8.7 Checked vs Unchecked Exceptions

| Type | Must Handle | Example |
|------|-------------|---------|
| Checked | Yes | IOException, SQLException |
| Unchecked | No | NullPointerException, ArithmeticException |

---

## 9. File I/O & Serialization

### 9.1 Reading Text Files

```java
import java.io.*;
import java.util.*;

public class FileReaderExample {
    public static void main(String[] args) {
        try {
            Scanner scanner = new Scanner(new File("data.txt"));
            
            while (scanner.hasNextLine()) {
                String line = scanner.nextLine();
                System.out.println(line);
            }
            
            scanner.close();
        } catch (FileNotFoundException e) {
            System.out.println("File not found: " + e.getMessage());
        }
    }
}
```

### 9.2 Writing to Text Files

```java
import java.io.*;

public class FileWriterExample {
    public static void main(String[] args) {
        try {
            PrintWriter writer = new PrintWriter(new FileWriter("output.txt"));
            
            writer.println("Hello, World!");
            writer.println("This is a new line.");
            writer.printf("Formatted number: %.2f%n", 3.14159);
            
            writer.close();
        } catch (IOException e) {
            System.out.println("Error writing file: " + e.getMessage());
        }
    }
}
```

### 9.3 String Tokenization

```java
String text = "apple,banana;orange grape|pear";

// Using Scanner with custom delimiter
Scanner scanner = new Scanner(text);
scanner.useDelimiter("[,;| ]+");

while (scanner.hasNext()) {
    System.out.println(scanner.next());
}
scanner.close();

// Output: apple, banana, orange, grape, pear
```

### 9.4 Object Serialization

```java
import java.io.*;

// Serializable class
public class Student implements Serializable {
    private String name;
    private int id;
    private double gpa;
    
    public Student(String name, int id, double gpa) {
        this.name = name;
        this.id = id;
        this.gpa = gpa;
    }
    
    @Override
    public String toString() {
        return name + " (ID: " + id + ", GPA: " + gpa + ")";
    }
}

// Write objects (Serialization)
public class WriteObjects {
    public static void main(String[] args) {
        Student[] students = {
            new Student("Ahmad", 1001, 3.5),
            new Student("Siti", 1002, 3.8)
        };
        
        try {
            ObjectOutputStream oos = new ObjectOutputStream(
                new FileOutputStream("students.dat"));
            oos.writeObject(students);
            oos.close();
            System.out.println("Students serialized!");
        } catch (IOException e) {
            System.out.println("Error: " + e.getMessage());
        }
    }
}

// Read objects (Deserialization)
public class ReadObjects {
    public static void main(String[] args) {
        try {
            ObjectInputStream ois = new ObjectInputStream(
                new FileInputStream("students.dat"));
            Student[] students = (Student[]) ois.readObject();
            ois.close();
            
            for (Student s : students) {
                System.out.println(s);
            }
        } catch (IOException | ClassNotFoundException e) {
            System.out.println("Error: " + e.getMessage());
        }
    }
}
```

### 9.5 Final Keyword

```java
// Final variable (constant)
final int MAX_SIZE = 100;
// MAX_SIZE = 200;  // ERROR: Cannot assign value to final variable

// Final method (cannot be overridden)
class Parent {
    final void finalMethod() {
        System.out.println("Cannot be overridden");
    }
}

// Final class (cannot be extended)
final class FinalClass {
    // Cannot be extended
}

// final parameter (cannot be modified)
public void method(final int value) {
    // value = 10;  // ERROR: Cannot assign value to final parameter
}
```

---

## 10. GUI Programming

### 10.1 Basic Swing Components

```java
import javax.swing.*;
import java.awt.*;

public class BasicGUI extends JFrame {
    public BasicGUI() {
        setTitle("Basic GUI");
        setSize(400, 300);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(new FlowLayout());
        
        // Components
        JLabel label = new JLabel("Enter your name:");
        JTextField textField = new JTextField(15);
        JButton button = new JButton("Submit");
        
        // Add components
        add(label);
        add(textField);
        add(button);
        
        setVisible(true);
    }
    
    public static void main(String[] args) {
        new BasicGUI();
    }
}
```

### 10.2 Event Handling

```java
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class ButtonExample extends JFrame implements ActionListener {
    private JButton button;
    private JLabel label;
    private int count = 0;
    
    public ButtonExample() {
        setTitle("Button Example");
        setSize(300, 200);
        setLayout(new FlowLayout());
        
        button = new JButton("Click me!");
        label = new JLabel("Count: 0");
        
        button.addActionListener(this);
        
        add(button);
        add(label);
        
        setVisible(true);
    }
    
    @Override
    public void actionPerformed(ActionEvent e) {
        count++;
        label.setText("Count: " + count);
    }
    
    public static void main(String[] args) {
        new ButtonExample();
    }
}
```

### 10.3 Radio Buttons

```java
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class RadioButtonExample extends JFrame implements ActionListener {
    private JRadioButton male, female;
    private JLabel result;
    
    public RadioButtonExample() {
        setTitle("Radio Button Example");
        setSize(300, 200);
        setLayout(new FlowLayout());
        
        male = new JRadioButton("Male");
        female = new JRadioButton("Female");
        result = new JLabel("Select gender");
        
        ButtonGroup group = new ButtonGroup();
        group.add(male);
        group.add(female);
        
        male.addActionListener(this);
        female.addActionListener(this);
        
        add(male);
        add(female);
        add(result);
        
        setVisible(true);
    }
    
    @Override
    public void actionPerformed(ActionEvent e) {
        if (e.getSource() == male) {
            result.setText("You selected: Male");
        } else {
            result.setText("You selected: Female");
        }
    }
    
    public static void main(String[] args) {
        new RadioButtonExample();
    }
}
```

### 10.4 BMI Calculator Example

```java
import javax.swing.*;
import java.awt.*;
import java.awt.event.*;
import java.text.DecimalFormat;

public class BMICalculator extends JFrame implements ActionListener {
    private JTextField weightField, heightField;
    private JButton calculateButton;
    private JLabel resultLabel;
    
    public BMICalculator() {
        setTitle("BMI Calculator");
        setSize(350, 250);
        setLayout(new GridLayout(5, 2, 5, 5));
        
        add(new JLabel("Weight (kg):"));
        weightField = new JTextField();
        add(weightField);
        
        add(new JLabel("Height (m):"));
        heightField = new JTextField();
        add(heightField);
        
        calculateButton = new JButton("Calculate");
        calculateButton.addActionListener(this);
        add(calculateButton);
        
        resultLabel = new JLabel("Result:");
        add(resultLabel);
        
        setVisible(true);
    }
    
    @Override
    public void actionPerformed(ActionEvent e) {
        try {
            double weight = Double.parseDouble(weightField.getText());
            double height = Double.parseDouble(heightField.getText());
            
            if (weight <= 0 || height <= 0) {
                JOptionPane.showMessageDialog(this, 
                    "Please enter positive values!");
                return;
            }
            
            double bmi = weight / Math.pow(height, 2);
            DecimalFormat df = new DecimalFormat("#0.00");
            
            String category;
            if (bmi < 18.5) category = "Underweight";
            else if (bmi < 25) category = "Normal";
            else if (bmi < 30) category = "Overweight";
            else category = "Obese";
            
            resultLabel.setText("BMI: " + df.format(bmi) + " (" + category + ")");
            
        } catch (NumberFormatException ex) {
            JOptionPane.showMessageDialog(this, "Please enter valid numbers!");
        }
    }
    
    public static void main(String[] args) {
        new BMICalculator();
    }
}
```

### 10.5 Common Swing Components

| Component | Description |
|-----------|-------------|
| JFrame | Main application window |
| JPanel | Container for grouping components |
| JButton | Clickable button |
| JLabel | Display text or image |
| JTextField | Single-line text input |
| JTextArea | Multi-line text area |
| JPasswordField | Password field (masked) |
| JCheckBox | Toggle button (on/off) |
| JRadioButton | Single selection button |
| JComboBox | Dropdown list |
| JList | List of selectable items |
| JTable | Table for data display |
| JScrollPane | Scrollable container |

---

## PART 4: REAL-WORLD PROJECTS

---

## 11. Condominium Management System

### 11.1 System Overview

A complete GUI application for managing condominium residents, payments, and administrative tasks.

### 11.2 Architecture

```
Condominium Management System
├── Homepage (Login screen)
├── Admin Portal
│   ├── Admin management
│   ├── Unit management
│   └── Payment tracking
├── Resident Portal
│   ├── Make payments
│   └── View payment history
└── Data Persistence
    ├── admin.txt
    ├── unit.txt
    └── receipt.txt
```

### 11.3 Data Models

```java
// Admin Model
public class Admin {
    private String username;
    private String password;
    
    public Admin(String username, String password) {
        this.username = username;
        this.password = password;
    }
    
    // Getters and setters...
}

// Unit Model
public class Unit {
    private String unitNumber;
    private String ownerName;
    private String username;
    private String password;
    private boolean[] paymentStatus;  // 12 months
    
    public Unit(String unitNumber, String ownerName, String username, String password) {
        this.unitNumber = unitNumber;
        this.ownerName = ownerName;
        this.username = username;
        this.password = password;
        this.paymentStatus = new boolean[12];  // All false initially
    }
    
    // Getters and setters...
}

// Receipt Model
public class Receipt {
    private String unitNumber;
    private String month;
    private String amount;
    private String date;
    private String reference;
    
    public Receipt(String unitNumber, String month, String amount, String date, String reference) {
        this.unitNumber = unitNumber;
        this.month = month;
        this.amount = amount;
        this.date = date;
        this.reference = reference;
    }
    
    // Getters and setters...
}
```

### 11.4 Data I/O Class

```java
import java.io.*;
import java.util.*;

public class DataIO {
    private static final String ADMIN_FILE = "admin.txt";
    private static final String UNIT_FILE = "unit.txt";
    private static final String RECEIPT_FILE = "receipt.txt";
    
    public static ArrayList<Admin> readAdmins() {
        ArrayList<Admin> admins = new ArrayList<>();
        try {
            Scanner scanner = new Scanner(new File(ADMIN_FILE));
            while (scanner.hasNextLine()) {
                String[] parts = scanner.nextLine().split(",");
                if (parts.length >= 2) {
                    admins.add(new Admin(parts[0], parts[1]));
                }
            }
            scanner.close();
        } catch (FileNotFoundException e) {
            System.out.println("Admin file not found");
        }
        return admins;
    }
    
    public static void writeAdmins(ArrayList<Admin> admins) {
        try {
            PrintWriter writer = new PrintWriter(new FileWriter(ADMIN_FILE));
            for (Admin admin : admins) {
                writer.println(admin.getUsername() + "," + admin.getPassword());
            }
            writer.close();
        } catch (IOException e) {
            System.out.println("Error writing admin file");
        }
    }
    
    // Similar methods for units and receipts...
}
```

### 11.5 Key Features

1. **Authentication**
   - Super admin with hardcoded password
   - Admin accounts stored in file
   - Resident accounts stored in file

2. **Admin Portal**
   - Create new admin accounts
   - Create new unit accounts
   - View all payment statuses

3. **Resident Portal**
   - Make monthly payments
   - View payment history
   - Generate receipts

4. **Data Persistence**
   - All data stored in text files
   - Automatic loading on startup
   - Automatic saving on changes

---

## 12. User Management System

### 12.1 System Overview

A CRUD (Create, Read, Update, Delete) application for managing users with a table display.

### 12.2 User Model

```java
public class User {
    private String name;
    private String pin;
    
    public User(String name, String pin) {
        this.name = name;
        this.pin = pin;
    }
    
    public String getName() {
        return name;
    }
    
    public void setName(String name) {
        this.name = name;
    }
    
    public String getPin() {
        return pin;
    }
    
    public void setPin(String pin) {
        this.pin = pin;
    }
    
    @Override
    public String toString() {
        return name + "," + pin;
    }
}
```

### 12.3 Main Application

```java
import javax.swing.*;
import javax.swing.table.DefaultTableModel;
import java.awt.*;
import java.awt.event.*;
import java.io.*;
import java.util.ArrayList;

public class UserManagementSystem extends JFrame implements ActionListener {
    private JTextField nameField, pinField;
    private JButton addButton, editButton, deleteButton, quitButton;
    private JTable table;
    private DefaultTableModel model;
    private ArrayList<User> users;
    
    public UserManagementSystem() {
        setTitle("User Management System");
        setSize(500, 400);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(new BorderLayout());
        
        // Input panel
        JPanel inputPanel = new JPanel(new GridLayout(3, 2, 5, 5));
        inputPanel.add(new JLabel("Name:"));
        nameField = new JTextField();
        inputPanel.add(nameField);
        inputPanel.add(new JLabel("PIN:"));
        pinField = new JTextField();
        inputPanel.add(pinField);
        
        // Button panel
        JPanel buttonPanel = new JPanel(new GridLayout(1, 4, 5, 5));
        addButton = new JButton("Add");
        editButton = new JButton("Edit");
        deleteButton = new JButton("Delete");
        quitButton = new JButton("Quit");
        
        addButton.addActionListener(this);
        editButton.addActionListener(this);
        deleteButton.addActionListener(this);
        quitButton.addActionListener(this);
        
        buttonPanel.add(addButton);
        buttonPanel.add(editButton);
        buttonPanel.add(deleteButton);
        buttonPanel.add(quitButton);
        
        // Table
        String[] columns = {"Name", "PIN"};
        model = new DefaultTableModel(columns, 0);
        table = new JTable(model);
        JScrollPane scrollPane = new JScrollPane(table);
        
        // Load users
        users = loadUsers();
        refreshTable();
        
        // Add to frame
        JPanel topPanel = new JPanel(new BorderLayout());
        topPanel.add(inputPanel, BorderLayout.NORTH);
        topPanel.add(buttonPanel, BorderLayout.SOUTH);
        
        add(topPanel, BorderLayout.NORTH);
        add(scrollPane, BorderLayout.CENTER);
        
        setVisible(true);
    }
    
    @Override
    public void actionPerformed(ActionEvent e) {
        if (e.getSource() == addButton) {
            addUser();
        } else if (e.getSource() == editButton) {
            editUser();
        } else if (e.getSource() == deleteButton) {
            deleteUser();
        } else if (e.getSource() == quitButton) {
            System.exit(0);
        }
    }
    
    private void addUser() {
        String name = nameField.getText().trim();
        String pin = pinField.getText().trim();
        
        if (name.isEmpty() || pin.isEmpty()) {
            JOptionPane.showMessageDialog(this, "Please fill all fields!");
            return;
        }
        
        users.add(new User(name, pin));
        saveUsers();
        refreshTable();
        
        nameField.setText("");
        pinField.setText("");
    }
    
    private void editUser() {
        int row = table.getSelectedRow();
        if (row == -1) {
            JOptionPane.showMessageDialog(this, "Select a user to edit!");
            return;
        }
        
        String name = nameField.getText().trim();
        String pin = pinField.getText().trim();
        
        if (name.isEmpty() || pin.isEmpty()) {
            JOptionPane.showMessageDialog(this, "Please fill all fields!");
            return;
        }
        
        User user = users.get(row);
        user.setName(name);
        user.setPin(pin);
        
        saveUsers();
        refreshTable();
        
        nameField.setText("");
        pinField.setText("");
    }
    
    private void deleteUser() {
        int row = table.getSelectedRow();
        if (row == -1) {
            JOptionPane.showMessageDialog(this, "Select a user to delete!");
            return;
        }
        
        int confirm = JOptionPane.showConfirmDialog(this,
            "Are you sure?", "Confirm Delete", JOptionPane.YES_NO_OPTION);
        
        if (confirm == JOptionPane.YES_OPTION) {
            users.remove(row);
            saveUsers();
            refreshTable();
        }
    }
    
    private void refreshTable() {
        model.setRowCount(0);
        for (User user : users) {
            model.addRow(new Object[]{user.getName(), user.getPin()});
        }
    }
    
    private ArrayList<User> loadUsers() {
        ArrayList<User> list = new ArrayList<>();
        try {
            BufferedReader reader = new BufferedReader(new FileReader("user.txt"));
            String line;
            while ((line = reader.readLine()) != null) {
                String[] parts = line.split(",");
                if (parts.length >= 2) {
                    list.add(new User(parts[0], parts[1]));
                }
            }
            reader.close();
        } catch (IOException e) {
            System.out.println("User file not found");
        }
        return list;
    }
    
    private void saveUsers() {
        try {
            PrintWriter writer = new PrintWriter(new FileWriter("user.txt"));
            for (User user : users) {
                writer.println(user.toString());
            }
            writer.close();
        } catch (IOException e) {
            System.out.println("Error saving users");
        }
    }
    
    public static void main(String[] args) {
        new UserManagementSystem();
    }
}
```

### 12.4 Key Features

1. **CRUD Operations**
   - Create new users
   - Read/View all users
   - Update existing users
   - Delete users

2. **Data Display**
   - JTable for tabular display
   - JScrollPane for scrolling
   - DefaultTableModel for data management

3. **User Interaction**
   - Selection for edit/delete
   - Confirmation dialog for delete
   - Input validation

4. **Data Persistence**
   - Save to text file
   - Load from text file
   - Automatic refresh

---

## 📊 QUICK REFERENCE

### Common Java Methods

| Method | Description | Example |
|--------|-------------|---------|
| `System.out.println()` | Print to console | `System.out.println("Hello");` |
| `Math.random()` | Random double [0,1) | `double r = Math.random();` |
| `Math.pow(a, b)` | a to the power of b | `double p = Math.pow(2, 8);` |
| `Integer.parseInt(s)` | String to int | `int i = Integer.parseInt("123");` |
| `Double.parseDouble(s)` | String to double | `double d = Double.parseDouble("3.14");` |
| `String.valueOf(x)` | Convert to string | `String s = String.valueOf(100);` |
| `Arrays.sort(arr)` | Sort array | `Arrays.sort(numbers);` |
| `Arrays.toString(arr)` | Array to string | `String s = Arrays.toString(arr);` |

### Common Swing Components

| Component | Constructor | Common Methods |
|-----------|-------------|----------------|
| JFrame | `new JFrame("Title")` | `setVisible()`, `setSize()`, `add()` |
| JButton | `new JButton("Text")` | `addActionListener()` |
| JLabel | `new JLabel("Text")` | `setText()`, `getText()` |
| JTextField | `new JTextField(15)` | `getText()`, `setText()` |
| JCheckBox | `new JCheckBox("Text")` | `isSelected()` |
| JRadioButton | `new JRadioButton("Text")` | `isSelected()` |
| JComboBox | `new JComboBox(items)` | `getSelectedItem()` |
| JOptionPane | - | `showMessageDialog()`, `showInputDialog()` |

### Exception Handling Pattern

```java
try {
    // Code that may throw exception
} catch (SpecificException e) {
    // Handle specific exception
} catch (GeneralException e) {
    // Handle general exception
} finally {
    // Always executes
}
```

### Inheritance Pattern

```java
public class Parent {
    protected int value;
    
    public Parent(int value) {
        this.value = value;
    }
    
    public void method() {
        System.out.println("Parent method");
    }
}

public class Child extends Parent {
    public Child(int value) {
        super(value);
    }
    
    @Override
    public void method() {
        super.method();  // Call parent method
        System.out.println("Child method");
    }
}
```

### Interface Pattern

```java
public interface MyInterface {
    void method1();
    void method2();
}

public class MyClass implements MyInterface {
    @Override
    public void method1() {
        // Implementation
    }
    
    @Override
    public void method2() {
        // Implementation
    }
}
```

---

## 🎯 EXAM TIPS

### Key Concepts to Master

1. **OOP Principles**
   - Encapsulation (private fields, public methods)
   - Inheritance (extends, super, overriding)
   - Polymorphism (overloading, overriding, casting)
   - Abstraction (abstract classes, interfaces)

2. **Control Flow**
   - if-else statements
   - switch-case
   - Loops (for, while, do-while)
   - Enhanced for loop

3. **Arrays**
   - Declaration and initialization
   - Accessing elements
   - Array operations (sort, search)

4. **Exception Handling**
   - try-catch-finally
   - Checked vs unchecked exceptions
   - Custom exceptions

5. **GUI Programming**
   - Swing components
   - Event handling
   - Layout managers

### Common Mistakes to Avoid

1. ❌ Forgetting to import necessary classes
2. ❌ Not closing file handles or resources
3. ❌ Confusing `==` with `.equals()` for strings
3. ❌ Not handling exceptions properly
4. ❌ Forgetting to call `super()` in subclass constructor
5. ❌ Not using `@Override` annotation
6. ❌ Confusing static vs instance members

### Best Practices

1. ✅ Use meaningful variable names
2. ✅ Follow naming conventions (PascalCase for classes, camelCase for methods)
3. ✅ Add comments for complex logic
4. ✅ Keep methods focused and small
5. ✅ Use proper exception handling
6. ✅ Close resources in finally block
7. ✅ Use interfaces for flexibility
8. ✅ Override `toString()` for meaningful output

---

## 📝 SUMMARY

This study guide covers all essential Java programming concepts from basic fundamentals to advanced object-oriented programming and GUI development. The progression follows a logical learning path:

1. **Fundamentals** - Basic syntax, data types, operators
2. **Control Flow** - Conditions, loops, arrays
3. **OOP Basics** - Classes, objects, methods
4. **Advanced OOP** - Encapsulation, inheritance, polymorphism
5. **Advanced Topics** - Exception handling, file I/O, serialization
6. **GUI Programming** - Swing components, event handling
7. **Real Projects** - Complete applications with data persistence

Master these concepts and you'll be well-prepared for Java programming exams and real-world development!

---

**End of Java Programming Complete Study Guide**

*For detailed lab solutions and code examples, refer to the individual lab sections in this guide.*