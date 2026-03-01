# Java Lab Solutions - Complete Guide

**Comprehensive solutions and explanations for all Java lab exercises**

---

## Table of Contents

- [Introduction](#introduction)
- [Getting Started](#getting-started)
- [Module 1: Basic Java Concepts](#module-1-basic-java-concepts)
  - [Week 01: Operators and Data Types](#week-01-operators-and-data-types)
  - [Week 02: Object-Oriented Programming Basics](#week-02-object-oriented-programming-basics)
  - [Lab 02: Basic Programming Exercises](#lab-02-basic-programming-exercises)
- [Module 2: OOP Fundamentals](#module-2-oop-fundamentals)
  - [Lecture 03: Packages and Access Modifiers](#lecture-03-packages-and-access-modifiers)
  - [Week 04: Encapsulation and Inheritance](#week-04-encapsulation-and-inheritance)
  - [Lab 03: Account Class Evolution](#lab-03-account-class-evolution)
- [Module 3: GUI Programming](#module-3-gui-programming)
  - [Lab 07: GUI Components and Event Handling](#lab-07-gui-components-and-event-handling)
- [Module 4: Advanced OOP](#module-4-advanced-oop)
  - [Week 08: Polymorphism](#week-08-polymorphism)
  - [Lab 08: String and Array Utilities](#lab-08-string-and-array-utilities)
  - [Week 09: Abstract Classes and Interfaces](#week-09-abstract-classes-and-interfaces)
  - [Lab 09: GUI Basics](#lab-09-gui-basics)
- [Module 5: Specialized Topics](#module-5-specialized-topics)
  - [Week 10: Exception Handling](#week-10-exception-handling)
  - [Lab 10: Account Inheritance System](#lab-10-account-inheritance-system)
  - [Week 12: Binary I/O and Serialization](#week-12-binary-io-and-serialization)
  - [Lab 12: Employee Management System](#lab-12-employee-management-system)
- [Module 6: Advanced Projects](#module-6-advanced-projects)
  - [Class Diagram: UML Relationships](#class-diagram-uml-relationships)
  - [Java Application 1: GUI User Management](#java-application-1-gui-user-management)
  - [Sample Project: Resident Management System](#sample-project-resident-management-system)
- [Best Practices and Tips](#best-practices-and-tips)
- [Common Pitfalls and Solutions](#common-pitfalls-and-solutions)

---

## Introduction

This guide provides comprehensive solutions and detailed explanations for all Java lab exercises across multiple modules. The curriculum covers:

- **Basic Java**: Operators, data types, control structures
- **OOP Fundamentals**: Classes, objects, encapsulation, inheritance
- **GUI Programming**: Components, layout managers, event handling
- **Advanced OOP**: Polymorphism, abstract classes, interfaces
- **Specialized Topics**: Exception handling, I/O, GUI programming
- **Projects**: Complete applications with real-world scenarios

### Learning Objectives

By completing these labs, you will:
1. Master Java syntax and fundamental concepts
2. Understand object-oriented programming principles
3. Develop problem-solving skills through practical exercises
4. Learn to write clean, maintainable code
5. Gain experience with GUI programming and file I/O

---

## Getting Started

### Prerequisites

- Java Development Kit (JDK) 8 or higher
- NetBeans IDE (recommended) or any Java IDE
- Basic understanding of programming concepts

### Setting Up Your Environment

1. **Install JDK**:
   ```bash
   # On Linux (Arch)
   sudo pacman -S jdk-openjdk

   # On Ubuntu/Debian
   sudo apt install default-jdk
   ```

2. **Install NetBeans**:
   ```bash
   # On Linux
   sudo pacman -S netbeans  # Arch
   # Or download from https://netbeans.apache.org/
   ```

3. **Verify Installation**:
   ```bash
   java -version
   javac -version
   ```

### Running the Labs

Each lab is organized as a NetBeans project:
1. Open NetBeans
2. File → Open Project
3. Navigate to the lab directory
4. Right-click the project → Run

---

## Module 1: Basic Java Concepts

### Week 01: Operators and Data Types

#### Learning Objectives
- Understand primitive data types
- Master all operator categories
- Learn type conversion and casting
- Practice short-circuit evaluation

#### Key Concepts

**Primitive Data Types:**
- `byte`, `short`, `int`, `long` (integers)
- `float`, `double` (floating-point)
- `char` (single character)
- `boolean` (true/false)

**Operator Categories:**
1. **Unary Operators**: `+`, `-`, `++`, `--`, `!`, `~`
2. **Binary Operators**: `+`, `-`, `*`, `/`, `%`
3. **Ternary Operator**: `condition ? value1 : value2`
4. **Relational Operators**: `==`, `!=`, `<`, `>`, `<=`, `>=`
5. **Logical Operators**: `&&`, `||`, `!`, `&`, `|`, `^`
6. **Bitwise Operators**: `&`, `|`, `^`, `~`, `<<`, `>>`, `>>>`

#### Exercise 1: Basic Data Types and Variables

**File**: `Week01/src/week01/Week01.java`

```java
package week01;

public class Week01 {
    public static void main(String[] args) {
        // Primitive data types
        int age = 25;
        long population = 7_800_000_000L;  // L for long
        double price = 19.99;
        float temperature = 36.5f;  // f for float
        char grade = 'A';
        boolean isStudent = true;

        // Display values
        System.out.println("Age: " + age);
        System.out.println("Population: " + population);
        System.out.println("Price: $" + price);
        System.out.println("Temperature: " + temperature + "°C");
        System.out.println("Grade: " + grade);
        System.out.println("Is Student: " + isStudent);

        // Type promotion example
        int a = 10;
        double b = a;  // int automatically promoted to double
        System.out.println("Type promotion: " + b);

        // Type casting example
        double c = 9.78;
        int d = (int) c;  // explicit casting, loses decimal part
        System.out.println("Type casting: " + d);
    }
}
```

**Explanation:**
- Java has 8 primitive data types
- Use `L` suffix for long literals
- Use `f` or `F` suffix for float literals
- Type promotion happens automatically (small to large)
- Explicit casting required for narrowing conversions
- Casting truncates the decimal part (no rounding)

**Output:**
```
Age: 25
Population: 7800000000
Price: $19.99
Temperature: 36.5°C
Grade: A
Is Student: true
Type promotion: 10.0
Type casting: 9
```

---

#### Exercise 2: Arithmetic Operators

**File**: `Week01/src/week01/Arithmetic.java`

```java
package week01;

public class Arithmetic {
    public static void main(String[] args) {
        int a = 10, b = 3;

        // Basic arithmetic
        System.out.println("Addition: " + (a + b));      // 13
        System.out.println("Subtraction: " + (a - b));   // 7
        System.out.println("Multiplication: " + (a * b)); // 30
        System.out.println("Division: " + (a / b));      // 3 (integer division)
        System.out.println("Modulus: " + (a % b));       // 1

        // Floating-point division
        System.out.println("Float Division: " + ((double)a / b)); // 3.333...

        // Increment/Decrement
        int x = 5;
        System.out.println("Prefix increment: " + (++x)); // 6 (increments first)
        System.out.println("Postfix increment: " + (x++)); // 6 (uses value, then increments)
        System.out.println("After postfix: " + x);        // 7

        // Compound assignment
        int y = 10;
        y += 5;  // y = y + 5;
        y -= 3;  // y = y - 3;
        y *= 2;  // y = y * 2;
        System.out.println("Compound assignment: " + y);
    }
}
```

**Explanation:**
- Integer division truncates the decimal part
- Use casting for precise division
- Prefix: operator before variable (operation first)
- Postfix: operator after variable (use value first)
- Compound assignments are shorthand for operations

---

#### Exercise 3: Logical Operators and Short-Circuit Evaluation

**File**: `Week01/src/week01/Logical.java`

```java
package week01;

public class Logical {
    public static void main(String[] args) {
        boolean a = true, b = false;

        // AND operator
        System.out.println("a && b: " + (a && b));  // false (both must be true)

        // OR operator
        System.out.println("a || b: " + (a || b));  // true (at least one true)

        // NOT operator
        System.out.println("!a: " + (!a));          // false

        // Short-circuit evaluation example
        int x = 5, y = 0;

        // && short-circuits: if first is false, second not evaluated
        // This prevents division by zero error!
        if (y != 0 && x / y > 1) {
            System.out.println("Result > 1");
        } else {
            System.out.println("Cannot divide by zero");
        }

        // | does NOT short-circuit: both sides always evaluated
        // This would cause division by zero error!
        // if (y != 0 | x / y > 1) { ... }

        System.out.println("Short-circuit example complete");

        // XOR operator (^)
        System.out.println("true ^ false: " + (true ^ false));  // true (different)
        System.out.println("true ^ true: " + (true ^ true));    // false (same)
    }
}
```

**Explanation:**
- `&&` and `||` are short-circuit operators
- Short-circuit evaluation improves performance and prevents errors
- `&` and `|` always evaluate both operands
- Use short-circuit operators when possible

**Output:**
```
a && b: false
a || b: true
!a: false
Cannot divide by zero
Short-circuit example complete
true ^ false: true
true ^ true: false
```

---

#### Exercise 4: Bitwise Operators

**File**: `Week01/src/week01/Bitwise.java`

```java
package week01;

public class Bitwise {
    public static void main(String[] args) {
        int a = 5;   // Binary: 0101
        int b = 3;   // Binary: 0011

        System.out.println("a = " + a + " (binary: " + Integer.toBinaryString(a) + ")");
        System.out.println("b = " + b + " (binary: " + Integer.toBinaryString(b) + ")");
        System.out.println();

        // Bitwise AND (&)
        // 0101 & 0011 = 0001 = 1
        System.out.println("a & b = " + (a & b) + " (binary: " + Integer.toBinaryString(a & b) + ")");

        // Bitwise OR (|)
        // 0101 | 0011 = 0111 = 7
        System.out.println("a | b = " + (a | b) + " (binary: " + Integer.toBinaryString(a | b) + ")");

        // Bitwise XOR (^)
        // 0101 ^ 0011 = 0110 = 6
        System.out.println("a ^ b = " + (a ^ b) + " (binary: " + Integer.toBinaryString(a ^ b) + ")");

        // Bitwise NOT (~)
        // ~0101 = 1010 (in two's complement: -6)
        System.out.println("~a = " + (~a) + " (binary: " + Integer.toBinaryString(~a) + ")");

        // Left shift (<<)
        // 0101 << 1 = 1010 = 10 (multiplies by 2)
        System.out.println("a << 1 = " + (a << 1) + " (binary: " + Integer.toBinaryString(a << 1) + ")");

        // Right shift (>>)
        // 0101 >> 1 = 0010 = 2 (divides by 2)
        System.out.println("a >> 1 = " + (a >> 1) + " (binary: " + Integer.toBinaryString(a >> 1) + ")");

        // Unsigned right shift (>>>)
        System.out.println("-5 >>> 1 = " + (-5 >>> 1));

        // Practical example: Check if a number is even
        int num = 10;
        if ((num & 1) == 0) {
            System.out.println(num + " is even");
        }

        // Practical example: Swap two numbers without temp variable
        int x = 10, y = 20;
        x = x ^ y;
        y = x ^ y;
        x = x ^ y;
        System.out.println("After swap: x = " + x + ", y = " + y);
    }
}
```

**Explanation:**
- Bitwise operators work on individual bits
- `&`: AND (both bits must be 1)
- `|`: OR (at least one bit must be 1)
- `^`: XOR (bits must be different)
- `~`: NOT (inverts all bits)
- `<<`: Left shift (multiplies by 2^n)
- `>>`: Right shift (divides by 2^n, preserves sign)
- `>>>`: Unsigned right shift (fills with zeros)

**Common Use Cases:**
- Checking even/odd: `(num & 1) == 0`
- Setting/clearing bits
- Efficient multiplication/division by powers of 2
- Swapping values without temporary variable

**Output:**
```
a = 5 (binary: 101)
b = 3 (binary: 11)

a & b = 1 (binary: 1)
a | b = 7 (binary: 111)
a ^ b = 6 (binary: 110)
~a = -6 (binary: 11111111111111111111111111111010)
a << 1 = 10 (binary: 1010)
a >> 1 = 2 (binary: 10)
-5 >>> 1 = 2147483645
10 is even
After swap: x = 20, y = 10
```

---

#### Exercise 5: Ternary Operator

**File**: `Week01/src/week01/Operator.java`

```java
package week01;

public class Operator {
    public static void main(String[] args) {
        // Ternary operator: condition ? value_if_true : value_if_false
        int age = 20;
        String status = (age >= 18) ? "Adult" : "Minor";
        System.out.println("Status: " + status);

        // Nested ternary
        int score = 85;
        String grade = (score >= 90) ? "A" :
                       (score >= 80) ? "B" :
                       (score >= 70) ? "C" :
                       (score >= 60) ? "D" : "F";
        System.out.println("Grade: " + grade);

        // Finding maximum of three numbers
        int a = 10, b = 20, c = 15;
        int max = (a > b) ? ((a > c) ? a : c) : ((b > c) ? b : c);
        System.out.println("Maximum: " + max);

        // Checking for null
        String name = null;
        String displayName = (name != null) ? name : "Unknown";
        System.out.println("Display Name: " + displayName);
    }
}
```

**Explanation:**
- Ternary operator is a compact if-else statement
- Format: `condition ? value1 : value2`
- Can be nested for multiple conditions
- Always returns a value
- Useful for simple conditional assignments

---

### Week 02: Object-Oriented Programming Basics

#### Learning Objectives
- Understand the transition from procedural to OOP
- Learn about objects and classes
- Understand pass-by-value semantics
- Master method encapsulation

#### Key Concepts

**OOP Principles:**
1. **Encapsulation**: Bundling data and methods together
2. **Abstraction**: Hiding implementation details
3. **Inheritance**: Reusing code through class hierarchy
4. **Polymorphism**: Same interface, different implementations

**Pass-by-Value:**
- Java always passes parameters by value
- For primitives: copy of the value
- For objects: copy of the reference (not the object itself)

#### Exercise 1: From Arrays to Objects

**File**: `Week02Lec01/src/oo1/Customer.java`

```java
package oo1;

public class Customer {
    // Instance variables (fields)
    private String name;
    private int id;
    private double balance;

    // Constructor
    public Customer(String name, int id, double balance) {
        this.name = name;
        this.id = id;
        this.balance = balance;
    }

    // Getters and Setters
    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public double getBalance() {
        return balance;
    }

    public void setBalance(double balance) {
        this.balance = balance;
    }
}
```

**File**: `Week02Lec01/src/oo1/NewMain.java`

```java
package oo1;

public class NewMain {
    public static void main(String[] args) {
        // Creating Customer objects
        Customer c1 = new Customer("Alice", 1001, 1000.00);
        Customer c2 = new Customer("Bob", 1002, 1500.00);
        Customer c3 = new Customer("Charlie", 1003, 500.00);

        // Array of objects
        Customer[] customers = {c1, c2, c3};

        // Display all customers
        System.out.println("Customer List:");
        System.out.println("------------");
        for (Customer c : customers) {
            System.out.println("ID: " + c.getId() +
                             ", Name: " + c.getName() +
                             ", Balance: $" + c.getBalance());
        }

        // Update balance
        c1.setBalance(1200.00);
        System.out.println("\nAfter update:");
        System.out.println("Alice's new balance: $" + c1.getBalance());
    }
}
```

**Explanation:**
- Objects encapsulate data (fields) and behavior (methods)
- Constructor initializes object state
- Private fields with public getters/setters (encapsulation)
- `this` keyword refers to current object
- Arrays can hold object references

**Output:**
```
Customer List:
------------
ID: 1001, Name: Alice, Balance: $1000.0
ID: 1002, Name: Bob, Balance: $1500.0
ID: 1003, Name: Charlie, Balance: $500.0

After update:
Alice's new balance: $1200.0
```

---

#### Exercise 2: Adding Methods to Objects

**File**: `Week02Lec01/src/oo2/Customer.java`

```java
package oo2;

public class Customer {
    private String name;
    private int id;
    private double balance;

    public Customer(String name, int id, double balance) {
        this.name = name;
        this.id = id;
        this.balance = balance;
    }

    // Withdraw method with 10% fee
    public boolean withdraw(double amount) {
        double fee = amount * 0.10;  // 10% fee
        double total = amount + fee;

        if (balance >= total) {
            balance -= total;
            System.out.println("Withdrawal successful. Fee: $" + fee);
            return true;
        } else {
            System.out.println("Insufficient funds. Required: $" + total);
            return false;
        }
    }

    public void deposit(double amount) {
        balance += amount;
        System.out.println("Deposit successful. New balance: $" + balance);
    }

    public void display() {
        System.out.println("Customer: " + name + ", Balance: $" + balance);
    }

    // Getters and setters
    public String getName() { return name; }
    public int getId() { return id; }
    public double getBalance() { return balance; }
}
```

**File**: `Week02Lec01/src/oo2/NewMain.java`

```java
package oo2;

public class NewMain {
    public static void main(String[] args) {
        Customer customer = new Customer("Alice", 1001, 1000.00);

        customer.display();

        // Deposit
        customer.deposit(500.00);

        // Withdraw (with 10% fee)
        customer.withdraw(200.00);  // Will deduct $220 total

        // Attempt large withdrawal
        customer.withdraw(1500.00);  // Will fail

        customer.display();
    }
}
```

**Explanation:**
- Methods encapsulate behavior within objects
- Objects manage their own state
- Methods can return values or perform actions
- Business logic is kept inside the class (good practice)

**Output:**
```
Customer: Alice, Balance: $1000.0
Deposit successful. New balance: $1500.0
Withdrawal successful. Fee: $20.0
Insufficient funds. Required: $1650.0
Customer: Alice, Balance: $1280.0
```

---

#### Exercise 3: Pass-by-Value Demonstration

**File**: `Week02Lec01/src/passbyvalue/Customer.java`

```java
package passbyvalue;

public class Customer {
    private String name;
    private double balance;

    public Customer(String name, double balance) {
        this.name = name;
        this.balance = balance;
    }

    public void setName(String name) {
        this.name = name;
    }

    public void setBalance(double balance) {
        this.balance = balance;
    }

    public void display() {
        System.out.println("Name: " + name + ", Balance: $" + balance);
    }
}
```

**File**: `Week02Lec01/src/passbyvalue/NewMain.java`

```java
package passbyvalue;

public class NewMain {
    public static void main(String[] args) {
        // Example 1: Primitive pass-by-value
        int x = 10;
        System.out.println("Before modify: x = " + x);
        modifyPrimitive(x);
        System.out.println("After modify: x = " + x);  // x unchanged

        // Example 2: Object reference pass-by-value
        Customer c = new Customer("Alice", 1000.00);
        System.out.println("\nBefore modify:");
        c.display();

        modifyObjectReference(c);  // Cannot change reference
        System.out.println("\nAfter modify reference:");
        c.display();  // c still refers to original object

        // Example 3: Modifying object state through reference
        modifyObjectState(c);
        System.out.println("\nAfter modify state:");
        c.display();  // Object state changed!
    }

    // Primitive: Copy of value passed
    public static void modifyPrimitive(int num) {
        num = 100;  // Changes only the local copy
        System.out.println("Inside modifyPrimitive: num = " + num);
    }

    // Object: Copy of reference passed
    // Cannot change the original reference
    public static void modifyObjectReference(Customer cust) {
        cust = new Customer("Bob", 2000.00);  // Changes only local reference
        System.out.println("Inside modifyObjectReference:");
        cust.display();
    }

    // Object: Can modify the object's state through the reference
    public static void modifyObjectState(Customer cust) {
        cust.setName("Charlie");
        cust.setBalance(3000.00);
        System.out.println("Inside modifyObjectState:");
        cust.display();
    }
}
```

**Explanation:**
- Java ALWAYS passes by value
- **Primitives**: Copy of the actual value
- **Objects**: Copy of the reference (pointer to object)
- Cannot change what object a variable refers to
- CAN modify the object's state through the reference
- This is a common interview question!

**Output:**
```
Before modify: x = 10
Inside modifyPrimitive: num = 100
After modify: x = 10

Before modify:
Name: Alice, Balance: $1000.0
Inside modifyObjectReference:
Name: Bob, Balance: $2000.0

After modify reference:
Name: Alice, Balance: $1000.0
Inside modifyObjectState:
Name: Charlie, Balance: $3000.0

After modify state:
Name: Charlie, Balance: $3000.0
```

---

### Lab 02: Basic Programming Exercises

#### Learning Objectives
- Practice control structures
- Work with arrays and loops
- Implement string manipulation
- Solve practical problems

#### Exercise 1: Power Function and String Methods

**File**: `Week02Lab02/src/week02lab02/Week02Lab02.java`

```java
package week02lab02;

public class Week02Lab02 {
    public static void main(String[] args) {
        // Math.pow() example
        double base = 2;
        double exponent = 10;
        double result = Math.pow(base, exponent);
        System.out.println(base + " ^ " + exponent + " = " + result);

        // String methods
        String text = "Hello World";

        System.out.println("\nString Methods:");
        System.out.println("Length: " + text.length());
        System.out.println("Uppercase: " + text.toUpperCase());
        System.out.println("Lowercase: " + text.toLowerCase());
        System.out.println("Character at index 0: " + text.charAt(0));
        System.out.println("Index of 'W': " + text.indexOf('W'));
        System.out.println("Substring (6, 11): " + text.substring(6, 11));
        System.out.println("Replace 'World' with 'Java': " + text.replace("World", "Java"));
        System.out.println("Contains 'Java': " + text.contains("Java"));
        System.out.println("Equals 'hello world': " + text.equalsIgnoreCase("hello world"));
    }
}
```

**Explanation:**
- `Math.pow(base, exponent)` calculates power
- String is immutable (creates new strings)
- `length()`: number of characters
- `charAt(index)`: character at position
- `substring(start, end)`: portion of string
- `indexOf()`: position of character/substring
- `toUpperCase()/toLowerCase()`: case conversion
- `replace()`: replace substrings
- `contains()`: check if substring exists

**Output:**
```
2.0 ^ 10.0 = 1024.0

String Methods:
Length: 11
Uppercase: HELLO WORLD
Lowercase: hello world
Character at index 0: H
Index of 'W': 6
Substring (6, 11): World
Replace 'World' with 'Java': Hello Java
Contains 'Java': false
Equals 'hello world': true
```

---

#### Exercise 2: Sum of Digits

**File**: `Week02Lab02/src/week02lab02/Exe3.java`

```java
package week02lab02;

import java.util.Scanner;

public class Exe3 {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter a number: ");
        int number = scanner.nextInt();

        // Handle negative numbers
        number = Math.abs(number);

        int sum = 0;
        int originalNumber = number;

        // Extract and sum digits
        while (number > 0) {
            int digit = number % 10;  // Get last digit
            sum += digit;             // Add to sum
            number /= 10;             // Remove last digit
        }

        System.out.println("Sum of digits in " + originalNumber + " = " + sum);

        scanner.close();
    }
}
```

**Explanation:**
- `% 10` extracts the last digit
- `/ 10` removes the last digit
- Loop until number becomes 0
- `Math.abs()` handles negative numbers

**Example Output:**
```
Enter a number: 12345
Sum of digits in 12345 = 15
```

---

#### Exercise 3: Grade Calculator

**File**: `Week02Lab02/src/week02lab02/Exe7.java`

```java
package week02lab02;

import java.util.Scanner;

public class Exe7 {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter student's score: ");
        int score = scanner.nextInt();

        String grade;

        // Determine grade
        if (score >= 90 && score <= 100) {
            grade = "A+";
        } else if (score >= 80) {
            grade = "A";
        } else if (score >= 75) {
            grade = "A-";
        } else if (score >= 70) {
            grade = "B+";
        } else if (score >= 65) {
            grade = "B";
        } else if (score >= 60) {
            grade = "B-";
        } else if (score >= 55) {
            grade = "C+";
        } else if (score >= 50) {
            grade = "C";
        } else if (score >= 45) {
            grade = "D";
        } else if (score >= 0) {
            grade = "F";
        } else {
            grade = "Invalid score";
        }

        System.out.println("Grade: " + grade);

        // Alternative using ternary operator
        String gradeTernary = (score >= 90) ? "A+" :
                              (score >= 80) ? "A" :
                              (score >= 75) ? "A-" :
                              (score >= 70) ? "B+" :
                              (score >= 65) ? "B" :
                              (score >= 60) ? "B-" :
                              (score >= 55) ? "C+" :
                              (score >= 50) ? "C" :
                              (score >= 45) ? "D" :
                              (score >= 0) ? "F" : "Invalid";
        System.out.println("Grade (ternary): " + gradeTernary);

        scanner.close();
    }
}
```

**Explanation:**
- Use if-else if-else chain for ranges
- Order matters (check highest first)
- Ternary operator can make code more compact
- Always validate input (check bounds)

**Example Output:**
```
Enter student's score: 85
Grade: A
Grade (ternary): A
```

---

#### Exercise 4: Array with Random Numbers

**File**: `Week02Lab02/src/week02lab02/Exe8.java`

```java
package week02lab02;

import java.util.Random;

public class Exe8 {
    public static void main(String[] args) {
        Random random = new Random();

        // Create array of 10 integers
        int[] numbers = new int[10];

        // Fill array with random numbers (1-100)
        System.out.println("Array elements:");
        for (int i = 0; i < numbers.length; i++) {
            numbers[i] = random.nextInt(100) + 1;  // 1 to 100
            System.out.print(numbers[i] + " ");
        }
        System.out.println();

        // Calculate sum
        int sum = 0;
        for (int num : numbers) {  // Enhanced for loop
            sum += num;
        }

        // Calculate average
        double average = (double) sum / numbers.length;

        // Find maximum
        int max = numbers[0];
        for (int num : numbers) {
            if (num > max) {
                max = num;
            }
        }

        // Find minimum
        int min = numbers[0];
        for (int num : numbers) {
            if (num < min) {
                min = num;
            }
        }

        // Display results
        System.out.println("\nStatistics:");
        System.out.println("Sum: " + sum);
        System.out.println("Average: " + average);
        System.out.println("Maximum: " + max);
        System.out.println("Minimum: " + min);
    }
}
```

**Explanation:**
- `Random.nextInt(n)` generates 0 to n-1
- Enhanced for loop: `for (type var : array)`
- Cast to double for precise average
- Initialize max/min with first element

**Example Output:**
```
Array elements:
42 17 89 5 63 28 91 34 7 55

Statistics:
Sum: 431
Average: 43.1
Maximum: 91
Minimum: 5
```

---

#### Exercise 5: Do-While Loop

**File**: `Week02Lab02/src/week02lab02/Exe10.java`

```java
package week02lab02;

import java.util.Scanner;

public class Exe10 {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String input;

        // Do-while loop: always executes at least once
        do {
            System.out.print("Enter a command (type 'No' to exit): ");
            input = scanner.nextLine();

            if (!input.equalsIgnoreCase("No")) {
                System.out.println("Processing: " + input);
                // Add your command processing logic here
            }

        } while (!input.equalsIgnoreCase("No"));

        System.out.println("Program exited.");

        scanner.close();
    }
}
```

**Explanation:**
- Do-while loop: condition checked AFTER execution
- Always runs at least once
- Good for menu-driven programs
- `equalsIgnoreCase()`: case-insensitive comparison

**Example Output:**
```
Enter a command (type 'No' to exit): start
Processing: start
Enter a command (type 'No' to exit): stop
Processing: stop
Enter a command (type 'No' to exit): No
Program exited.
```

---

## Module 2: OOP Fundamentals

### Lecture 03: Packages and Access Modifiers

#### Learning Objectives
- Understand package organization
- Master access modifiers
- Learn protected access in inheritance
- Understand package-private access

#### Key Concepts

**Access Modifiers Visibility:**

| Modifier | Class | Package | Subclass | World |
|----------|-------|---------|----------|-------|
| `public` | ✓ | ✓ | ✓ | ✓ |
| `protected` | ✓ | ✓ | ✓ | ✗ |
| default (no modifier) | ✓ | ✓ | ✗ | ✗ |
| `private` | ✓ | ✗ | ✗ | ✗ |

**Package Structure:**
- Organizes related classes
- Prevents naming conflicts
- Provides access control
- `package` statement at top of file

#### Exercise 1: Access Modifier Demonstration

**File**: `Lec03/src/package1/ClassX1.java`

```java
package package1;

public class ClassX1 {
    // All access modifiers demonstrated
    public int publicField = 1;
    protected int protectedField = 2;
    int defaultField = 3;  // Package-private
    private int privateField = 4;

    public ClassX1() {
        System.out.println("ClassX1 constructor");
        demonstrateAccess();
    }

    public void demonstrateAccess() {
        // All accessible within same class
        System.out.println("Within ClassX1:");
        System.out.println("  Public: " + publicField);
        System.out.println("  Protected: " + protectedField);
        System.out.println("  Default: " + defaultField);
        System.out.println("  Private: " + privateField);
    }

    public void publicMethod() {
        System.out.println("Public method called");
    }

    protected void protectedMethod() {
        System.out.println("Protected method called");
    }

    void defaultMethod() {
        System.out.println("Default method called");
    }

    private void privateMethod() {
        System.out.println("Private method called");
    }
}
```

**File**: `Lec03/src/package1/ClassX2.java`

```java
package package1;

public class ClassX2 {
    public static void main(String[] args) {
        ClassX1 obj = new ClassX1();

        // Same package access
        System.out.println("\nFrom ClassX2 (same package):");
        System.out.println("  Public: " + obj.publicField);        // ✓ Accessible
        System.out.println("  Protected: " + obj.protectedField);  // ✓ Accessible
        System.out.println("  Default: " + obj.defaultField);      // ✓ Accessible
        // System.out.println("  Private: " + obj.privateField);   // ✗ Error!

        obj.publicMethod();        // ✓ Accessible
        obj.protectedMethod();     // ✓ Accessible
        obj.defaultMethod();       // ✓ Accessible
        // obj.privateMethod();    // ✗ Error!
    }
}
```

**File**: `Lec03/src/package2/ClassY1.java`

```java
package package2;
import package1.ClassX1;

public class ClassY1 extends ClassX1 {
    public ClassY1() {
        super();  // Call superclass constructor
        System.out.println("ClassY1 constructor");
    }

    public void demonstrateAccess() {
        // Subclass in different package
        System.out.println("\nFrom ClassY1 (subclass, different package):");
        System.out.println("  Public: " + publicField);        // ✓ Accessible
        System.out.println("  Protected: " + protectedField);  // ✓ Accessible (inherited)
        // System.out.println("  Default: " + defaultField);  // ✗ Not accessible
        // System.out.println("  Private: " + privateField);  // ✗ Not accessible

        publicMethod();        // ✓ Accessible
        protectedMethod();     // ✓ Accessible (inherited)
        // defaultMethod();     // ✗ Not accessible
        // privateMethod();     // ✗ Not accessible
    }
}
```

**File**: `Lec03/src/package2/ClassY2.java`

```java
package package2;
import package1.ClassX1;

public class ClassY2 {
    public static void main(String[] args) {
        ClassX1 obj = new ClassX1();

        // Different package, non-subclass
        System.out.println("\nFrom ClassY2 (different package, non-subclass):");
        System.out.println("  Public: " + obj.publicField);        // ✓ Accessible
        // System.out.println("  Protected: " + obj.protectedField); // ✗ Not accessible
        // System.out.println("  Default: " + obj.defaultField);    // ✗ Not accessible
        // System.out.println("  Private: " + obj.privateField);    // ✗ Not accessible

        obj.publicMethod();        // ✓ Accessible
        // obj.protectedMethod();   // ✗ Not accessible
        // obj.defaultMethod();     // ✗ Not accessible
        // obj.privateMethod();     // ✗ Not accessible
    }
}
```

**Explanation:**
- **public**: Accessible everywhere
- **protected**: Accessible in same package and subclasses
- **default (package-private)**: Only accessible in same package
- **private**: Only accessible within the class
- Use the most restrictive modifier possible

---

#### Exercise 2: Composition (Has-A Relationship)

**File**: `Lec03/src/lec03/Car.java`

```java
package lec03;

public class Car {
    private String make;
    private String model;
    private int year;

    public Car(String make, String model, int year) {
        this.make = make;
        this.model = model;
        this.year = year;
    }

    public void start() {
        System.out.println(make + " " + model + " is starting...");
    }

    public void stop() {
        System.out.println(make + " " + model + " is stopping.");
    }

    public void display() {
        System.out.println(year + " " + make + " " + model);
    }
}
```

**File**: `Lec03/src/lec03/Student.java`

```java
package lec03;

public class Student {
    private String name;
    private int id;
    private Car car;  // Composition: Student has-a Car

    public Student(String name, int id) {
        this.name = name;
        this.id = id;
    }

    public Student(String name, int id, Car car) {
        this.name = name;
        this.id = id;
        this.car = car;
    }

    public void setCar(Car car) {
        this.car = car;
    }

    public void driveCar() {
        if (car != null) {
            car.start();
            System.out.println(name + " is driving the car.");
            car.stop();
        } else {
            System.out.println(name + " doesn't have a car.");
        }
    }

    public void display() {
        System.out.println("Student: " + name + ", ID: " + id);
        if (car != null) {
            System.out.print("  Owns: ");
            car.display();
        } else {
            System.out.println("  No car");
        }
    }
}
```

**File**: `Lec03/src/lec03/Lec03.java`

```java
package lec03;

public class Lec03 {
    public static void main(String[] args) {
        // Create Car objects
        Car car1 = new Car("Toyota", "Camry", 2020);
        Car car2 = new Car("Honda", "Civic", 2021);

        // Create Student objects
        Student student1 = new Student("Alice", 1001, car1);
        Student student2 = new Student("Bob", 1002);
        Student student3 = new Student("Charlie", 1003, car2);

        // Display students
        System.out.println("Student Information:");
        System.out.println("====================");
        student1.display();
        student2.display();
        student3.display();

        // Bob buys a car
        System.out.println("\nBob buys a car:");
        student2.setCar(new Car("Ford", "Mustang", 2022));
        student2.display();

        // Demonstrate driving
        System.out.println("\nDriving demonstrations:");
        student1.driveCar();
        student2.driveCar();
        student3.driveCar();
    }
}
```

**Explanation:**
- Composition: "has-a" relationship
- One object contains another object
- Promotes code reuse
- Flexible relationships (can be null)
- Different from inheritance ("is-a" relationship)

**Output:**
```
Student Information:
====================
Student: Alice, ID: 1001
  Owns: 2020 Toyota Camry
Student: Bob, ID: 1002
  No car
Student: Charlie, ID: 1003
  Owns: 2021 Honda Civic

Bob buys a car:
Student: Bob, ID: 1002
  Owns: 2022 Ford Mustang

Driving demonstrations:
Toyota Camry is starting...
Alice is driving the car.
Toyota Camry is stopping.
Ford Mustang is starting...
Bob is driving the car.
Ford Mustang is stopping.
Honda Civic is starting...
Charlie is driving the car.
Honda Civic is stopping.
```

---

### Week 04: Encapsulation and Inheritance

#### Learning Objectives
- Understand encapsulation principles
- Implement getters and setters
- Master inheritance concepts
- Learn method overriding

#### Key Concepts

**Encapsulation:**
- Hide internal state
- Provide controlled access
- Validate data in setters
- Maintain invariants

**Inheritance:**
- "is-a" relationship
- Code reuse
- Single inheritance (Java)
- `extends` keyword

#### Exercise 1: Encapsulation

**File**: `Week04Lec04/src/encapsulation/Customer.java`

```java
package encapsulation;

public class Customer {
    // Private fields (hidden from outside)
    private String name;
    private int id;
    private double balance;

    public Customer(String name, int id, double balance) {
        this.name = name;
        this.id = id;
        setBalance(balance);  // Use setter for validation
    }

    // Getters (read access)
    public String getName() {
        return name;
    }

    public int getId() {
        return id;
    }

    public double getBalance() {
        return balance;
    }

    // Setters (write access with validation)
    public void setName(String name) {
        if (name != null && !name.trim().isEmpty()) {
            this.name = name;
        } else {
            System.out.println("Error: Name cannot be empty!");
        }
    }

    public void setId(int id) {
        if (id > 0) {
            this.id = id;
        } else {
            System.out.println("Error: ID must be positive!");
        }
    }

    public void setBalance(double balance) {
        if (balance >= 0) {
            this.balance = balance;
        } else {
            System.out.println("Error: Balance cannot be negative!");
        }
    }

    // Business logic methods
    public boolean deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            System.out.println("Deposited: $" + amount + ". New balance: $" + balance);
            return true;
        } else {
            System.out.println("Error: Deposit amount must be positive!");
            return false;
        }
    }

    public boolean withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
            System.out.println("Withdrawn: $" + amount + ". New balance: $" + balance);
            return true;
        } else if (amount > balance) {
            System.out.println("Error: Insufficient funds!");
            return false;
        } else {
            System.out.println("Error: Withdrawal amount must be positive!");
            return false;
        }
    }

    public void display() {
        System.out.println("Customer: " + name + ", ID: " + id + ", Balance: $" + balance);
    }
}
```

**File**: `Week04Lec04/src/encapsulation/NewMain.java`

```java
package encapsulation;

public class NewMain {
    public static void main(String[] args) {
        // Create customer with encapsulated data
        Customer customer = new Customer("Alice", 1001, 1000.00);
        customer.display();

        // Attempt invalid operations (will be rejected)
        System.out.println("\nAttempting invalid operations:");
        customer.setName("");           // Rejected
        customer.setBalance(-500);      // Rejected
        customer.withdraw(-100);        // Rejected

        // Valid operations
        System.out.println("\nValid operations:");
        customer.deposit(500.00);
        customer.withdraw(200.00);
        customer.withdraw(2000.00);     // Insufficient funds

        // Direct field access is not possible!
        // customer.balance = 1000000;  // ERROR: balance is private

        customer.display();
    }
}
```

**Explanation:**
- Private fields prevent direct access
- Getters provide read access
- Setters provide write access with validation
- Business logic kept in methods
- Maintains data integrity

**Output:**
```
Customer: Alice, ID: 1001, Balance: $1000.0

Attempting invalid operations:
Error: Name cannot be empty!
Error: Balance cannot be negative!
Error: Withdrawal amount must be positive!

Valid operations:
Deposited: $500.0. New balance: $1500.0
Withdrawn: $200.0. New balance: $1300.0
Error: Insufficient funds!
Customer: Alice, ID: 1001, Balance: $1300.0
```

---

#### Exercise 2: Inheritance and Method Overriding

**File**: `Week04Lec04/src/inheritance/ClassA.java`

```java
package inheritance;

public class ClassA {
    protected String message = "Message from ClassA";

    public ClassA() {
        System.out.println("ClassA constructor");
    }

    public void methodA() {
        System.out.println("ClassA.methodA() - " + message);
    }

    public void lunch() {
        System.out.println("ClassA is having lunch");
    }

    public void display() {
        System.out.println("This is ClassA");
    }
}
```

**File**: `Week04Lec04/src/inheritance/ClassB1.java`

```java
package inheritance;

public class ClassB1 extends ClassA {
    private int b1 = 10;
    private int b2 = 20;

    public ClassB1() {
        super();  // Call superclass constructor
        System.out.println("ClassB1 constructor");
    }

    // Method overriding
    @Override
    public void methodA() {
        System.out.println("ClassB1.methodA() - Overridden!");
        // Can still call superclass method
        super.methodA();
    }

    public void methodB() {
        System.out.println("ClassB1.methodB() - b1=" + b1 + ", b2=" + b2);
    }

    public int getB1() {
        return b1;
    }

    public int getB2() {
        return b2;
    }

    @Override
    public void display() {
        System.out.println("This is ClassB1 (extends ClassA)");
    }
}
```

**File**: `Week04Lec04/src/inheritance/ClassB2.java`

```java
package inheritance;

public class ClassB2 extends ClassA {
    public ClassB2() {
        super();
        System.out.println("ClassB2 constructor");
    }

    // Does not override any methods
    // Inherits all methods from ClassA
}
```

**File**: `Week04Lec04/src/inheritance/MultiLevelClassC.java`

```java
package inheritance;

public class MultiLevelClassC extends ClassB1 {
    private int c = 30;

    public MultiLevelClassC() {
        super();
        System.out.println("MultiLevelClassC constructor");
    }

    @Override
    public void methodA() {
        System.out.println("MultiLevelClassC.methodA() - Overridden again!");
        super.methodA();
    }

    public void methodC() {
        System.out.println("MultiLevelClassC.methodC() - c=" + c);
        System.out.println("  Has access to: b1=" + getB1() + ", b2=" + getB2());
    }

    @Override
    public void display() {
        System.out.println("This is MultiLevelClassC (extends ClassB1, which extends ClassA)");
    }
}
```

**File**: `Week04Lec04/src/inheritance/NewMain.java`

```java
package inheritance;

public class NewMain {
    public static void main(String[] args) {
        System.out.println("=== Inheritance Demonstration ===\n");

        // ClassB1 extends ClassA
        System.out.println("Creating ClassB1 object:");
        ClassB1 b1 = new ClassB1();
        b1.methodA();      // Overridden method
        b1.methodB();      // New method in ClassB1
        b1.lunch();        // Inherited from ClassA
        b1.display();

        System.out.println("\nCreating ClassB2 object:");
        ClassB2 b2 = new ClassB2();
        b2.methodA();      // Inherited from ClassA
        b2.lunch();        // Inherited from ClassA
        b2.display();      // Inherited from ClassA

        System.out.println("\nMulti-level inheritance (ClassA -> ClassB1 -> ClassC):");
        MultiLevelClassC c = new MultiLevelClassC();
        c.methodA();       // Overridden in ClassC
        c.methodB();       // Inherited from ClassB1
        c.methodC();       // New method in ClassC
        c.lunch();         // Inherited from ClassA
        c.display();

        // Polymorphism example
        System.out.println("\nPolymorphism example:");
        ClassA poly;
        poly = new ClassB1();      // Upcasting
        poly.methodA();           // Calls ClassB1.methodA()
        poly.display();

        poly = new MultiLevelClassC();  // Upcasting
        poly.methodA();           // Calls MultiLevelClassC.methodA()
        poly.display();

        // Note: Java does NOT support multiple inheritance
        // ClassD cannot extend both ClassB1 and ClassB2
    }
}
```

**Explanation:**
- `extends`: create subclass
- `super`: call superclass constructor/method
- `@Override`: annotation to indicate overriding
- Subclass inherits all non-private members
- Private members are NOT inherited
- Protected members accessible in subclasses
- Java supports only single inheritance
- Multi-level inheritance: A -> B -> C

**Output:**
```
=== Inheritance Demonstration ===

Creating ClassB1 object:
ClassA constructor
ClassB1 constructor
ClassB1.methodA() - Overridden!
ClassA.methodA() - Message from ClassA
ClassB1.methodB() - b1=10, b2=20
ClassA is having lunch
This is ClassB1 (extends ClassA)

Creating ClassB2 object:
ClassA constructor
ClassB2 constructor
ClassA.methodA() - Message from ClassA
ClassA is having lunch
This is ClassA

Multi-level inheritance (ClassA -> ClassB1 -> ClassC):
ClassA constructor
ClassB1 constructor
MultiLevelClassC constructor
MultiLevelClassC.methodA() - Overridden again!
ClassB1.methodA() - Overridden!
ClassA.methodA() - Message from ClassA
ClassB1.methodB() - b1=10, b2=20
MultiLevelClassC.methodC() - c=30
  Has access to: b1=10, b2=20
ClassA is having lunch
This is MultiLevelClassC (extends ClassB1, which extends ClassA)

Polymorphism example:
ClassA constructor
ClassB1 constructor
ClassB1.methodA() - Overridden!
ClassA.methodA() - Message from ClassA
This is ClassB1 (extends ClassA)
ClassA constructor
ClassB1 constructor
MultiLevelClassC constructor
MultiLevelClassC.methodA() - Overridden again!
ClassB1.methodA() - Overridden!
ClassA.methodA() - Message from ClassA
This is MultiLevelClassC (extends ClassB1, which extends ClassA)
```

---

### Lab 03: Account Class Evolution

#### Learning Objectives
- Understand class evolution
- Learn static vs instance members
- Master toString() method
- Work with enums

#### Exercise 1: Account Class with Static Members

**File**: `Lab03/src/lab03/Account.java`

```java
package lab03;

public class Account {
    // Instance variables (each object has its own)
    private String accountNumber;
    private String holderName;
    private double balance;

    // Static variable (shared by all instances)
    private static String bankName = "Universal Bank";
    private static int totalAccounts = 0;

    // Static initializer
    static {
        System.out.println("Bank initialized: " + bankName);
    }

    public Account(String accountNumber, String holderName, double balance) {
        this.accountNumber = accountNumber;
        this.holderName = holderName;
        this.balance = balance;
        totalAccounts++;  // Increment shared counter
    }

    // Instance methods
    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            System.out.println("Deposited: $" + amount);
        }
    }

    public boolean withdraw(double amount) {
        if (amount > 0 && balance >= amount) {
            balance -= amount;
            System.out.println("Withdrawn: $" + amount);
            return true;
        }
        System.out.println("Withdrawal failed!");
        return false;
    }

    public void display() {
        System.out.println("Bank: " + bankName);
        System.out.println("Account: " + accountNumber);
        System.out.println("Holder: " + holderName);
        System.out.println("Balance: $" + balance);
        System.out.println();
    }

    // Override toString()
    @Override
    public String toString() {
        return "Account[" + accountNumber + ", " + holderName + ", $" + balance + "]";
    }

    // Static methods
    public static String getBankName() {
        return bankName;
    }

    public static int getTotalAccounts() {
        return totalAccounts;
    }

    public static void setBankName(String name) {
        bankName = name;
    }

    // Getters and setters
    public String getAccountNumber() { return accountNumber; }
    public String getHolderName() { return holderName; }
    public double getBalance() { return balance; }
}
```

**File**: `Lab03/src/lab03/Lab03.java`

```java
package lab03;
import java.util.Date;

public class Lab03 {
    public static void main(String[] args) {
        // Display current date
        Date today = new Date();
        System.out.println("Today's date: " + today);
        System.out.println();

        // Create accounts
        Account acc1 = new Account("ACC001", "Alice", 1000.00);
        Account acc2 = new Account("ACC002", "Bob", 1500.00);
        Account acc3 = new Account("ACC003", "Charlie", 500.00);

        // Display accounts
        System.out.println("Account Details:");
        acc1.display();
        acc2.display();
        acc3.display();

        // Using toString()
        System.out.println("Using toString():");
        System.out.println(acc1);
        System.out.println(acc2);
        System.out.println(acc3);

        // Static members
        System.out.println("\nStatic Information:");
        System.out.println("Bank Name: " + Account.getBankName());
        System.out.println("Total Accounts: " + Account.getTotalAccounts());

        // Change bank name (affects all accounts)
        Account.setBankName("Global Bank");
        System.out.println("\nAfter changing bank name:");
        acc1.display();

        // Transactions
        System.out.println("Transactions:");
        acc1.deposit(500.00);
        acc1.withdraw(200.00);
        acc2.withdraw(2000.00);  // Insufficient funds

        System.out.println("\nFinal balances:");
        System.out.println(acc1);
        System.out.println(acc2);
        System.out.println(acc3);
    }
}
```

**Explanation:**
- **Static variables**: shared by all instances
- **Static methods**: called on class, not objects
- **Static initializer**: runs once when class loads
- **toString()**: provides string representation
- Use static for class-wide data/constants

---

#### Exercise 2: Enum for Type-Safe Constants

**File**: `Lab03/src/exe2/Velocity.java`

```java
package exe2;

public enum Velocity {
    SLOW(1),
    MEDIUM(2),
    FAST(3),
    VERY_FAST(4);

    private final int speedLevel;

    // Enum constructor (private by default)
    Velocity(int speedLevel) {
        this.speedLevel = speedLevel;
    }

    public int getSpeedLevel() {
        return speedLevel;
    }

    public String getDescription() {
        switch (this) {
            case SLOW: return "Gentle breeze";
            case MEDIUM: return "Moderate airflow";
            case FAST: return "Strong wind";
            case VERY_FAST: return "Hurricane force";
            default: return "Unknown";
        }
    }
}
```

**File**: `Lab03/src/exe2/Fan.java`

```java
package exe2;

public class Fan {
    private String brand;
    private Velocity currentSpeed;

    public Fan(String brand) {
        this.brand = brand;
        this.currentSpeed = Velocity.OFF;  // Default off
    }

    public void setSpeed(Velocity speed) {
        this.currentSpeed = speed;
        System.out.println(brand + " fan speed set to: " + speed);
        System.out.println("  Description: " + speed.getDescription());
        System.out.println("  Speed level: " + speed.getSpeedLevel());
    }

    public void increaseSpeed() {
        Velocity[] speeds = Velocity.values();
        int currentIndex = currentSpeed.ordinal();
        if (currentIndex < speeds.length - 1) {
            currentSpeed = speeds[currentIndex + 1];
            System.out.println("Speed increased to: " + currentSpeed);
        } else {
            System.out.println("Already at maximum speed!");
        }
    }

    public void decreaseSpeed() {
        Velocity[] speeds = Velocity.values();
        int currentIndex = currentSpeed.ordinal();
        if (currentIndex > 0) {
            currentSpeed = speeds[currentIndex - 1];
            System.out.println("Speed decreased to: " + currentSpeed);
        } else {
            System.out.println("Already at minimum speed!");
        }
    }

    public void display() {
        System.out.println(brand + " Fan:");
        System.out.println("  Current speed: " + currentSpeed);
        System.out.println("  Description: " + currentSpeed.getDescription());
    }
}
```

**File**: `Lab03/src/exe2/NewMain.java`

```java
package exe2;

public class NewMain {
    public static void main(String[] args) {
        // Create fan
        Fan fan = new Fan("Dyson");

        // Demonstrate enum usage
        System.out.println("=== Fan Control Demo ===\n");

        fan.setSpeed(Velocity.SLOW);
        System.out.println();
        Thread.sleep(1000);

        fan.increaseSpeed();
        System.out.println();
        Thread.sleep(1000);

        fan.increaseSpeed();
        System.out.println();
        Thread.sleep(1000);

        fan.increaseSpeed();
        System.out.println();
        Thread.sleep(1000);

        fan.increaseSpeed();  // Already at max
        System.out.println();
        Thread.sleep(1000);

        fan.decreaseSpeed();
        System.out.println();
        Thread.sleep(1000);

        fan.display();

        // Display all enum values
        System.out.println("\n=== All Velocity Values ===");
        for (Velocity v : Velocity.values()) {
            System.out.println(v + ": " + v.getDescription() +
                             " (Level: " + v.getSpeedLevel() + ")");
        }
    }
}
```

**Explanation:**
- **Enum**: type-safe constant set
- Each enum value is an object
- Can have fields, methods, constructors
- `values()`: array of all enum constants
- `ordinal()`: position in enum declaration
- Use enum instead of int constants

---

## Module 3: GUI Programming

### Lab 07: GUI Components and Event Handling

#### Learning Objectives
- Create JFrame windows and panels
- Use various GUI components (buttons, labels, text fields, checkboxes, radio buttons)
- Handle different types of events (action, item, mouse)
- Understand layout managers
- Implement interactive GUI applications

#### Key Concepts

**GUI Components:**
- `JFrame`: Main application window
- `JPanel`: Container for components
- `JLabel`: Display text or images
- `JTextField`: Single-line text input
- `JButton`: Clickable button
- `JRadioButton`: Mutually exclusive options
- `Checkbox`: Toggleable options

**Event Handling:**
- `ActionListener`: Button clicks, menu selections
- `ItemListener`: Checkbox/radio button state changes
- `MouseListener`: Mouse interactions
- `ButtonGroup`: Group radio buttons for mutual exclusion

**Layout Managers:**
- `BorderLayout`: North, South, East, West, Center
- `FlowLayout`: Left-to-right, top-to-bottom
- `GridLayout`: Grid of equal-sized cells

#### Exercise 1: Basic JFrame with MouseListener

**File**: `Week07Lec08/src/week07lec08/Week07Lec08.java`

```java
package week07lec08;

import javax.swing.JFrame;

public class Week07Lec08 extends JFrame {
    public static void main(String[] args) {
        new Week07Lec08();
    }

    public Week07Lec08() {
        // Configure frame
        setSize(500, 300);
        setLocation(1200, 500);

        // Add mouse listener
        addMouseListener(new LAB64());

        // Make visible
        setVisible(true);
    }
}
```

**File**: `Week07Lec08/src/week07lec08/LAB64.java`

```java
package week07lec08;

import java.awt.event.MouseEvent;
import java.awt.event.MouseListener;

public class LAB64 implements MouseListener {

    @Override
    public void mouseEntered(MouseEvent e) {
        System.out.println("She loves me!");
    }

    @Override
    public void mouseExited(MouseEvent e) {
        System.out.println("She doesn't love me!");
    }

    @Override
    public void mouseClicked(MouseEvent e) {
        System.out.println("x: " + e.getX() + "\ty: " + e.getY());
    }

    @Override
    public void mousePressed(MouseEvent e) {
        // Optional: Handle mouse press
    }

    @Override
    public void mouseReleased(MouseEvent e) {
        // Optional: Handle mouse release
    }
}
```

**Explanation:**
- `JFrame`: Creates main window
- `setSize(width, height)`: Set window dimensions
- `setLocation(x, y)`: Position window on screen
- `MouseListener`: Interface for mouse events
- `mouseEntered()`: Cursor enters component
- `mouseExited()`: Cursor leaves component
- `mouseClicked()`: Full click (press + release)
- `getX()`, `getY()`: Mouse coordinates
- Must implement all methods in MouseListener

**Output (Console):**
```
She loves me!      // When mouse enters window
x: 250    y: 150  // When clicked
She doesn't love me!  // When mouse exits
```

---

#### Exercise 2: BMI Calculator GUI

**File**: `Week07Lec08/src/week07lec08/BMI.java`

```java
package week07lec08;

import java.awt.BorderLayout;
import java.awt.Button;
import java.awt.Color;
import java.awt.Font;
import java.awt.GridLayout;
import java.awt.Label;
import java.awt.Panel;
import java.awt.TextField;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.text.DecimalFormat;

import javax.swing.JFrame;
import javax.swing.JOptionPane;

public class BMI implements ActionListener {
    JFrame x;
    Panel c, h2, w2, b2;
    Label h, w;
    TextField h1, w1;
    Button b;

    public BMI() {
        // Create main frame
        x = new JFrame();
        x.setSize(450, 150);
        x.setLocation(1200, 200);

        // Create center panel with grid layout
        c = new Panel();
        c.setLayout(new GridLayout(2, 2));

        // Height input
        h = new Label("Enter your height in meter:");
        h.setFont(new Font(Font.SANS_SERIF, Font.BOLD, 15));
        h1 = new TextField(20);
        h2 = new Panel();
        h2.add(h1);

        // Weight input
        w = new Label("Enter your weight in kg:");
        w.setFont(new Font(Font.SANS_SERIF, Font.BOLD, 15));
        w1 = new TextField(20);
        w2 = new Panel();
        w2.add(w1);

        // Add to center panel
        c.add(h);
        c.add(h2);
        c.add(w);
        c.add(w2);
        x.add(c, BorderLayout.CENTER);

        // Create button
        b = new Button("BMI Calculation");
        b.addActionListener(this);
        b2 = new Panel();
        b2.setBackground(Color.PINK);
        b2.add(b);
        x.add(b2, BorderLayout.SOUTH);

        // Display
        x.setVisible(true);
    }

    @Override
    public void actionPerformed(ActionEvent e) {
        try {
            if (e.getActionCommand() == "BMI Calculation") {
                // Get input values
                double h = Double.parseDouble(h1.getText());
                double w = Double.parseDouble(w1.getText());

                // Validate input
                if (h <= 0 || w <= 0) {
                    throw new Exception();
                }

                // Calculate BMI
                double bmi = w / Math.pow(h, 2);

                // Clear fields
                h1.setText("");
                w1.setText("");

                // Display result
                JOptionPane.showMessageDialog(x,
                    "Your BMI is: " + new DecimalFormat("#0.00").format(bmi));
            }
        } catch (Exception ex) {
            // Handle invalid input
            h1.setText(" ");
            w1.setText(" ");
            JOptionPane.showMessageDialog(x, "Invalid input!");
        }
    }

    public static void main(String[] args) {
        new BMI();
    }
}
```

**Explanation:**
- `GridLayout(2, 2)`: 2 rows, 2 columns
- `Label`: Display-only text component
- `TextField`: Single-line text input
- `Button`: Clickable button with text
- `BorderLayout`: 5 regions (N, S, E, W, CENTER)
- `DecimalFormat`: Format numbers for display
- `ActionListener`: Handle button clicks
- `JOptionPane`: Display dialog boxes
- Exception handling for invalid input
- BMI formula: weight / height²

**BMI Categories:**
- Under 18.5: Underweight
- 18.5-24.9: Normal
- 25-29.9: Overweight
- 30+: Obese

---

#### Exercise 3: Color Mixer with Checkboxes

**File**: `Week07Lec08/src/week07lec08/Colour.java`

```java
package week07lec08;

import java.awt.BorderLayout;
import java.awt.Checkbox;
import java.awt.Color;
import java.awt.Panel;
import java.awt.event.ItemEvent;
import java.awt.event.ItemListener;

import javax.swing.JFrame;

public class Colour implements ItemListener {
    JFrame x;
    Panel c, s;
    Checkbox r, g, b;

    public Colour() {
        // Create main frame
        x = new JFrame();
        x.setSize(500, 300);
        x.setLocation(1200, 300);

        // Create center panel (color display)
        c = new Panel();
        c.setBackground(Color.black);
        x.add(c, BorderLayout.CENTER);

        // Create checkboxes
        r = new Checkbox("RED");
        g = new Checkbox("GREEN");
        b = new Checkbox("BLUE");

        // Add item listeners
        r.addItemListener(this);
        g.addItemListener(this);
        b.addItemListener(this);

        // Create bottom panel for checkboxes
        s = new Panel();
        s.add(r);
        s.add(g);
        s.add(b);
        x.add(s, BorderLayout.SOUTH);

        // Display
        x.setVisible(true);
    }

    @Override
    public void itemStateChanged(ItemEvent e) {
        int red = 0, green = 0, blue = 0;

        // Check checkbox states
        if (r.getState()) {
            red = 255;
        }
        if (g.getState()) {
            green = 255;
        }
        if (b.getState()) {
            blue = 255;
        }

        // Update background color
        c.setBackground(new Color(red, green, blue));
    }

    public static void main(String[] args) {
        new Colour();
    }
}
```

**Explanation:**
- `Checkbox`: Toggleable option (can be independent)
- `ItemListener`: Handle checkbox state changes
- `getState()`: Check if checkbox is selected
- `Color(red, green, blue)`: Create RGB color
- `setBackground()`: Change component background
- Multiple checkboxes can be selected simultaneously
- Color mixing: 0 = off, 255 = full intensity

**Color Combinations:**
- None selected: Black (0, 0, 0)
- RED only: Red (255, 0, 0)
- GREEN only: Green (0, 255, 0)
- BLUE only: Blue (0, 0, 255)
- RED + GREEN: Yellow (255, 255, 0)
- RED + BLUE: Magenta (255, 0, 255)
- GREEN + BLUE: Cyan (0, 255, 255)
- All three: White (255, 255, 255)

---

#### Exercise 4: Gender Selection with Radio Buttons

**File**: `Week07(09)Lab08/src/week07/pkg09/lab08/Week0709Lab08.java`

```java
package week07.pkg09.lab08;

import java.awt.BorderLayout;
import java.awt.Color;
import java.awt.Font;
import java.awt.Label;
import java.awt.Panel;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

import javax.swing.ButtonGroup;
import javax.swing.JFrame;
import javax.swing.JRadioButton;

public class Week0709Lab08 implements ActionListener {
    JFrame x;
    Panel s;
    Label y;
    JRadioButton m, f;
    ButtonGroup z;

    public Week0709Lab08() {
        // Create main frame
        x = new JFrame();
        x.setSize(500, 300);
        x.setLocation(1200, 300);

        // Create center label
        y = new Label("Choose your gender:", Label.CENTER);
        y.setFont(new Font(Font.SANS_SERIF, Font.BOLD, 36));
        x.add(y, BorderLayout.CENTER);

        // Create radio buttons
        m = new JRadioButton("MALE");
        f = new JRadioButton("FEMALE");

        // Add action listeners
        m.addActionListener(this);
        f.addActionListener(this);

        // Group radio buttons (mutually exclusive)
        z = new ButtonGroup();
        z.add(m);
        z.add(f);

        // Create bottom panel
        s = new Panel();
        s.setBackground(Color.PINK);
        s.add(m);
        s.add(f);
        x.add(s, BorderLayout.SOUTH);

        // Display
        x.setVisible(true);
    }

    @Override
    public void actionPerformed(ActionEvent e) {
        if (e.getSource() == m) {
            y.setText("You are a man!");
        } else if (e.getSource() == f) {
            y.setText("You are a girl!");
        }
    }

    public static void main(String[] args) {
        new Week0709Lab08();
    }
}
```

**Explanation:**
- `JRadioButton`: Mutually exclusive option
- `ButtonGroup`: Group radio buttons for exclusivity
- Only one radio button in group can be selected
- `Label.CENTER`: Center text alignment
- `Font.SANS_SERIF`: Sans-serif font family
- `Font.BOLD`: Bold font style
- `getSource()`: Identify which component triggered event
- `setText()`: Update label text dynamically

**Key Differences:**
- **Checkbox**: Multiple can be selected
- **JRadioButton**: Only one can be selected (when in ButtonGroup)
- **JRadioButton** requires ButtonGroup for mutual exclusivity
- **Checkbox** is independent

**Output:**
- Select "MALE" → Label shows "You are a man!"
- Select "FEMALE" → Label shows "You are a girl!"

---

#### Exercise 5: Enhanced BMI Calculator with Categories

Here's an enhanced version of the BMI calculator that shows BMI categories:

```java
package week07lec08;

import java.awt.BorderLayout;
import java.awt.Button;
import java.awt.Color;
import java.awt.Font;
import java.awt.GridLayout;
import java.awt.Label;
import java.awt.Panel;
import java.awt.TextField;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.text.DecimalFormat;

import javax.swing.JFrame;
import javax.swing.JOptionPane;

public class BMIEnhanced implements ActionListener {
    JFrame x;
    Panel c, h2, w2, b2;
    Label h, w;
    TextField h1, w1;
    Button b;

    public BMIEnhanced() {
        x = new JFrame("BMI Calculator Enhanced");
        x.setSize(450, 180);
        x.setLocation(1200, 200);
        x.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        c = new Panel();
        c.setLayout(new GridLayout(2, 2, 5, 5));  // Add gaps

        h = new Label("Enter your height (m):");
        h.setFont(new Font(Font.SANS_SERIF, Font.BOLD, 14));
        h1 = new TextField(20);
        h2 = new Panel();
        h2.add(h1);

        w = new Label("Enter your weight (kg):");
        w.setFont(new Font(Font.SANS_SERIF, Font.BOLD, 14));
        w1 = new TextField(20);
        w2 = new Panel();
        w2.add(w1);

        c.add(h);
        c.add(h2);
        c.add(w);
        c.add(w2);
        x.add(c, BorderLayout.CENTER);

        b = new Button("Calculate BMI");
        b.addActionListener(this);
        b2 = new Panel();
        b2.setBackground(Color.PINK);
        b2.add(b);
        x.add(b2, BorderLayout.SOUTH);

        x.setVisible(true);
    }

    @Override
    public void actionPerformed(ActionEvent e) {
        try {
            double height = Double.parseDouble(h1.getText());
            double weight = Double.parseDouble(w1.getText());

            if (height <= 0 || weight <= 0) {
                throw new IllegalArgumentException("Values must be positive");
            }

            double bmi = weight / Math.pow(height, 2);
            DecimalFormat df = new DecimalFormat("#0.00");

            // Determine category
            String category;
            String advice;
            if (bmi < 18.5) {
                category = "Underweight";
                advice = "Consider consulting a nutritionist.";
            } else if (bmi < 25) {
                category = "Normal";
                advice = "Maintain your healthy lifestyle!";
            } else if (bmi < 30) {
                category = "Overweight";
                advice = "Consider increasing physical activity.";
            } else {
                category = "Obese";
                advice = "Please consult a healthcare provider.";
            }

            // Display detailed result
            String message = String.format(
                "Your BMI: %s\nCategory: %s\n\n%s",
                df.format(bmi), category, advice
            );

            JOptionPane.showMessageDialog(x, message, "BMI Result", JOptionPane.INFORMATION_MESSAGE);

            // Clear fields
            h1.setText("");
            w1.setText("");

        } catch (NumberFormatException ex) {
            JOptionPane.showMessageDialog(x, "Please enter valid numbers!", "Error", JOptionPane.ERROR_MESSAGE);
        } catch (IllegalArgumentException ex) {
            JOptionPane.showMessageDialog(x, ex.getMessage(), "Error", JOptionPane.ERROR_MESSAGE);
        }
    }

    public static void main(String[] args) {
        new BMIEnhanced();
    }
}
```

**Enhancements:**
- Added window title
- Added close operation
- Added gaps between grid cells
- BMI categorization
- Health advice
- Better error messages
- Clearer result display

---

### Lab 7 Summary

**Key Concepts Learned:**
1. **GUI Components**: JFrame, Panel, Label, TextField, Button, Checkbox, JRadioButton
2. **Layout Managers**: BorderLayout, GridLayout, FlowLayout
3. **Event Handling**: ActionListener, ItemListener, MouseListener
4. **Color Management**: RGB color model, setBackground()
5. **Input Validation**: Exception handling for user input
6. **User Feedback**: JOptionPane dialogs

**Best Practices:**
- Always set visible last (after adding components)
- Use appropriate layout managers
- Validate user input
- Provide clear feedback to users
- Handle exceptions gracefully
- Set meaningful window titles
- Use proper fonts and colors for readability

**Common Patterns:**
```java
// Pattern 1: Basic GUI setup
JFrame frame = new JFrame("Title");
frame.setSize(width, height);
frame.setLocation(x, y);
frame.add(component);
frame.setVisible(true);

// Pattern 2: Event handling
button.addActionListener(new ActionListener() {
    @Override
    public void actionPerformed(ActionEvent e) {
        // Handle event
    }
});

// Pattern 3: Input validation
try {
    double value = Double.parseDouble(textField.getText());
    if (value <= 0) {
        throw new IllegalArgumentException();
    }
} catch (Exception ex) {
    JOptionPane.showMessageDialog(frame, "Invalid input!");
}
```

---

## Module 4: Advanced OOP

### Week 08: Polymorphism

#### Learning Objectives
- Understand polymorphism types
- Master upcasting and downcasting
- Learn instanceof operator
- Practice runtime polymorphism

#### Key Concepts

**Types of Polymorphism:**
1. **Compile-time (Overloading)**: Same method name, different parameters
2. **Runtime (Overriding)**: Subclass provides its own implementation
3. **Type Promotion**: Automatic conversion

**Casting:**
- **Upcasting**: Subclass → Superclass (always safe)
- **Downcasting**: Superclass → Subclass (needs instanceof check)

#### Exercise 1: Polymorphism Demonstration

**File**: `Week08Lec06/src/polymorphism4/ClassA.java`

```java
package polymorphism4;

public class ClassA {
    protected String name = "ClassA";

    public ClassA() {
        System.out.println("ClassA constructor");
    }

    public void methodA() {
        System.out.println("ClassA.methodA() - " + name);
    }

    public void display() {
        System.out.println("This is ClassA");
    }
}
```

**File**: `Week08Lec06/src/polymorphism4/ClassB.java`

```java
package polymorphism4;

public class ClassB extends ClassA {
    protected String name = "ClassB";  // Field shadowing

    public ClassB() {
        super();
        System.out.println("ClassB constructor");
    }

    @Override
    public void methodA() {
        System.out.println("ClassB.methodA() - " + name);
    }

    public void methodB() {
        System.out.println("ClassB.methodB() - " + name);
    }

    @Override
    public void display() {
        System.out.println("This is ClassB (extends ClassA)");
    }
}
```

**File**: `Week08Lec06/src/polymorphism4/ClassC.java`

```java
package polymorphism4;

public class ClassC extends ClassB {
    protected String name = "ClassC";  // Field shadowing

    public ClassC() {
        super();
        System.out.println("ClassC constructor");
    }

    @Override
    public void methodA() {
        System.out.println("ClassC.methodA() - " + name);
    }

    public void methodC() {
        System.out.println("ClassC.methodC() - " + name);
    }

    @Override
    public void display() {
        System.out.println("This is ClassC (extends ClassB)");
    }
}
```

**File**: `Week08Lec06/src/polymorphism4/NewMain.java`

```java
package polymorphism4;

public class NewMain {
    public static void main(String[] args) {
        System.out.println("=== Polymorphism Demonstration ===\n");

        // Upcasting examples
        System.out.println("1. Upcasting (always safe):");
        ClassA a1 = new ClassB();  // Upcast
        a1.methodA();              // Calls ClassB.methodA()
        a1.display();              // Calls ClassB.display()
        // a1.methodB();           // ERROR: ClassA doesn't have methodB()

        System.out.println("\n2. Downcasting (needs instanceof):");
        ClassA a2 = new ClassC();
        if (a2 instanceof ClassB) {
            ClassB b2 = (ClassB) a2;  // Safe downcast
            b2.methodA();             // Calls ClassC.methodA()
            b2.methodB();             // ClassB has methodB()
        }

        if (a2 instanceof ClassC) {
            ClassC c2 = (ClassC) a2;  // Safe downcast
            c2.methodA();             // Calls ClassC.methodA()
            c2.methodB();             // Inherited from ClassB
            c2.methodC();             // ClassC has methodC()
        }

        System.out.println("\n3. Runtime type determination:");
        ClassA[] objects = {
            new ClassA(),
            new ClassB(),
            new ClassC()
        };

        for (ClassA obj : objects) {
            System.out.print("Object: ");
            obj.display();
            System.out.print("  Type: ");

            if (obj instanceof ClassC) {
                System.out.println("ClassC");
                ((ClassC) obj).methodC();
            } else if (obj instanceof ClassB) {
                System.out.println("ClassB");
                ((ClassB) obj).methodB();
            } else {
                System.out.println("ClassA");
            }
        }
    }
}
```

**Explanation:**
- Upcasting: always safe, loses access to subclass methods
- Downcasting: risky, use instanceof to check
- Runtime polymorphism: method determined by actual object type
- Field shadowing: subclass field hides superclass field
- instanceof: checks if object is instance of class

**Output:**
```
=== Polymorphism Demonstration ===

1. Upcasting (always safe):
ClassA constructor
ClassB constructor
ClassB.methodA() - ClassB
This is ClassB (extends ClassA)

2. Downcasting (needs instanceof):
ClassA constructor
ClassB constructor
ClassC constructor
ClassC.methodA() - ClassC
ClassB.methodA() - ClassC
ClassB.methodB() - ClassC
ClassC.methodA() - ClassC
ClassC.methodA() - ClassC
ClassC.methodB() - ClassC
ClassC.methodC() - ClassC

3. Runtime type determination:
ClassA constructor
Object: This is ClassA
  Type: ClassA
ClassA constructor
ClassB constructor
Object: This is ClassB (extends ClassA)
  Type: ClassB
ClassB.methodB() - ClassB
ClassA constructor
ClassB constructor
ClassC constructor
Object: This is ClassC (extends ClassB)
  Type: ClassC
ClassC.methodC() - ClassC
```

---

### Lab 08: String and Array Utilities

#### Learning Objectives
- Master String manipulation
- Learn Scanner vs StringTokenizer
- Work with file I/O
- Use Arrays utility class

#### Exercise 1: File Processing

**File**: `Week08Lab09/src/week08lab09/Week08Lab09.java`

```java
package week08lab09;

import java.io.File;
import java.io.FileNotFoundException;
import java.util.Scanner;

public class Week08Lab09 {
    public static void main(String[] args) {
        try {
            // Open file
            File file = new File("input.txt");
            Scanner scanner = new Scanner(file);

            int lines = 0;
            int words = 0;
            int characters = 0;

            // Process file line by line
            while (scanner.hasNextLine()) {
                String line = scanner.nextLine();
                lines++;

                // Count characters
                characters += line.length();

                // Count words
                String[] wordArray = line.split("\\s+");
                words += wordArray.length;
            }

            scanner.close();

            // Display results
            System.out.println("File Statistics:");
            System.out.println("Lines: " + lines);
            System.out.println("Words: " + words);
            System.out.println("Characters: " + characters);

        } catch (FileNotFoundException e) {
            System.out.println("File not found: " + e.getMessage());
        }
    }
}
```

**Explanation:**
- `Scanner`: versatile for parsing
- `hasNextLine()`: check if more lines exist
- `nextLine()`: read entire line
- `split("\\s+")`: split by whitespace
- Always close resources (or use try-with-resources)

---

#### Exercise 2: Scanner vs StringTokenizer

**File**: `Week08Lab09/src/week08lab09/Exe2.java`

```java
package week08lab09;

import java.util.Scanner;
import java.util.StringTokenizer;

public class Exe2 {
    public static void main(String[] args) {
        String input = "Java,Python,C++,JavaScript,Go";

        System.out.println("Original string: " + input);
        System.out.println();

        // Method 1: Scanner with delimiter
        System.out.println("Using Scanner:");
        Scanner scanner = new Scanner(input);
        scanner.useDelimiter(",");

        while (scanner.hasNext()) {
            System.out.println("  " + scanner.next());
        }
        scanner.close();

        System.out.println();

        // Method 2: StringTokenizer
        System.out.println("Using StringTokenizer:");
        StringTokenizer tokenizer = new StringTokenizer(input, ",");

        while (tokenizer.hasMoreTokens()) {
            System.out.println("  " + tokenizer.nextToken());
        }

        System.out.println();

        // Method 3: String.split()
        System.out.println("Using String.split():");
        String[] tokens = input.split(",");

        for (String token : tokens) {
            System.out.println("  " + token);
        }
    }
}
```

**Explanation:**
- **Scanner**: flexible, can read from various sources
- **StringTokenizer**: faster for simple tokenization (legacy)
- **String.split()**: returns array, most convenient
- Use Scanner for complex parsing, split() for simple cases

---

#### Exercise 3: Array Sorting

**File**: `Week08Lab09/src/week08lab09/Exe3.java`

```java
package week08lab09;

import java.util.Arrays;
import java.util.Random;

public class Exe3 {
    public static void main(String[] args) {
        // Create array with random numbers
        int[] numbers = new int[10];
        Random random = new Random();

        System.out.println("Original array:");
        for (int i = 0; i < numbers.length; i++) {
            numbers[i] = random.nextInt(100) + 1;
            System.out.print(numbers[i] + " ");
        }
        System.out.println();

        // Sort array
        Arrays.sort(numbers);

        System.out.println("\nSorted array:");
        for (int num : numbers) {
            System.out.print(num + " ");
        }
        System.out.println();

        // Binary search
        int target = 50;
        int index = Arrays.binarySearch(numbers, target);

        System.out.println("\nSearching for " + target + ":");
        if (index >= 0) {
            System.out.println("Found at index: " + index);
        } else {
            System.out.println("Not found");
        }

        // Fill array
        int[] filled = new int[5];
        Arrays.fill(filled, 42);
        System.out.println("\nFilled array: " + Arrays.toString(filled));

        // Compare arrays
        int[] arr1 = {1, 2, 3};
        int[] arr2 = {1, 2, 3};
        int[] arr3 = {1, 2, 4};

        System.out.println("\nArray comparisons:");
        System.out.println("arr1 equals arr2: " + Arrays.equals(arr1, arr2));
        System.out.println("arr1 equals arr3: " + Arrays.equals(arr1, arr3));
    }
}
```

**Explanation:**
- `Arrays.sort()`: sorts array (uses quicksort)
- `Arrays.binarySearch()`: searches sorted array
- `Arrays.fill()`: fills array with value
- `Arrays.equals()`: compares arrays
- `Arrays.toString()`: converts array to string

---

### Week 09: Abstract Classes and Interfaces

#### Learning Objectives
- Understand abstract classes
- Master interfaces
- Learn multiple interface implementation
- Practice polymorphism with abstract classes

#### Key Concepts

**Abstract Classes:**
- Cannot be instantiated
- Can have abstract and concrete methods
- Can have instance variables
- Single inheritance

**Interfaces:**
- Purely abstract (all methods abstract)
- All fields are public static final
- Multiple inheritance
- Define contracts

#### Exercise 1: Abstract Shape Class

**File**: `Week09Lec07/src/week09lec07/Shape.java`

```java
package week09lec07;

public abstract class Shape {
    private String color;

    public Shape(String color) {
        this.color = color;
    }

    // Abstract method: must be implemented by subclasses
    public abstract double calculateArea();

    // Concrete method: inherited by all subclasses
    public void display() {
        System.out.println("Shape color: " + color);
        System.out.println("Area: " + calculateArea());
    }

    public String getColor() {
        return color;
    }

    public void setColor(String color) {
        this.color = color;
    }
}
```

**File**: `Week09Lec07/src/week09lec07/Circle.java`

```java
package week09lec07;

public class Circle extends Shape {
    private double radius;

    public Circle(String color, double radius) {
        super(color);
        this.radius = radius;
    }

    @Override
    public double calculateArea() {
        return Math.PI * radius * radius;
    }

    public double getRadius() {
        return radius;
    }

    public void setRadius(double radius) {
        this.radius = radius;
    }
}
```

**File**: `Week09Lec07/src/week09lec07/Rectangle.java`

```java
package week09lec07;

public class Rectangle extends Shape {
    private double width;
    private double height;

    public Rectangle(String color, double width, double height) {
        super(color);
        this.width = width;
        this.height = height;
    }

    @Override
    public double calculateArea() {
        return width * height;
    }

    public double getWidth() {
        return width;
    }

    public void setWidth(double width) {
        this.width = width;
    }

    public double getHeight() {
        return height;
    }

    public void setHeight(double height) {
        this.height = height;
    }
}
```

**File**: `Week09Lec07/src/week09lec07/Triangle.java`

```java
package week09lec07;

public class Triangle extends Shape {
    private double base;
    private double height;

    public Triangle(String color, double base, double height) {
        super(color);
        this.base = base;
        this.height = height;
    }

    @Override
    public double calculateArea() {
        return 0.5 * base * height;
    }

    public double getBase() {
        return base;
    }

    public void setBase(double base) {
        this.base = base;
    }

    public double getHeight() {
        return height;
    }

    public void setHeight(double height) {
        this.height = height;
    }
}
```

**File**: `Week09Lec07/src/week09lec07/Week09Lec07.java`

```java
package week09lec07;

public class Week09Lec07 {
    public static void main(String[] args) {
        // Cannot instantiate abstract class
        // Shape s = new Shape("Red");  // ERROR!

        // Create concrete shapes
        Circle circle = new Circle("Red", 5.0);
        Rectangle rectangle = new Rectangle("Blue", 4.0, 6.0);
        Triangle triangle = new Triangle("Green", 8.0, 6.0);

        // Display each shape
        System.out.println("=== Shape Calculations ===\n");

        circle.display();
        System.out.println();

        rectangle.display();
        System.out.println();

        triangle.display();
        System.out.println();

        // Polymorphism with abstract class
        System.out.println("=== Polymorphism ===\n");
        Shape[] shapes = {circle, rectangle, triangle};

        double totalArea = 0;
        for (Shape shape : shapes) {
            shape.display();
            totalArea += shape.calculateArea();
            System.out.println();
        }

        System.out.println("Total area: " + totalArea);
    }
}
```

**Explanation:**
- Abstract classes define common structure
- Abstract methods must be implemented
- Concrete classes provide implementations
- Polymorphism works with abstract classes
- Cannot create objects of abstract class

**Output:**
```
=== Shape Calculations ===

Shape color: Red
Area: 78.53981633974483

Shape color: Blue
Area: 24.0

Shape color: Green
Area: 24.0

=== Polymorphism ===

Shape color: Red
Area: 78.53981633974483

Shape color: Blue
Area: 24.0

Shape color: Green
Area: 24.0

Total area: 126.53981633974483
```

---

#### Exercise 2: Interfaces

**File**: `Week09Lec07/src/interfacesample/InterfaceA.java`

```java
package interfacesample;

public interface InterfaceA {
    // All methods are public and abstract by default
    double methodA1();
    double methodA2();

    // All fields are public, static, and final by default
    double CONSTANT_A = 100.0;
}
```

**File**: `Week09Lec07/src/interfacesample/InterfaceB.java`

```java
package interfacesample;

// Interface can extend another interface
public interface InterfaceB extends InterfaceA {
    double methodB1();
    double methodB2();

    double CONSTANT_B = 200.0;
}
```

**File**: `Week09Lec07/src/interfacesample/ClassA.java`

```java
package interfacesample;
import java.awt.event.ActionListener;
import javax.swing.JButton;
import javax.swing.JFrame;

public class ClassA implements InterfaceA, ActionListener {
    private JButton button;

    public ClassA() {
        button = new JButton("Click me");
        button.addActionListener(this);
    }

    @Override
    public double methodA1() {
        return CONSTANT_A * 1.5;
    }

    @Override
    public double methodA2() {
        return CONSTANT_A * 2.5;
    }

    @Override
    public void actionPerformed(java.awt.event.ActionEvent e) {
        System.out.println("Button clicked!");
        System.out.println("methodA1(): " + methodA1());
        System.out.println("methodA2(): " + methodA2());
    }
}
```

**File**: `Week09Lec07/src/interfacesample/ClassB.java`

```java
package interfacesample;

public class ClassB implements InterfaceB {
    @Override
    public double methodA1() {
        return CONSTANT_A * 2.0;
    }

    @Override
    public double methodA2() {
        return CONSTANT_A * 3.0;
    }

    @Override
    public double methodB1() {
        return CONSTANT_B * 1.5;
    }

    @Override
    public double methodB2() {
        return CONSTANT_B * 2.5;
    }
}
```

**Explanation:**
- Interfaces define contracts
- All methods are abstract (Java 8+ allows default methods)
- All fields are constants (public static final)
- Classes can implement multiple interfaces
- Interfaces can extend other interfaces

---

### Lab 09: GUI Basics

#### Learning Objectives
- Create JFrame windows
- Use layout managers
- Handle events
- Create interactive GUIs

#### Exercise 1: Basic GUI with Event Handling

**File**: `Week07Lec08/src/week07lec08/Week07Lec08.java`

```java
package week07lec08;

import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class Week07Lec08 extends JFrame {
    private JLabel label;
    private JButton button;
    private int clickCount = 0;

    public Week07Lec08() {
        // Set frame properties
        setTitle("My First GUI");
        setSize(300, 200);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLocationRelativeTo(null);  // Center on screen

        // Create components
        label = new JLabel("Click count: 0", SwingConstants.CENTER);
        button = new JButton("Click Me");

        // Add event listener
        button.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                clickCount++;
                label.setText("Click count: " + clickCount);
            }
        });

        // Add components to frame
        setLayout(new BorderLayout());
        add(label, BorderLayout.CENTER);
        add(button, BorderLayout.SOUTH);
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(new Runnable() {
            @Override
            public void run() {
                Week07Lec08 gui = new Week07Lec08();
                gui.setVisible(true);
            }
        });
    }
}
```

**Explanation:**
- `JFrame`: main window
- `JLabel`: display text
- `JButton`: clickable button
- `ActionListener`: handles button clicks
- `BorderLayout`: default layout
- Always create GUI on Event Dispatch Thread

---

#### Exercise 2: BMI Calculator

**File**: `Week07Lec08/src/week07lec08/BMI.java`

```java
package week07lec08;

import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class BMI extends JFrame {
    private JTextField weightField, heightField, resultField;
    private JButton calculateButton, clearButton;

    public BMI() {
        setTitle("BMI Calculator");
        setSize(350, 250);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLocationRelativeTo(null);

        // Create components
        JLabel weightLabel = new JLabel("Weight (kg):");
        JLabel heightLabel = new JLabel("Height (m):");
        JLabel resultLabel = new JLabel("BMI:");

        weightField = new JTextField(10);
        heightField = new JTextField(10);
        resultField = new JTextField(10);
        resultField.setEditable(false);

        calculateButton = new JButton("Calculate");
        clearButton = new JButton("Clear");

        // Event listeners
        calculateButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                calculateBMI();
            }
        });

        clearButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                weightField.setText("");
                heightField.setText("");
                resultField.setText("");
            }
        });

        // Layout
        JPanel panel = new JPanel(new GridLayout(4, 2, 5, 5));
        panel.add(weightLabel);
        panel.add(weightField);
        panel.add(heightLabel);
        panel.add(heightField);
        panel.add(resultLabel);
        panel.add(resultField);
        panel.add(calculateButton);
        panel.add(clearButton);

        add(panel);
    }

    private void calculateBMI() {
        try {
            double weight = Double.parseDouble(weightField.getText());
            double height = Double.parseDouble(heightField.getText());

            if (weight <= 0 || height <= 0) {
                JOptionPane.showMessageDialog(this,
                    "Weight and height must be positive!",
                    "Error",
                    JOptionPane.ERROR_MESSAGE);
                return;
            }

            double bmi = weight / (height * height);
            resultField.setText(String.format("%.2f", bmi));

            String category;
            if (bmi < 18.5) {
                category = "Underweight";
            } else if (bmi < 25) {
                category = "Normal";
            } else if (bmi < 30) {
                category = "Overweight";
            } else {
                category = "Obese";
            }

            JOptionPane.showMessageDialog(this,
                "BMI: " + String.format("%.2f", bmi) + "\n" +
                "Category: " + category,
                "BMI Result",
                JOptionPane.INFORMATION_MESSAGE);

        } catch (NumberFormatException ex) {
            JOptionPane.showMessageDialog(this,
                "Please enter valid numbers!",
                "Error",
                JOptionPane.ERROR_MESSAGE);
        }
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(() -> {
            BMI bmi = new BMI();
            bmi.setVisible(true);
        });
    }
}
```

**Explanation:**
- Input validation
- Exception handling for invalid input
- JOptionPane for dialogs
- GridLayout for organized layout
- BMI calculation and categorization

---

## Module 5: Specialized Topics

### Week 10: Exception Handling

#### Learning Objectives
- Understand exception types
- Master try-catch-finally blocks
- Learn custom exceptions
- Handle checked vs unchecked exceptions

#### Key Concepts

**Exception Hierarchy:**
```
Throwable
├── Error (serious problems, don't catch)
└── Exception
    ├── RuntimeException (unchecked)
    └── Other exceptions (checked)
```

**Types:**
- **Checked**: Must be declared or caught
- **Unchecked**: RuntimeException and its subclasses

#### Exercise 1: Basic Exception Handling

**File**: `Week10Lec09/src/week10lec09/TryCatch.java`

```java
package week10lec09;

public class TryCatch {
    public static void main(String[] args) {
        int[] numbers = {1, 2, 3};

        System.out.println("=== Try-Catch Demo ===\n");

        // This will cause ArrayIndexOutOfBoundsException
        try {
            System.out.println("Accessing index 5:");
            System.out.println(numbers[5]);  // Error!
            System.out.println("This line won't execute");
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Caught exception: " + e.getMessage());
            System.out.println("Exception type: " + e.getClass().getSimpleName());
        }

        System.out.println("\nProgram continues after exception");

        // Safe access
        try {
            System.out.println("\nAccessing index 2:");
            System.out.println(numbers[2]);
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Caught exception: " + e.getMessage());
        }
    }
}
```

**Explanation:**
- Try block: code that might throw exception
- Catch block: handle specific exception
- Program continues after handling
- Use specific exception types

---

#### Exercise 2: Multiple Catch Blocks

**File**: `Week10Lec09/src/week10lec09/Multiple.java`

```java
package week10lec09;

public class Multiple {
    public static void main(String[] args) {
        System.out.println("=== Multiple Catch Blocks ===\n");

        // Example 1: ArithmeticException
        try {
            int result = 10 / 0;
        } catch (ArithmeticException e) {
            System.out.println("Caught ArithmeticException: " + e.getMessage());
        }

        // Example 2: NumberFormatException
        try {
            String str = "abc";
            int num = Integer.parseInt(str);
        } catch (NumberFormatException e) {
            System.out.println("Caught NumberFormatException: " + e.getMessage());
        }

        // Example 3: Multiple catch blocks
        try {
            String[] inputs = {"10", "0", "abc"};
            int a = Integer.parseInt(inputs[0]);
            int b = Integer.parseInt(inputs[1]);
            int result = a / b;
        } catch (ArithmeticException e) {
            System.out.println("Division by zero!");
        } catch (NumberFormatException e) {
            System.out.println("Invalid number format!");
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Array index out of bounds!");
        }

        // Catching multiple exceptions (Java 7+)
        try {
            // Code that might throw multiple exceptions
            String str = "abc";
            int num = Integer.parseInt(str);
        } catch (NumberFormatException | ArrayIndexOutOfBoundsException e) {
            System.out.println("Caught: " + e.getClass().getSimpleName());
        }
    }
}
```

**Explanation:**
- Multiple catch blocks for different exceptions
- Order matters: specific before general
- Java 7+: catch multiple exceptions with `|`
- Always catch most specific exceptions first

---

#### Exercise 3: Finally Block

**File**: `Week10Lec09/src/week10lec09/Finally.java`

```java
package week10lec09;

public class Finally {
    public static void main(String[] args) {
        System.out.println("=== Finally Block Demo ===\n");

        // Example 1: Exception occurs
        try {
            System.out.println("Inside try block");
            int result = 10 / 0;
        } catch (ArithmeticException e) {
            System.out.println("Caught: " + e.getMessage());
        } finally {
            System.out.println("Finally block always executes");
        }

        System.out.println();

        // Example 2: No exception
        try {
            System.out.println("Inside try block (no exception)");
            int result = 10 / 2;
            System.out.println("Result: " + result);
        } catch (ArithmeticException e) {
            System.out.println("Caught: " + e.getMessage());
        } finally {
            System.out.println("Finally block still executes");
        }

        System.out.println();

        // Example 3: Finally with return
        System.out.println("Method with return: " + methodWithFinally());

        System.out.println();

        // Example 4: Finally overriding return
        System.out.println("Finally overrides return: " + methodFinallyOverrides());
    }

    public static int methodWithFinally() {
        try {
            return 1;
        } finally {
            System.out.println("Finally block (after return)");
        }
    }

    public static int methodFinallyOverrides() {
        try {
            return 1;
        } catch (Exception e) {
            return 2;
        } finally {
            System.out.println("Finally block (will override return)");
            return 3;  // This overrides the return!
        }
    }
}
```

**Explanation:**
- Finally block always executes
- Executes even if exception occurs
- Executes even if return statement
- Finally can override return value (avoid this!)
- Use for cleanup (close resources)

**Output:**
```
=== Finally Block Demo ===

Inside try block
Caught: / by zero
Finally block always executes

Inside try block (no exception)
Result: 5
Finally block still executes

Finally block (after return)
Method with return: 1

Finally block (will override return)
Finally overrides return: 3
```

---

#### Exercise 4: Custom Exception

**File**: `Week10Lec09/src/exe4/NotEnoughMoney.java`

```java
package exe4;

// Custom checked exception
public class NotEnoughMoney extends Exception {
    private double required;
    private double available;

    public NotEnoughMoney(double required, double available) {
        super("Insufficient funds: Required $" + required + ", Available $" + available);
        this.required = required;
        this.available = available;
    }

    public double getRequired() {
        return required;
    }

    public double getAvailable() {
        return available;
    }

    public double getShortage() {
        return required - available;
    }
}
```

**File**: `Week10Lec09/src/exe4/Account.java`

```java
package exe4;

public class Account {
    private String accountNumber;
    private double balance;

    public Account(String accountNumber, double balance) {
        this.accountNumber = accountNumber;
        this.balance = balance;
    }

    // Method that throws checked exception
    public void withdraw(double amount) throws NotEnoughMoney {
        if (amount > balance) {
            throw new NotEnoughMoney(amount, balance);
        }
        balance -= amount;
        System.out.println("Withdrawn: $" + amount);
    }

    public void deposit(double amount) {
        if (amount <= 0) {
            throw new IllegalArgumentException("Deposit amount must be positive");
        }
        balance += amount;
        System.out.println("Deposited: $" + amount);
    }

    public double getBalance() {
        return balance;
    }

    public String getAccountNumber() {
        return accountNumber;
    }
}
```

**File**: `Week10Lec09/src/exe4/NewMain.java`

```java
package exe4;

public class NewMain {
    public static void main(String[] args) {
        Account account = new Account("ACC001", 1000.00);

        try {
            System.out.println("Initial balance: $" + account.getBalance());

            // Successful withdrawal
            account.withdraw(500.00);
            System.out.println("Current balance: $" + account.getBalance());

            // Failed withdrawal (custom exception)
            account.withdraw(1000.00);  // Throws NotEnoughMoney

        } catch (NotEnoughMoney e) {
            System.out.println("\nException caught: " + e.getMessage());
            System.out.println("Shortage: $" + e.getShortage());
        }

        // Unchecked exception (IllegalArgumentException)
        try {
            account.deposit(-100);
        } catch (IllegalArgumentException e) {
            System.out.println("\nIllegalArgumentException: " + e.getMessage());
        }
    }
}
```

**Explanation:**
- Create custom exception by extending Exception
- Checked exception: must be declared or caught
- Unchecked exception: extends RuntimeException
- Add useful information to exception
- Use meaningful exception messages

**Output:**
```
Initial balance: $1000.0
Withdrawn: $500.0
Current balance: $500.0

Exception caught: Insufficient funds: Required $1000.0, Available $500.0
Shortage: $500.0

IllegalArgumentException: Deposit amount must be positive
```

---

### Lab 10: Account Inheritance System

#### Learning Objectives
- Apply inheritance in practical scenario
- Understand method overriding
- Work with abstract classes
- Implement business logic

#### Exercise: Account Hierarchy

**File**: `Week10Lab06/src/week10lab06/Account.java`

```java
package week10lab06;

public abstract class Account {
    protected String accountNumber;
    protected String holderName;
    protected double balance;

    public Account(String accountNumber, String holderName, double balance) {
        this.accountNumber = accountNumber;
        this.holderName = holderName;
        this.balance = balance;
    }

    public abstract void withdraw(double amount);

    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            System.out.println("Deposited: $" + amount);
        }
    }

    public void display() {
        System.out.println("Account: " + accountNumber);
        System.out.println("Holder: " + holderName);
        System.out.println("Balance: $" + balance);
    }

    // Getters and setters
    public String getAccountNumber() { return accountNumber; }
    public String getHolderName() { return holderName; }
    public double getBalance() { return balance; }
}
```

**File**: `Week10Lab06/src/week10lab06/SavingAccount.java`

```java
package week10lab06;

public class SavingAccount extends Account {
    private double interestRate;

    public SavingAccount(String accountNumber, String holderName,
                        double balance, double interestRate) {
        super(accountNumber, holderName, balance);
        this.interestRate = interestRate;
    }

    @Override
    public void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
            System.out.println("Withdrawn: $" + amount + " (Savings)");
        } else {
            System.out.println("Insufficient funds in savings account!");
        }
    }

    public void addInterest() {
        double interest = balance * (interestRate / 100);
        balance += interest;
        System.out.println("Interest added: $" + interest);
    }

    public double getInterestRate() {
        return interestRate;
    }
}
```

**File**: `Week10Lab06/src/week10lab06/CheckingAccount.java`

```java
package week10lab06;

public class CheckingAccount extends Account {
    private double overdraftLimit;

    public CheckingAccount(String accountNumber, String holderName,
                          double balance, double overdraftLimit) {
        super(accountNumber, holderName, balance);
        this.overdraftLimit = overdraftLimit;
    }

    @Override
    public void withdraw(double amount) {
        if (amount > 0 && (balance + overdraftLimit) >= amount) {
            balance -= amount;
            System.out.println("Withdrawn: $" + amount + " (Checking)");

            if (balance < 0) {
                System.out.println("Warning: Account in overdraft!");
            }
        } else {
            System.out.println("Exceeds overdraft limit!");
        }
    }

    public double getOverdraftLimit() {
        return overdraftLimit;
    }
}
```

**File**: `Week10Lab06/src/week10lab06/Week10Lab06.java`

```java
package week10lab06;

public class Week10Lab06 {
    public static void main(String[] args) {
        System.out.println("=== Account System Demo ===\n");

        // Create accounts
        SavingAccount savings = new SavingAccount("SAV001", "Alice", 1000.00, 2.5);
        CheckingAccount checking = new CheckingAccount("CHK001", "Bob", 500.00, 200.00);

        // Test savings account
        System.out.println("Savings Account:");
        savings.display();
        savings.deposit(500.00);
        savings.withdraw(200.00);
        savings.withdraw(2000.00);  // Insufficient funds
        savings.addInterest();
        System.out.println();

        // Test checking account
        System.out.println("Checking Account:");
        checking.display();
        checking.deposit(300.00);
        checking.withdraw(400.00);
        checking.withdraw(600.00);  // Uses overdraft
        checking.withdraw(500.00);  // Exceeds limit
        System.out.println();

        // Polymorphism
        System.out.println("Polymorphism Demo:");
        Account[] accounts = {savings, checking};

        for (Account acc : accounts) {
            acc.display();
            System.out.println();
        }
    }
}
```

**Explanation:**
- Abstract class defines common structure
- Subclasses implement specific behavior
- Overriding provides specialized functionality
- Overdraft feature in checking accounts
- Polymorphism with array of accounts

**Output:**
```
=== Account System Demo ===

Savings Account:
Account: SAV001
Holder: Alice
Balance: $1000.0
Deposited: $500.0
Withdrawn: $200.0 (Savings)
Insufficient funds in savings account!
Interest added: $32.5

Checking Account:
Account: CHK001
Holder: Bob
Balance: $500.0
Deposited: $300.0
Withdrawn: $400.0 (Checking)
Withdrawn: $600.0 (Checking)
Warning: Account in overdraft!
Exceeds overdraft limit!

Polymorphism Demo:
Account: SAV001
Holder: Alice
Balance: $1332.5

Account: CHK001
Holder: Bob
Balance: $-200.0
```

---

### Week 12: Binary I/O and Serialization

#### Learning Objectives
- Understand serialization
- Work with ObjectInputStream/ObjectOutputStream
- Learn file persistence
- Handle field shadowing

#### Exercise: Student Serialization

**File**: `Week12Binary/src/week12binary/Student.java`

```java
package week12binary;

import java.io.Serializable;

public class Student implements Serializable {
    private String name;
    private int pin;
    private transient double balance;  // transient = not serialized

    public Student(String name, int pin, double balance) {
        this.name = name;
        this.pin = pin;
        this.balance = balance;
    }

    public void display() {
        System.out.println("Name: " + name);
        System.out.println("PIN: " + pin);
        System.out.println("Balance: $" + balance);
    }

    // Getters and setters
    public String getName() { return name; }
    public int getPin() { return pin; }
    public double getBalance() { return balance; }
}
```

**File**: `Week12Binary/src/week12binary/Write.java`

```java
package week12binary;

import java.io.*;

public class Write {
    public static void main(String[] args) {
        // Create student array
        Student[] students = {
            new Student("Alice", 1234, 1000.00),
            new Student("Bob", 5678, 1500.00),
            new Student("Charlie", 9012, 500.00)
        };

        // Write to file
        try {
            ObjectOutputStream oos = new ObjectOutputStream(
                new FileOutputStream("Tuesday.txt"));

            // Write the entire array
            oos.writeObject(students);

            oos.close();
            System.out.println("Students saved to file successfully!");

        } catch (IOException e) {
            System.out.println("Error writing to file: " + e.getMessage());
        }
    }
}
```

**File**: `Week12Binary/src/week12binary/Read.java`

```java
package week12binary;

import java.io.*;

public class Read {
    public static void main(String[] args) {
        try {
            ObjectInputStream ois = new ObjectInputStream(
                new FileInputStream("Tuesday.txt"));

            // Read the student array
            Student[] students = (Student[]) ois.readObject();

            ois.close();

            // Display students
            System.out.println("Students loaded from file:");
            System.out.println("================================");

            for (Student s : students) {
                s.display();
                System.out.println();
            }

        } catch (IOException | ClassNotFoundException e) {
            System.out.println("Error reading from file: " + e.getMessage());
        }
    }
}
```

**Explanation:**
- `Serializable`: marker interface for serialization
- `ObjectOutputStream`: writes objects to file
- `ObjectInputStream`: reads objects from file
- `transient`: fields not serialized (sensitive data)
- Binary format (not human-readable)
- Must catch ClassNotFoundException

---

### Lab 12: Employee Management System

#### Learning Objectives
- Implement interface-based design
- Create polymorphic employee types
- Calculate different salary structures
- Apply SOLID principles

#### Exercise: Employee Hierarchy

**File**: `Week12Lab07/src/week12lab07/Payable.java`

```java
package week12lab07;

public interface Payable {
    double getSalary();
    String getName();
}
```

**File**: `Week12Lab07/src/week12lab07/Employee.java`

```java
package week12lab07;

public abstract class Employee implements Payable {
    protected String name;
    protected int id;

    public Employee(String name, int id) {
        this.name = name;
        this.id = id;
    }

    // Abstract method: must be implemented by subclasses
    public abstract double getWeeklyHours();

    @Override
    public String getName() {
        return name;
    }

    public int getId() {
        return id;
    }

    public void display() {
        System.out.println("ID: " + id + ", Name: " + name);
    }
}
```

**File**: `Week12Lab07/src/week12lab07/FullTime.java`

```java
package week12lab07;

public class FullTime extends Employee {
    private double monthlySalary;

    public FullTime(String name, int id, double monthlySalary) {
        super(name, id);
        this.monthlySalary = monthlySalary;
    }

    @Override
    public double getSalary() {
        return monthlySalary;
    }

    @Override
    public double getWeeklyHours() {
        return 40;  // Standard full-time hours
    }

    @Override
    public void display() {
        super.display();
        System.out.println("Type: Full-Time");
        System.out.println("Monthly Salary: $" + monthlySalary);
        System.out.println("Weekly Hours: " + getWeeklyHours());
    }
}
```

**File**: `Week12Lab07/src/week12lab07/PartTime.java`

```java
package week12lab07;

public class PartTime extends Employee {
    private double hourlyRate;
    private double hoursWorked;

    public PartTime(String name, int id, double hourlyRate, double hoursWorked) {
        super(name, id);
        this.hourlyRate = hourlyRate;
        this.hoursWorked = hoursWorked;
    }

    @Override
    public double getSalary() {
        return hourlyRate * hoursWorked;
    }

    @Override
    public double getWeeklyHours() {
        return hoursWorked;
    }

    public void setHoursWorked(double hours) {
        this.hoursWorked = hours;
    }

    @Override
    public void display() {
        super.display();
        System.out.println("Type: Part-Time");
        System.out.println("Hourly Rate: $" + hourlyRate);
        System.out.println("Hours Worked: " + hoursWorked);
        System.out.println("Weekly Salary: $" + getSalary());
    }
}
```

**File**: `Week12Lab07/src/week12lab07/Assistant.java`

```java
package week12lab07;

public class Assistant extends Employee {
    private String department;

    public Assistant(String name, int id, String department) {
        super(name, id);
        this.department = department;
    }

    @Override
    public double getSalary() {
        return 0;  // Assistants may not have salary
    }

    @Override
    public double getWeeklyHours() {
        return 20;  // Typical assistant hours
    }

    @Override
    public void display() {
        super.display();
        System.out.println("Type: Assistant");
        System.out.println("Department: " + department);
        System.out.println("Weekly Hours: " + getWeeklyHours());
    }
}
```

**File**: `Week12Lab07/src/week12lab07/Week12Lab07.java`

```java
package week12lab07;

public class Week12Lab07 {
    public static void main(String[] args) {
        System.out.println("=== Employee Management System ===\n");

        // Create employees
        FullTime fullTime = new FullTime("Alice", 1001, 5000.00);
        PartTime partTime = new PartTime("Bob", 1002, 25.00, 30.0);
        Assistant assistant = new Assistant("Charlie", 1003, "IT");

        // Display employee details
        System.out.println("Employee Details:");
        System.out.println("==================\n");

        fullTime.display();
        System.out.println();

        partTime.display();
        System.out.println();

        assistant.display();
        System.out.println();

        // Polymorphism with Payable interface
        System.out.println("Payroll (using Payable interface):");
        System.out.println("==================================\n");

        Payable[] employees = {fullTime, partTime, assistant};

        double totalPayroll = 0;
        for (Payable emp : employees) {
            System.out.println(emp.getName() + ": $" + emp.getSalary());
            totalPayroll += emp.getSalary();
        }

        System.out.println("\nTotal Payroll: $" + totalPayroll);

        // Update part-time hours
        System.out.println("\nUpdating part-time hours:");
        partTime.setHoursWorked(40.0);
        System.out.println("New salary for " + partTime.getName() + ": $" + partTime.getSalary());
    }
}
```

**Explanation:**
- Interface defines contract (Payable)
- Abstract class provides common structure
- Each subclass implements specific salary calculation
- Polymorphism through interface
- Flexible design (easy to add new employee types)

**Output:**
```
=== Employee Management System ===

Employee Details:
==================

ID: 1001, Name: Alice
Type: Full-Time
Monthly Salary: $5000.0
Weekly Hours: 40.0

ID: 1002, Name: Bob
Type: Part-Time
Hourly Rate: $25.0
Hours Worked: 30.0
Weekly Salary: $750.0

ID: 1003, Name: Charlie
Type: Assistant
Department: IT
Weekly Hours: 20.0

Payroll (using Payable interface):
==================================

Alice: $5000.0
Bob: $750.0
Charlie: $0.0

Total Payroll: $5750.0

Updating part-time hours:
New salary for Bob: $1000.0
```

---

## Module 6: Advanced Projects

### Class Diagram: UML Relationships

#### Learning Objectives
- Understand UML relationship types
- Learn association, aggregation, composition
- Implement different relationship patterns
- Design class hierarchies

#### Key Concepts

**Relationship Types:**
- **Association**: Uses relationship (weak)
- **Aggregation**: Has-a relationship (ownership, independent lifecycle)
- **Composition**: Strong has-a (ownership, dependent lifecycle)

#### Exercise: Relationship Implementation

**File**: `ClassDiagram/src/classdiagram/Owner.java`

```java
package classdiagram;

import java.util.ArrayList;
import java.util.List;

public class Owner {
    private String name;

    // Association: Owner has associated Association objects (weak)
    private List<Association> associations = new ArrayList<>();

    // Aggregation: Owner owns Aggregation objects (independent lifecycle)
    private List<Aggregation> aggregations = new ArrayList<>();

    // Composition: Owner owns Composition objects (dependent lifecycle)
    private List<Composition> compositions = new ArrayList<>();

    public Owner(String name) {
        this.name = name;
    }

    // Association methods
    public void addAssociation(Association a) {
        associations.add(a);
    }

    // Aggregation methods
    public void addAggregation(Aggregation a) {
        aggregations.add(a);
    }

    // Composition methods
    public void addComposition(Composition c) {
        compositions.add(c);
    }

    public void display() {
        System.out.println("Owner: " + name);
        System.out.println("Associations: " + associations.size());
        System.out.println("Aggregations: " + aggregations.size());
        System.out.println("Compositions: " + compositions.size());
    }
}
```

**Explanation:**
- **Association**: Objects can exist independently
- **Aggregation**: Owner has objects, but objects can exist independently
- **Composition**: Objects cannot exist without owner
- Composition lifecycle tied to owner

---

### Java Application 1: GUI User Management

#### Learning Objectives
- Build complete CRUD application
- Implement file persistence
- Use JTable for data display
- Handle user input validation

#### Exercise: User Management System

**File**: `JavaApplication1/src/javaapplication1/User.java`

```java
package javaapplication1;

public class User {
    private String username;
    private String password;
    private String email;

    public User(String username, String password, String email) {
        this.username = username;
        this.password = password;
        this.email = email;
    }

    public String getUsername() { return username; }
    public String getPassword() { return password; }
    public String getEmail() { return email; }

    public void setUsername(String username) { this.username = username; }
    public void setPassword(String password) { this.password = password; }
    public void setEmail(String email) { this.email = email; }

    @Override
    public String toString() {
        return username + "," + password + "," + email;
    }
}
```

**File**: `JavaApplication1/src/javaapplication1/JavaApplication1.java`

```java
package javaapplication1;

import javax.swing.*;
import javax.swing.table.DefaultTableModel;
import java.awt.*;
import java.awt.event.*;
import java.io.*;
import java.util.ArrayList;

public class JavaApplication1 extends JFrame {
    private JTextField usernameField, passwordField, emailField;
    private JButton addButton, editButton, deleteButton, saveButton;
    private JTable table;
    private DefaultTableModel model;
    private ArrayList<User> users;

    public JavaApplication1() {
        users = new ArrayList<>();
        loadUsers();

        initComponents();
        refreshTable();
    }

    private void initComponents() {
        setTitle("User Management System");
        setSize(600, 400);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLocationRelativeTo(null);

        // Input panel
        JPanel inputPanel = new JPanel(new GridLayout(3, 2, 5, 5));
        inputPanel.add(new JLabel("Username:"));
        usernameField = new JTextField();
        inputPanel.add(usernameField);
        inputPanel.add(new JLabel("Password:"));
        passwordField = new JTextField();
        inputPanel.add(passwordField);
        inputPanel.add(new JLabel("Email:"));
        emailField = new JTextField();
        inputPanel.add(emailField);

        // Button panel
        JPanel buttonPanel = new JPanel(new FlowLayout());
        addButton = new JButton("Add");
        editButton = new JButton("Edit");
        deleteButton = new JButton("Delete");
        saveButton = new JButton("Save");

        buttonPanel.add(addButton);
        buttonPanel.add(editButton);
        buttonPanel.add(deleteButton);
        buttonPanel.add(saveButton);

        // Table
        model = new DefaultTableModel(new String[]{"Username", "Password", "Email"}, 0);
        table = new JTable(model);

        // Event listeners
        addButton.addActionListener(e -> addUser());
        editButton.addActionListener(e -> editUser());
        deleteButton.addActionListener(e -> deleteUser());
        saveButton.addActionListener(e -> saveUsers());

        // Layout
        setLayout(new BorderLayout());
        add(inputPanel, BorderLayout.NORTH);
        add(new JScrollPane(table), BorderLayout.CENTER);
        add(buttonPanel, BorderLayout.SOUTH);
    }

    private void addUser() {
        String username = usernameField.getText();
        String password = passwordField.getText();
        String email = emailField.getText();

        // Check for duplicate username
        for (User u : users) {
            if (u.getUsername().equals(username)) {
                JOptionPane.showMessageDialog(this, "Username already exists!");
                return;
            }
        }

        users.add(new User(username, password, email));
        clearFields();
        refreshTable();
    }

    private void editUser() {
        int selectedRow = table.getSelectedRow();
        if (selectedRow == -1) {
            JOptionPane.showMessageDialog(this, "Please select a user to edit!");
            return;
        }

        String username = model.getValueAt(selectedRow, 0).toString();
        User user = findUser(username);

        if (user != null) {
            user.setUsername(usernameField.getText());
            user.setPassword(passwordField.getText());
            user.setEmail(emailField.getText());
            refreshTable();
        }
    }

    private void deleteUser() {
        int selectedRow = table.getSelectedRow();
        if (selectedRow == -1) {
            JOptionPane.showMessageDialog(this, "Please select a user to delete!");
            return;
        }

        String username = model.getValueAt(selectedRow, 0).toString();
        users.removeIf(u -> u.getUsername().equals(username));
        refreshTable();
    }

    private void saveUsers() {
        try (PrintWriter writer = new PrintWriter(new FileWriter("user.txt"))) {
            for (User u : users) {
                writer.println(u.toString());
            }
            JOptionPane.showMessageDialog(this, "Users saved successfully!");
        } catch (IOException e) {
            JOptionPane.showMessageDialog(this, "Error saving users: " + e.getMessage());
        }
    }

    private void loadUsers() {
        try (Scanner scanner = new Scanner(new File("user.txt"))) {
            while (scanner.hasNextLine()) {
                String line = scanner.nextLine();
                String[] parts = line.split(",");
                if (parts.length == 3) {
                    users.add(new User(parts[0], parts[1], parts[2]));
                }
            }
        } catch (FileNotFoundException e) {
            // File doesn't exist yet, that's okay
        }
    }

    private User findUser(String username) {
        for (User u : users) {
            if (u.getUsername().equals(username)) {
                return u;
            }
        }
        return null;
    }

    private void refreshTable() {
        model.setRowCount(0);
        for (User u : users) {
            model.addRow(new Object[]{u.getUsername(), u.getPassword(), u.getEmail()});
        }
    }

    private void clearFields() {
        usernameField.setText("");
        passwordField.setText("");
        emailField.setText("");
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(() -> {
            JavaApplication1 app = new JavaApplication1();
            app.setVisible(true);
        });
    }
}
```

**Explanation:**
- Complete CRUD functionality
- File persistence (user.txt)
- Duplicate username check
- JTable for data display
- Input validation
- Event-driven architecture

---

### Sample Project: Resident Management System

#### Learning Objectives
- Understand incomplete project structure
- Identify missing implementations
- Learn to complete partial code
- Fix compilation errors

#### Issues Identified

1. **Receipt class is empty** - needs implementation
2. **Admin login not implemented** - missing logic
3. **Resident login not implemented** - missing logic
4. **DataIO missing methods** - for Unit and Receipt
5. **AdminPage.create() has 6 errors** - missing DataIO methods

#### Solution: Complete the Project

**File**: `Sample/src/sample/Receipt.java` (FIXED)

```java
package sample;

import java.util.Date;

public class Receipt {
    private int receiptNumber;
    private int month;
    private Unit unit;
    private Admin admin;
    private Date date;
    private double amount;

    public Receipt(int receiptNumber, int month, Unit unit, Admin admin) {
        this.receiptNumber = receiptNumber;
        this.month = month;
        this.unit = unit;
        this.admin = admin;
        this.date = new Date();
        this.amount = 100.00;  // Fixed monthly fee
    }

    // Getters and setters
    public int getReceiptNumber() {
        return receiptNumber;
    }

    public int getMonth() {
        return month;
    }

    public Unit getUnit() {
        return unit;
    }

    public Admin getAdmin() {
        return admin;
    }

    public Date getDate() {
        return date;
    }

    public double getAmount() {
        return amount;
    }

    public void setAmount(double amount) {
        this.amount = amount;
    }

    @Override
    public String toString() {
        return "Receipt[" + receiptNumber + ", Month: " + month +
               ", Unit: " + unit.getNumber() + ", Amount: $" + amount + "]";
    }
}
```

**File**: `Sample/src/sample/DataIO.java` (FIXED - Added missing methods)

```java
package sample;
import java.io.File;
import java.io.PrintWriter;
import java.util.ArrayList;
import java.util.Scanner;

public class DataIO {
    public static ArrayList<Admin> allAdmin = new ArrayList<Admin>();
    public static ArrayList<Unit> allUnit = new ArrayList<Unit>();
    public static ArrayList<Receipt> allReceipt = new ArrayList<Receipt>();

    // Admin methods
    public static Admin checkName(String name) {
        Admin found = null;
        for (Admin x : allAdmin) {
            if (name.equals(x.getName())) {
                found = x;
                break;
            }
        }
        return found;
    }

    // Unit methods (NEW)
    public static Unit checkNumber(int number) {
        Unit found = null;
        for (Unit u : allUnit) {
            if (u.getNumber() == number) {
                found = u;
                break;
            }
        }
        return found;
    }

    // Unit name check (NEW)
    public static Unit chackName(String name) {  // Note: typo in original method name
        Unit found = null;
        for (Unit u : allUnit) {
            if (name.equals(u.getName())) {
                found = u;
                break;
            }
        }
        return found;
    }

    // Write all data (FIXED)
    public static void write() {
        try {
            // Write admins
            PrintWriter adminWriter = new PrintWriter("admin.txt");
            for (Admin x : allAdmin) {
                adminWriter.println(x.getName());
                adminWriter.println(x.getPassword());
            }
            adminWriter.close();

            // Write units
            PrintWriter unitWriter = new PrintWriter("unit.txt");
            for (Unit u : allUnit) {
                unitWriter.println(u.getNumber());
                unitWriter.println(u.getPassword());
                unitWriter.println(u.getName());
            }
            unitWriter.close();

            // Write receipts
            PrintWriter receiptWriter = new PrintWriter("receipt.txt");
            for (Receipt r : allReceipt) {
                receiptWriter.println(r.getReceiptNumber());
                receiptWriter.println(r.getMonth());
                receiptWriter.println(r.getUnit().getNumber());
                receiptWriter.println(r.getAdmin().getName());
                receiptWriter.println(r.getAmount());
            }
            receiptWriter.close();

        } catch (Exception e) {
            System.out.println("Error in write ..........");
            e.printStackTrace();
        }
    }

    // Read all data (FIXED)
    public static void read() {
        try {
            // Read admins
            Scanner adminScanner = new Scanner(new File("admin.txt"));
            while (adminScanner.hasNext()) {
                String name = adminScanner.nextLine();
                int password = Integer.parseInt(adminScanner.nextLine());
                allAdmin.add(new Admin(name, password));
            }
            adminScanner.close();

            // Read units
            Scanner unitScanner = new Scanner(new File("unit.txt"));
            while (unitScanner.hasNext()) {
                int number = Integer.parseInt(unitScanner.nextLine());
                int password = Integer.parseInt(unitScanner.nextLine());
                String name = unitScanner.nextLine();
                allUnit.add(new Unit(number, password, name));
            }
            unitScanner.close();

        } catch (Exception e) {
            System.out.println("Error in read ..........");
        }
    }
}
```

**File**: `Sample/src/sample/Homepage.java` (FIXED - Added login logic)

```java
package sample;
import java.awt.Button;
import java.awt.FlowLayout;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import javax.swing.JFrame;
import javax.swing.JOptionPane;

public class Homepage implements ActionListener {
    JFrame x;
    Button superadmin, admin, resident, stop;
    public static AdminPage adminPage;
    public static ResidentPage residentPage;

    public Homepage() {
        x = new JFrame();
        x.setSize(200, 150);
        x.setLocation(500, 200);
        x.setLayout(new FlowLayout());
        superadmin = new Button("Super Admin");
        admin = new Button("Admin");
        resident = new Button("Resident");
        stop = new Button("Shut Down");
        superadmin.addActionListener(this);
        admin.addActionListener(this);
        resident.addActionListener(this);
        stop.addActionListener(this);
        x.add(superadmin);
        x.add(admin);
        x.add(resident);
        x.add(stop);
        x.setVisible(true);
    }

    public void actionPerformed(ActionEvent e) {
        try {
            if (e.getSource() == stop) {
                String input = JOptionPane.showInputDialog("Enter super admin password:");
                if (input.equals("12345")) {
                    DataIO.write();
                    System.exit(0);
                } else {
                    throw new Exception();
                }
            } else if (e.getSource() == superadmin) {
                String input = JOptionPane.showInputDialog("Enter super admin password:");
                if (input.equals("12345")) {
                    input = JOptionPane.showInputDialog("Enter new admin username:");
                    if (DataIO.checkName(input) == null) {
                        int password = Integer.parseInt(
                            JOptionPane.showInputDialog("Enter new admin password:"));
                        DataIO.allAdmin.add(new Admin(input, password));
                        DataIO.write();
                        JOptionPane.showMessageDialog(x, "Admin created successfully!");
                    } else {
                        throw new Exception();
                    }
                } else {
                    throw new Exception();
                }
            } else if (e.getSource() == admin) {
                // Admin login
                String username = JOptionPane.showInputDialog("Enter admin username:");
                String passwordStr = JOptionPane.showInputDialog("Enter admin password:");
                int password = Integer.parseInt(passwordStr);

                Admin admin = DataIO.checkName(username);
                if (admin != null && admin.getPassword() == password) {
                    Sample.loginAdmin = admin;
                    x.setVisible(false);
                    adminPage = new AdminPage();
                    adminPage.x.setVisible(true);
                    JOptionPane.showMessageDialog(x, "Login successful!");
                } else {
                    JOptionPane.showMessageDialog(x, "Invalid credentials!");
                }
            } else if (e.getSource() == resident) {
                // Resident login
                String unitNumStr = JOptionPane.showInputDialog("Enter unit number:");
                int unitNum = Integer.parseInt(unitNumStr);
                String passwordStr = JOptionPane.showInputDialog("Enter unit password:");
                int password = Integer.parseInt(passwordStr);

                Unit unit = DataIO.checkNumber(unitNum);
                if (unit != null && unit.getPassword() == password) {
                    x.setVisible(false);
                    residentPage = new ResidentPage();
                    residentPage.x.setVisible(true);
                    JOptionPane.showMessageDialog(x, "Login successful!");
                } else {
                    JOptionPane.showMessageDialog(x, "Invalid credentials!");
                }
            }
        } catch (Exception ex) {
            JOptionPane.showMessageDialog(x, "Invalid Input!");
        }
    }
}
```

**File**: `Sample/src/sample/AdminPage.java` (FIXED - Removed compilation errors)

```java
package sample;
import java.awt.Button;
import java.awt.FlowLayout;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import javax.swing.JFrame;
import javax.swing.JOptionPane;

public class AdminPage implements ActionListener {
    JFrame x;
    Button create, pay, edit, logout;

    public AdminPage() {
        x = new JFrame();
        x.setSize(200, 150);
        x.setLocation(1000, 200);
        x.setLayout(new FlowLayout());
        create = new Button("New Account");
        pay = new Button("Payment");
        edit = new Button("Update Personal Details");
        logout = new Button("Logout");
        create.addActionListener(this);
        pay.addActionListener(this);
        edit.addActionListener(this);
        logout.addActionListener(this);
        x.add(create);
        x.add(pay);
        x.add(edit);
        x.add(logout);
    }

    public void actionPerformed(ActionEvent e) {
        try {
            if (e.getSource() == logout) {
                Sample.loginAdmin = null;
                x.setVisible(false);
                Sample.homepage.x.setVisible(true);
            } else if (e.getSource() == create) {
                // Fixed: All DataIO methods now exist
                int number = Integer.parseInt(
                    JOptionPane.showInputDialog("Enter new unit number:"));
                if (number < 10 || number > 99) {
                    throw new Exception();
                }
                if (DataIO.checkNumber(number) != null) {
                    throw new Exception();
                }
                String name = JOptionPane.showInputDialog("Enter new unit username:");
                if (DataIO.chackName(name) != null) {
                    throw new Exception();
                }
                int password = Integer.parseInt(
                    JOptionPane.showInputDialog("Enter new unit password:"));
                DataIO.allUnit.add(new Unit(number, password, name));
                DataIO.write();
                JOptionPane.showMessageDialog(x, "Unit created successfully!");
            } else if (e.getSource() == pay) {
                int unit = Integer.parseInt(
                    JOptionPane.showInputDialog("Enter unit number:"));
                if (DataIO.checkNumber(unit) == null) {
                    throw new Exception();
                }
                if (DataIO.checkNumber(unit).getMyReceipt().size() == 12) {
                    throw new Exception();
                }
                int number = DataIO.allReceipt.size() + 10001;
                int month = DataIO.checkNumber(unit).getMyReceipt().size() + 1;
                JOptionPane.showMessageDialog(x, "Number: " + number +
                    "\nUnit: " + DataIO.checkNumber(unit).getNumber() +
                    "\nMonth: " + month + "\nAdmin: " + Sample.loginAdmin.getName());
                Receipt r = new Receipt(number, month,
                    DataIO.checkNumber(unit), Sample.loginAdmin);
                DataIO.allReceipt.add(r);
                DataIO.checkNumber(unit).getMyReceipt().add(r);
                Sample.loginAdmin.getMyReceipt().add(r);
                DataIO.write();
                JOptionPane.showMessageDialog(x, "Payment recorded successfully!");
            } else if (e.getSource() == edit) {
                JOptionPane.showMessageDialog(x, "Edit functionality not implemented yet.");
            }
        } catch (Exception ex) {
            JOptionPane.showMessageDialog(x, "Invalid Input!");
        }
    }
}
```

**File**: `Sample/src/sample/ResidentPage.java` (FIXED - Added implementation)

```java
package sample;
import java.awt.Button;
import java.awt.FlowLayout;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import javax.swing.JFrame;
import javax.swing.JOptionPane;

public class ResidentPage implements ActionListener {
    JFrame x;
    Button viewPayments, logout;

    public ResidentPage() {
        x = new JFrame();
        x.setSize(300, 150);
        x.setLocation(1250, 200);
        x.setLayout(new FlowLayout());
        viewPayments = new Button("View Payments");
        logout = new Button("Logout");
        viewPayments.addActionListener(this);
        logout.addActionListener(this);
        x.add(viewPayments);
        x.add(logout);
    }

    public void actionPerformed(ActionEvent e) {
        if (e.getSource() == logout) {
            x.setVisible(false);
            Sample.homepage.x.setVisible(true);
        } else if (e.getSource() == viewPayments) {
            // Display payment history (placeholder)
            JOptionPane.showMessageDialog(x, "Payment history feature coming soon!");
        }
    }
}
```

**File**: `Sample/src/sample/Sample.java` (FIXED - Main entry point)

```java
package sample;

public class Sample {
    public static Admin loginAdmin;
    public static Homepage homepage;

    public static void main(String[] args) {
        // Load data from files
        DataIO.read();

        // Create and show homepage
        homepage = new Homepage();
    }
}
```

**Explanation:**
- **Receipt class**: Added full implementation with fields and methods
- **DataIO**: Added missing methods (checkNumber, chackName, allUnit, allReceipt)
- **Homepage**: Added admin and resident login logic
- **AdminPage**: Fixed by implementing missing DataIO methods
- **ResidentPage**: Added basic implementation
- **Sample**: Main entry point with data loading

**Key Fixes:**
1. Implemented Receipt class with all necessary fields
2. Added Unit and Receipt management to DataIO
3. Implemented admin login authentication
4. Implemented resident login authentication
5. Fixed all compilation errors in AdminPage
6. Added ResidentPage basic functionality

---

## Best Practices and Tips

### Coding Standards

1. **Naming Conventions:**
   - Classes: `PascalCase` (e.g., `CustomerAccount`)
   - Methods: `camelCase` (e.g., `calculateBalance`)
   - Variables: `camelCase` (e.g., `accountBalance`)
   - Constants: `UPPER_SNAKE_CASE` (e.g., `MAX_RETRIES`)
   - Packages: `lowercase` (e.g., `com.company.project`)

2. **Code Organization:**
   - One class per file
   - Package statement first
   - Import statements next
   - Class documentation
   - Fields before methods
   - Public before private

3. **Comments:**
   - Document complex logic
   - Explain "why", not "what"
   - Keep comments up-to-date
   - Use Javadoc for public APIs

### Design Principles

1. **Encapsulation:**
   - Make fields private
   - Provide getters/setters
   - Validate in setters
   - Keep implementation hidden

2. **Single Responsibility:**
   - Each class has one job
   - Each method does one thing
   - Break down complex methods

3. **DRY (Don't Repeat Yourself):**
   - Extract common code
   - Use inheritance
   - Create utility methods
   - Avoid copy-paste

4. **KISS (Keep It Simple):**
   - Write clear, simple code
   - Avoid over-engineering
   - Use straightforward solutions
   - Prioritize readability

### Performance Tips

1. **String Handling:**
   - Use `StringBuilder` for concatenation in loops
   - Avoid unnecessary string creation
   - Use `equals()` not `==` for comparison

2. **Collections:**
   - Use `ArrayList` for frequent access
   - Use `LinkedList` for frequent insertion/deletion
   - Use `HashSet` for fast lookup
   - Use appropriate initial capacity

3. **Loops:**
   - Use enhanced for loop when possible
   - Minimize work inside loops
   - Cache values used repeatedly

---

## Common Pitfalls and Solutions

### Pitfall 1: Comparing Strings with `==`

**Problem:**
```java
String s1 = new String("hello");
String s2 = new String("hello");
if (s1 == s2) {  // WRONG! Compares references
    // This won't execute
}
```

**Solution:**
```java
if (s1.equals(s2)) {  // CORRECT! Compares values
    // This will execute
}
```

---

### Pitfall 2: Null Pointer Exception

**Problem:**
```java
String name = null;
int length = name.length();  // NullPointerException!
```

**Solution:**
```java
String name = null;
int length = (name != null) ? name.length() : 0;
// Or use Objects.requireNonNull()
// Or use Optional<String>
```

---

### Pitfall 3: Forgetting to Close Resources

**Problem:**
```java
FileInputStream fis = new FileInputStream("file.txt");
// Do something
// If exception occurs, file not closed!
```

**Solution:**
```java
// Try-with-resources (Java 7+)
try (FileInputStream fis = new FileInputStream("file.txt")) {
    // Do something
} // Automatically closed

// Or use finally block
FileInputStream fis = null;
try {
    fis = new FileInputStream("file.txt");
    // Do something
} finally {
    if (fis != null) {
        fis.close();
    }
}
```

---

### Pitfall 4: Integer Overflow

**Problem:**
```java
int result = 2000000000 * 2;  // Overflow! Negative number
```

**Solution:**
```java
long result = 2000000000L * 2;  // Use long literal
// Or check for overflow
```

---

### Pitfall 5: Modifying List While Iterating

**Problem:**
```java
List<String> list = new ArrayList<>();
list.add("a");
list.add("b");

for (String s : list) {
    if (s.equals("a")) {
        list.remove(s);  // ConcurrentModificationException!
    }
}
```

**Solution:**
```java
// Use Iterator
Iterator<String> iter = list.iterator();
while (iter.hasNext()) {
    String s = iter.next();
    if (s.equals("a")) {
        iter.remove();  // Safe!
    }
}

// Or use removeIf() (Java 8+)
list.removeIf(s -> s.equals("a"));
```

---

### Pitfall 6: Confusing Assignment with Comparison

**Problem:**
```java
if (x = 5) {  // Assignment, not comparison! Compile error in Java (unless boolean)
    // Won't compile for non-boolean
}
```

**Solution:**
```java
if (x == 5) {  // Correct comparison
    // Executes if x equals 5
}

// Or use yoda condition (recommended)
if (5 == x) {  // Prevents accidental assignment
    // Won't compile if you write (5 = x)
}
```

---

### Pitfall 7: Not Implementing equals() and hashCode()

**Problem:**
```java
Person p1 = new Person("Alice");
Person p2 = new Person("Alice");
Set<Person> set = new HashSet<>();
set.add(p1);
set.add(p2);
System.out.println(set.size());  // 2! Should be 1
```

**Solution:**
```java
@Override
public boolean equals(Object obj) {
    if (this == obj) return true;
    if (obj == null || getClass() != obj.getClass()) return false;
    Person person = (Person) obj;
    return name.equals(person.name);
}

@Override
public int hashCode() {
    return Objects.hash(name);
}
```

---

### Pitfall 8: Forgetting to Override toString()

**Problem:**
```java
Person p = new Person("Alice");
System.out.println(p);  // Prints something like Person@15db9742
```

**Solution:**
```java
@Override
public String toString() {
    return "Person{name='" + name + "'}";
}
// Output: Person{name='Alice'}
```

---

### Pitfall 9: Ignoring Exception Messages

**Problem:**
```java
try {
    // Some code
} catch (Exception e) {
    // Empty catch block!
}
```

**Solution:**
```java
try {
    // Some code
} catch (Exception e) {
    logger.error("Operation failed", e);  // Log the error
    e.printStackTrace();  // Or print stack trace
}
```

---

### Pitfall 10: Using Magic Numbers

**Problem:**
```java
if (score > 90) {  // What does 90 mean?
    // ...
}
```

**Solution:**
```java
private static final int EXCELLENT_SCORE = 90;

if (score > EXCELLENT_SCORE) {  // Clearer intent
    // ...
}
```

---

## Summary


### Topics Covered:

1. **Basic Java**: Operators, data types, control structures
2. **OOP Fundamentals**: Classes, objects, encapsulation, inheritance
3. **GUI Programming**: Components, layout managers, event handling
4. **Advanced OOP**: Polymorphism, abstract classes, interfaces
5. **Specialized Topics**: Exception handling, I/O, GUI programming
6. **Projects**: Complete applications with real-world scenarios

### Key Takeaways:

- Practice makes perfect - complete all exercises
- Understand the "why", not just the "how"
- Follow naming conventions and best practices
- Test your code thoroughly
- Learn from mistakes and refactor often
- Build incrementally and document your code
