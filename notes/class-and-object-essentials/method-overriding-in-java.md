# 🐲 Method Overriding

---

## 🧠 What is Method Overriding?

### 📌 **Definition:**

> **Method Overriding** is when a **subclass** provides its **own implementation** of a **method** that is already defined in the **superclass**.

---

## 📦 Real-Life Analogy

👨‍👦‍👦 Parent says "go to work",
👶 Child (subclass) says "I go to coding job",
Same method, **custom behavior** → that's overriding!

---

## 🔧 Syntax

```java
class Parent {
    void show() {
        System.out.println("Parent's version");
    }
}

class Child extends Parent {
    @Override
    void show() {
        System.out.println("Child's version");
    }
}
```

✅ Usage:

```java
Parent obj = new Child();
obj.show(); // Output: Child's version ✅
```

➡️ Called based on **object type** at **runtime** = **dynamic method dispatch**

---

## ✅ Key Rules of Method Overriding

| Rule 🔧                                             | Description 📌                                     |
| --------------------------------------------------- | -------------------------------------------------- |
| Method name must be same                            | 🔁 Exactly same method signature                   |
| Parameters must match                               | 🔁 Same number, type, and order                    |
| Return type must be same or covariant               | ✅ Subclass of parent return type allowed (Java 5+) |
| Access modifier can't be more restrictive           | 🔐 e.g., `public` cannot become `protected`        |
| Can't override `static`, `final`, `private` methods | ❌ These are not polymorphic                        |
| Use `@Override` annotation                          | ✅ Compiler check, best practice                    |

---

## 🧠 Dynamic Method Dispatch

> Method resolution happens **at runtime**, based on the actual **object type**, not reference type.

```java
Parent p = new Child();
p.show(); // 🔥 Calls Child's method, not Parent’s
```

---

## 🔧 Example: Animal → Dog

```java
class Animal {
    void sound() {
        System.out.println("Some generic sound");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Bark");
    }
}
```

```java
Animal a = new Dog();
a.sound(); // Output: Bark ✅
```

---

## ⚔️ Method Overriding vs Method Overloading

| Feature               | Overloading  | Overriding                |
| --------------------- | ------------ | ------------------------- |
| Class level           | Same class   | Subclass + superclass     |
| Parameters            | Must differ  | Must be same              |
| Return type           | Can vary     | Must be same or covariant |
| Polymorphism          | Compile-time | Runtime                   |
| `@Override` required? | ❌ No         | ✅ Best practice           |

---

## 🧪 Interview Gotcha

🧠 **Q:** Can constructors be overridden?

❌ **No**, because constructors are **not inherited**.

---

## 🔥 Real-World Example

### ⚙️ Base Controller in Spring Boot:

```java
class BaseController {
    public void handleRequest() {
        System.out.println("Base: Handling request");
    }
}

class UserController extends BaseController {
    @Override
    public void handleRequest() {
        System.out.println("UserController: Custom logic");
    }
}
```

➡️ You write different versions of `handleRequest()` for each controller — that’s overriding in **real-world MVC!**

---

## ⚠️ Special Cases

| Keyword 🔧        | Impact                             |
| ----------------- | ---------------------------------- |
| `super.method()`  | Call the parent version explicitly |
| `final` method    | ❌ Cannot be overridden             |
| `static` method   | ❌ Hidden, not overridden           |
| `private` method  | ❌ Not inherited, so not overridden |
| `abstract` method | ✅ Must be overridden               |

---

## ✅ Best Practices

| Tip 💡                            | Reason ✅                            |
| --------------------------------- | ----------------------------------- |
| Use `@Override`                   | Avoid accidental mismatches         |
| Prefer `super.method()` if needed | Reuse parent logic                  |
| Respect LSP (Liskov Principle)    | Don't break behavior expectation    |
| Avoid changing access to private  | Will not override, causes confusion |

---

## 🧠 Memory/Execution Diagram

```java
Parent p = new Child(); → Actual object is Child

        p.show(); → JVM looks into Child at runtime
```

---

## 🏁 Summary Table

| 🔧 Feature           | 🧪 Overriding Behavior       |
| -------------------- | ---------------------------- |
| Method Signature     | Must be same                 |
| Return Type          | Same or subclass (covariant) |
| Access Modifier      | Same or **more public**      |
| Object Type decides  | ✅ Runtime decision           |
| `@Override` required | ✅ Recommended                |

---
[🏠 Back to Home](../..)