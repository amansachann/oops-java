# 🏗️ Class & Class Definition

## 🧱 What is a **Class**?

### 📌 **Definition**:

> A **class** is a **blueprint** or **template** for creating objects.
> It defines the **properties (fields)** and **behaviors (methods)** an object will have.

### 💡 Real-world Example:

> **Car class** = Blueprint
> From that, we create many **Car objects** (BMW, Tesla, etc.)

---

### 🧾 Java Syntax:

```java
class Car {
    // Fields (state)
    String brand;
    int speed;

    // Method (behavior)
    void accelerate() {
        speed += 10;
        System.out.println(brand + " is going at " + speed + " km/h");
    }
}
```

---

## 🚗 What is an **Object**?

### 📌 **Definition**:

> An **object** is a real-world **instance of a class**.
> It has **its own copy** of all fields and can call the class methods.

### 💡 Real-world Example:

If `Car` is a class, then:

* `Car bmw = new Car();` → bmw is an object
* `Car tesla = new Car();` → tesla is another object

---

### 🔧 Java Object Creation:

```java
public class Main {
    public static void main(String[] args) {
        // Creating an object (instance) of Car
        Car bmw = new Car();          // Object
        bmw.brand = "BMW";            // Set field
        bmw.accelerate();             // Call method
    }
}
```

---

## 🧠 Diagram: Class vs Object

```
           CLASS (Blueprint)
           ---------------------
           | brand: String     |
           | speed: int        |
           | accelerate()      |
           ---------------------

            ↓ creates

     +--------------------+
     | OBJECT: bmw        |
     | brand = "BMW"      |
     | speed = 0          |
     +--------------------+

     +--------------------+
     | OBJECT: tesla      |
     | brand = "Tesla"    |
     | speed = 0          |
     +--------------------+
```

---

## 🔄 Recap: Difference Between Class & Object

| 🏗️ Class                    | 🚗 Object                         |
| ---------------------------- | --------------------------------- |
| Blueprint or template        | Actual instance                   |
| Defines structure & behavior | Holds actual data & runs behavior |
| No memory is allocated       | Memory is allocated when created  |
| One class → many objects     | Each object has its own state     |

---

## ✅ Best Practices

* Use **CamelCase** for class names: `BankAccount`, `Student`
* Keep fields **private**, use **getters/setters** (Encapsulation)
* Create **constructors** to initialize objects
* Avoid making everything `static` unless necessary

---

## 🔥 Real-World Mini Task (Optional for Practice)

```java
class Student {
    String name;
    int roll;

    void display() {
        System.out.println("Name: " + name + ", Roll: " + roll);
    }
}

public class Test {
    public static void main(String[] args) {
        Student s1 = new Student();
        s1.name = "Aman";
        s1.roll = 101;
        s1.display();
    }
}
```

---

## 🏁 Summary

| Term   | Meaning                                         |
| ------ | ----------------------------------------------- |
| Class  | Blueprint — defines what an object will have/do |
| Object | Real-world entity — actual data + behavior      |

---
[🏠 Back to Home](../../README.md)
