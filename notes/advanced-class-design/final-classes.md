# ‼️ Final Classes

---

## 🧠 What is a Final Class?

### 📌 Definition:

> A `final` class in Java **cannot be extended**.
> It is declared using the `final` keyword before the class name.

```java
final class Bank {
    void printRate() {
        System.out.println("Rate: 7.5%");
    }
}
```

✅ Any attempt to extend it will result in a **compile-time error**.

---

## 🚫 Example: Inheriting Final Class

```java
class ICICI extends Bank {  // ❌ ERROR: Cannot subclass final class
    void printRate() {
        System.out.println("ICICI Rate");
    }
}
```

🛑 **Output:** `Cannot inherit from final class 'Bank'`

---

## ✅ When to Use Final Classes?

| 💡 Scenario                       | 🔒 Why Use Final Class?                     |
| --------------------------------- | ------------------------------------------- |
| Security-sensitive code           | Prevent others from overriding or extending |
| Immutable objects (e.g. `String`) | Ensures structure cannot be altered         |
| Utility/helper classes            | Prevent misuse via inheritance              |
| API design                        | Lock critical behavior from being changed   |

---

## 🔐 Real-Life Analogy

> **Final class** = “No modifications allowed 🚫”
> Jaise Aadhaar Card — har kisi ka alag hai, aur tu usko **change ya extend nahi** kar sakta!

---

## ✅ Example: Immutable Class Design

```java
final class Employee {
    private final int id;
    private final String name;

    public Employee(int id, String name) {
        this.id = id;
        this.name = name;
    }

    public int getId() { return id; }
    public String getName() { return name; }
}
```

✅ Immutable + Final → Secure & thread-safe

---

## 🧼 Best Practices

| ✅ Do's                                     | ❌ Don'ts                                       |
| ------------------------------------------ | ---------------------------------------------- |
| Use final class for critical logic         | Don’t mark classes final without strong reason |
| Combine with final fields for immutability | Avoid final if future extension is likely      |
| Use for utility/helper classes (e.g. Math) | Don’t mark class final just to "hide" bugs     |

---

## ⚔️ Final Class vs Final Method vs Final Variable

| 🔑 Type          | 🔒 Effect                               |
| ---------------- | --------------------------------------- |
| `final class`    | ❌ Cannot be extended                    |
| `final method`   | ❌ Cannot be overridden in subclass      |
| `final variable` | ❌ Cannot be reassigned once initialized |

---

## 📦 Built-in Final Classes in Java

| 🚀 Final Class      | 📌 Purpose                       |
| ------------------- | -------------------------------- |
| `String`            | Immutable text                   |
| `Integer`, `Double` | Immutable wrapper classes        |
| `Math`              | Utility methods (abs, pow, etc.) |
| `System`            | JVM-level system operations      |
| `StringBuffer`      | Thread-safe mutable string       |

---

## 🏁 Summary Table

| 📌 Feature         | Final Class 🔒                         |
| ------------------ | -------------------------------------- |
| Syntax             | `final class MyClass {}`               |
| Inheritable?       | ❌ No                                   |
| Common use cases   | Immutability, security, utility        |
| Combine with       | `final fields`, `private constructors` |
| Real-world example | `java.lang.String`, `java.lang.Math`   |

---
[🏠 Back to Home](../..)