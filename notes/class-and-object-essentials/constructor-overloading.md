# 🏋️‍♂️ Constructor Overloading

---

## 🧱 What is a Constructor?

### 📌 **Definition**:

> A **constructor** is a special method used to **create and initialize objects**.

* Has **same name as the class**
* No return type (not even `void`)
* Called **automatically** when an object is created

```java
class Car {
    Car() {
        System.out.println("Car object created");
    }
}
```

---

## 🎯 What is Constructor Overloading?

### 📌 **Definition**:

> **Constructor Overloading** means **multiple constructors** in the same class with **different parameter lists**.

✅ Just like method overloading, but used for **initializing objects in different ways**.

---

## 💡 Real-Life Example

🧠 Think of building a **Pizza**:

| 🍕 Constructor Version               | 📦 Purpose                        |
| ------------------------------------ | --------------------------------- |
| `Pizza()`                            | Default cheese pizza              |
| `Pizza(String size)`                 | Medium-size pizza                 |
| `Pizza(String size, String topping)` | Medium pizza with olives/toppings |

---

## 🔧 Java Example: Constructor Overloading

```java
class Student {
    String name;
    int roll;

    // Default constructor
    Student() {
        name = "Unknown";
        roll = 0;
    }

    // Parameterized constructor 1
    Student(String name) {
        this.name = name;
        roll = -1;
    }

    // Parameterized constructor 2
    Student(String name, int roll) {
        this.name = name;
        this.roll = roll;
    }

    void show() {
        System.out.println("Name: " + name + ", Roll: " + roll);
    }
}
```

✅ Usage:

```java
public class Main {
    public static void main(String[] args) {
        Student s1 = new Student();
        Student s2 = new Student("Aman");
        Student s3 = new Student("Ravi", 101);

        s1.show();
        s2.show();
        s3.show();
    }
}
```

---

## 🧠 Memory & Behavior

* Each constructor creates a **separate instance**
* Based on **arguments**, appropriate constructor is called
* Supports **code reuse** by calling one constructor from another using `this(...)`

---

## 🔄 Calling One Constructor from Another (Constructor Chaining)

```java
class Box {
    int length, width;

    // Constructor chaining using this()
    Box() {
        this(10, 20); // Calls parameterized constructor
    }

    Box(int l, int w) {
        length = l;
        width = w;
    }

    void show() {
        System.out.println("Length: " + length + ", Width: " + width);
    }
}
```

---

## 💥 Why Use Constructor Overloading?

| ✅ Use Case                    | 🎯 Benefit                              |
| ----------------------------- | --------------------------------------- |
| Set default vs custom values  | Flexibility                             |
| Partial object initialization | Less data → still construct object      |
| Different input types         | Overload with different parameter types |
| Clean, readable code          | No need for separate `init()` methods   |

---

## ⚠️ Best Practices

| ⚙️ Practice                            | 💡 Tip                                        |
| -------------------------------------- | --------------------------------------------- |
| Use `this(...)` to avoid duplication   | Call one constructor from another             |
| Prefer meaningful parameter names      | Improves readability                          |
| Avoid too many overloaded constructors | Use builder pattern if over 3–4 params        |
| Combine with method overloading wisely | For flexible object creation & behavior setup |

---

## 🧭 Visual Summary

```
     +--------------------------+
     |      Constructor         |
     +--------------------------+
     | Student()                |
     | Student(String name)     |
     | Student(String, int)     |
     +--------------------------+
```

Each version → called based on number/type of arguments passed during object creation 👇

```java
new Student();                   // Default
new Student("Aman");             // One-arg
new Student("Aman", 101);        // Two-arg
```

---
[🏠 Back to Home](../..)
