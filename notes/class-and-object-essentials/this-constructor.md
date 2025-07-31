# ♻️ this() Constructor

---

## 🧠 What is `this()` in Java?

### 📌 **Definition:**

> `this()` is used to **call another constructor** of the same class from within a constructor.

### ✅ Key Point:

* Must be the **first statement** in the constructor ⚠️
  (Java rule — nahi to compile-time error ❌)

---

## 🔧 Syntax

```java
this();             // Calls default constructor
this(arg1, arg2);   // Calls parameterized constructor
```

---

## 🎯 Why use `this()`?

| ✅ Use Case              | 💡 Benefit                           |
| ----------------------- | ------------------------------------ |
| Constructor chaining    | Reuse logic across constructors      |
| Avoid code duplication  | Cleaner, DRY (Don't Repeat Yourself) |
| Default values fallback | Useful when setting defaults         |

---

## 💡 Real-Life Analogy

🧱 Think of constructing a building:
Instead of rewriting the base each time, reuse the **foundation constructor** and add extra floors.

---

## 🔧 Example 1: Chaining Constructors

```java
class Student {
    String name;
    int roll;

    Student() {
        this("Unknown", -1); // calling parameterized constructor
    }

    Student(String name) {
        this(name, -1); // calling another constructor
    }

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
        Student s1 = new Student();           // Uses default
        Student s2 = new Student("Aman");     // Uses one-param
        Student s3 = new Student("Ravi", 101); // Uses two-param

        s1.show();
        s2.show();
        s3.show();
    }
}
```

---

## 📌 Diagram: Constructor Chaining with `this()`

```
Student() → this("Unknown", -1)
                ↓
Student(String name, int roll)
```

```
Student("Aman") → this("Aman", -1)
                        ↓
Student(String name, int roll)
```

---

## 🚫 Invalid Usage of `this()`

```java
Student(String name) {
    System.out.println("Hello"); // ❌ this() is NOT the first line
    this(name, -1);              // Compile-time error!
}
```

⚠️ Fix: Put `this(...)` as the **very first line** in constructor.

---

## ✅ Best Practices

| 💡 Tip                             | ✅ Reason                             |
| ---------------------------------- | ------------------------------------ |
| Use `this()` to reduce duplication | Better maintainability & readability |
| Always put `this()` at line 1      | It’s required by the compiler        |
| Avoid deep chaining (>3 levels)    | Use Builder pattern if too complex   |

---

## 🧪 Interview Tip

🧠 **Q:** Can we use both `this()` and `super()` in the same constructor?
❌ **No!** Only one can be used, and both must be the **first statement**.
👉 You have to choose: either call **parent** constructor (`super()`) or **another constructor** (`this()`).

---

## 🧭 Summary

| 🔧 Expression      | 💬 Meaning                               |
| ------------------ | ---------------------------------------- |
| `this()`           | Call default constructor                 |
| `this(arg1, arg2)` | Call another constructor with args       |
| Must be 1st line   | Compiler enforces this strictly          |
| Same class only    | Can’t call constructors of other classes |

---

## 🛠 Mini Task for You (Practice Challenge)

```java
class Book {
    String title;
    double price;

    Book() {
        this("Unknown", 0.0);
    }

    Book(String title) {
        this(title, 99.0);
    }

    Book(String title, double price) {
        this.title = title;
        this.price = price;
    }

    void show() {
        System.out.println(title + " - ₹" + price);
    }
}
```

Try this:

```java
Book b1 = new Book();
Book b2 = new Book("Java Mastery");
Book b3 = new Book("DSA Pro", 499.0);
```

---
[🏠 Back to Home](../../README.md)