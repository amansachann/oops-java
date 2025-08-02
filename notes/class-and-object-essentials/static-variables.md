# 💫 Static Variables in Java

---

## 🧠 What is a Static Variable?

### 📌 **Definition:**

> A **static variable** is a **class-level variable** that is **shared among all objects** of that class.

---

## 🏢 Instance vs Static Variable

| 🧱 Instance Variable              | 🏢 Static Variable                     |
| --------------------------------- | -------------------------------------- |
| Belongs to **object**             | Belongs to **class**                   |
| Stored in **Heap**                | Stored in **Method Area**              |
| Each object gets its **own copy** | Only **one copy** shared by all        |
| Access via `object.var`           | Access via `ClassName.var` (preferred) |

---

## 🔧 Syntax

```java
class MyClass {
    static int count = 0; // static variable
}
```

✅ Access:

```java
MyClass.count = 10;
```

---

## 🎯 Why Use Static Variables?

| ✅ Use Case                    | 🎯 Reason                    |
| ----------------------------- | ---------------------------- |
| Shared data among all objects | Like number of instances     |
| Constants                     | Like `PI`, `MAX_VALUE`, etc. |
| Caching or global config      | Store common config/settings |

---

## 🔧 Example: Tracking Object Count

```java
class Student {
    String name;
    static int count = 0; // shared across all objects

    Student(String name) {
        this.name = name;
        count++;
    }

    void show() {
        System.out.println(name + " | Total Students: " + count);
    }
}
```

```java
public class Main {
    public static void main(String[] args) {
        Student s1 = new Student("Aman");
        Student s2 = new Student("Ravi");

        s1.show(); // Aman | Total Students: 2
        s2.show(); // Ravi | Total Students: 2
    }
}
```

---

## 🧠 Memory Diagram

```
+-------------------+     +-----------------+
|  Heap (Objects)   |     |  Method Area    |
|-------------------|     |-----------------|
| s1: name = "Aman" |     | count = 2       | ← static (one copy)
| s2: name = "Ravi" |     |-----------------|
+-------------------+     +-----------------+
```

---

## ⚠️ Important Rules

| Rule                                      | Details                                        |
| ----------------------------------------- | ---------------------------------------------- |
| Static variable loads **once**            | When class is loaded in memory                 |
| Cannot access instance variables directly | `static` context doesn't have access to `this` |
| Can be accessed without object            | Prefer using `ClassName.staticVar`             |
| Common across all objects                 | Perfect for counters, constants, config, etc.  |

---

## ✅ Best Practices

| 💡 Tip                                    | ✅ Reason                                   |
| ----------------------------------------- | ------------------------------------------ |
| Access via `ClassName.var`                | Improves readability                       |
| Use for **constants** with `final static` | e.g., `public static final int MAX = 100;` |
| Avoid storing mutable shared state        | Leads to bugs in multithreaded code        |
| Don’t misuse static for global variables  | Breaks encapsulation, OOP principles       |

---

## 🧪 Real-World Use Case

```java
class Config {
    static String appName = "Mindify";
    static String version = "1.0.0";
}
```

✅ Access it anywhere:

```java
System.out.println(Config.appName); // Mindify
```

---

## 🚫 Common Mistake

```java
class A {
    static int x = 5;

    void change() {
        x++;
    }
}

A a1 = new A();
A a2 = new A();
a1.change();
System.out.println(a2.x); // Output: 6 ✅
```

> Both `a1` and `a2` **share** the same `x` → only one copy exists.

---

## 🏁 Summary Table

| Feature         | Static Variable                        |
| --------------- | -------------------------------------- |
| Belongs to      | Class                                  |
| Accessed by     | `ClassName.var` (preferred)            |
| Memory Location | Method Area                            |
| Shared by       | All objects                            |
| Default Value   | Like instance vars (`0`, `null`, etc.) |

---
[🏠 Back to Home](../..)