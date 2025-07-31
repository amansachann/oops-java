# 🍁 Interface Inheritance

---

## 🧠 What is Interface Inheritance?

### 📌 Definition:

> **Interface inheritance** means one interface **extending** another interface using the `extends` keyword.

✅ A Java interface can **inherit from one or more interfaces**.

---

## 🔧 Syntax

```java
interface A {
    void show();
}

interface B extends A {
    void display();
}
```

```java
class MyClass implements B {
    public void show() {
        System.out.println("Showing A");
    }

    public void display() {
        System.out.println("Displaying B");
    }
}
```

✅ Usage:

```java
B obj = new MyClass();
obj.show();     // Showing A
obj.display();  // Displaying B
```

---

## 🎯 Key Rules

| Rule ✅                       | Description                          |
| ---------------------------- | ------------------------------------ |
| Keyword used                 | `extends` (not `implements`)         |
| Multiple inheritance allowed | ✅ Yes (comma-separated interfaces)   |
| Must override all methods    | Implementing class must override all |
| No method body (Java 7)      | All inherited methods are abstract   |

---

## 🔗 Multiple Interface Inheritance

```java
interface X {
    void methodX();
}

interface Y {
    void methodY();
}

interface Z extends X, Y {
    void methodZ();
}
```

✅ Class implementing Z must implement all 3 methods:

```java
class Demo implements Z {
    public void methodX() { System.out.println("X"); }
    public void methodY() { System.out.println("Y"); }
    public void methodZ() { System.out.println("Z"); }
}
```

---

## ⚠️ Diamond Problem? ❌ Nope!

Java **resolves multiple inheritance conflict** at compile time for interfaces because:

* All methods are abstract by default.
* No method body = No conflict!

✅ Java handles it cleanly.

---

## 🧱 Real-World Example

```java
interface Engine {
    void start();
}

interface ElectricEngine extends Engine {
    void charge();
}

class Tesla implements ElectricEngine {
    public void start() {
        System.out.println("Tesla started silently.");
    }

    public void charge() {
        System.out.println("Tesla charging...");
    }
}
```

---

## 💡 Interface vs Class Inheritance

| Feature              | Interface Inheritance 🧬  | Class Inheritance 🧱    |
| -------------------- | ------------------------- | ----------------------- |
| Keyword              | `extends`                 | `extends`               |
| Multiple inheritance | ✅ Allowed                 | ❌ Not allowed           |
| Method type          | abstract, default, static | abstract + concrete     |
| Used for             | Behavior                  | Shared state + behavior |

---

## 🚫 Common Mistakes

| ❌ Mistake                                              | ⚠️ Issue             |
| ------------------------------------------------------ | -------------------- |
| Using `implements` for interfaces extending interfaces | Should use `extends` |
| Not implementing all inherited methods                 | Compile-time error   |
| Thinking interface can't extend multiple interfaces    | It can! ✅            |

---

## 🏁 Summary Table

| Feature              | Interface Inheritance                   |
| -------------------- | --------------------------------------- |
| Inherits from        | One or more interfaces                  |
| Keyword used         | `extends`                               |
| Methods inherited    | All abstract (or default/static if any) |
| Multiple inheritance | ✅ Supported                             |
| Implementation       | Done in class using `implements`        |

---
[🏠 Back to Home](../../README.md)