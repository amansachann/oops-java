# 🎨 Fields / Variables in Java 

## 📌 What Are Fields/Variables?

> In Java, **variables** are containers used to **store data**.
> A **field** is a variable declared inside a **class but outside any method** — also known as a **member variable**.

---

## 🧠 Types of Variables in Java

| 🔢 Type                   | 📍 Where Declared               | ♻️ Lifetime               | 🧠 Keyword |
| ------------------------- | ------------------------------- | ------------------------- | ---------- |
| 🏛️ **Instance Variable** | Inside class, outside methods   | Per object (non-static)   | No keyword |
| 🏢 **Static Variable**    | Inside class, with `static`     | Shared across all objects | `static`   |
| 🧪 **Local Variable**     | Inside method/block/constructor | Temporary (stack memory)  | No keyword |
| 🧱 **Parameter Variable** | In method signature             | Temporary (stack memory)  | No keyword |

---

## ✅ 1. Instance Variable

```java
class Car {
    String brand;   // Instance variable
    int speed;

    void showDetails() {
        System.out.println("Brand: " + brand);
    }
}
```

* Stored in **heap memory**
* Separate copy for **each object**
* Accessed via `object.brand`

---

## ✅ 2. Static Variable

```java
class Car {
    static int numberOfCars = 0; // Shared variable

    Car() {
        numberOfCars++; // Increment on every object creation
    }
}
```

* Stored in **method area**
* Shared by **all objects**
* Accessed via `Car.numberOfCars`

---

## ✅ 3. Local Variable

```java
class Example {
    void show() {
        int x = 10; // Local variable
        System.out.println(x);
    }
}
```

* Declared inside a **method or block**
* Stored in **stack**
* Must be **initialized before use**

---

## ✅ 4. Parameter Variable

```java
class Calculator {
    int add(int a, int b) { // a, b → parameter variables
        return a + b;
    }
}
```

* Declared in **method signature**
* Temporary, stack memory
* Used to pass input to methods

---

## ⚙️ Memory Allocation Overview

| 🔍 Variable Type  | 📦 Memory Area | 🎯 Scope     | 🧼 Destroyed When           |
| ----------------- | -------------- | ------------ | --------------------------- |
| Instance Variable | Heap           | Per object   | Object is garbage collected |
| Static Variable   | Method Area    | Class level  | Class is unloaded           |
| Local / Parameter | Stack          | Method/block | Method finishes execution   |

---

## 🔐 Access Modifiers (Visibility)

| Modifier    | Who Can Access?            |
| ----------- | -------------------------- |
| `private`   | Only inside the same class |
| `default`   | Same package               |
| `protected` | Same package + subclasses  |
| `public`    | Anywhere                   |

---

## 🧪 Real Example Using All Types

```java
class Student {
    static String college = "IIT"; // static field
    String name;                   // instance field

    Student(String name) {
        this.name = name;
    }

    void show() {
        String msg = "Hello";     // local variable
        System.out.println(msg + " " + name + " from " + college);
    }

    void greet(String greetMsg) { // parameter variable
        System.out.println(greetMsg + ", " + name);
    }
}
```

---

## 💡 Best Practices

| ✅ Practice                           | 💥 Why It Matters                             |
| ------------------------------------ | --------------------------------------------- |
| Use `private` fields                 | For **encapsulation**                         |
| Use `final` if variable won't change | Prevents accidental reassignment              |
| Name variables clearly               | Improves readability (`userName` > `x`)       |
| Avoid static unless needed           | Shared state = risk of bugs                   |
| Initialize local variables           | No default values — will cause compile errors |

---

## 🔁 Summary Table

| 📌 Variable Type | 🔐 Scope      | ♻️ Lifetime        | 📦 Stored In | 💡 Example               |
| ---------------- | ------------- | ------------------ | ------------ | ------------------------ |
| Instance         | Object        | Until object dies  | Heap         | `String name;`           |
| Static           | Class         | Until program ends | Method Area  | `static int count;`      |
| Local            | Method/Block  | Method execution   | Stack        | `int i = 5;`             |
| Parameter        | Method Header | Method execution   | Stack        | `void add(int a, int b)` |

---
[🏠 Back to Home](../../README.md)