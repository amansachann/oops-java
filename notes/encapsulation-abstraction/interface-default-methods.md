# 💥 Interface Default Methods (Java 8)

---

## 🧠 What is a Default Method in an Interface?

### 📌 Definition:

> A **default method** in an interface is a method that has a **default implementation** and **doesn't need to be overridden** by implementing classes (unless you want to override it).

✅ Introduced in **Java 8** to enable **backward compatibility** without breaking existing code.

---

## 🔧 Syntax

```java
interface Vehicle {
    void start(); // abstract method

    default void fuelType() {
        System.out.println("Uses petrol or diesel");
    }
}
```

---

## 🏗️ Implementing Class Example

```java
class Car implements Vehicle {
    public void start() {
        System.out.println("Car started");
    }
}
```

```java
Vehicle v = new Car();
v.start();     // Car started
v.fuelType();  // Uses petrol or diesel ✅ (from default method)
```

---

## 💡 Why Default Methods?

| ✅ Benefit              | 📘 Explanation                                          |
| ---------------------- | ------------------------------------------------------- |
| Backward compatibility | Add methods to interfaces without breaking older code ✅ |
| Shared behavior        | Provide common logic to all implementations             |
| Reduced duplication    | Avoid writing same code in every class                  |
| Framework-friendly     | Used heavily in **Java Streams**, **Collections API**   |

---

## 🧪 Overriding Default Method

```java
class ElectricCar implements Vehicle {
    public void start() {
        System.out.println("Electric Car started silently");
    }

    @Override
    public void fuelType() {
        System.out.println("Uses electricity 🔋");
    }
}
```

✅ Output:

```
Electric Car started silently  
Uses electricity 🔋
```

---

## 🧬 Multiple Interfaces with Same Default Method

```java
interface A {
    default void show() {
        System.out.println("A");
    }
}

interface B {
    default void show() {
        System.out.println("B");
    }
}

class MyClass implements A, B {
    @Override
    public void show() {
        A.super.show(); // or B.super.show()
    }
}
```

✅ Java forces you to **resolve the conflict manually** 👇

```java
MyClass m = new MyClass();
m.show(); // A
```

---

## 🧠 Rules of Default Methods

| Rule ✅                           | Description                               |
| -------------------------------- | ----------------------------------------- |
| Must have a method body          | Unlike abstract methods                   |
| Must use `default` keyword       | Otherwise treated as abstract             |
| Can be overridden                | Optional, not mandatory                   |
| Cannot be `static` or `abstract` | Default = only one of its kind            |
| Conflict with class method?      | Class method **wins** (overrides default) |

---

## ⚠️ Common Mistakes

| ❌ Mistake                          | ⚠️ Problem                                 |
| ---------------------------------- | ------------------------------------------ |
| Declaring static method as default | Compile-time error ❌                       |
| Not resolving method conflict      | Multiple default methods = compile error ❌ |
| Thinking default = optional method | Still part of interface, just has fallback |

---

## 🏁 Summary Table

| Feature             | Default Method                     |
| ------------------- | ---------------------------------- |
| Java version        | Java 8+                            |
| Method body         | ✅ Yes                              |
| Overridable?        | ✅ Yes                              |
| Used in interface?  | ✅ Only inside interface            |
| Access modifier     | Always `public`                    |
| Conflict resolution | Must override in class if conflict |

---

## 🧱 Real-World Example (Functional Interface Combo)

```java
interface Logger {
    default void log(String msg) {
        System.out.println("[LOG]: " + msg);
    }
}

class FileLogger implements Logger {
    // No override needed unless custom logic
}
```

✅ Output:

```java
new FileLogger().log("Saving file...");
// [LOG]: Saving file...
```

---
[🏠 Back to Home](../../README.md)