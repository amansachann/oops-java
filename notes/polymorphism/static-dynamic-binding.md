# 📒 Late Binding vs Early Binding

---

## 🧠 What is Binding?

> **Binding** = Deciding which method/variable to call.

| Type                               | Description                       |
| ---------------------------------- | --------------------------------- |
| **Early Binding** (Static Binding) | Decision made at **compile time** |
| **Late Binding** (Dynamic Binding) | Decision made at **runtime**      |

---

## 🔁 Early Binding (Static Binding)

### 📌 Definition:

> When method call is resolved **during compile time**, it's called **early/static binding**.

✅ Used for:

* **private** methods
* **static** methods
* **final** methods
* **overloaded** methods

---

### 🧪 Example:

```java
class Demo {
    static void staticMethod() {
        System.out.println("Static Method");
    }

    void show(int x) {
        System.out.println("int: " + x);
    }

    void show(double x) {
        System.out.println("double: " + x);
    }
}
```

```java
Demo d = new Demo();
d.show(10);        // int: 10 ✅ early binding (method overloading)
d.staticMethod();  // Static Method ✅ early binding
```

---

## ⏳ Late Binding (Dynamic Binding)

### 📌 Definition:

> When method call is resolved **during runtime**, it's called **late/dynamic binding**.

✅ Happens when:

* A **parent class reference** refers to **child class object**
* The method is **overridden**

---

### 🧪 Example:

```java
class Animal {
    void speak() {
        System.out.println("Animal speaks");
    }
}

class Dog extends Animal {
    @Override
    void speak() {
        System.out.println("Dog barks 🐶");
    }
}

Animal a = new Dog();
a.speak();  // ✅ Late binding (runtime pe method resolve hoti hai)
```

---

## 🎯 Key Differences Table

| Feature                | 🧮 Early Binding                   | ⏱️ Late Binding                         |
| ---------------------- | ---------------------------------- | --------------------------------------- |
| When decision is made  | Compile time                       | Runtime                                 |
| Also called            | Static Binding                     | Dynamic Binding                         |
| Used for               | Overloaded, private, static, final | Overridden methods                      |
| Supports polymorphism? | ❌ No                               | ✅ Yes                                   |
| Faster execution?      | ✅ Yes (compiler optimized)         | ❌ Slightly slower (runtime decision)    |
| Example                | `obj.show(10)`                     | `parentRef.speak()` with `child` object |

---

## 🧱 Real-World Analogy

| Binding Type  | Analogy 📖                                                               |
| ------------- | ------------------------------------------------------------------------ |
| Early Binding | **Scripted play**: roles decided before the show — no change at runtime. |
| Late Binding  | **Improv comedy**: roles played dynamically based on audience input.     |

---

## ✅ Best Practices

| 👍 Do's                                                      | 👎 Don'ts                                          |
| ------------------------------------------------------------ | -------------------------------------------------- |
| Use early binding for **performance**-critical static logic  | Avoid static/final methods if you plan to override |
| Use late binding for **flexible** polymorphic design         | Don’t mix static with polymorphism concepts        |
| Always use `@Override` to ensure runtime methods are correct | Avoid downcasting without `instanceof`             |

---

## 🔚 Summary

| Binding Type  | Use Case                         | Example                           |
| ------------- | -------------------------------- | --------------------------------- |
| Early Binding | Overloading, static, private     | `void show(int x)`                |
| Late Binding  | Overriding, runtime polymorphism | `a.speak()` where `a = new Dog()` |

---
[🏠 Back to Home](../../README.md)
