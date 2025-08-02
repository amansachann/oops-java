# 🧩 What is OOP?

🧱 **Object-Oriented Programming (OOP)** is a programming paradigm that organizes code around **objects** — real-world entities that combine **data (state)** and **behavior (methods)**.

---

## 🎯 Four Pillars of OOP (The Core Concepts)

| 🧱 Pillar            | 🔍 Description                                                        | 🎯 Real-world Example                     |
| -------------------- | --------------------------------------------------------------------- | ----------------------------------------- |
| 🔐 **Encapsulation** | Bundling data and methods together + hiding internal details          | ATM hides its internal mechanism          |
| 🧬 **Inheritance**   | One class (child) inherits properties of another (parent)             | Dog 🐶 inherits from Animal 🐾            |
| 🧠 **Polymorphism**  | One interface, many implementations (Method Overriding + Overloading) | Same remote, controls TV or AC            |
| 🧱 **Abstraction**   | Hiding complex logic and exposing only essential details              | Car 🚗 accelerator — hides engine details |

---

## 🧠 Real-World Analogy: **Car**

| Component       | Maps to OOP Concept        |
| --------------- | -------------------------- |
| Car 🚗          | Object                     |
| Engine, Speed   | Fields / State             |
| Drive(), Stop() | Methods / Behavior         |
| Car Blueprint   | Class (template of object) |

---

## 🔍 OOP in Java – Basic Example

```java
// 🔧 Class Definition (Blueprint)
class Car {
    // 🔐 Encapsulation: Private fields
    private String brand;
    private int speed;

    // Constructor
    Car(String brand) {
        this.brand = brand;
        this.speed = 0;
    }

    // Public method to access private field (Abstraction)
    public void accelerate() {
        speed += 10;
        System.out.println(brand + " is now going at " + speed + " km/h");
    }
}

// 🚀 Main Class
public class Main {
    public static void main(String[] args) {
        Car c1 = new Car("Tesla");
        c1.accelerate(); // Output: Tesla is now going at 10 km/h
    }
}
```

---

## 🔄 Inheritance Example

```java
// 👨‍👧 Parent class
class Animal {
    void speak() {
        System.out.println("Animal speaks");
    }
}

// 🐶 Child class
class Dog extends Animal {
    // Method Overriding (Polymorphism)
    @Override
    void speak() {
        System.out.println("Dog barks");
    }
}
```

---

## ⚡ Method Overloading vs Overriding (Polymorphism)

```java
// Overloading
class Calculator {
    int add(int a, int b) {
        return a + b;
    }

    double add(double a, double b) {
        return a + b;
    }
}

// Overriding is shown in the Dog example above 👆
```

---

## 🧠 Why Use OOP?

✅ **Modularity** – Code is organized in self-contained objects  
✅ **Reusability** – Classes can be reused via inheritance  
✅ **Maintainability** – Code is easier to change and extend  
✅ **Scalability** – Better structure for large apps  

---

## 🔥 Advanced Concepts in OOP (we'll go deep into these next):

* **Interface vs Abstract Class**
* **Composition vs Inheritance**
* **SOLID Principles**
* **Design Patterns (Factory, Singleton, etc.)**
* **Liskov Substitution Principle**
* **Open/Closed Principle**
* **Law of Demeter**
* **Dependency Inversion**

---

## ✅ Summary Diagram

```
              +-------------------+
              |    Class          |
              +-------------------+
              | - fields (state)  |
              | - methods (behavior) |
              +-------------------+
                      |
                  creates
                      ↓
              +------------------+
              |     Object       |
              +------------------+

4 Pillars:
- Encapsulation 🔐
- Inheritance 🧬
- Polymorphism 🧠
- Abstraction 🎭
```
[🏠 Back to Home](../..)