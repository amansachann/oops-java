# 🥊 Abstract vs Final vs Static

---

## 🧠 Conceptual Differences

| 🔑 Keyword | 🎯 Purpose                                                                  |
| ---------- | --------------------------------------------------------------------------- |
| `abstract` | Blueprint banata hai — implementation **subclass pe chhoda** jata hai 👷‍♂️ |
| `final`    | Kuch bhi **change ya override karne se rokta hai** 🚫                       |
| `static`   | Class-level member banata hai — **shared across all instances** 📦          |

---

## 🧪 Comparison Table: Class Level

| Feature                    | `abstract`             | `final`             | `static`                |
| -------------------------- | ---------------------- | ------------------- | ----------------------- |
| Can be instantiated?       | ❌ No                   | ✅ Yes               | ✅ (if not abstract)     |
| Can be extended?           | ✅ Must be              | ❌ No                | ✅ Yes                   |
| Can have abstract methods? | ✅ Yes                  | ❌ No                | ❌ No                    |
| Example                    | `abstract class Shape` | `final class Bank`  | `class AppUtils`        |
| Common Use                 | Base class (design)    | Prevent inheritance | Utility/shared behavior |

---

## 🧪 Comparison Table: Method Level

| Feature                  | `abstract`        | `final`                | `static`                       |
| ------------------------ | ----------------- | ---------------------- | ------------------------------ |
| Must be overridden?      | ✅ Yes             | ❌ Cannot be overridden | ❌ Cannot be overridden         |
| Must have a body?        | ❌ No              | ✅ Yes                  | ✅ Yes                          |
| Belongs to object/class? | Subclass (object) | Subclass               | Class-level                    |
| Use in interfaces?       | ✅ (1 abstract)    | ❌ Not allowed          | ✅ From Java 8 (static methods) |

---

## 🧪 Comparison Table: Variable Level

| Feature               | `abstract` | `final`          | `static`              |
| --------------------- | ---------- | ---------------- | --------------------- |
| Can be declared?      | ❌ No       | ✅ Yes            | ✅ Yes                 |
| Value reassignable?   | —          | ❌ No             | ✅ (unless final too)  |
| Shared among objects? | —          | ❌ (per instance) | ✅ Yes                 |
| Constant declaration? | —          | ✅ Yes            | ✅ Often used together |

```java
public static final double PI = 3.14159;
```

---

## 📦 Use Case Examples

### ✅ `abstract`

```java
abstract class Animal {
    abstract void sound();
}
```

### ✅ `final`

```java
final class Constants {
    static final int MAX = 100;
}
```

### ✅ `static`

```java
class Utils {
    static void printHello() {
        System.out.println("Hello!");
    }
}
```

---

## ⚔️ Valid & Invalid Combinations

| Combination                | ✅ Valid? | Notes                                          |
| -------------------------- | -------- | ---------------------------------------------- |
| `final class`              | ✅        | Can't be extended                              |
| `abstract class`           | ✅        | Can't be instantiated                          |
| `static method`            | ✅        | Belongs to class                               |
| `final method`             | ✅        | Can't be overridden                            |
| `abstract method`          | ✅        | No body; must be in abstract class             |
| `static final variable`    | ✅        | Used for constants                             |
| `abstract + final method`  | ❌        | Contradiction: can't override + must override  |
| `abstract + static method` | ❌        | Static can't be abstract                       |
| `abstract + final class`   | ❌        | Contradiction: can't extend + must be extended |

---

## 🧼 Best Practices

| ✅ Do’s                                       | ❌ Don’ts                                      |
| -------------------------------------------- | --------------------------------------------- |
| Use `final` for locking APIs                 | Don’t use `abstract` with `static` or `final` |
| Use `static` for utility/helper/shared logic | Avoid overusing `final` unnecessarily         |
| Use `abstract` to define flexible contracts  | Don’t mix conflicting modifiers               |

---

## 🏁 Summary Snapshot

| Feature           | `abstract` 🧩      | `final` 🔒           | `static` ⚙️          |
| ----------------- | ------------------ | -------------------- | -------------------- |
| Purpose           | Blueprint          | No override/extend   | Class-level sharing  |
| Class             | Must be extended   | Cannot be extended   | Regular              |
| Method            | Must be overridden | Cannot be overridden | Shared, not override |
| Variable          | —                  | Immutable            | Shared               |
| Used in Interface | ✅ (1 method)       | ❌                    | ✅ (Java 8+)          |

---
[🏠 Back to Home](../..)