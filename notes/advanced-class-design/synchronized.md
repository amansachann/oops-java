# 🛡️ synchronized

---

## 🧠 What is a Synchronized Method?

### 📌 Definition:

> A **synchronized method** in Java ensures that **only one thread at a time can execute** that method on the **same object**.
> It locks the **intrinsic lock (monitor)** of the object (or class for static methods).

---

## ✅ Syntax

### 🔹 Instance Method:

```java
public synchronized void instanceMethod() {
    // only one thread per object can access this at a time
}
```

### 🔹 Static Method:

```java
public static synchronized void staticMethod() {
    // only one thread per class can access this at a time
}
```

---

## 🚦 How It Works?

| 🔒 Method Type                 | 🔐 Lock Acquired On              |
| ------------------------------ | -------------------------------- |
| `synchronized` instance method | Object instance (`this`)         |
| `synchronized` static method   | Class object (`ClassName.class`) |

---

## 🔥 Example

### ✅ Without Synchronization (Unsafe)

```java
class Counter {
    int count = 0;

    public void increment() {
        count++;
    }
}
```

Multiple threads might increment at the same time — leading to data corruption ❌

---

### ✅ With `synchronized` (Safe)

```java
class Counter {
    int count = 0;

    public synchronized void increment() {
        count++;
    }
}
```

Now, only **one thread** can enter the `increment()` method at a time ✅

---

## 🧪 Example with Threads

```java
class Counter {
    int count = 0;

    public synchronized void increment() {
        count++;
    }
}

public class Test {
    public static void main(String[] args) throws Exception {
        Counter c = new Counter();

        Thread t1 = new Thread(() -> {
            for (int i = 0; i < 1000; i++) c.increment();
        });

        Thread t2 = new Thread(() -> {
            for (int i = 0; i < 1000; i++) c.increment();
        });

        t1.start(); t2.start();
        t1.join(); t2.join();

        System.out.println("Final Count: " + c.count); // ✅ 2000 expected
    }
}
```

---

## 📊 `synchronized` vs `volatile`

| Feature    | `synchronized` 🔐                | `volatile` 🔁               |
| ---------- | -------------------------------- | --------------------------- |
| Guarantees | **Atomicity + Visibility**       | Only **Visibility**         |
| Locks      | Yes (mutex)                      | No                          |
| Slow?      | Slightly slower (context switch) | Fast (no lock involved)     |
| Use Case   | Compound operations (e.g., `++`) | Flags / single reads/writes |

---

## 🧼 Best Practices

| ✅ Do’s                                       | ❌ Don’ts                                            |
| -------------------------------------------- | --------------------------------------------------- |
| Use when multiple threads update shared data | Don’t overuse — may lead to performance bottlenecks |
| Combine with proper exception handling       | Don’t hold locks longer than needed                 |
| Prefer `ReentrantLock` for advanced use      | Don’t synchronize on publicly accessible objects    |

---

## 🏁 Summary Table

| 📌 Feature                   | Synchronized Method 🔐               |
| ---------------------------- | ------------------------------------ |
| Controls                     | Thread access to critical sections   |
| Lock based on                | `this` or class (for static methods) |
| Thread safety                | ✅ Yes                                |
| Affects performance?         | ✅ Slightly due to locking            |
| Combine with other keywords? | ✅ Yes (`final`, `private`, etc.)     |

---

## 🔄 Reentrant Nature of synchronized

```java
public synchronized void outer() {
    inner(); // allowed — Java locks are reentrant
}

public synchronized void inner() {
    // same thread can acquire lock again
}
```

---

[🏠 Back to Home](../..)