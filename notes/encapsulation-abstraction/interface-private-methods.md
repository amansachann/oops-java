# 🔇 Interface Private Methods (Java 9)

---

## 🧠 What is a Private Method in an Interface?

### 📌 Definition:

> A **private method in an interface** is used to **share common code** between `default` and `static` methods **within the same interface**, but is **not accessible outside** the interface.

✅ Introduced in **Java 9**

---

## 🔧 Syntax

```java
interface Logger {
    default void logInfo(String msg) {
        log("INFO", msg);
    }

    default void logError(String msg) {
        log("ERROR", msg);
    }

    // 👇 Private helper method
    private void log(String level, String msg) {
        System.out.println("[" + level + "] " + msg);
    }
}
```

✅ Usage:

```java
class ConsoleLogger implements Logger {}

ConsoleLogger c = new ConsoleLogger();
c.logInfo("App started");   // [INFO] App started
c.logError("Crash!");       // [ERROR] Crash!
```

---

## 🔬 Why Private Methods?

| ✅ Reason                     | 📘 Explanation                                           |
| ---------------------------- | -------------------------------------------------------- |
| 🧱 Code Reuse                | Avoid repeating logic in multiple default/static methods |
| 🔒 Encapsulation             | Hide helper logic from implementing classes              |
| 🧼 Cleaner Interfaces        | Separate public API and internal helpers                 |
| ✅ No Break in OOP Principles | Private methods stay hidden and safe                     |

---

## 🎯 Types of Private Interface Methods

| Type                | Example                   |
| ------------------- | ------------------------- |
| 🛡️ `private`       | Reused by default methods |
| 🧪 `private static` | Reused by static methods  |

---

## 🧪 Private Static Method Example

```java
interface Util {
    static void showDate() {
        print("Today's date is 31st July");
    }

    private static void print(String msg) {
        System.out.println(msg);
    }
}
```

✅ Usage:

```java
Util.showDate(); // ✅ Works
// Util.print("Hello"); ❌ Not allowed
```

---

## ⚠️ Rules for Private Methods

| Rule ✅                                | Restriction ❌                          |
| ------------------------------------- | -------------------------------------- |
| Must have a method body               | No abstract private methods allowed    |
| Can only be used within the interface | Not accessible in implementing classes |
| Cannot be `public`, `protected`       | Only `private` or `private static`     |
| No override allowed                   | They're not inherited                  |

---

## ⚠️ Common Mistakes

| ❌ Mistake                             | ⚠️ Problem                                         |
| ------------------------------------- | -------------------------------------------------- |
| Trying to call private method outside | Compile-time error ❌                               |
| Forgetting method body                | Interface methods must have body (if not abstract) |
| Trying to override private method     | Not allowed ❌                                      |

---

## 🏁 Summary Table

| Feature      | Interface Private Methods 🛡️ |
| ------------ | ----------------------------- |
| Java version | Java 9+                       |
| Access level | `private` / `private static`  |
| Called from  | Only inside interface         |
| Used in      | `default` / `static` methods  |
| Inheritable? | ❌ No                          |
| Overridable? | ❌ No                          |

---

## 🧱 Real-World Analogy

> **Private method in interface = helper function in utility class**  
> But yeh sirf **interface ke andar hi chalta hai**, implementing class ko kuch pata nahi 🔒

---

[🏠 Back to Home](../..)
