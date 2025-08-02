# 🏃‍♂️ Runtime Polymorphism

---

## 🧠 What is Runtime Polymorphism?

### 📌 Definition:

> **Runtime Polymorphism** occurs when a **parent class reference** is used to **call an overridden method** in a **child class**, and the **actual method to call is decided at runtime**.

✅ Also called: **Dynamic Method Dispatch**  
✅ Achieved via: **Method Overriding**

---

## 🔧 Basic Example

```java
class Animal {
    void sound() {
        System.out.println("Animal makes a sound");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Dog barks 🐶");
    }
}

class Cat extends Animal {
    @Override
    void sound() {
        System.out.println("Cat meows 🐱");
    }
}
```

✅ Runtime behavior:

```java
Animal a;

a = new Dog();
a.sound(); // Dog barks 🐶

a = new Cat();
a.sound(); // Cat meows 🐱
```

> ☝️ **Compiler dekhta hai reference type**, lekin **JVM dekhta hai actual object** — that’s why it’s called *runtime* polymorphism 🧠⚡

---

## 🎯 Why Use Runtime Polymorphism?

| ✅ Benefit              | 📘 Explanation                             |
| ---------------------- | ------------------------------------------ |
| Flexible architecture  | One interface, multiple behaviors          |
| Reduces coupling       | Use parent reference — hide implementation |
| Promotes scalability   | Add new subtypes without changing old code |
| Backbone of frameworks | Spring, Hibernate, Java Collections use it |

---

## 🧪 Method Overriding Rules

| Rule ✅                          | Description                                 |
| ------------------------------- | ------------------------------------------- |
| Same method name                | Must be same in parent & child              |
| Same parameters                 | Parameter list must match                   |
| Return type                     | Can be same or **covariant**                |
| Access level                    | Same or **more visible** (not less)         |
| Must not reduce exception scope | Checked exceptions can't be more strict     |
| Can't override `final` methods  | ❌ Compile-time error                        |
| Can't override `static` methods | ❌ Static methods are hidden, not overridden |

---

## ⚠️ Invalid Overriding Example

```java
class A {
    final void show() { }  // ❌ Can't be overridden
}
class B extends A {
    void show() { }  // ❌ Compile-time error
}
```

---

## 🧱 Real-World Analogy

> **Remote (Parent) can operate multiple TVs (Child objects)**
> Lekin **actual behavior** depends on **TV type**, not remote 😎📺

---

## 🧬 Real-World Example: Payment System

```java
class Payment {
    void pay() {
        System.out.println("Generic payment");
    }
}

class UPI extends Payment {
    void pay() {
        System.out.println("Paid using UPI 💸");
    }
}

class CreditCard extends Payment {
    void pay() {
        System.out.println("Paid using Credit Card 💳");
    }
}
```

✅ Usage:

```java
Payment p;

p = new UPI();
p.pay(); // Paid using UPI 💸

p = new CreditCard();
p.pay(); // Paid using Credit Card 💳
```

---

## 🔄 Compile-Time vs Run-Time Polymorphism

| Feature              | Compile-Time 🧮         | Run-Time ⏱️                 |
| -------------------- | ----------------------- | --------------------------- |
| Achieved via         | Method Overloading      | Method Overriding           |
| Decision made at     | Compile time            | Runtime                     |
| Binding              | Static Binding          | Dynamic Binding             |
| Parameters required? | Yes (signature matters) | No (just override behavior) |
| Flexibility          | Less                    | More                        |

---

## 🏁 Summary Table

| Feature               | Runtime Polymorphism              |
| --------------------- | --------------------------------- |
| Java mechanism        | Method Overriding                 |
| Decision made at      | Runtime                           |
| Method binding        | Dynamic                           |
| Requires inheritance? | ✅ Yes                             |
| Achieved via          | Parent reference, child object    |
| Real-world use        | Everywhere: frameworks, libraries |

---

## 🧠 Bonus Tip: Use `@Override`

Always use `@Override` annotation to:

* ✅ Ensure method is properly overridden
* ✅ Avoid typo errors
* ✅ Make code readable & maintainable

---
