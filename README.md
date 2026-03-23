
---

# Abstraction in Java (OOP)

## 1. Introduction to Object Oriented Programming

Object Oriented Programming (OOP) is a programming paradigm based on the concept of **objects and classes**.

The four main pillars of OOP are:

1. **Encapsulation**
2. **Abstraction**
3. **Inheritance**
4. **Polymorphism**

Among these, **Abstraction** plays a key role in **reducing complexity and designing large software systems**.

---

# 2. What is Abstraction?

### Definition

**Abstraction is the process of hiding implementation details and showing only the essential features of an object.**

In abstraction, the user **interacts with the functionality**, but **does not see the internal implementation**.

### Key Idea

Focus on:

✔ What an object does
❌ How it does it

---

# 3. Real Life Examples of Abstraction

### 1. ATM Machine

User sees options like:

* Withdraw Money
* Deposit Money
* Check Balance

But internally the ATM performs:

* Database queries
* PIN authentication
* Bank server communication

The user **does not see these details**, which means **abstraction is applied**.

---

### 2. Car Driving Example

When driving a car:

User interacts with:

* Steering
* Accelerator
* Brake

But does not know about:

* Engine combustion
* Gear mechanisms
* Fuel injection

The internal working is hidden.

---

### 3. Mobile Phone

You press a button to call someone.

You do not know:

* Signal transmission
* Network routing
* Cellular tower processing

That is **abstraction**.

---

# 4. Why Abstraction is Important

Abstraction helps programmers in many ways.

### 1. Reduces Complexity

Large software systems contain millions of lines of code.

Abstraction helps developers **focus only on necessary details**.

---

### 2. Improves Maintainability

If implementation changes internally, users don't need to change their code.

---

### 3. Enhances Security

Sensitive implementation details are hidden.

Example:

Banking algorithms

---

### 4. Code Reusability

Abstract structures allow reuse of code.

---

### 5. Helps in Modular Programming

Systems can be divided into modules.

---

# 5. Abstraction in Java

Java implements abstraction using two main mechanisms:

1. **Abstract Classes**
2. **Interfaces**

Both provide **abstraction but in different ways**.

---

# 6. Abstract Class in Java

## Definition

An **abstract class is a class that cannot be instantiated and may contain abstract methods.**

It is used as a **base class for other classes**.

---

## Syntax

```java
abstract class ClassName
{
    abstract void methodName();
}
```

---

## Example

```java
abstract class Shape {

    abstract void draw();

}
```

Here:

`draw()` has **no implementation**.

Subclasses must define it.

---

# 7. Example Program of Abstract Class

```java
abstract class Animal {

    abstract void sound();

}

class Dog extends Animal {

    void sound() {
        System.out.println("Dog barks");
    }

}

class Cat extends Animal {

    void sound() {
        System.out.println("Cat meows");
    }

}

public class Test {

    public static void main(String[] args) {

        Dog d = new Dog();
        d.sound();

        Cat c = new Cat();
        c.sound();

    }

}
```

### Output

```
Dog barks
Cat meows
```

Explanation:

Animal class defines **abstract behavior**.

Dog and Cat **implement the behavior**.

---

# 8. Abstract Methods

## Definition

An abstract method is a **method without a body**.

It only declares functionality.

---

### Syntax

```java
abstract returnType methodName();
```

Example:

```java
abstract void display();
```

---

### Key Points

* No implementation
* Must be overridden in subclass
* Declared using **abstract keyword**

---

# 9. Rules of Abstract Classes

### Rule 1

Abstract class must use keyword **abstract**.

```java
abstract class Vehicle {}
```

---

### Rule 2

Abstract classes **cannot be instantiated**.

Invalid:

```java
Vehicle v = new Vehicle();
```

---

### Rule 3

Abstract classes can contain:

* Abstract methods
* Concrete methods
* Constructors
* Static methods
* Variables

---

### Rule 4

If a class contains abstract methods, it **must be abstract**.

---

### Rule 5

Subclasses must **override abstract methods**.

---

# 10. Concrete Methods

Concrete methods are **normal methods with implementation**.

Example:

```java
abstract class Test {

    abstract void display();

    void show() {
        System.out.println("Concrete method");
    }

}
```

---

# 11. Constructors in Abstract Class

Abstract classes **can have constructors**.

Example:

```java
abstract class Animal {

    Animal() {
        System.out.println("Animal constructor");
    }

}
```

When subclass object is created, constructor is called.

---

# 12. Interface in Java

## Definition

An **interface is a blueprint of a class that contains abstract methods.**

Interfaces provide **complete abstraction**.

---

## Syntax

```java
interface InterfaceName {

    void methodName();

}
```

---

# 13. Example of Interface

```java
interface Vehicle {

    void start();

}

class Bike implements Vehicle {

    public void start() {
        System.out.println("Bike starts");
    }

}

class Car implements Vehicle {

    public void start() {
        System.out.println("Car starts");
    }

}
```

---

# 14. Rules of Interface

### Rule 1

Methods are **public and abstract by default**.

```
void display();
```

Actually means

```
public abstract void display();
```

---

### Rule 2

Variables are **public static final**.

Example:

```java
int x = 10;
```

Means:

```java
public static final int x = 10;
```

---

### Rule 3

Interfaces **cannot have constructors**.

---

### Rule 4

A class uses **implements keyword**.

```java
class Test implements InterfaceName
```

---

# 15. Multiple Inheritance using Interfaces

Java does not support multiple inheritance with classes.

But it supports it with interfaces.

Example:

```java
interface A {

    void show();

}

interface B {

    void display();

}

class Test implements A, B {

    public void show() {
        System.out.println("Show method");
    }

    public void display() {
        System.out.println("Display method");
    }

}
```

---

# 16. Abstract Class vs Interface

| Feature              | Abstract Class      | Interface           |
| -------------------- | ------------------- | ------------------- |
| Keyword              | abstract            | interface           |
| Methods              | Abstract + Concrete | Mostly Abstract     |
| Variables            | Any                 | public static final |
| Constructor          | Allowed             | Not allowed         |
| Multiple Inheritance | Not supported       | Supported           |

---

# 17. Abstraction vs Encapsulation

Students often confuse these.

| Abstraction                             | Encapsulation                    |
| --------------------------------------- | -------------------------------- |
| Hides implementation                    | Hides data                       |
| Achieved using abstract class/interface | Achieved using private variables |
| Focus on design                         | Focus on security                |

Example:

Abstraction → What object does
Encapsulation → Protect object data

---

# 18. Partial Abstraction

Abstract classes support **partial abstraction**.

Meaning:

Some methods have implementation.

Example:

```java
abstract class Test {

    abstract void show();

    void display() {
        System.out.println("Hello");
    }

}
```

---

# 19. Full Abstraction

Interfaces support **100% abstraction** (before Java 8).

Example:

```java
interface A {

    void show();

    void display();

}
```

---

# 20. Real World Software Example

### Banking System

Abstract class:

```
BankAccount
```

Subclasses:

```
SavingsAccount
CurrentAccount
```

Abstract methods:

```
calculateInterest()
withdraw()
deposit()
```

Each account type implements them differently.

---

# 21. Advantages of Abstraction

### 1. Reduces complexity

Large systems become manageable.

---

### 2. Improves code maintainability

Changes in internal code do not affect users.

---

### 3. Improves code reusability

Common functionality reused.

---

### 4. Provides security

Internal implementation hidden.

---

### 5. Helps in designing large systems

Essential for enterprise applications.

---

# 22. Disadvantages of Abstraction

### 1. Increased design complexity

Requires proper planning.

### 2. More classes and interfaces

May increase number of files.

---

# 23. Key Interview / Viva Questions

### Q1 What is abstraction in Java?

Abstraction is the process of hiding implementation details and exposing only essential features.

---

### Q2 How is abstraction implemented in Java?

Using:

* Abstract classes
* Interfaces

---

### Q3 Can we create object of abstract class?

No.

---

### Q4 Can abstract class have constructor?

Yes.

---

### Q5 Can interface have variables?

Yes, but they are **public static final**.

---

# 24. Summary

Abstraction is a fundamental concept in Java OOP.

It allows developers to:

* Hide complex implementation
* Expose only necessary functionality
* Improve code maintainability
* Build scalable software systems

Java achieves abstraction using:

* **Abstract Classes**
* **Interfaces**

Understanding abstraction is essential for building **real-world applications and frameworks**.

---
# Assignment: Abstract Class (Complex Example – Banking System)

## Problem Statement

Write a Java program to demonstrate the concept of **Abstract Class** using a Banking System.

Create an abstract class **Account** having:

* Data members: accountNumber, name, balance
* Abstract methods:

  * deposit()
  * withdraw()
  * calculateInterest()
* Concrete method:

  * displayAccountDetails()

Create two derived classes:

* **SavingAccount**
* **CurrentAccount**

Override abstract methods in both derived classes.

Write a **menu driven driver program** to perform operations like:

1. Deposit
2. Withdraw
3. Display Details
4. Calculate Interest

---


```

---

```

---

## Result

Thus, the Java program demonstrating **Abstract Class with real life Banking System and implementation in derived classes** was successfully implemented.

---

