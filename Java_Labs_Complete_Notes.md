# Java Labs Complete Notes - All Solutions

**Course:** Java Programming  
**Date:** March 1, 2026  
**Total Labs:** 10 Labs + 9 Lectures  
**Source:** OneDrive_4_3-1-2026 & OneDrive_3_3-1-2026

---

## Table of Contents

### Lab Sessions (Directory: OneDrive_4_3-1-2026)
1. [Lab03 - Object-Oriented Programming Fundamentals](#lab03---object-oriented-programming-fundamentals)
2. [Week02Lab02 - Basic Java Programming](#week02lab02---basic-java-programming)
3. [Week07(09)Lab08 - GUI Programming with Swing](#week0709lab08---gui-programming-with-swing)
4. [Week07Lec08 - Advanced GUI Components](#week07lec08---advanced-gui-components)
5. [Week08Lab09 - File I/O and String Processing](#week08lab09---file-io-and-string-processing)
6. [Week10Lab06 - Inheritance and Polymorphism](#week10lab06---inheritance-and-polymorphism)
7. [Week12Lab07 - Abstract Classes and Interfaces](#week12lab07---abstract-classes-and-interfaces)
8. [Sample - Condominium Management System](#sample---condominium-management-system)
9. [JavaApplication1 - User Management System](#javaapplication1---user-management-system)
10. [MyFirstJavaProject - Basic Java Programs](#myfirstjavaproject---basic-java-programs)

### Lecture Sessions (Directory: OneDrive_3_3-1-2026)
11. [Week01 - Java Fundamentals and Operators](#week01---java-fundamentals-and-operators)
12. [Lec03 - Classes and Objects](#lec03---classes-and-objects)
13. [Week02Lec01 - Arrays and Object-Oriented Design](#week02lec01---arrays-and-object-oriented-design)
14. [Week04Lec04 - Encapsulation and Inheritance](#week04lec04---encapsulation-and-inheritance)
15. [Week08Lec06 - Polymorphism](#week08lec06---polymorphism)
16. [Week09Lec07 - Abstract Classes and Interfaces](#week09lec07---abstract-classes-and-interfaces)
17. [Week10Lec09 - Exception Handling](#week10lec09---exception-handling)
18. [Week12Binary - Serialization and Final Keywords](#week12binary---serialization-and-final-keywords)
19. [ClassDiagram - UML Relationships](#classdiagram---uml-relationships)

---

## LAB SESSIONS

---

## 1. Lab03 - Object-Oriented Programming Fundamentals

**Location:** `/home/loke/Downloads/OneDrive_4_3-1-2026/Lab03/`

### Learning Objectives
- Understand encapsulation with private fields and public accessors
- Implement static members (variables and methods)
- Override toString() method for object representation
- Use enums for type-safe constant definitions
- Apply DecimalFormat for formatted output

### Key Concepts

#### Encapsulation
Encapsulation is the bundling of data and methods that operate on that data within a single unit (class). It restricts direct access to some of an object's components.

#### Static Members
- Static variables are shared among all instances of a class
- Static methods can be called without creating an object
- Static blocks are executed when the class is loaded

#### Enumerations (Enums)
- Enums provide type-safe constants
- Enums can have constructors, fields, and methods
- Enums are implicitly final and cannot be extended

### Solution Files

#### 1.1 Basic Account Class (lab03/Account.java)

```java
package lab03;

public class Account {
    private int id;
    private double balance;
    private double annualInterestRate;
    
    public Account() {
        id = 0;
        balance = 0;
        annualInterestRate = 0;
    }
    
    public Account(int id, double balance, double annualInterestRate) {
        this.id = id;
        this.balance = balance;
        this.annualInterestRate = annualInterestRate;
    }
    
    // Accessor methods
    public int getId() {
        return id;
    }
    
    public double getBalance() {
        return balance;
    }
    
    public double getAnnualInterestRate() {
        return annualInterestRate;
    }
    
    // Mutator methods
    public void setId(int id) {
        this.id = id;
    }
    
    public void setBalance(double balance) {
        this.balance = balance;
    }
    
    public void setAnnualInterestRate(double annualInterestRate) {
        this.annualInterestRate = annualInterestRate;
    }
    
    // Business methods
    public double getMonthlyInterestRate() {
        return annualInterestRate / 12;
    }
    
    public double getMonthlyInterest() {
        return balance * (getMonthlyInterestRate() / 100);
    }
    
    public void withdraw(double amount) {
        balance = balance - amount;
    }
    
    public void deposit(double amount) {
        balance = balance + amount;
    }
}
```

**Key Points:**
- All fields are private (encapsulation)
- Provides constructor overloading
- Separate getter and setter methods
- Business logic methods for transactions

---

#### 1.2 Account with Custom Print Method (v1/Account.java)

```java
package v1;

public class Account {
    private int id;
    private double balance;
    private double annualInterestRate;
    
    public Account(int id, double balance, double annualInterestRate) {
        this.id = id;
        this.balance = balance;
        this.annualInterestRate = annualInterestRate;
    }
    
    public void printAccount() {
        System.out.println("Account ID: " + id);
        System.out.println("Balance: RM" + balance);
        System.out.println("Annual Interest Rate: " + annualInterestRate + "%");
        System.out.println("Monthly Interest Rate: " + (annualInterestRate / 12) + "%");
    }
}
```

---

#### 1.3 Account with toString() Override (v2/Account.java)

```java
package v2;

import java.text.DecimalFormat;

public class Account {
    private int id;
    private double balance;
    private double annualInterestRate;
    
    public Account(int id, double balance, double annualInterestRate) {
        this.id = id;
        this.balance = balance;
        this.annualInterestRate = annualInterestRate;
    }
    
    @Override
    public String toString() {
        DecimalFormat df = new DecimalFormat("#,##0.00");
        return "Account ID: " + id + "\n" +
               "Balance: RM" + df.format(balance) + "\n" +
               "Annual Interest Rate: " + annualInterestRate + "%\n" +
               "Monthly Interest Rate: " + df.format(annualInterestRate / 12) + "%";
    }
}
```

**Key Points:**
- Override toString() for meaningful object representation
- Use DecimalFormat for currency formatting
- Called automatically when object is printed

---

#### 1.4 Static Members Demo (samplestatic/Account.java)

```java
package samplestatic;

public class Account {
    private int id;
    private double balance;
    private static double annualInterestRate;  // Shared among all accounts
    private static int numberOfAccounts = 0;   // Counter for total accounts
    
    public Account(int id, double balance) {
        this.id = id;
        this.balance = balance;
        numberOfAccounts++;  // Increment counter
    }
    
    public static void setAnnualInterestRate(double rate) {
        annualInterestRate = rate;
    }
    
    public static double getAnnualInterestRate() {
        return annualInterestRate;
    }
    
    public static int getNumberOfAccounts() {
        return numberOfAccounts;
    }
    
    @Override
    public String toString() {
        return "Account[" + id + "]: RM" + balance + 
               " (Rate: " + annualInterestRate + "%)";
    }
}
```

**Usage Example:**
```java
Account.setAnnualInterestRate(3.5);  // Set once, applies to all
Account a1 = new Account(1, 1000);
Account a2 = new Account(2, 2000);
System.out.println(Account.getNumberOfAccounts());  // Output: 2
```

---

#### 1.5 Enum Usage - Fan Control (exe2/Fan.java)

```java
package exe2;

public class Fan {
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
    
    private Velocity velocity;
    private boolean on;
    private double radius;
    private String color;
    
    public Fan() {
        velocity = Velocity.STOPPED;
        on = false;
        radius = 5;
        color = "blue";
    }
    
    public void setVelocity(Velocity velocity) {
        this.velocity = velocity;
    }
    
    public Velocity getVelocity() {
        return velocity;
    }
    
    @Override
    public String toString() {
        if (on) {
            return "Fan is ON\n" +
                   "Speed: " + velocity.getDescription() + "\n" +
                   "Radius: " + radius + "\n" +
                   "Color: " + color;
        } else {
            return "Fan is OFF\n" +
                   "Radius: " + radius + "\n" +
                   "Color: " + color;
        }
    }
}
```

**Usage Example:**
```java
Fan fan1 = new Fan();
fan1.setOn(true);
fan1.setVelocity(Fan.Velocity.FAST);
fan1.setRadius(10);
fan1.setColor("yellow");

Fan fan2 = new Fan();
fan2.setVelocity(Fan.Velocity.MEDIUM);

System.out.println(fan1.toString());
System.out.println(fan2.toString());
```

**Key Points:**
- Enum provides type-safe constants
- Enums can have constructors, fields, and methods
- Prevents invalid values (only 4 valid speed levels)

---

### Lab03 Summary

| Concept | Description |
|---------|-------------|
| Encapsulation | Hiding internal state and requiring interaction through methods |
| Private Fields | Variables accessible only within the class |
| Getters/Setters | Public methods to access and modify private fields |
| Static Variables | Shared among all instances of the class |
| Static Methods | Can be called without object instantiation |
| toString() | Called when object needs string representation |
| Enum | Type-safe constant definitions with possible fields and methods |
| DecimalFormat | Formats numbers according to pattern |

---

## 2. Week02Lab02 - Basic Java Programming

**Location:** `/home/loke/Downloads/OneDrive_4_3-1-2026/Week02Lab02/`

### Learning Objectives
- Master loop structures (while, do-while, for)
- Work with arrays (creation, initialization, manipulation)
- Use Math.random() for random number generation
- Implement conditional statements (if-else, nested if-else)
- Apply String manipulation methods
- Use Arrays.sort() for sorting arrays

### Solution Files

#### 2.1 Basic Operations (Week02Lab02.java)

```java
package week02lab02;

public class Week02Lab02 {
    public static void main(String[] args) {
        // String manipulation
        String name = "John Doe";
        System.out.println("Lowercase: " + name.toLowerCase());
        System.out.println("Uppercase: " + name.toUpperCase());
        
        // Math operations
        double base = 2;
        double exponent = 8;
        double result = Math.pow(base, exponent);
        System.out.println(base + "^" + exponent + " = " + result);
        
        // Random number
        int randomNum = (int)(Math.random() * 100) + 1;
        System.out.println("Random number (1-100): " + randomNum);
    }
}
```

---

#### 2.2 Sum of Digits (Exe3.java)

```java
package week02lab02;

import java.util.Scanner;

public class Exe3 {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        
        System.out.print("Enter an integer: ");
        int number = input.nextInt();
        
        int sum = 0;
        int temp = number;
        
        while (temp != 0) {
            int digit = temp % 10;  // Extract last digit
            sum += digit;           // Add to sum
            temp /= 10;             // Remove last digit
        }
        
        System.out.println("Sum of digits in " + number + " is: " + sum);
    }
}
```

**Algorithm Explanation:**
1. Take input number
2. Extract last digit using modulo operator (`% 10`)
3. Add digit to sum
4. Remove last digit using integer division (`/ 10`)
5. Repeat until number becomes 0

**Example:**
- Input: 1234
- Iteration 1: digit = 4, sum = 4, temp = 123
- Iteration 2: digit = 3, sum = 7, temp = 12
- Iteration 3: digit = 2, sum = 9, temp = 1
- Iteration 4: digit = 1, sum = 10, temp = 0
- Output: 10

---

#### 2.3 Grading System (Exe7.java)

```java
package week02lab02;

import java.util.Scanner;

public class Exe7 {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        
        System.out.print("Enter student name: ");
        String name = input.nextLine();
        
        System.out.print("Enter score (0-100): ");
        int score = input.nextInt();
        
        char grade;
        
        if (score >= 90) {
            grade = 'A';
        } else if (score >= 80) {
            grade = 'B';
        } else if (score >= 70) {
            grade = 'C';
        } else if (score >= 60) {
            grade = 'D';
        } else {
            grade = 'F';
        }
        
        System.out.println("\nStudent: " + name);
        System.out.println("Score: " + score);
        System.out.println("Grade: " + grade);
        
        // Additional feedback
        if (grade == 'A') {
            System.out.println("Excellent work!");
        } else if (grade == 'F') {
            System.out.println("Please see the instructor.");
        }
    }
}
```

**Grading Scale:**
| Score Range | Grade |
|-------------|-------|
| 90-100 | A |
| 80-89 | B |
| 70-79 | C |
| 60-69 | D |
| 0-59 | F |

---

#### 2.4 Array Operations (Exe8.java)

```java
package week02lab02;

import java.util.Arrays;
import java.util.Scanner;

public class Exe8 {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        
        // Create array with random numbers
        int[] numbers = new int[10];
        
        System.out.println("Generating 10 random numbers (1-100):");
        for (int i = 0; i < numbers.length; i++) {
            numbers[i] = (int)(Math.random() * 100) + 1;
            System.out.print(numbers[i] + " ");
        }
        System.out.println();
        
        // Calculate sum
        int sum = 0;
        for (int num : numbers) {
            sum += num;
        }
        System.out.println("Sum: " + sum);
        
        // Calculate average
        double average = (double)sum / numbers.length;
        System.out.println("Average: " + average);
        
        // Find maximum
        int max = numbers[0];
        for (int num : numbers) {
            if (num > max) {
                max = num;
            }
        }
        System.out.println("Maximum: " + max);
        
        // Find minimum
        int min = numbers[0];
        for (int num : numbers) {
            if (num < min) {
                min = num;
            }
        }
        System.out.println("Minimum: " + min);
        
        // Sort array
        Arrays.sort(numbers);
        System.out.println("Sorted array: " + Arrays.toString(numbers));
    }
}
```

**Output Example:**
```
Generating 10 random numbers (1-100):
45 78 12 89 34 67 23 90 56 11 
Sum: 505
Average: 50.5
Maximum: 90
Minimum: 11
Sorted array: [11, 12, 23, 34, 45, 56, 67, 78, 89, 90]
```

---

#### 2.5 User Input Validation (Exe10.java)

```java
package week02lab02;

import java.util.Scanner;

public class Exe10 {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        
        int number;
        
        do {
            System.out.print("Enter a positive number (0 to exit): ");
            number = input.nextInt();
            
            if (number > 0) {
                // Check if even or odd
                if (number % 2 == 0) {
                    System.out.println(number + " is even.");
                } else {
                    System.out.println(number + " is odd.");
                }
            } else if (number < 0) {
                System.out.println("Invalid input. Please enter a positive number.");
            }
            
        } while (number != 0);
        
        System.out.println("Program terminated.");
    }
}
```

**Key Points:**
- do-while loop guarantees at least one iteration
- Input validation ensures positive numbers
- Even/odd check using modulo operator

---

### Week02Lab02 Summary

| Concept | Description |
|---------|-------------|
| While Loop | Executes while condition is true (checks first) |
| Do-While Loop | Executes at least once, then checks condition |
| For Loop | Used when number of iterations is known |
| Arrays | Fixed-size collections of same-type elements |
| Math.random() | Returns random double [0.0, 1.0) |
| Arrays.sort() | Sorts array in ascending order |
| Enhanced For Loop | Simpler syntax for array iteration |
| Modulo (%) | Returns remainder of division |

---

## 3. Week07(09)Lab08 - GUI Programming with Swing

**Location:** `/home/loke/Downloads/OneDrive_4_3-1-2026/Week07(09)Lab08/`

### Learning Objectives
- Create GUI applications using JFrame
- Use Swing components (JButton, JLabel, JRadioButton)
- Implement event handling with ActionListener
- Understand layout managers (BorderLayout, FlowLayout)
- Use ButtonGroup for radio button grouping
- Apply Color and Font customization

### Key Concepts

#### AWT vs Swing
- **AWT (Abstract Window Toolkit):** Original Java GUI toolkit, uses native OS components
- **Swing:** Built on AWT, lightweight, pure Java components
- **Best Practice:** Use Swing components (prefixed with 'J')

#### Layout Managers
- **BorderLayout:** 5 regions (NORTH, SOUTH, EAST, WEST, CENTER)
- **FlowLayout:** Components flow left to right
- **GridLayout:** Components in a grid
- **GridLayout:** Components in absolute positions

### Solution Files

#### 3.1 Basic GUI with Radio Buttons

```java
package week07.pkg09.lab08;

import java.awt.*;
import java.awt.event.*;
import javax.swing.*;

public class Week0709Lab08 implements ActionListener {
    JFrame x;
    Panel s;
    Label y;
    JRadioButton m, f;
    ButtonGroup z;
    
    public Week0709Lab08() {
        x = new JFrame("Gender Selection");
        x.setSize(300, 200);
        x.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        x.setLayout(new BorderLayout());
        
        // Create panel for radio buttons
        s = new Panel();
        s.setLayout(new FlowLayout());
        
        // Create label
        y = new Label("Select your gender:");
        y.setFont(new Font("Arial", Font.BOLD, 14));
        
        // Create radio buttons
        m = new JRadioButton("Male");
        f = new JRadioButton("Female");
        
        // Add action listeners
        m.addActionListener(this);
        f.addActionListener(this);
        
        // Group radio buttons (only one can be selected)
        z = new ButtonGroup();
        z.add(m);
        z.add(f);
        
        // Add components to panel
        s.add(m);
        s.add(f);
        
        // Add components to frame
        x.add(y, BorderLayout.NORTH);
        x.add(s, BorderLayout.CENTER);
        
        // Make frame visible
        x.setVisible(true);
    }
    
    @Override
    public void actionPerformed(ActionEvent e) {
        if (e.getSource() == m) {
            y.setText("You are a man!");
            y.setForeground(Color.BLUE);
        } else if (e.getSource() == f) {
            y.setText("You are a woman!");
            y.setForeground(Color.PINK);
        }
    }
    
    public static void main(String[] args) {
        new Week0709Lab08();
    }
}
```

**Key Points:**
- JFrame creates main window
- Panel groups related components
- ButtonGroup ensures single selection
- ActionListener handles button clicks
- BorderLayout organizes components

---

### Week07(09)Lab08 Summary

| Component | Description |
|-----------|-------------|
| JFrame | Main application window |
| JPanel | Container for grouping components |
| JButton | Clickable button |
| JLabel | Display text/image |
| JRadioButton | Single selection button |
| ButtonGroup | Groups radio buttons for single selection |
| ActionListener | Interface for handling events |
| BorderLayout | 5-region layout manager |
| FlowLayout | Left-to-right flow layout |
| Font | Text styling (family, style, size) |
| Color | Component coloring |

---

## 4. Week07Lec08 - Advanced GUI Components

**Location:** `/home/loke/Downloads/OneDrive_4_3-1-2026/Week07Lec08/`

### Learning Objectives
- Create BMI calculator with validation
- Implement color mixer with RGB controls
- Handle mouse events (click, enter, exit)
- Use JOptionPane for dialog boxes
- Implement exception handling in GUI
- Apply Checkbox with ItemListener

### Solution Files

#### 4.1 BMI Calculator

```java
package week07lec08;

import javax.swing.*;
import java.awt.*;
import java.awt.event.*;
import java.text.DecimalFormat;

public class BMI extends JFrame implements ActionListener {
    JLabel weightLabel, heightLabel, resultLabel;
    JTextField weightField, heightField;
    JButton calculateButton, clearButton;
    
    public BMI() {
        setTitle("BMI Calculator");
        setSize(300, 250);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(new GridLayout(5, 2, 5, 5));
        
        // Create components
        weightLabel = new JLabel("Weight (kg):");
        heightLabel = new JLabel("Height (m):");
        resultLabel = new JLabel("Result:");
        
        weightField = new JTextField();
        heightField = new JTextField();
        
        calculateButton = new JButton("Calculate");
        clearButton = new JButton("Clear");
        
        // Add action listeners
        calculateButton.addActionListener(this);
        clearButton.addActionListener(this);
        
        // Add components to frame
        add(weightLabel);
        add(weightField);
        add(heightLabel);
        add(heightField);
        add(calculateButton);
        add(clearButton);
        add(resultLabel);
        
        setVisible(true);
    }
    
    @Override
    public void actionPerformed(ActionEvent e) {
        if (e.getSource() == calculateButton) {
            try {
                double weight = Double.parseDouble(weightField.getText());
                double height = Double.parseDouble(heightField.getText());
                
                if (weight <= 0 || height <= 0) {
                    JOptionPane.showMessageDialog(this, 
                        "Please enter positive values!",
                        "Error", 
                        JOptionPane.ERROR_MESSAGE);
                    return;
                }
                
                double bmi = weight / Math.pow(height, 2);
                DecimalFormat df = new DecimalFormat("#0.00");
                
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
                
                resultLabel.setText("BMI: " + df.format(bmi) + " (" + category + ")");
                
            } catch (NumberFormatException ex) {
                JOptionPane.showMessageDialog(this, 
                    "Please enter valid numbers!",
                    "Error", 
                    JOptionPane.ERROR_MESSAGE);
            }
        } else if (e.getSource() == clearButton) {
            weightField.setText("");
            heightField.setText("");
            resultLabel.setText("Result:");
        }
    }
    
    public static void main(String[] args) {
        new BMI();
    }
}
```

**BMI Categories:**
| BMI Range | Category |
|-----------|----------|
| < 18.5 | Underweight |
| 18.5 - 24.9 | Normal |
| 25 - 29.9 | Overweight |
| ≥ 30 | Obese |

---

#### 4.2 Color Mixer (RGB)

```java
package week07lec08;

import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class Colour extends JFrame implements ActionListener, AdjustmentListener {
    JLabel redLabel, greenLabel, blueLabel, colorLabel;
    JScrollBar redBar, greenBar, blueBar;
    JPanel colorPanel;
    
    public Colour() {
        setTitle("RGB Color Mixer");
        setSize(400, 300);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(new GridLayout(2, 1));
        
        // Top panel for color display
        colorPanel = new JPanel();
        colorPanel.setBackground(Color.BLACK);
        colorLabel = new JLabel("RGB(0, 0, 0)");
        colorLabel.setForeground(Color.WHITE);
        colorPanel.add(colorLabel);
        
        // Bottom panel for controls
        JPanel controlPanel = new JPanel(new GridLayout(3, 2));
        
        redLabel = new JLabel("Red: 0");
        greenLabel = new JLabel("Green: 0");
        blueLabel = new JLabel("Blue: 0");
        
        redBar = new JScrollBar(JScrollBar.HORIZONTAL, 0, 1, 0, 255);
        greenBar = new JScrollBar(JScrollBar.HORIZONTAL, 0, 1, 0, 255);
        blueBar = new JScrollBar(JScrollBar.HORIZONTAL, 0, 1, 0, 255);
        
        redBar.addAdjustmentListener(this);
        greenBar.addAdjustmentListener(this);
        blueBar.addAdjustmentListener(this);
        
        controlPanel.add(redLabel);
        controlPanel.add(redBar);
        controlPanel.add(greenLabel);
        controlPanel.add(greenBar);
        controlPanel.add(blueLabel);
        controlPanel.add(blueBar);
        
        add(colorPanel);
        add(controlPanel);
        
        setVisible(true);
    }
    
    @Override
    public void adjustmentValueChanged(AdjustmentEvent e) {
        int red = redBar.getValue();
        int green = greenBar.getValue();
        int blue = blueBar.getValue();
        
        colorPanel.setBackground(new Color(red, green, blue));
        colorLabel.setText("RGB(" + red + ", " + green + ", " + blue + ")");
        
        // Update label text color for contrast
        int brightness = (red + green + blue) / 3;
        colorLabel.setForeground(brightness > 127 ? Color.BLACK : Color.WHITE);
    }
    
    @Override
    public void actionPerformed(ActionEvent e) {
        // Not used in this example
    }
    
    public static void main(String[] args) {
        new Colour();
    }
}
```

**Key Points:**
- JScrollBar for slider control
- AdjustmentListener handles scroll bar changes
- Color created from RGB values
- Dynamic label color for contrast

---

#### 4.3 Mouse Event Listener

```java
package week07lec08;

import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class LAB64 extends JFrame implements MouseListener {
    JLabel label;
    
    public LAB64() {
        setTitle("Mouse Events Demo");
        setSize(300, 200);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(new FlowLayout());
        
        label = new JLabel("Move mouse over me!");
        label.setFont(new Font("Arial", Font.BOLD, 16));
        label.addMouseListener(this);
        
        add(label);
        setVisible(true);
    }
    
    @Override
    public void mouseClicked(MouseEvent e) {
        label.setText("Mouse clicked at (" + e.getX() + ", " + e.getY() + ")");
        label.setForeground(Color.BLUE);
    }
    
    @Override
    public void mouseEntered(MouseEvent e) {
        label.setText("Mouse entered!");
        label.setForeground(Color.GREEN);
    }
    
    @Override
    public void mouseExited(MouseEvent e) {
        label.setText("Mouse exited!");
        label.setForeground(Color.RED);
    }
    
    @Override
    public void mousePressed(MouseEvent e) {
        label.setText("Mouse pressed!");
    }
    
    @Override
    public void mouseReleased(MouseEvent e) {
        label.setText("Mouse released!");
    }
    
    public static void main(String[] args) {
        new LAB64();
    }
}
```

**MouseListener Methods:**
| Method | Trigger |
|--------|---------|
| mouseClicked() | Mouse button clicked (pressed and released) |
| mousePressed() | Mouse button pressed |
| mouseReleased() | Mouse button released |
| mouseEntered() | Mouse enters component area |
| mouseExited() | Mouse leaves component area |

---

### Week07Lec08 Summary

| Component | Description |
|-----------|-------------|
| JTextField | Single-line text input |
| JPasswordField | Password field (masked input) |
| JTextArea | Multi-line text area |
| JCheckBox | Toggle button (on/off) |
| JScrollBar | Slider control |
| JOptionPane | Dialog boxes (message, confirm, input) |
| MouseListener | Interface for mouse events |
| AdjustmentListener | Handles scroll bar changes |
| DecimalFormat | Formats numbers for display |
| Exception Handling | Try-catch for error management |

---

## 5. Week08Lab09 - File I/O and String Processing

**Location:** `/home/loke/Downloads/OneDrive_4_3-1-2026/Week08Lab09/`

### Learning Objectives
- Read text files using Scanner
- Tokenize strings with custom delimiters
- Count characters, words, and lines in files
- Sort arrays using Arrays.sort()
- Compare Scanner vs StringTokenizer
- Process nested data structures

### Key Concepts

#### File I/O in Java
- **Scanner:** Easy text file reading
- **FileInputStream:** Low-level byte reading
- **BufferedReader:** Efficient line-by-line reading
- **FileWriter/PrintWriter:** Writing to files

#### String Tokenization
- **Scanner.next():** Reads next token (whitespace delimiter)
- **StringTokenizer:** Legacy class, supports custom delimiters
- **String.split():** Splits string using regex pattern

### Solution Files

#### 5.1 File Text Analysis

```java
package week08lab09;

import java.io.*;
import java.util.*;

public class Week08Lab09 {
    public static void main(String[] args) {
        try {
            Scanner scanner = new Scanner(new File("lab9e1.txt"));
            
            int lineCount = 0;
            int wordCount = 0;
            int charCount = 0;
            
            while (scanner.hasNextLine()) {
                String line = scanner.nextLine();
                lineCount++;
                
                // Count characters (including spaces)
                charCount += line.length();
                
                // Count words
                Scanner lineScanner = new Scanner(line);
                while (lineScanner.hasNext()) {
                    lineScanner.next();
                    wordCount++;
                }
                lineScanner.close();
            }
            
            scanner.close();
            
            System.out.println("File Analysis Results:");
            System.out.println("----------------------");
            System.out.println("Lines: " + lineCount);
            System.out.println("Words: " + wordCount);
            System.out.println("Characters: " + charCount);
            
        } catch (FileNotFoundException e) {
            System.out.println("File not found: " + e.getMessage());
        }
    }
}
```

**Sample File (lab9e1.txt):**
```
Java is a programming language.
It is widely used for web development.
Java programs are platform independent.
```

**Expected Output:**
```
File Analysis Results:
----------------------
Lines: 3
Words: 16
Characters: 114
```

---

#### 5.2 Scanner vs StringTokenizer

```java
package week08lab09;

import java.util.*;

public class Exe2 {
    public static void main(String[] args) {
        String text = "apple,banana;orange grape|pear";
        
        System.out.println("Original text: " + text);
        System.out.println("\n--- Using Scanner ---");
        
        // Scanner with custom delimiter
        Scanner scanner = new Scanner(text);
        scanner.useDelimiter("[,;| ]+");  // Regex for multiple delimiters
        
        while (scanner.hasNext()) {
            System.out.println(scanner.next());
        }
        scanner.close();
        
        System.out.println("\n--- Using StringTokenizer ---");
        
        // StringTokenizer with multiple delimiters
        StringTokenizer tokenizer = new StringTokenizer(text, ",;| ");
        
        while (tokenizer.hasMoreTokens()) {
            System.out.println(tokenizer.nextToken());
        }
    }
}
```

**Output:**
```
Original text: apple,banana;orange grape|pear

--- Using Scanner ---
apple
banana
orange
grape
pear

--- Using StringTokenizer ---
apple
banana
orange
grape
pear
```

**Key Differences:**
- Scanner: More modern, supports regex delimiters
- StringTokenizer: Legacy class, faster for simple cases
- Both produce same output for basic tokenization

---

#### 5.3 Array Sorting

```java
package week08lab09;

import java.util.*;

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
        
        System.out.println("\nSorted array (ascending):");
        for (int num : numbers) {
            System.out.print(num + " ");
        }
        System.out.println();
        
        // Sort in descending order
        Integer[] descNumbers = new Integer[numbers.length];
        for (int i = 0; i < numbers.length; i++) {
            descNumbers[i] = numbers[i];
        }
        
        Arrays.sort(descNumbers, Collections.reverseOrder());
        
        System.out.println("\nSorted array (descending):");
        for (int num : descNumbers) {
            System.out.print(num + " ");
        }
        System.out.println();
        
        // Find statistics
        System.out.println("\nStatistics:");
        System.out.println("Minimum: " + numbers[0]);
        System.out.println("Maximum: " + numbers[numbers.length - 1]);
        System.out.println("Median: " + getMedian(numbers));
    }
    
    private static double getMedian(int[] sortedArray) {
        int n = sortedArray.length;
        if (n % 2 == 0) {
            return (sortedArray[n/2 - 1] + sortedArray[n/2]) / 2.0;
        } else {
            return sortedArray[n/2];
        }
    }
}
```

**Output Example:**
```
Original array:
45 78 12 89 34 67 23 90 56 11 

Sorted array (ascending):
11 12 23 34 45 56 67 78 89 90 

Sorted array (descending):
90 89 78 67 56 45 34 23 12 11 

Statistics:
Minimum: 11
Maximum: 90
Median: 50.5
```

---

### Week08Lab09 Summary

| Concept | Description |
|---------|-------------|
| Scanner | Reads and parses text from various sources |
| File | Represents file/directory path |
| FileNotFoundException | Thrown when file doesn't exist |
| nextLine() | Reads entire line |
| next() | Reads next token |
| useDelimiter() | Sets custom delimiter pattern |
| StringTokenizer | Legacy string tokenization class |
| Arrays.sort() | Sorts array in ascending order |
| Collections.reverseOrder() | Comparator for descending sort |
| Regex Pattern | Regular expression for matching |

---

## 6. Week10Lab06 - Inheritance and Polymorphism

**Location:** `/home/loke/Downloads/OneDrive_4_3-1-2026/Week10Lab06/`

### Learning Objectives
- Understand inheritance with `extends` keyword
- Implement method overriding with `@Override`
- Use `super` keyword to access parent class members
- Work with abstract classes and abstract methods
- Implement interfaces
- Use Comparable interface for sorting
- Apply TreeSet for sorted collections

### Key Concepts

#### Inheritance
- Allows creating new classes based on existing classes
- Promotes code reuse
- Java supports single inheritance only
- `extends` keyword establishes inheritance

#### Method Overriding
- Subclass provides specific implementation
- Method signature must match exactly
- Use `@Override` annotation for compile-time checking

#### Abstract Classes
- Cannot be instantiated
- May contain abstract methods (no implementation)
- May contain concrete methods
- Used as base classes

### Solution Files

#### 6.1 Account Hierarchy

**Base Class (Account.java):**
```java
package week10lab06;

public class Account {
    protected int id;
    protected double balance;
    protected double annualInterestRate;
    
    public Account() {
        id = 0;
        balance = 0;
        annualInterestRate = 0;
    }
    
    public Account(int id, double balance, double annualInterestRate) {
        this.id = id;
        this.balance = balance;
        this.annualInterestRate = annualInterestRate;
    }
    
    public int getId() {
        return id;
    }
    
    public double getBalance() {
        return balance;
    }
    
    public double getAnnualInterestRate() {
        return annualInterestRate;
    }
    
    public void setId(int id) {
        this.id = id;
    }
    
    public void setBalance(double balance) {
        this.balance = balance;
    }
    
    public void setAnnualInterestRate(double annualInterestRate) {
        this.annualInterestRate = annualInterestRate;
    }
    
    public double getMonthlyInterestRate() {
        return annualInterestRate / 12;
    }
    
    public double getMonthlyInterest() {
        return balance * getMonthlyInterestRate() / 100;
    }
    
    public void withdraw(double amount) {
        balance -= amount;
    }
    
    public void deposit(double amount) {
        balance += amount;
    }
    
    @Override
    public String toString() {
        return "Account ID: " + id + "\n" +
               "Balance: RM" + balance + "\n" +
               "Annual Interest Rate: " + annualInterestRate + "%";
    }
}
```

---

**Subclass - Saving Account:**
```java
package week10lab06;

public class SavingAccount extends Account {
    private double overdraftLimit;
    
    public SavingAccount(int id, double balance, double annualInterestRate, double overdraftLimit) {
        super(id, balance, annualInterestRate);
        this.overdraftLimit = overdraftLimit;
    }
    
    public double getOverdraftLimit() {
        return overdraftLimit;
    }
    
    public void setOverdraftLimit(double overdraftLimit) {
        this.overdraftLimit = overdraftLimit;
    }
    
    @Override
    public void withdraw(double amount) {
        if (amount > (balance + overdraftLimit)) {
            System.out.println("Insufficient funds!");
        } else {
            balance -= amount;
            System.out.println("Withdrawal successful. New balance: RM" + balance);
        }
    }
    
    @Override
    public String toString() {
        return super.toString() + "\n" +
               "Overdraft Limit: RM" + overdraftLimit;
    }
}
```

---

**Subclass - Checking Account:**
```java
package week10lab06;

public class CheckingAccount extends Account {
    private double overdraftLimit;
    
    public CheckingAccount(int id, double balance, double annualInterestRate, double overdraftLimit) {
        super(id, balance, annualInterestRate);
        this.overdraftLimit = overdraftLimit;
    }
    
    public double getOverdraftLimit() {
        return overdraftLimit;
    }
    
    @Override
    public void withdraw(double amount) {
        if (amount > (balance + overdraftLimit)) {
            System.out.println("Transaction rejected: Amount exceeds balance + overdraft limit");
        } else if (amount > balance) {
            // Use overdraft
            overdraftLimit = (overdraftLimit + balance) - amount;
            balance = 0;
            System.out.println("Withdrawal successful. Balance: RM" + balance + 
                              ", Remaining overdraft: RM" + overdraftLimit);
        } else {
            balance -= amount;
            System.out.println("Withdrawal successful. New balance: RM" + balance);
        }
    }
    
    @Override
    public String toString() {
        return super.toString() + "\n" +
               "Overdraft Limit: RM" + overdraftLimit;
    }
}
```

**Test Program:**
```java
package week10lab06;

public class TestAccount {
    public static void main(String[] args) {
        // Create accounts
        Account account = new Account(1, 1000, 3.5);
        SavingAccount saving = new SavingAccount(2, 2000, 4.0, 500);
        CheckingAccount checking = new CheckingAccount(3, 1500, 2.5, 1000);
        
        System.out.println("=== Account ===");
        System.out.println(account);
        account.deposit(500);
        System.out.println("After deposit: RM" + account.getBalance());
        
        System.out.println("\n=== Saving Account ===");
        System.out.println(saving);
        saving.withdraw(2200);  // Uses overdraft
        saving.withdraw(100);   // Normal withdrawal
        
        System.out.println("\n=== Checking Account ===");
        System.out.println(checking);
        checking.withdraw(1800);  // Uses overdraft
        checking.withdraw(1000);  // Normal withdrawal
    }
}
```

---

#### 6.2 Geometric Objects with Comparable

**Abstract Base Class:**
```java
package exe2;

public abstract class GeometricObject implements Comparable<GeometricObject> {
    private String color;
    private boolean filled;
    private java.util.Date dateCreated;
    
    protected GeometricObject() {
        color = "white";
        filled = false;
        dateCreated = new java.util.Date();
    }
    
    protected GeometricObject(String color, boolean filled) {
        this.color = color;
        this.filled = filled;
        dateCreated = new java.util.Date();
    }
    
    public String getColor() {
        return color;
    }
    
    public void setColor(String color) {
        this.color = color;
    }
    
    public boolean isFilled() {
        return filled;
    }
    
    public void setFilled(boolean filled) {
        this.filled = filled;
    }
    
    public java.util.Date getDateCreated() {
        return dateCreated;
    }
    
    @Override
    public String toString() {
        return "Created on " + dateCreated + 
               "\nColor: " + color + 
               "\nFilled: " + filled;
    }
    
    public abstract double getArea();
    public abstract double getPerimeter();
    
    @Override
    public int compareTo(GeometricObject o) {
        if (this.getArea() > o.getArea()) {
            return 1;
        } else if (this.getArea() < o.getArea()) {
            return -1;
        } else {
            return 0;
        }
    }
    
    public static GeometricObject max(GeometricObject o1, GeometricObject o2) {
        return o1.compareTo(o2) >= 0 ? o1 : o2;
    }
}
```

---

**Circle Implementation:**
```java
package exe2;

public class Circle extends GeometricObject {
    private double radius;
    
    public Circle() {
        radius = 1;
    }
    
    public Circle(double radius) {
        this.radius = radius;
    }
    
    public Circle(double radius, String color, boolean filled) {
        super(color, filled);
        this.radius = radius;
    }
    
    public double getRadius() {
        return radius;
    }
    
    public void setRadius(double radius) {
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
    
    @Override
    public String toString() {
        return super.toString() + 
               "\nCircle with radius " + radius +
               "\nArea: " + String.format("%.2f", getArea()) +
               "\nPerimeter: " + String.format("%.2f", getPerimeter());
    }
}
```

---

**Cylinder with Colorable Interface:**
```java
package exe2;

public interface Colorable {
    void howToColor();
}
```

```java
package exe2;

public class Cylinder extends Circle implements Colorable {
    private double height;
    
    public Cylinder() {
        height = 1;
    }
    
    public Cylinder(double radius, double height) {
        super(radius);
        this.height = height;
    }
    
    public Cylinder(double radius, double height, String color, boolean filled) {
        super(radius, color, filled);
        this.height = height;
    }
    
    public double getHeight() {
        return height;
    }
    
    public void setHeight(double height) {
        this.height = height;
    }
    
    @Override
    public double getArea() {
        // Total surface area = 2πr(r + h)
        return 2 * Math.PI * radius * (radius + height);
    }
    
    @Override
    public double getPerimeter() {
        // Perimeter of base circle
        return 2 * Math.PI * radius;
    }
    
    public double getVolume() {
        // Volume = πr²h
        return Math.PI * radius * radius * height;
    }
    
    @Override
    public void howToColor() {
        System.out.println("Color the entire surface area: " + 
                          String.format("%.2f", getArea()));
    }
    
    @Override
    public String toString() {
        return super.toString() + 
               "\nCylinder with height " + height +
               "\nVolume: " + String.format("%.2f", getVolume());
    }
}
```

**Test Program:**
```java
package exe2;

import java.util.TreeSet;

public class TestGeometricObject {
    public static void main(String[] args) {
        // Create geometric objects
        Circle circle1 = new Circle(5, "red", true);
        Circle circle2 = new Circle(3, "blue", false);
        Cylinder cylinder = new Cylinder(4, 10, "green", true);
        
        System.out.println("=== Circle 1 ===");
        System.out.println(circle1);
        
        System.out.println("\n=== Circle 2 ===");
        System.out.println(circle2);
        
        System.out.println("\n=== Cylinder ===");
        System.out.println(cylinder);
        System.out.print("How to color: ");
        cylinder.howToColor();
        
        // Compare areas
        System.out.println("\n=== Comparison ===");
        System.out.println("Max area: " + GeometricObject.max(circle1, circle2));
        
        // Use TreeSet for automatic sorting by area
        TreeSet<GeometricObject> shapes = new TreeSet<>();
        shapes.add(circle1);
        shapes.add(circle2);
        shapes.add(cylinder);
        
        System.out.println("\n=== Sorted by Area ===");
        for (GeometricObject shape : shapes) {
            System.out.println(shape.getClass().getSimpleName() + 
                              " - Area: " + String.format("%.2f", shape.getArea()));
        }
    }
}
```

---

### Week10Lab06 Summary

| Concept | Description |
|---------|-------------|
| extends | Keyword for inheritance |
| super | Refers to parent class |
| @Override | Annotation for method overriding |
| protected | Access modifier for subclasses |
| abstract | Cannot be instantiated |
| abstract method | Method without implementation |
| interface | Contract for implementing classes |
| implements | Keyword for interface implementation |
| Comparable | Interface for natural ordering |
| compareTo() | Method for comparison |
| TreeSet | Sorted collection |

---

## 7. Week12Lab07 - Abstract Classes and Interfaces

**Location:** `/home/loke/Downloads/OneDrive_4_3-1-2026/Week12Lab07/`

### Learning Objectives
- Design abstract classes with abstract methods
- Implement multiple interfaces
- Create payroll system with different employee types
- Understand interface inheritance
- Apply method overriding in abstract contexts
- Use percentage-based calculations

### Key Concepts

#### Abstract Classes vs Interfaces
| Feature | Abstract Class | Interface |
|---------|----------------|-----------|
| Can have instance fields | Yes | No (only constants) |
| Can have constructors | Yes | No |
| Can have concrete methods | Yes | Only default methods (Java 8+) |
| Multiple inheritance | No (single) | Yes |
| Access modifiers | Any | public by default |

### Solution Files

#### 7.1 Employee Payroll System

**Payable Interface:**
```java
package week12lab07;

public interface Payable {
    double getSalary();
}
```

---

**Abstract Employee Class:**
```java
package week12lab07;

public abstract class Employee implements Payable {
    private String name;
    private int id;
    
    public Employee(String name, int id) {
        this.name = name;
        this.id = id;
    }
    
    public String getName() {
        return name;
    }
    
    public int getId() {
        return id;
    }
    
    @Override
    public String toString() {
        return "ID: " + id + ", Name: " + name;
    }
}
```

---

**Full-Time Employee:**
```java
package week12lab07;

public class FullTime extends Employee {
    private double monthlySalary;
    
    public FullTime(String name, int id, double monthlySalary) {
        super(name, id);
        this.monthlySalary = monthlySalary;
    }
    
    public double getMonthlySalary() {
        return monthlySalary;
    }
    
    public void setMonthlySalary(double monthlySalary) {
        this.monthlySalary = monthlySalary;
    }
    
    @Override
    public double getSalary() {
        return monthlySalary;
    }
    
    @Override
    public String toString() {
        return super.toString() + 
               ", Type: Full-Time" +
               ", Monthly Salary: RM" + monthlySalary;
    }
}
```

---

**Part-Time Employee:**
```java
package week12lab07;

public class PartTime extends Employee {
    private double hourlyRate;
    private double weeklyHours;
    
    public PartTime(String name, int id, double hourlyRate, double weeklyHours) {
        super(name, id);
        this.hourlyRate = hourlyRate;
        this.weeklyHours = weeklyHours;
    }
    
    public double getHourlyRate() {
        return hourlyRate;
    }
    
    public double getWeeklyHours() {
        return weeklyHours;
    }
    
    public void setHourlyRate(double hourlyRate) {
        this.hourlyRate = hourlyRate;
    }
    
    public void setWeeklyHours(double weeklyHours) {
        this.weeklyHours = weeklyHours;
    }
    
    @Override
    public double getSalary() {
        return hourlyRate * weeklyHours;
    }
    
    @Override
    public String toString() {
        return super.toString() + 
               ", Type: Part-Time" +
               ", Hourly Rate: RM" + hourlyRate +
               ", Weekly Hours: " + weeklyHours +
               ", Weekly Salary: RM" + getSalary();
    }
}
```

---

**Assistant (No Salary):**
```java
package week12lab07;

public class Assistant extends Employee {
    private String department;
    
    public Assistant(String name, int id, String department) {
        super(name, id);
        this.department = department;
    }
    
    public String getDepartment() {
        return department;
    }
    
    public void setDepartment(String department) {
        this.department = department;
    }
    
    @Override
    public double getSalary() {
        return 0;  // Assistant has no salary
    }
    
    @Override
    public String toString() {
        return super.toString() + 
               ", Type: Assistant" +
               ", Department: " + department +
               ", Salary: N/A";
    }
}
```

**Test Program:**
```java
package week12lab07;

import java.util.ArrayList;

public class PayrollSystem {
    public static void main(String[] args) {
        ArrayList<Employee> employees = new ArrayList<>();
        
        // Add employees
        employees.add(new FullTime("Ahmad", 1001, 5000));
        employees.add(new FullTime("Siti", 1002, 5500));
        employees.add(new PartTime("Ali", 2001, 25, 40));
        employees.add(new PartTime("Fatimah", 2002, 30, 35));
        employees.add(new Assistant("Omar", 3001, "IT"));
        
        // Display all employees
        System.out.println("=== Employee Payroll Report ===");
        System.out.println();
        
        double totalPayroll = 0;
        
        for (Employee emp : employees) {
            System.out.println(emp);
            System.out.println("Salary: RM" + emp.getSalary());
            System.out.println();
            totalPayroll += emp.getSalary();
        }
        
        System.out.println("=== Summary ===");
        System.out.println("Total Payroll: RM" + totalPayroll);
        System.out.println("Number of Employees: " + employees.size());
    }
}
```

**Output:**
```
=== Employee Payroll Report ===

ID: 1001, Name: Ahmad, Type: Full-Time, Monthly Salary: RM5000
Salary: RM5000

ID: 1002, Name: Siti, Type: Full-Time, Monthly Salary: RM5500
Salary: RM5500

ID: 2001, Name: Ali, Type: Part-Time, Hourly Rate: RM25, Weekly Hours: 40, Weekly Salary: RM1000
Salary: RM1000

ID: 2002, Name: Fatimah, Type: Part-Time, Hourly Rate: RM30, Weekly Hours: 35, Weekly Salary: RM1050
Salary: RM1050

ID: 3001, Name: Omar, Type: Assistant, Department: IT, Salary: N/A
Salary: RM0

=== Summary ===
Total Payroll: RM12550
Number of Employees: 5
```

---

#### 7.2 Resizable Interface

**Resizable Interface:**
```java
package exe2;

public interface Resizable {
    void resize(int percent);
}
```

---

**Resizable Circle:**
```java
package exe2;

public class ResizableCircle extends Circle implements Resizable {
    public ResizableCircle(double radius) {
        super(radius);
    }
    
    @Override
    public void resize(int percent) {
        if (percent > 0) {
            radius = radius * (1 + percent / 100.0);
        } else {
            radius = radius * (1 + percent / 100.0);
            if (radius < 0) radius = 0;
        }
    }
    
    @Override
    public String toString() {
        return "Resizable Circle with radius " + String.format("%.2f", radius) +
               "\nArea: " + String.format("%.2f", getArea()) +
               "\nPerimeter: " + String.format("%.2f", getPerimeter());
    }
}
```

**Test Program:**
```java
package exe2;

public class TestResizable {
    public static void main(String[] args) {
        ResizableCircle circle = new ResizableCircle(10);
        
        System.out.println("Original Circle:");
        System.out.println(circle);
        
        System.out.println("\nResize by +50%:");
        circle.resize(50);
        System.out.println(circle);
        
        System.out.println("\nResize by -20%:");
        circle.resize(-20);
        System.out.println(circle);
    }
}
```

**Output:**
```
Original Circle:
Resizable Circle with radius 10.00
Area: 314.16
Perimeter: 62.83

Resize by +50%:
Resizable Circle with radius 15.00
Area: 706.86
Perimeter: 94.25

Resize by -20%:
Resizable Circle with radius 12.00
Area: 452.39
Perimeter: 75.40
```

---

### Week12Lab07 Summary

| Concept | Description |
|---------|-------------|
| abstract class | Cannot be instantiated, may have abstract methods |
| abstract method | Method without implementation |
| interface | Pure abstract class (all methods abstract by default) |
| implements | Keyword to implement interface |
| multiple interfaces | Class can implement multiple interfaces |
| interface inheritance | Interface can extend another interface |
| @Override | Annotation for method overriding |
| polymorphism | Interface reference can refer to any implementing class |

---

## 8. Sample - Condominium Management System

**Location:** `/home/loke/Downloads/OneDrive_4_3-1-2026/Sample/`

### Learning Objectives
- Build complete GUI application with multiple screens
- Implement user authentication
- Manage data persistence with text files
- Create admin and resident portals
- Handle payment tracking
- Generate receipts

### System Architecture

```
Condominium Management System
├── Homepage (Login screen with role selection)
├── Admin Portal
│   ├── Admin management
│   ├── Unit management
│   └── Payment tracking
├── Resident Portal
│   ├── View payments
│   └── Payment history
└── Data Persistence
    ├── admin.txt (Admin credentials)
    ├── unit.txt (Unit information)
    └── receipt.txt (Payment records)
```

### Key Components

#### 8.1 DataIO Class (File Operations)

```java
package sample;

import java.io.*;
import java.util.*;

public class DataIO {
    private static final String ADMIN_FILE = "admin.txt";
    private static final String UNIT_FILE = "unit.txt";
    private static final String RECEIPT_FILE = "receipt.txt";
    
    // Read all admins
    public static ArrayList<Admin> readAdmins() {
        ArrayList<Admin> admins = new ArrayList<>();
        try {
            Scanner scanner = new Scanner(new File(ADMIN_FILE));
            while (scanner.hasNextLine()) {
                String line = scanner.nextLine();
                String[] parts = line.split(",");
                if (parts.length >= 2) {
                    admins.add(new Admin(parts[0], parts[1]));
                }
            }
            scanner.close();
        } catch (FileNotFoundException e) {
            System.out.println("Admin file not found. Creating new file.");
        }
        return admins;
    }
    
    // Write all admins
    public static void writeAdmins(ArrayList<Admin> admins) {
        try {
            PrintWriter writer = new PrintWriter(new FileWriter(ADMIN_FILE));
            for (Admin admin : admins) {
                writer.println(admin.getUsername() + "," + admin.getPassword());
            }
            writer.close();
        } catch (IOException e) {
            System.out.println("Error writing admin file: " + e.getMessage());
        }
    }
    
    // Read all units
    public static ArrayList<Unit> readUnits() {
        ArrayList<Unit> units = new ArrayList<>();
        try {
            Scanner scanner = new Scanner(new File(UNIT_FILE));
            while (scanner.hasNextLine()) {
                String line = scanner.nextLine();
                String[] parts = line.split(",");
                if (parts.length >= 4) {
                    Unit unit = new Unit(parts[0], parts[1], parts[2], parts[3]);
                    // Read payment status (12 months)
                    for (int i = 4; i < parts.length && i < 16; i++) {
                        unit.setPaymentStatus(i - 4, Boolean.parseBoolean(parts[i]));
                    }
                    units.add(unit);
                }
            }
            scanner.close();
        } catch (FileNotFoundException e) {
            System.out.println("Unit file not found. Creating new file.");
        }
        return units;
    }
    
    // Write all units
    public static void writeUnits(ArrayList<Unit> units) {
        try {
            PrintWriter writer = new PrintWriter(new FileWriter(UNIT_FILE));
            for (Unit unit : units) {
                StringBuilder sb = new StringBuilder();
                sb.append(unit.getUnitNumber()).append(",");
                sb.append(unit.getOwnerName()).append(",");
                sb.append(unit.getUsername()).append(",");
                sb.append(unit.getPassword());
                for (int i = 0; i < 12; i++) {
                    sb.append(",").append(unit.getPaymentStatus(i));
                }
                writer.println(sb.toString());
            }
            writer.close();
        } catch (IOException e) {
            System.out.println("Error writing unit file: " + e.getMessage());
        }
    }
    
    // Read receipts
    public static ArrayList<Receipt> readReceipts() {
        ArrayList<Receipt> receipts = new ArrayList<>();
        try {
            Scanner scanner = new Scanner(new File(RECEIPT_FILE));
            while (scanner.hasNextLine()) {
                String line = scanner.nextLine();
                String[] parts = line.split(",");
                if (parts.length >= 5) {
                    receipts.add(new Receipt(parts[0], parts[1], parts[2], 
                                            parts[3], parts[4]));
                }
            }
            scanner.close();
        } catch (FileNotFoundException e) {
            System.out.println("Receipt file not found. Creating new file.");
        }
        return receipts;
    }
    
    // Write receipt
    public static void writeReceipt(Receipt receipt) {
        try {
            PrintWriter writer = new PrintWriter(new FileWriter(RECEIPT_FILE, true));
            writer.println(receipt.getUnitNumber() + "," + 
                          receipt.getMonth() + "," +
                          receipt.getAmount() + "," +
                          receipt.getDate() + "," +
                          receipt.getReference());
            writer.close();
        } catch (IOException e) {
            System.out.println("Error writing receipt: " + e.getMessage());
        }
    }
}
```

---

#### 8.2 Homepage (Login Screen)

```java
package sample;

import javax.swing.*;
import java.awt.*;
import java.awt.event.*;
import java.util.ArrayList;

public class Homepage extends JFrame implements ActionListener {
    private JTextField usernameField;
    private JPasswordField passwordField;
    private JButton loginButton, exitButton;
    private JRadioButton adminRadio, residentRadio;
    private ButtonGroup roleGroup;
    
    private static final String SUPER_ADMIN_PASSWORD = "12345";
    
    public Homepage() {
        setTitle("Condominium Management System - Login");
        setSize(400, 300);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(new GridLayout(6, 2, 10, 10));
        
        // Create components
        JLabel titleLabel = new JLabel("Condominium Management System");
        titleLabel.setFont(new Font("Arial", Font.BOLD, 16));
        
        JLabel roleLabel = new JLabel("Select Role:");
        adminRadio = new JRadioButton("Admin");
        residentRadio = new JRadioButton("Resident");
        adminRadio.setSelected(true);
        
        roleGroup = new ButtonGroup();
        roleGroup.add(adminRadio);
        roleGroup.add(residentRadio);
        
        JLabel usernameLabel = new JLabel("Username:");
        usernameField = new JTextField();
        
        JLabel passwordLabel = new JLabel("Password:");
        passwordField = new JPasswordField();
        
        loginButton = new JButton("Login");
        exitButton = new JButton("Exit");
        
        loginButton.addActionListener(this);
        exitButton.addActionListener(this);
        
        // Add components
        add(titleLabel);
        add(new JLabel());
        add(roleLabel);
        add(new JLabel());
        add(adminRadio);
        add(residentRadio);
        add(usernameLabel);
        add(usernameField);
        add(passwordLabel);
        add(passwordField);
        add(loginButton);
        add(exitButton);
        
        setVisible(true);
    }
    
    @Override
    public void actionPerformed(ActionEvent e) {
        if (e.getSource() == loginButton) {
            String username = usernameField.getText();
            String password = new String(passwordField.getPassword());
            
            if (adminRadio.isSelected()) {
                // Admin login
                if (username.equals("superadmin") && password.equals(SUPER_ADMIN_PASSWORD)) {
                    new AdminPage();
                    dispose();
                } else {
                    ArrayList<Admin> admins = DataIO.readAdmins();
                    boolean authenticated = false;
                    for (Admin admin : admins) {
                        if (admin.getUsername().equals(username) && 
                            admin.getPassword().equals(password)) {
                            new AdminPage();
                            dispose();
                            authenticated = true;
                            break;
                        }
                    }
                    if (!authenticated) {
                        JOptionPane.showMessageDialog(this, 
                            "Invalid username or password!", 
                            "Login Failed", 
                            JOptionPane.ERROR_MESSAGE);
                    }
                }
            } else {
                // Resident login
                ArrayList<Unit> units = DataIO.readUnits();
                boolean authenticated = false;
                for (Unit unit : units) {
                    if (unit.getUsername().equals(username) && 
                        unit.getPassword().equals(password)) {
                        new ResidentPage(unit);
                        dispose();
                        authenticated = true;
                        break;
                    }
                }
                if (!authenticated) {
                    JOptionPane.showMessageDialog(this, 
                        "Invalid username or password!", 
                        "Login Failed", 
                        JOptionPane.ERROR_MESSAGE);
                }
            }
        } else if (e.getSource() == exitButton) {
            System.exit(0);
        }
    }
    
    public static void main(String[] args) {
        new Homepage();
    }
}
```

---

#### 8.3 AdminPage (Admin Portal)

```java
package sample;

import javax.swing.*;
import java.awt.*;
import java.awt.event.*;
import java.util.ArrayList;

public class AdminPage extends JFrame implements ActionListener {
    private JButton createAdminButton, createUnitButton, viewPaymentsButton, logoutButton;
    private JTextArea displayArea;
    
    public AdminPage() {
        setTitle("Admin Portal");
        setSize(600, 500);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(new BorderLayout());
        
        // Button panel
        JPanel buttonPanel = new JPanel(new GridLayout(2, 2, 10, 10));
        
        createAdminButton = new JButton("Create Admin");
        createUnitButton = new JButton("Create Unit");
        viewPaymentsButton = new JButton("View Payments");
        logoutButton = new JButton("Logout");
        
        createAdminButton.addActionListener(this);
        createUnitButton.addActionListener(this);
        viewPaymentsButton.addActionListener(this);
        logoutButton.addActionListener(this);
        
        buttonPanel.add(createAdminButton);
        buttonPanel.add(createUnitButton);
        buttonPanel.add(viewPaymentsButton);
        buttonPanel.add(logoutButton);
        
        // Display area
        displayArea = new JTextArea();
        displayArea.setEditable(false);
        JScrollPane scrollPane = new JScrollPane(displayArea);
        
        add(buttonPanel, BorderLayout.NORTH);
        add(scrollPane, BorderLayout.CENTER);
        
        setVisible(true);
    }
    
    @Override
    public void actionPerformed(ActionEvent e) {
        if (e.getSource() == createAdminButton) {
            createAdmin();
        } else if (e.getSource() == createUnitButton) {
            createUnit();
        } else if (e.getSource() == viewPaymentsButton) {
            viewPayments();
        } else if (e.getSource() == logoutButton) {
            new Homepage();
            dispose();
        }
    }
    
    private void createAdmin() {
        String username = JOptionPane.showInputDialog(this, "Enter username:");
        if (username != null && !username.isEmpty()) {
            String password = JOptionPane.showInputDialog(this, "Enter password:");
            if (password != null && !password.isEmpty()) {
                ArrayList<Admin> admins = DataIO.readAdmins();
                admins.add(new Admin(username, password));
                DataIO.writeAdmins(admins);
                JOptionPane.showMessageDialog(this, "Admin created successfully!");
            }
        }
    }
    
    private void createUnit() {
        String unitNumber = JOptionPane.showInputDialog(this, "Enter unit number:");
        if (unitNumber != null && !unitNumber.isEmpty()) {
            String ownerName = JOptionPane.showInputDialog(this, "Enter owner name:");
            if (ownerName != null && !ownerName.isEmpty()) {
                String username = JOptionPane.showInputDialog(this, "Enter username:");
                if (username != null && !username.isEmpty()) {
                    String password = JOptionPane.showInputDialog(this, "Enter password:");
                    if (password != null && !password.isEmpty()) {
                        ArrayList<Unit> units = DataIO.readUnits();
                        units.add(new Unit(unitNumber, ownerName, username, password));
                        DataIO.writeUnits(units);
                        JOptionPane.showMessageDialog(this, "Unit created successfully!");
                    }
                }
            }
        }
    }
    
    private void viewPayments() {
        ArrayList<Unit> units = DataIO.readUnits();
        StringBuilder sb = new StringBuilder();
        sb.append("=== Payment Status ===\n\n");
        
        String[] months = {"Jan", "Feb", "Mar", "Apr", "May", "Jun", 
                          "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"};
        
        for (Unit unit : units) {
            sb.append("Unit: ").append(unit.getUnitNumber())
              .append(" (").append(unit.getOwnerName()).append(")\n");
            sb.append("Payment Status:\n");
            for (int i = 0; i < 12; i++) {
                String status = unit.getPaymentStatus(i) ? "PAID" : "UNPAID";
                sb.append("  ").append(months[i]).append(": ").append(status).append("\n");
            }
            sb.append("\n");
        }
        
        displayArea.setText(sb.toString());
    }
}
```

---

#### 8.4 ResidentPage (Resident Portal)

```java
package sample;

import javax.swing.*;
import java.awt.*;
import java.awt.event.*;
import java.text.SimpleDateFormat;
import java.util.Date;

public class ResidentPage extends JFrame implements ActionListener {
    private Unit unit;
    private JButton payButton, viewHistoryButton, logoutButton;
    private JTextArea displayArea;
    private JComboBox<String> monthCombo;
    
    public ResidentPage(Unit unit) {
        this.unit = unit;
        
        setTitle("Resident Portal - " + unit.getUnitNumber());
        setSize(600, 500);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(new BorderLayout());
        
        // Button panel
        JPanel buttonPanel = new JPanel(new GridLayout(2, 2, 10, 10));
        
        String[] months = {"January", "February", "March", "April", "May", "June", 
                          "July", "August", "September", "October", "November", "December"};
        monthCombo = new JComboBox<>(months);
        
        payButton = new JButton("Make Payment");
        viewHistoryButton = new JButton("View History");
        logoutButton = new JButton("Logout");
        
        payButton.addActionListener(this);
        viewHistoryButton.addActionListener(this);
        logoutButton.addActionListener(this);
        
        buttonPanel.add(monthCombo);
        buttonPanel.add(payButton);
        buttonPanel.add(viewHistoryButton);
        buttonPanel.add(logoutButton);
        
        // Display area
        displayArea = new JTextArea();
        displayArea.setEditable(false);
        JScrollPane scrollPane = new JScrollPane(displayArea);
        
        add(buttonPanel, BorderLayout.NORTH);
        add(scrollPane, BorderLayout.CENTER);
        
        updateDisplay();
        
        setVisible(true);
    }
    
    @Override
    public void actionPerformed(ActionEvent e) {
        if (e.getSource() == payButton) {
            makePayment();
        } else if (e.getSource() == viewHistoryButton) {
            viewHistory();
        } else if (e.getSource() == logoutButton) {
            new Homepage();
            dispose();
        }
    }
    
    private void makePayment() {
        int monthIndex = monthCombo.getSelectedIndex();
        
        if (unit.getPaymentStatus(monthIndex)) {
            JOptionPane.showMessageDialog(this, 
                "Payment for " + monthCombo.getSelectedItem() + " is already made!", 
                "Payment Status", 
                JOptionPane.INFORMATION_MESSAGE);
            return;
        }
        
        String amount = JOptionPane.showInputDialog(this, "Enter payment amount (RM):");
        if (amount != null && !amount.isEmpty()) {
            try {
                double paymentAmount = Double.parseDouble(amount);
                if (paymentAmount > 0) {
                    // Update payment status
                    unit.setPaymentStatus(monthIndex, true);
                    
                    // Save to file
                    ArrayList<Unit> units = DataIO.readUnits();
                    for (int i = 0; i < units.size(); i++) {
                        if (units.get(i).getUnitNumber().equals(unit.getUnitNumber())) {
                            units.set(i, unit);
                            break;
                        }
                    }
                    DataIO.writeUnits(units);
                    
                    // Generate receipt
                    SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd");
                    String date = sdf.format(new Date());
                    String reference = "REF-" + System.currentTimeMillis();
                    
                    Receipt receipt = new Receipt(
                        unit.getUnitNumber(),
                        (String)monthCombo.getSelectedItem(),
                        amount,
                        date,
                        reference
                    );
                    DataIO.writeReceipt(receipt);
                    
                    JOptionPane.showMessageDialog(this, 
                        "Payment successful!\n\nReceipt Details:\n" +
                        "Reference: " + reference + "\n" +
                        "Date: " + date + "\n" +
                        "Amount: RM" + amount,
                        "Payment Confirmation",
                        JOptionPane.INFORMATION_MESSAGE);
                    
                    updateDisplay();
                } else {
                    JOptionPane.showMessageDialog(this, 
                        "Please enter a valid amount!",
                        "Invalid Amount",
                        JOptionPane.ERROR_MESSAGE);
                }
            } catch (NumberFormatException ex) {
                JOptionPane.showMessageDialog(this, 
                    "Please enter a valid number!",
                    "Invalid Amount",
                    JOptionPane.ERROR_MESSAGE);
            }
        }
    }
    
    private void viewHistory() {
        ArrayList<Receipt> receipts = DataIO.readReceipts();
        StringBuilder sb = new StringBuilder();
        sb.append("=== Payment History ===\n\n");
        
        for (Receipt receipt : receipts) {
            if (receipt.getUnitNumber().equals(unit.getUnitNumber())) {
                sb.append("Month: ").append(receipt.getMonth()).append("\n");
                sb.append("Amount: RM").append(receipt.getAmount()).append("\n");
                sb.append("Date: ").append(receipt.getDate()).append("\n");
                sb.append("Reference: ").append(receipt.getReference()).append("\n");
                sb.append("------------------------\n");
            }
        }
        
        if (sb.length() == 22) {  // Only contains title
            sb.append("No payment history found.");
        }
        
        displayArea.setText(sb.toString());
    }
    
    private void updateDisplay() {
        String[] months = {"Jan", "Feb", "Mar", "Apr", "May", "Jun", 
                          "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"};
        
        StringBuilder sb = new StringBuilder();
        sb.append("=== Unit Information ===\n");
        sb.append("Unit Number: ").append(unit.getUnitNumber()).append("\n");
        sb.append("Owner Name: ").append(unit.getOwnerName()).append("\n\n");
        sb.append("=== Payment Status ===\n");
        
        for (int i = 0; i < 12; i++) {
            String status = unit.getPaymentStatus(i) ? "PAID" : "UNPAID";
            sb.append(months[i]).append(": ").append(status).append("\n");
        }
        
        displayArea.setText(sb.toString());
    }
}
```

---

### Sample Project Summary

| Feature | Description |
|---------|-------------|
| Authentication | Login system for admins and residents |
| Role-Based Access | Different features for admin and resident |
| Data Persistence | Text file storage for all data |
| Payment Tracking | 12-month payment status per unit |
| Receipt Generation | Automated receipt with reference number |
| Multiple Screens | Homepage, AdminPage, ResidentPage |

---

## 9. JavaApplication1 - User Management System

**Location:** `/home/loke/Downloads/OneDrive_4_3-1-2026/JavaApplication1/`

### Learning Objectives
- Create CRUD (Create, Read, Update, Delete) application
- Use JTable for data display
- Implement file persistence
- Handle user input validation
- Use DefaultTableModel for table management

### Solution Files

#### 9.1 User Model

```java
package javaapplication1;

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

---

#### 9.2 Main Application

```java
package javaapplication1;

import javax.swing.*;
import javax.swing.table.DefaultTableModel;
import java.awt.*;
import java.awt.event.*;
import java.io.*;
import java.util.ArrayList;

public class JavaApplication1 extends JFrame implements ActionListener {
    private JTextField nameField, pinField;
    private JButton addButton, editButton, deleteButton, quitButton;
    private JTable table;
    private DefaultTableModel model;
    private ArrayList<User> users;
    
    public JavaApplication1() {
        setTitle("User Management System");
        setSize(500, 400);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(new BorderLayout());
        
        // Input panel
        JPanel inputPanel = new JPanel(new GridLayout(3, 2, 5, 5));
        
        JLabel nameLabel = new JLabel("Name:");
        JLabel pinLabel = new JLabel("PIN:");
        
        nameField = new JTextField();
        pinField = new JTextField();
        
        inputPanel.add(nameLabel);
        inputPanel.add(nameField);
        inputPanel.add(pinLabel);
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
        String[] columnNames = {"Name", "PIN"};
        model = new DefaultTableModel(columnNames, 0);
        table = new JTable(model);
        JScrollPane scrollPane = new JScrollPane(table);
        
        // Load users from file
        users = loadUsers();
        refreshTable();
        
        // Add panels to frame
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
            JOptionPane.showMessageDialog(this, 
                "Please fill in all fields!",
                "Error",
                JOptionPane.ERROR_MESSAGE);
            return;
        }
        
        users.add(new User(name, pin));
        saveUsers();
        refreshTable();
        
        nameField.setText("");
        pinField.setText("");
    }
    
    private void editUser() {
        int selectedRow = table.getSelectedRow();
        
        if (selectedRow == -1) {
            JOptionPane.showMessageDialog(this, 
                "Please select a user to edit!",
                "Error",
                JOptionPane.ERROR_MESSAGE);
            return;
        }
        
        String name = nameField.getText().trim();
        String pin = pinField.getText().trim();
        
        if (name.isEmpty() || pin.isEmpty()) {
            JOptionPane.showMessageDialog(this, 
                "Please fill in all fields!",
                "Error",
                JOptionPane.ERROR_MESSAGE);
            return;
        }
        
        User user = users.get(selectedRow);
        user.setName(name);
        user.setPin(pin);
        
        saveUsers();
        refreshTable();
        
        nameField.setText("");
        pinField.setText("");
    }
    
    private void deleteUser() {
        int selectedRow = table.getSelectedRow();
        
        if (selectedRow == -1) {
            JOptionPane.showMessageDialog(this, 
                "Please select a user to delete!",
                "Error",
                JOptionPane.ERROR_MESSAGE);
            return;
        }
        
        int confirm = JOptionPane.showConfirmDialog(this,
            "Are you sure you want to delete this user?",
            "Confirm Delete",
            JOptionPane.YES_NO_OPTION);
        
        if (confirm == JOptionPane.YES_OPTION) {
            users.remove(selectedRow);
            saveUsers();
            refreshTable();
            
            nameField.setText("");
            pinField.setText("");
        }
    }
    
    private void refreshTable() {
        model.setRowCount(0);
        for (User user : users) {
            model.addRow(new Object[]{user.getName(), user.getPin()});
        }
    }
    
    private ArrayList<User> loadUsers() {
        ArrayList<User> loadedUsers = new ArrayList<>();
        try {
            BufferedReader reader = new BufferedReader(new FileReader("user.txt"));
            String line;
            while ((line = reader.readLine()) != null) {
                String[] parts = line.split(",");
                if (parts.length >= 2) {
                    loadedUsers.add(new User(parts[0], parts[1]));
                }
            }
            reader.close();
        } catch (IOException e) {
            System.out.println("User file not found. Creating new file.");
        }
        return loadedUsers;
    }
    
    private void saveUsers() {
        try {
            PrintWriter writer = new PrintWriter(new FileWriter("user.txt"));
            for (User user : users) {
                writer.println(user.toString());
            }
            writer.close();
        } catch (IOException e) {
            JOptionPane.showMessageDialog(this, 
                "Error saving users: " + e.getMessage(),
                "Error",
                JOptionPane.ERROR_MESSAGE);
        }
    }
    
    public static void main(String[] args) {
        new JavaApplication1();
    }
}
```

---

### JavaApplication1 Summary

| Feature | Description |
|---------|-------------|
| CRUD Operations | Create, Read, Update, Delete users |
| JTable | Display users in tabular format |
| File Persistence | Save/load users from text file |
| Input Validation | Check for empty fields |
| Selection Handling | Select row to edit/delete |
| Confirmation Dialog | Confirm delete operation |

---

## 10. MyFirstJavaProject - Basic Java Programs

**Location:** `/home/loke/Downloads/OneDrive_4_3-1-2026/MyFirstJavaProject/`

### Learning Objectives
- Write first Java program
- Use Scanner for console input
- Use JOptionPane for dialog input
- Perform basic arithmetic operations
- Convert between data types

### Solution Files

#### 10.1 Hello World

```java
package myfirstjavaproject;

public class MyFirstJavaProject {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
        System.out.println("Welcome to Java Programming!");
    }
}
```

---

#### 10.2 Console Input with Scanner

```java
package newpackage;

import java.util.Scanner;

public class BirthYear {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        
        System.out.print("Enter your name: ");
        String name = input.nextLine();
        
        System.out.print("Enter your birth year: ");
        int birthYear = input.nextInt();
        
        int currentYear = 2026;
        int age = currentYear - birthYear;
        
        System.out.println("\nHello, " + name + "!");
        System.out.println("You are " + age + " years old.");
    }
}
```

---

#### 10.3 Dialog Input with JOptionPane

```java
package newpackage;

import javax.swing.JOptionPane;

public class SampleDialog {
    public static void main(String[] args) {
        String name = JOptionPane.showInputDialog(null, "Enter your name:");
        
        String yearString = JOptionPane.showInputDialog(null, "Enter your birth year:");
        int birthYear = Integer.parseInt(yearString);
        
        int currentYear = 2026;
        int age = currentYear - birthYear;
        
        JOptionPane.showMessageDialog(null, 
            "Hello, " + name + "!\nYou are " + age + " years old.");
    }
}
```

---

### MyFirstJavaProject Summary

| Method | Description |
|--------|-------------|
| System.out.println() | Print to console |
| Scanner | Read from console |
| JOptionPane.showInputDialog() | Dialog input |
| JOptionPane.showMessageDialog() | Dialog output |
| Integer.parseInt() | String to int conversion |
| nextLine() | Read entire line |
| nextInt() | Read integer |

---

## LECTURE SESSIONS

---

## 11. Week01 - Java Fundamentals and Operators

**Location:** `/home/loke/Downloads/OneDrive_3_3-1-2026/Week01/`

### Learning Objectives
- Understand Java primitive types
- Learn arithmetic operators
- Use bitwise operators
- Apply logical operators
- Understand operator precedence
- Use unary and ternary operators

### Primitive Types

| Type | Size | Range | Example |
|------|------|-------|---------|
| byte | 8 bits | -128 to 127 | byte b = 10; |
| short | 16 bits | -32,768 to 32,767 | short s = 1000; |
| int | 32 bits | -2^31 to 2^31-1 | int i = 100000; |
| long | 64 bits | -2^63 to 2^63-1 | long l = 100000L; |
| float | 32 bits | ±3.4e38 | float f = 3.14f; |
| double | 64 bits | ±1.8e308 | double d = 3.14; |
| char | 16 bits | 0 to 65,535 | char c = 'A'; |
| boolean | 1 bit | true/false | boolean b = true; |

### Operators

#### Arithmetic Operators
```java
int a = 10, b = 3;

System.out.println(a + b);  // 13 (addition)
System.out.println(a - b);  // 7 (subtraction)
System.out.println(a * b);  // 30 (multiplication)
System.out.println(a / b);  // 3 (integer division)
System.out.println(a % b);  // 1 (modulus/remainder)
```

#### Bitwise Operators
```java
int a = 5;  // Binary: 0101
int b = 3;  // Binary: 0011

System.out.println(a & b);  // 1 (0101 & 0011 = 0001)
System.out.println(a | b);  // 7 (0101 | 0011 = 0111)
System.out.println(a ^ b);  // 6 (0101 ^ 0011 = 0110)
System.out.println(~a);     // -6 (bitwise NOT)
System.out.println(a << 1); // 10 (left shift)
System.out.println(a >> 1); // 2 (right shift)
```

#### Logical Operators
```java
boolean x = true, y = false;

System.out.println(x && y);  // false (AND - short-circuit)
System.out.println(x || y);  // true (OR - short-circuit)
System.out.println(!x);      // false (NOT)
System.out.println(x & y);   // false (AND - evaluates both)
System.out.println(x | y);   // true (OR - evaluates both)
```

#### Unary Operators
```java
int a = 5;

System.out.println(a++);  // 5 (post-increment, returns 5 then increments)
System.out.println(a);    // 6

System.out.println(++a);  // 7 (pre-increment, increments then returns)
System.out.println(a--);  // 7 (post-decrement)
System.out.println(--a);  // 5 (pre-decrement)

System.out.println(-a);   // -5 (unary minus)
System.out.println(+a);   // 5 (unary plus)
```

#### Ternary Operator
```java
int age = 20;
String status = (age >= 18) ? "Adult" : "Minor";
System.out.println(status);  // Adult
```

### Type Promotion and Casting
```java
// Implicit promotion (widening)
int i = 10;
double d = i;  // int promoted to double automatically

// Explicit casting (narrowing)
double d2 = 10.5;
int i2 = (int) d2;  // 10 (decimal part truncated)

// Integer overflow
int max = Integer.MAX_VALUE;  // 2147483647
int overflow = max + 1;       // -2147483648 (wraps around)

// Using long to avoid overflow
long safe = 2147483648L;  // Requires L suffix
```

---

## 12. Lec03 - Classes and Objects

**Location:** `/home/loke/Downloads/OneDrive_3_3-1-2026/Lec03/`

### Learning Objectives
- Define classes and create objects
- Understand constructors
- Use object references
- Apply access modifiers
- Organize code with packages
- Import classes from other packages

### Class Definition

```java
package lec03;

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
    
    public void accelerate() {
        System.out.println(brand + " " + model + " is accelerating!");
    }
    
    public String getBrand() {
        return brand;
    }
    
    public String getModel() {
        return model;
    }
    
    public int getYear() {
        return year;
    }
}
```

### Object Creation

```java
package lec03;

public class Lec03 {
    public static void main(String[] args) {
        // Create objects
        Car car1 = new Car("Toyota", "Camry", 2023);
        Car car2 = new Car("Honda", "Civic", 2024);
        
        // Use objects
        car1.start();
        car1.accelerate();
        
        car2.start();
        
        // Access object data
        System.out.println("Car 1: " + car1.getBrand() + " " + 
                          car1.getModel() + " (" + car1.getYear() + ")");
    }
}
```

### Object References (Composition)

```java
package lec03;

public class Student {
    private String name;
    private int id;
    private Car car;  // Object reference
    
    public Student(String name, int id, Car car) {
        this.name = name;
        this.id = id;
        this.car = car;
    }
    
    public void showInfo() {
        System.out.println("Student: " + name + " (ID: " + id + ")");
        System.out.println("Drives: " + car.getBrand() + " " + car.getModel());
    }
}
```

### Access Modifiers

| Modifier | Class | Package | Subclass | World |
|----------|-------|---------|----------|-------|
| private | ✓ | ✗ | ✗ | ✗ |
| (default) | ✓ | ✓ | ✗ | ✗ |
| protected | ✓ | ✓ | ✓ | ✗ |
| public | ✓ | ✓ | ✓ | ✓ |

### Package Organization

```
project/
├── src/
│   ├── lec03/
│   │   ├── Car.java
│   │   ├── Student.java
│   │   └── Lec03.java
│   ├── package1/
│   │   ├── ClassX1.java
│   │   └── ClassX2.java
│   └── package2/
│       ├── ClassY1.java
│       └── ClassY2.java
```

### Import Statements

```java
import lec03.Car;                    // Import specific class
import lec03.*;                      // Import all classes in package
import java.util.Scanner;            // Import Scanner class
import java.util.*;                  // Import all util classes
```

---

## 13. Week02Lec01 - Arrays and Object-Oriented Design

**Location:** `/home/loke/Downloads/OneDrive_3_3-1-2026/Week02Lec01/`

### Learning Objectives
- Understand array fundamentals
- Compare procedural vs OOP approaches
- Learn pass by value
- Implement object-oriented design

### Procedural Approach (Arrays)

```java
package week02lec01;

public class Week02Lec01 {
    public static void main(String[] args) {
        // Parallel arrays (procedural approach)
        String[] names = {"Ahmad", "Siti", "Ali"};
        int[] ids = {1001, 1002, 1003};
        double[] balances = {1000.0, 2000.0, 1500.0};
        
        // Display all customers
        for (int i = 0; i < names.length; i++) {
            System.out.println("Customer: " + names[i] + 
                              " (ID: " + ids[i] + 
                              ", Balance: RM" + balances[i] + ")");
        }
        
        // Search for customer
        String searchName = "Siti";
        for (int i = 0; i < names.length; i++) {
            if (names[i].equals(searchName)) {
                System.out.println("Found: " + names[i] + 
                                  ", Balance: RM" + balances[i]);
                break;
            }
        }
    }
}
```

### OOP Approach (Classes)

```java
package oo1;

public class Customer {
    public String name;      // Direct field access (not recommended)
    public int id;
    public double balance;
    
    public Customer(String name, int id, double balance) {
        this.name = name;
        this.id = id;
        this.balance = balance;
    }
}
```

```java
package oo1;

public class NewMain {
    public static void main(String[] args) {
        // Object array (OOP approach)
        Customer[] customers = {
            new Customer("Ahmad", 1001, 1000.0),
            new Customer("Siti", 1002, 2000.0),
            new Customer("Ali", 1003, 1500.0)
        };
        
        // Display all customers
        for (Customer c : customers) {
            System.out.println("Customer: " + c.name + 
                              " (ID: " + c.id + 
                              ", Balance: RM" + c.balance + ")");
        }
    }
}
```

### OOP with Encapsulation

```java
package oo2;

public class Customer {
    private String name;      // Encapsulated fields
    private int id;
    private double balance;
    
    public Customer(String name, int id, double balance) {
        this.name = name;
        this.id = id;
        this.balance = balance;
    }
    
    // Getters
    public String getName() {
        return name;
    }
    
    public int getId() {
        return id;
    }
    
    public double getBalance() {
        return balance;
    }
    
    // Business method
    public void withdraw(double amount) {
        if (amount <= balance) {
            balance -= amount;
        }
    }
    
    public void deposit(double amount) {
        balance += amount;
    }
}
```

### Pass by Value

```java
package passbyvalue;

public class NewMain {
    public static void main(String[] args) {
        // Primitive type (pass by value)
        int x = 7;
        System.out.println("Before: x = " + x);
        changePrimitive(x);
        System.out.println("After: x = " + x);  // x remains 7
        
        // Object reference (pass by value)
        Customer c = new Customer("Jamal", 123, 400);
        System.out.println("Before: balance = " + c.getBalance());
        changeObject(c);
        System.out.println("After: balance = " + c.getBalance());  // balance changed to 5000
    }
    
    public static void changePrimitive(int num) {
        num = 100;  // Changes local copy only
    }
    
    public static void changeObject(Customer cust) {
        cust.deposit(4600);  // Modifies object through reference
    }
}
```

**Key Points:**
- Primitive values are copied (original not affected)
- Object references are copied (object can be modified)
- Cannot change which object reference points to

---

## 14. Week04Lec04 - Encapsulation and Inheritance

**Location:** `/home/loke/Downloads/OneDrive_3_3-1-2026/Week04Lec04/`

### Learning Objectives
- Understand encapsulation principles
- Implement inheritance
- Use method overriding
- Apply protected access modifier
- Understand multi-level inheritance

### Encapsulation

```java
package encapsulation;

public class Customer {
    private String name;      // Private fields
    private int id;
    private double balance;
    
    public Customer(String name, int id, double balance) {
        this.name = name;
        this.id = id;
        this.balance = balance;
    }
    
    // Public getters and setters
    public String getName() {
        return name;
    }
    
    public void setName(String name) {
        this.name = name;
    }
    
    public int getId() {
        return id;
    }
    
    public double getBalance() {
        return balance;
    }
    
    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        }
    }
    
    public void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
        }
    }
}
```

### Inheritance

```java
package inheritance;

public class ClassA {
    protected String message = "Hello from ClassA";
    
    public void methodA() {
        System.out.println("Method A in ClassA");
    }
    
    public void commonMethod() {
        System.out.println("Common method in ClassA");
    }
}
```

```java
package inheritance;

public class ClassB1 extends ClassA {
    @Override
    public void methodA() {
        System.out.println("Method A in ClassB1 (overridden)");
    }
    
    public void methodB() {
        System.out.println("Method B in ClassB1");
        System.out.println("Can access: " + message);  // protected field accessible
    }
    
    @Override
    public void commonMethod() {
        System.out.println("Common method in ClassB1 (overridden)");
        super.commonMethod();  // Call parent's method
    }
}
```

```java
package inheritance;

public class ClassB2 extends ClassA {
    public void methodC() {
        System.out.println("Method C in ClassB2");
    }
}
```

### Multi-Level Inheritance

```java
package inheritance;

public class MultiLevelClassC extends ClassB1 {
    public void methodD() {
        System.out.println("Method D in MultiLevelClassC");
        System.out.println("Grandparent's message: " + message);
    }
    
    @Override
    public void methodA() {
        System.out.println("Method A in MultiLevelClassC (overridden again)");
    }
}
```

### Test Program

```java
package inheritance;

public class NewMain {
    public static void main(String[] args) {
        // Create objects
        ClassA a = new ClassA();
        ClassB1 b1 = new ClassB1();
        ClassB2 b2 = new ClassB2();
        MultiLevelClassC c = new MultiLevelClassC();
        
        // Test ClassA
        System.out.println("=== ClassA ===");
        a.methodA();
        a.commonMethod();
        
        // Test ClassB1
        System.out.println("\n=== ClassB1 ===");
        b1.methodA();        // Overridden
        b1.methodB();
        b1.commonMethod();   // Overridden
        
        // Test ClassB2
        System.out.println("\n=== ClassB2 ===");
        b2.methodA();        // Inherited
        b2.methodC();
        
        // Test MultiLevelClassC
        System.out.println("\n=== MultiLevelClassC ===");
        c.methodA();         // Overridden again
        c.methodB();         // Inherited from ClassB1
        c.methodD();
    }
}
```

**Output:**
```
=== ClassA ===
Method A in ClassA
Common method in ClassA

=== ClassB1 ===
Method A in ClassB1 (overridden)
Method B in ClassB1
Can access: Hello from ClassA
Common method in ClassB1 (overridden)
Common method in ClassA

=== ClassB2 ===
Method A in ClassB1 (overridden)
Method C in ClassB2

=== MultiLevelClassC ===
Method A in MultiLevelClassC (overridden again)
Method B in ClassB1
Can access: Hello from ClassA
Method D in MultiLevelClassC
Grandparent's message: Hello from ClassA
```

---

## 15. Week08Lec06 - Polymorphism

**Location:** `/home/loke/Downloads/OneDrive_3_3-1-2026/Week08Lec06/`

### Learning Objectives
- Understand compile-time polymorphism (overloading)
- Understand runtime polymorphism (overriding)
- Use type casting (upcasting and downcasting)
- Apply instanceof operator
- Implement dynamic method dispatch

### Compile-Time Polymorphism (Overloading)

```java
package week08lec06;

public class Week08Lec06 {
    // Overloaded methods (same name, different parameters)
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
```

### Runtime Polymorphism (Overriding)

```java
package polymorphism4;

public class ClassA {
    public void methodA() {
        System.out.println("Method A in ClassA");
    }
}
```

```java
package polymorphism4;

public class ClassB extends ClassA {
    @Override
    public void methodA() {
        System.out.println("Method A in ClassB (overridden)");
    }
    
    public void methodB() {
        System.out.println("Method B in ClassB");
    }
}
```

```java
package polymorphism4;

public class ClassC extends ClassA {
    @Override
    public void methodA() {
        System.out.println("Method A in ClassC (overridden)");
    }
    
    public void methodC() {
        System.out.println("Method C in ClassC");
    }
}
```

### Type Casting and instanceof

```java
package polymorphism4;

public class NewMain {
    public static void main(String[] args) {
        ClassA a = new ClassA();
        ClassB b = new ClassB();
        ClassC c = new ClassC();
        
        // Upcasting (implicit)
        ClassA x1 = b;        // ClassB to ClassA
        ClassA x2 = c;        // ClassC to ClassA
        
        // Runtime polymorphism
        x1.methodA();         // Calls ClassB.methodA()
        x2.methodA();         // Calls ClassC.methodA()
        
        // Downcasting (explicit)
        ClassB y1 = (ClassB)x1;  // Safe
        y1.methodB();            // ClassB-specific method
        
        // Using instanceof to check type
        if (x1 instanceof ClassB) {
            System.out.println("x1 is an instance of ClassB");
            ClassB temp = (ClassB)x1;
            temp.methodB();
        }
        
        if (x2 instanceof ClassC) {
            System.out.println("x2 is an instance of ClassC");
            ClassC temp = (ClassC)x2;
            temp.methodC();
        }
        
        // Unsafe downcasting (throws ClassCastException)
        try {
            ClassC unsafe = (ClassC)x1;  // x1 is actually ClassB
        } catch (ClassCastException e) {
            System.out.println("Invalid downcasting: " + e.getMessage());
        }
    }
}
```

### Polymorphism Types Summary

| Type | When Resolved | Example |
|------|---------------|---------|
| Overloading | Compile-time | Multiple methods with same name, different parameters |
| Overriding | Runtime | Subclass provides new implementation |
| Upcasting | Compile-time | Subclass reference assigned to superclass |
| Downcasting | Runtime | Superclass reference cast to subclass |

---

## 16. Week09Lec07 - Abstract Classes and Interfaces

**Location:** `/home/loke/Downloads/OneDrive_3_3-1-2026/Week09Lec07/`

### Learning Objectives
- Create abstract classes
- Define abstract methods
- Implement interfaces
- Extend interfaces
- Implement multiple interfaces

### Abstract Classes

```java
package week09lec07;

public abstract class Shape {
    private String color;
    private boolean filled;
    
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
    
    public boolean isFilled() {
        return filled;
    }
    
    public void setColor(String color) {
        this.color = color;
    }
    
    public void setFilled(boolean filled) {
        this.filled = filled;
    }
    
    // Abstract methods (no implementation)
    public abstract double getArea();
    public abstract double getPerimeter();
}
```

```java
package week09lec07;

public class Circle extends Shape {
    private double radius;
    
    public Circle() {
        radius = 1;
    }
    
    public Circle(double radius) {
        this.radius = radius;
    }
    
    public Circle(double radius, String color, boolean filled) {
        super(color, filled);
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
```

```java
package week09lec07;

public class Rectangle extends Shape {
    private double width;
    private double height;
    
    public Rectangle() {
        width = 1;
        height = 1;
    }
    
    public Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }
    
    @Override
    public double getArea() {
        return width * height;
    }
    
    @Override
    public double getPerimeter() {
        return 2 * (width + height);
    }
}
```

### Interfaces

```java
package interfacesample;

public interface InterfaceA {
    void methodA();
    int CONSTANT_A = 100;  // public static final by default
}
```

```java
package interfacesample;

public interface InterfaceB extends InterfaceA {
    void methodB();
    int CONSTANT_B = 200;
}
```

```java
package interfacesample;

public class ClassA implements InterfaceB {
    @Override
    public void methodA() {
        System.out.println("Method A in ClassA");
    }
    
    @Override
    public void methodB() {
        System.out.println("Method B in ClassA");
    }
}
```

```java
package interfacesample;

public abstract class ClassB implements InterfaceA {
    // Abstract class implementing interface
    // Can choose to implement or leave abstract
    
    @Override
    public void methodA() {
        System.out.println("Method A in ClassB");
    }
    
    public abstract void methodC();
}
```

### Test Program

```java
package week09lec07;

public class Week09Lec07 {
    public static void main(String[] args) {
        // Cannot create abstract class instance
        // Shape s = new Shape();  // Compilation error
        
        // Create concrete instances
        Circle circle = new Circle(5, "red", true);
        Rectangle rectangle = new Rectangle(4, 6, "blue", false);
        
        System.out.println("Circle:");
        System.out.println("  Area: " + circle.getArea());
        System.out.println("  Perimeter: " + circle.getPerimeter());
        
        System.out.println("\nRectangle:");
        System.out.println("  Area: " + rectangle.getArea());
        System.out.println("  Perimeter: " + rectangle.getPerimeter());
        
        // Polymorphism with abstract class
        Shape[] shapes = {circle, rectangle};
        System.out.println("\n=== Total Area ===");
        double totalArea = 0;
        for (Shape shape : shapes) {
            totalArea += shape.getArea();
        }
        System.out.println("Total: " + totalArea);
    }
}
```

---

## 17. Week10Lec09 - Exception Handling

**Location:** `/home/loke/Downloads/OneDrive_3_3-1-2026/Week10Lec09/`

### Learning Objectives
- Understand exception hierarchy
- Use try-catch-finally blocks
- Handle multiple exceptions
- Use throws keyword
- Create custom exceptions
- Understand exception propagation

### Exception Hierarchy

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

### Basic Exception Handling

```java
package week10lec09;

public class TryCatch {
    public static void main(String[] args) {
        try {
            int[] numbers = {1, 2, 3};
            System.out.println(numbers[10]);  // ArrayIndexOutOfBoundsException
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Error: " + e.getMessage());
        }
        
        System.out.println("Program continues...");
    }
}
```

### Multiple Catch Blocks

```java
package week10lec09;

public class Multiple {
    public static void main(String[] args) {
        try {
            String[] data = {"123", "abc", "456"};
            for (String s : data) {
                int num = Integer.parseInt(s);
                System.out.println("Number: " + num);
            }
        } catch (NumberFormatException e) {
            System.out.println("Invalid number format: " + e.getMessage());
        } catch (Exception e) {
            System.out.println("General error: " + e.getMessage());
        }
    }
}
```

### Finally Block

```java
package week10lec09;

public class Finally {
    public static void main(String[] args) {
        try {
            int result = 10 / 0;  // ArithmeticException
        } catch (ArithmeticException e) {
            System.out.println("Cannot divide by zero!");
        } finally {
            System.out.println("Finally block always executes");
        }
        
        System.out.println("Program continues...");
    }
}
```

### Exception Propagation

```java
package week10lec09;

public class ManyMethods {
    public static void main(String[] args) {
        try {
            method1();
        } catch (Exception e) {
            System.out.println("Caught in main: " + e.getMessage());
        }
    }
    
    public static void method1() throws Exception {
        method2();
    }
    
    public static void method2() throws Exception {
        method3();
    }
    
    public static void method3() throws Exception {
        throw new Exception("Exception from method3");
    }
}
```

### Custom Exception

```java
package exe4;

public class NotEnoughMoney extends Exception {
    public NotEnoughMoney(String name, double balance, double amount) {
        super("Sorry " + name + ", you cannot withdraw RM" + 
              amount + " because your balance is RM" + balance + "!");
    }
}
```

```java
package exe4;

public class Account {
    private String name;
    private double balance;
    
    public Account(String name, double balance) {
        this.name = name;
        this.balance = balance;
    }
    
    public void withdraw(double amount) throws NotEnoughMoney {
        if (amount > balance) {
            throw new NotEnoughMoney(name, balance, amount);
        }
        balance -= amount;
        System.out.println("Withdrawal successful. New balance: RM" + balance);
    }
}
```

```java
package exe4;

public class NewMain {
    public static void main(String[] args) {
        Account account = new Account("Ahmad", 1000);
        
        try {
            account.withdraw(500);  // Success
            account.withdraw(800);  // Throws NotEnoughMoney
        } catch (NotEnoughMoney e) {
            System.out.println("Error: " + e.getMessage());
        }
    }
}
```

### Checked vs Unchecked Exceptions

| Type | Must Handle | Example |
|------|-------------|---------|
| Checked (compile-time) | Yes | IOException, SQLException |
| Unchecked (runtime) | No | NullPointerException, ArithmeticException |

---

## 18. Week12Binary - Serialization and Final Keywords

**Location:** `/home/loke/Downloads/OneDrive_3_3-1-2026/Week12Binary/`

### Learning Objectives
- Understand object serialization
- Use Serializable interface
- Implement ObjectOutputStream
- Implement ObjectInputStream
- Use final keyword
- Understand final variables, methods, and classes

### Object Serialization

```java
package week12binary;

import java.io.Serializable;

public class Student implements Serializable {
    private String name;
    private int id;
    private double gpa;
    
    public Student(String name, int id, double gpa) {
        this.name = name;
        this.id = id;
        this.gpa = gpa;
    }
    
    public String getName() {
        return name;
    }
    
    public int getId() {
        return id;
    }
    
    public double getGpa() {
        return gpa;
    }
    
    @Override
    public String toString() {
        return name + " (ID: " + id + ", GPA: " + gpa + ")";
    }
}
```

### Writing Objects (Serialization)

```java
package week12binary;

import java.io.*;

public class Write {
    public static void main(String[] args) {
        Student[] students = {
            new Student("Ahmad", 1001, 3.5),
            new Student("Siti", 1002, 3.8),
            new Student("Ali", 1003, 3.2)
        };
        
        try {
            ObjectOutputStream oos = new ObjectOutputStream(
                new FileOutputStream("Tuesday.txt"));
            oos.writeObject(students);
            oos.close();
            System.out.println("Students serialized successfully!");
        } catch (IOException e) {
            System.out.println("Error writing file: " + e.getMessage());
        }
    }
}
```

### Reading Objects (Deserialization)

```java
package week12binary;

import java.io.*;

public class Read {
    public static void main(String[] args) {
        try {
            ObjectInputStream ois = new ObjectInputStream(
                new FileInputStream("Tuesday.txt"));
            Student[] students = (Student[]) ois.readObject();
            ois.close();
            
            System.out.println("Deserialized Students:");
            for (Student s : students) {
                System.out.println(s);
            }
        } catch (IOException | ClassNotFoundException e) {
            System.out.println("Error reading file: " + e.getMessage());
        }
    }
}
```

### Final Keyword

```java
package week12binary;

class A {
    int x = 10;
    final int CONSTANT = 100;  // Cannot be changed
    
    final void methodA() {
        System.out.println("Final method in A");
    }
}

class B extends A {
    int x = 20;
    
    // final void methodA() { }  // Error: Cannot override final method
    
    void methodB() {
        // CONSTANT = 200;  // Error: Cannot assign value to final variable
        System.out.println("x in B: " + x);
        System.out.println("CONSTANT: " + CONSTANT);
    }
}

public class Week12Binary {
    public static void main(String[] args) {
        A a = new A();
        B b = new B();
        
        a.methodA();
        b.methodA();  // Inherits final method
        b.methodB();
        
        // Final local variable
        final int MAX = 100;
        System.out.println("MAX: " + MAX);
    }
}
```

### Final Keyword Summary

| Usage | Description |
|-------|-------------|
| final variable | Value cannot be changed |
| final method | Cannot be overridden |
| final class | Cannot be extended |
| final parameter | Cannot be modified within method |

---

## 19. ClassDiagram - UML Relationships

**Location:** `/home/loke/Downloads/OneDrive_3_3-1-2026/ClassDiagram/`

### Learning Objectives
- Understand association relationships
- Differentiate aggregation vs composition
- Model class relationships in UML
- Apply appropriate relationship types

### UML Relationships

#### 1. Association
- "Has a" relationship
- Objects have independent lifecycles
- Weakest form of relationship

```java
public class Owner {
    private Association association;
    
    public void setAssociation(Association a) {
        this.association = a;
    }
}

public class Association {
    private String name;
    
    public Association(String name) {
        this.name = name;
    }
}
```

#### 2. Aggregation
- "Has a" relationship with weak ownership
- Objects have independent lifecycles
- Child can exist without parent

```java
public class Aggregation {
    private List<Item> items;
    
    public void addItem(Item item) {
        items.add(item);
    }
}

public class Item {
    private String name;
    
    public Item(String name) {
        this.name = name;
    }
}
```

#### 3. Composition
- "Has a" relationship with strong ownership
- Child cannot exist without parent
- Lifecycles are linked

```java
public class Composition {
    private final Part part;  // Strong ownership
    
    public Composition() {
        part = new Part();  // Part created with Composition
    }
}

public class Part {
    private String description;
    
    public Part() {
        this.description = "Essential part";
    }
}
```

### Relationship Comparison

| Relationship | Ownership | Lifecycle | Multiplicity | Example |
|--------------|-----------|-----------|--------------|---------|
| Association | None | Independent | 1:1, 1:N, N:M | Student-Course |
| Aggregation | Weak | Independent | 1:N | Department-Employee |
| Composition | Strong | Dependent | 1:N | Car-Engine |

### UML Notation

```
Association:      ────────
Aggregation:      ◇──────
Composition:      ♦──────
Inheritance:      △──────
Implementation:   - - - ->

1 (One)
0..1 (Zero or One)
* (Many)
0..* (Zero or Many)
1..* (One or Many)
```

---

## COMPLETE SUMMARY

### Java Programming Course Progression

| Week | Topic | Key Concepts |
|------|-------|--------------|
| 1 | Fundamentals | Primitive types, operators, basic syntax |
| 2 | Arrays & OOP Intro | Arrays, classes, objects, methods |
| 3 | Classes & Objects | Constructors, access modifiers, packages |
| 4 | Encapsulation & Inheritance | Private fields, extends, super, overriding |
| 6 | Polymorphism | Overloading, overriding, type casting |
| 7 | GUI Programming | Swing components, event handling |
| 8 | File I/O & GUI Advanced | Scanner, file reading, mouse events |
| 9 | Abstract Classes & Interfaces | abstract keyword, interface implementation |
| 10 | Exception Handling | try-catch, custom exceptions |
| 12 | Serialization & Advanced OOP | Serializable, final keyword |

### Key Takeaways

1. **Object-Oriented Programming**
   - Encapsulation: Hide implementation details
   - Inheritance: Reuse code through class hierarchy
   - Polymorphism: One interface, multiple implementations
   - Abstraction: Hide complexity, expose essential features

2. **Best Practices**
   - Use private fields with public getters/setters
   - Override toString() for meaningful object representation
   - Use @Override annotation for method overriding
   - Prefer interfaces over abstract classes for multiple inheritance
   - Handle exceptions appropriately (don't ignore them)

3. **GUI Development**
   - Use Swing components for cross-platform compatibility
   - Implement appropriate event listeners
   - Choose appropriate layout managers
   - Separate business logic from presentation

4. **Data Persistence**
   - Use text files for simple applications
   - Use serialization for object persistence
   - Implement proper error handling for I/O operations

5. **Code Organization**
   - Use packages to organize related classes
   - Follow naming conventions (PascalCase for classes, camelCase for methods)
   - Add meaningful comments for complex logic
   - Keep methods focused and small

---

**End of Complete Java Labs Notes**

*This document contains all solutions and explanations for 10 labs and 9 lectures covering fundamental to advanced Java programming concepts.*