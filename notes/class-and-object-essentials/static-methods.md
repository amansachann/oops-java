# ⭐ Static Methods 

---

## 🧠 What is a Static Method?

### 📌 \*\*Definition:

> A **static method** belongs to the **class**, not to any specific object.
> You can call it **without creating an object**.

---

## 🔧 Syntax

```java
class MyClass {
    static void greet() {
        System.out.println("Hello from static method!");
    }
}
```

✅ Usage:

```java
MyClass.greet(); // ✅ No need to create object
```

---

## 🎯 When to Use Static Methods?

| ✅ Use Case             | 🎯 Reason                                |
| ---------------------- | ---------------------------------------- |
| Utility/helper methods | No object state needed (`Math.max`)      |
| Factory methods        | Return prebuilt instances                |
| Entry point            | `public static void main(String[] args)` |
| Shared/common logic    | Like config loaders, converters          |

---

## 🏢 Static vs Instance Methods

| Feature                   | `static` Method      | Instance Method |
| ------------------------- | -------------------- | --------------- |
| Belongs to                | Class                | Object          |
| Access via                | `ClassName.method()` | `obj.method()`  |
| Can access instance vars? | ❌ No                 | ✅ Yes           |
| Uses `this`?              | ❌ Not allowed        | ✅ Available     |

---

## 🔧 Example: Static Utility Method

```java
class MathUtil {
    static int square(int x) {
        return x * x;
    }
}

public class Main {
    public static void main(String[] args) {
        System.out.println(MathUtil.square(5)); // 25
    }
}
```

---

## ⚠️ Important Rules of Static Methods

| 🚫 Rule                            | ❗ Why?                           |
| ---------------------------------- | -------------------------------- |
| ❌ Cannot use `this` or `super`     | They belong to object, not class |
| ❌ Cannot access instance variables | Because no object is created     |
| ✅ Can access static variables      | Belongs to same class level      |
| ✅ Can be overloaded                | Like any other method            |

---

## 🔧 Static Method with Static Variable

```java
class Counter {
    static int count = 0;

    static void increment() {
        count++;
    }

    static void show() {
        System.out.println("Count: " + count);
    }
}
```

✅ Usage:

```java
Counter.increment();
Counter.show(); // Count: 1
```

---

## 💡 Real-World Use Case: Logger Utility

```java
class Logger {
    static void log(String msg) {
        System.out.println("[LOG]: " + msg);
    }
}
```

```java
Logger.log("App started"); // No object needed
```

---

## 🧠 Memory Diagram

```
         +-----------------------------+
         |       Method Area           |
         |-----------------------------|
         | Class: Logger               |
         | - static void log(...)      | ← Stored once
         +-----------------------------+
```

🧾 Memory efficient — only one copy exists!

---

## ✅ Best Practices

| 💡 Tip                                | ✅ Why?                         |
| ------------------------------------- | ------------------------------ |
| Use for utility/helper logic          | No need to manage object state |
| Don’t access instance data            | Leads to compile error         |
| Follow naming conventions             | e.g., `parseInt`, `loadConfig` |
| Group with static constants if needed | Use config/constants class     |

---

## 🧪 Common Interview Question

🧠 **Q:** Can a `static` method call a non-static method?
❌ **No**, unless it does so via an object.

```java
class A {
    void instanceMethod() {
        System.out.println("I’m non-static");
    }

    static void staticMethod() {
        // instanceMethod(); ❌ ERROR
        new A().instanceMethod(); ✅ OK
    }
}
```

---

## 🏁 Summary Table

| 🔧 Feature             | 🔥 Static Method     |
| ---------------------- | -------------------- |
| Belongs to             | Class (not object)   |
| Access via             | `ClassName.method()` |
| Uses `this` / `super`? | ❌ Not allowed        |
| Can access static vars | ✅ Yes                |
| Memory efficiency      | ✅ Only one copy      |

---

[🏠 Back to Home](../../README.md)
