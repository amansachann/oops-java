# 🏌️‍♂️ finalize() [Deprecated]

---

## 🧠 What is `finalize()` in Java?

### 📌 Definition:

> `finalize()` is a method in the `Object` class that the **Garbage Collector (GC)** calls **before destroying an object**.

🧾 Syntax:

```java
protected void finalize() throws Throwable
```

---

## 🔍 Purpose

* Cleanup resources **before** the object is garbage collected
* Close files, network sockets, or release memory (old practice)

---

## 🧪 Basic Example:

```java
class Demo {
    @Override
    protected void finalize() throws Throwable {
        System.out.println("finalize() called for Demo");
    }
}

public class Test {
    public static void main(String[] args) {
        Demo d = new Demo();
        d = null; // Eligible for GC

        System.gc(); // Request GC (not guaranteed)
        System.out.println("Main method ends");
    }
}
```

🟡 Output may include:

```
Main method ends
finalize() called for Demo
```

> ⚠️ But calling `System.gc()` does **not guarantee** immediate `finalize()` execution!

---

## ❌ Why It’s Deprecated (Java 9+)

* **Unpredictable timing** (GC may not run immediately)
* **Performance issues**
* **Security risks** (object resurrection possible)
* Modern alternatives are **better** (like `try-with-resources`)

> ⚠️ Java 9: Marked `finalize()` as **deprecated**
> ⚠️ Java 18+: Scheduled for **removal**

---

## 🛑 Problems with `finalize()`

| Issue                 | Description                             |
| --------------------- | --------------------------------------- |
| ❌ Unpredictable       | You don’t know when (or if) it will run |
| ❌ Expensive           | Slows down GC performance               |
| ❌ Object resurrection | Object can be "revived" in `finalize()` |
| ❌ Deprecated          | Not recommended in modern Java          |

---

## ✅ Recommended Alternatives

| Use Case               | Modern Solution                        |
| ---------------------- | -------------------------------------- |
| Releasing resources    | `try-with-resources` (`AutoCloseable`) |
| File or stream cleanup | Override `close()` method              |
| Custom cleanup logic   | Use explicit `dispose()` method        |

---

## 🧑‍🏫 Real-World Analogy

> `finalize()` = Tumhara ghar jalne se pehle **ek warning letter** milta hai 📩  
> But aaj kal log **smoke detectors aur auto-shutdown** system use karte hain! 🔥

---

## 🏁 Summary Table

| Feature            | `finalize()` Method 🧹                |
| ------------------ | ------------------------------------- |
| Declared in        | `java.lang.Object`                    |
| Access Modifier    | `protected`                           |
| Called by          | JVM's Garbage Collector               |
| Purpose            | Last-minute cleanup (legacy style)    |
| Guaranteed to run? | ❌ No                                  |
| Deprecated?        | ✅ Yes (Java 9 onwards)                |
| Better alternative | `try-with-resources`, `AutoCloseable` |

---
