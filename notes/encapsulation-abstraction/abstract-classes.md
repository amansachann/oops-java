# 🔍 Abstract Classes 

---

## 🧠 What is an Abstract Class?

### 📌 Definition:

> An **abstract class** is a class that **cannot be instantiated** and may contain **abstract methods** (without implementation) as well as **concrete methods** (with implementation).

---

## 🚫 Key Rule:

> **You cannot create an object of an abstract class** ❌

---

## 🔧 Syntax

```java
abstract class Shape {
    abstract void draw(); // No body — must be implemented in subclass

    void print() { // Concrete method
        System.out.println("This is a shape");
    }
}
```

---

## 🏗️ Subclass Implementation

```java
class Circle extends Shape {
    @Override
    void draw() {
        System.out.println("Drawing Circle");
    }
}
```

✅ Usage:

```java
Shape s = new Circle(); // ✅ Polymorphism
s.draw();               // Drawing Circle
s.print();              // This is a shape
```

---

## 🎯 When to Use Abstract Classes?

| ✅ Use Case                              | 📘 Explanation                        |
| --------------------------------------- | ------------------------------------- |
| Want to provide **base structure**      | Some methods implemented, some forced |
| Require **shared code + enforce rules** | Concrete + abstract mix               |
| Need polymorphism                       | Abstract reference, concrete object   |
| Have **common base class logic**        | Reduce duplication                    |

---

## 🧱 Real-World Example

```java
abstract class Animal {
    abstract void sound(); // Must be implemented

    void eat() {
        System.out.println("Eating...");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Bark!");
    }
}
```

✅ Output:

```
Bark!  
Eating...
```

---

## 🧠 Important Rules

| Rule 🔒                              | Explanation ✅                            |
| ------------------------------------ | ---------------------------------------- |
| Can't instantiate abstract class     | Only reference allowed                   |
| Can have constructors                | For initialization (called via subclass) |
| Can have abstract + concrete methods | Allows flexibility                       |
| Can have fields & static methods     | Yes ✅                                    |
| Can extend only one abstract class   | Because Java supports single inheritance |

---

## 🆚 Abstract Class vs Interface

| Feature              | Abstract Class 🧱     | Interface 🧬                                  |
| -------------------- | --------------------- | --------------------------------------------- |
| Method types         | Abstract + Concrete   | Abstract (Java 7), + default/static (Java 8+) |
| Constructor          | ✅ Yes                 | ❌ No                                          |
| Fields               | ✅ Instance/Static     | Only `public static final`                    |
| Multiple inheritance | ❌ No                  | ✅ Yes                                         |
| Use case             | Base class with logic | Pure abstraction (before Java 8)              |

---

## ⚠️ Common Mistakes

| ❌ Mistake                             | ⚠️ Why it's a Problem            |
| ------------------------------------- | -------------------------------- |
| Trying to instantiate abstract class  | Compile-time error               |
| Not implementing all abstract methods | Subclass must be abstract too    |
| Thinking abstract = interface         | Different concepts and use cases |

---

## 📦 UML Diagram

```
            +---------------------+
            |   abstract Shape    | ◄──── Abstract Class
            +---------------------+
            | + draw() : void     | ◄──── Abstract Method
            | + print() : void    | ◄──── Concrete Method
            +---------------------+
                     ▲
                     |
         +-----------+-----------+
         |                       |
     Circle                 Rectangle
```

---

## 🏁 Summary Table

| Feature                 | Abstract Class                |
| ----------------------- | ----------------------------- |
| Can instantiate?        | ❌ No                          |
| Can have fields?        | ✅ Yes                         |
| Can have constructors?  | ✅ Yes                         |
| Can have mixed methods? | ✅ Abstract + Concrete         |
| Used for?               | Common base logic + structure |

---
[🏠 Back to Home](../..)