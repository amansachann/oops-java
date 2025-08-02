# ✍️ Interface

---

## 🧠 What is an Interface?

### 📌 Definition:

> An **interface** in Java is a **contract** that defines **what a class must do**, but **not how it does it**.
> 
> It contains **abstract methods** (without body) and from Java 8+, it can also have **default** and **static methods**.

---

## 🔧 Syntax

```java
interface Animal {
    void makeSound(); // abstract method (by default)
}
```

```java
class Dog implements Animal {
    public void makeSound() {
        System.out.println("Bark! 🐶");
    }
}
```

---

## 🎯 Why Use Interfaces?

| ✅ Benefit                | 📘 Explanation                             |
| ------------------------ | ------------------------------------------ |
| Pure Abstraction         | Only defines **what**, not **how**         |
| Multiple Inheritance     | A class can implement multiple interfaces  |
| Loose Coupling           | Makes code more flexible & maintainable    |
| Strategy Design Patterns | Behavior defined through interface         |
| Used by Frameworks       | Spring, Hibernate, JDBC rely on interfaces |

---

## 🛠️ Key Rules

| Feature               | Interface                                 |
| --------------------- | ----------------------------------------- |
| Method type (Java 7)  | Only abstract                             |
| Method type (Java 8+) | abstract, `default`, `static`             |
| Method modifiers      | `public abstract` (default)               |
| Field modifiers       | `public static final` (default)           |
| Inheritance           | A class can implement multiple interfaces |
| Object creation?      | ❌ Not allowed (no constructors)           |

---

## 🧪 Example with Default & Static (Java 8+)

```java
interface Vehicle {
    void start(); // abstract

    default void fuelType() {
        System.out.println("Uses petrol/diesel");
    }

    static void serviceReminder() {
        System.out.println("Service every 6 months");
    }
}
```

---

## 📦 Interface + Class Example

```java
interface Payment {
    void pay(double amount);
}

class UPI implements Payment {
    public void pay(double amount) {
        System.out.println("Paid ₹" + amount + " via UPI");
    }
}

class Card implements Payment {
    public void pay(double amount) {
        System.out.println("Paid ₹" + amount + " via Card");
    }
}
```

✅ Usage:

```java
Payment p = new UPI();
p.pay(500); // Paid ₹500 via UPI
```

---

## 👥 Multiple Interface Implementation

```java
interface A {
    void show();
}

interface B {
    void display();
}

class C implements A, B {
    public void show() {
        System.out.println("Show A");
    }
    public void display() {
        System.out.println("Display B");
    }
}
```

---

## ⚔️ Interface vs Abstract Class

| Feature      | Interface 🧬               | Abstract Class 🧱          |
| ------------ | -------------------------- | -------------------------- |
| Inheritance  | Multiple ✅                 | Single ❌                   |
| Constructor  | ❌ No                       | ✅ Yes                      |
| Method Types | abstract, default, static  | abstract + concrete        |
| Fields       | `public static final` only | Can be any type            |
| Use Case     | Behavior contract          | Base class with some logic |

---

## 🚫 Common Mistakes

| ❌ Mistake                            | ⚠️ Why it's a Problem                   |
| ------------------------------------ | --------------------------------------- |
| Trying to create object of interface | Not allowed — interface is abstract     |
| Forgetting to implement all methods  | Compiler error unless class is abstract |
| Declaring field as mutable           | Not allowed — all fields are final      |

---

## 🏁 Summary Table

| Feature              | Interface                     |
| -------------------- | ----------------------------- |
| Methods              | abstract, default, static     |
| Fields               | `public static final`         |
| Object creation      | ❌ Not possible                |
| Multiple inheritance | ✅ Yes                         |
| Real usage           | Spring, REST APIs, OOP design |

---

## 🔥 Real-World Analogy

> **Interface = Contract**  
> "A class **signs** the interface and promises to **deliver all services** defined by it."

---
[🏠 Back to Home](../..)