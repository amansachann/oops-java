# 🍀 volatile

---

## 🧠 What is `volatile` in Java?

### 📌 Definition:

> `volatile` is a **modifier** used in multithreaded programming to ensure that a **variable's value is always read from main memory**, **not from thread cache**.

---

### ✅ Syntax:

```java
volatile dataType variableName;
```

---

## 🔍 Problem Without `volatile`

* Threads have their own **CPU cache**.
* If one thread updates a shared variable, **other threads may not see the updated value**.
* ❌ Leads to bugs like infinite loops, stale reads, race conditions.

---

## 🔒 What `volatile` Solves

| ⚠️ Problem                | ✅ `volatile` Solution                             |
| ------------------------- | ------------------------------------------------- |
| Visibility issue          | Always reads latest value from **main memory**    |
| Cached value may be stale | Guarantees freshness across threads               |
| Thread-local copies       | Prevents caching of variable between thread reads |

---

## ✅ Example: Without vs With `volatile`

### 🔴 Without `volatile` (infinite loop risk!)

```java
class MyTask extends Thread {
    boolean running = true;

    public void run() {
        while (running) {
            // do work...
        }
    }

    public void stopTask() {
        running = false;
    }
}
```

If `stopTask()` is called from another thread, it may **not break the loop** because `running` might be cached.

---

### ✅ With `volatile`

```java
class MyTask extends Thread {
    volatile boolean running = true;

    public void run() {
        while (running) {
            // do work...
        }
    }

    public void stopTask() {
        running = false;
    }
}
```

Now `running` is always read from main memory — loop stops as expected 🔁✅

---

## 💡 Key Properties of `volatile`

| 🔍 Property                   | ✅ Description                               |
| ----------------------------- | ------------------------------------------- |
| Visibility guarantee          | Always read latest value from main memory   |
| No locking required           | Lightweight compared to `synchronized`      |
| No atomicity for compound ops | `x++` is not atomic even if `x` is volatile |
| Works with single variable    | Not for groups of variables                 |

---

## ⚠️ What `volatile` Does NOT Do

❌ It does **not** make the operation **atomic**.

```java
volatile int count = 0;

public void increment() {
    count++; // NOT atomic! => Read, Modify, Write = 3 steps!
}
```

✅ For atomicity, use:

* `synchronized`
* `AtomicInteger`, etc. (from `java.util.concurrent.atomic`)

---

## 🧼 Best Practices

| ✅ Do’s                                          | ❌ Don’ts                                           |
| ----------------------------------------------- | -------------------------------------------------- |
| Use `volatile` for simple flags or status flags | Don’t use for compound operations (`x++`, etc.)    |
| Use when **visibility** is the only concern     | Don’t assume it prevents race conditions           |
| Use with `double`/`long` to avoid tearing       | Don’t use with `synchronized` unless really needed |

---

## 🏁 Summary Table

| 📌 Feature            | `volatile` Keyword 🔁                     |
| --------------------- | ----------------------------------------- |
| Scope                 | Variables only (instance variables)       |
| Ensures               | **Visibility**, not atomicity             |
| Prevents              | Caching of values by threads              |
| Common Use            | Flags, state indicators in multithreading |
| Safer alternative for | Simple `boolean` flags                    |

---

[🏠 Back to Home](../..)