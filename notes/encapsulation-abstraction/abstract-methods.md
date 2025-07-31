# 🔪 Abstract Methods

---

## 🧠 What is an Abstract Method?

### 📌 Definition:

> An **abstract method** is a method that **has no body/implementation**, and **must be implemented** by a subclass.

### ✅ Declared using the `abstract` keyword and ends with a semicolon `;`.

---

## 🔧 Syntax

```java
abstract class Animal {
    abstract void makeSound(); // No body ❌
}
```

➡️ Any subclass **must override** this method.

---

## 🏗️ Example: Subclass Implementation

```java
class Dog extends Animal {
    @Override
    void makeSound() {
        System.out.println("Bark! 🐶");
    }
}
```

✅ Usage:

```java
Animal a = new Dog();
a.makeSound(); // Output: Bark!
```

---

## ⚠️ Key Rules

| Rule 🔒                                           | Explanation ✅                           |
| ------------------------------------------------- | --------------------------------------- |
| Must be in an abstract class                      | Abstract methods **cannot** exist alone |
| No method body                                    | Ends with `;`, no `{}` block            |
| Must be overridden                                | Subclass must provide implementation    |
| If subclass doesn’t override, it must be abstract | Or compiler will throw error ❌          |
| Can be `public` or `protected`                    | But **not private/final/static** ❌      |

---

## 🧠 Why Use Abstract Methods?

| Benefit ✅                     | Explanation 📘                                    |
| ----------------------------- | ------------------------------------------------- |
| Enforce subclass behavior     | Child classes **must implement** required methods |
| Support polymorphism          | Abstract reference, concrete implementation       |
| Avoid incomplete code sharing | Define structure, not logic                       |
| Cleaner and scalable design   | Excellent for **template pattern**, OOP modeling  |

---

## 🧱 Real-World Example

```java
abstract class Vehicle {
    abstract void start(); // Force every vehicle to define how it starts

    void stop() {
        System.out.println("Stopping vehicle...");
    }
}

class Car extends Vehicle {
    @Override
    void start() {
        System.out.println("Starting car with key...");
    }
}

class ElectricScooter extends Vehicle {
    @Override
    void start() {
        System.out.println("Starting scooter with app...");
    }
}
```

✅ Output:

```
Starting car with key...
Starting scooter with app...
```

---

## 🔄 Abstract Method vs Concrete Method

| Feature             | Abstract Method 🔧            | Concrete Method 🔨          |
| ------------------- | ----------------------------- | --------------------------- |
| Method Body         | ❌ No                          | ✅ Yes                       |
| Class Type          | Only in abstract classes      | Any class                   |
| Must be overridden? | ✅ Yes                         | ❌ No (optional)             |
| Use case            | Force subclasses to implement | Provide common/shared logic |

---

## 🧪 Invalid Code (Don’t Do This!)

```java
abstract void sayHi(); // ❌ Cannot be outside a class

class A {
    abstract void sayHi(); // ❌ Class must be abstract too
}
```

✅ Fix:

```java
abstract class A {
    abstract void sayHi(); // ✅
}
```

---

## 🏁 Summary Table

| Feature                | Value                       |
| ---------------------- | --------------------------- |
| Has implementation?    | ❌ No                        |
| Ends with `;`          | ✅ Yes                       |
| Defined inside?        | Abstract class only         |
| Purpose                | Enforce rules on subclasses |
| Can be private/static? | ❌ No                        |
| Can be overloaded?     | ✅ Yes (same as any method)  |

---
[🏠 Back to Home](../../README.md)