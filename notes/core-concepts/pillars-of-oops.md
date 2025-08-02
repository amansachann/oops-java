# 🔥 **Master the 4 Pillars of OOP**


## 🧭 Overview Table

| 🧱 Principle         | 💬 Definition                                                     | 🧠 Real-world Analogy                | 🔧 Java Keyword                 |
| -------------------- | ----------------------------------------------------------------- | ------------------------------------ | ------------------------------- |
| 🎭 **Abstraction**   | Hides complex implementation, shows only essentials               | Car pedals hide the engine mechanism | `abstract`, `interface`         |
| 🔐 **Encapsulation** | Binds data + methods, hides internal state using access modifiers | ATM hides internal balance           | `private`, `getter/setter`      |
| 🧬 **Inheritance**   | Child class inherits from parent class                            | Dog inherits from Animal             | `extends`                       |
| 🧠 **Polymorphism**  | Same interface, many implementations (Overriding/Overloading)     | Remote works with TV, AC             | `@Override`, method overloading |

---

## 🎭 1. **Abstraction**

### 📌 Definition:

> **Expose only what is necessary, hide internal logic.**

### ✅ Benefits:

* Hides complexity
* Cleaner API
* Focus on "what", not "how"

### 💡 Real-World:

When you use a **coffee machine**, you press a button — you don’t know its internal plumbing.

### 🔧 Java Example:

```java
// Interface = 100% abstraction
interface Vehicle {
    void start();
}

// Class implements abstract logic
class Car implements Vehicle {
    public void start() {
        System.out.println("Car starts with key");
    }
}
```

---

## 🔐 2. **Encapsulation**

### 📌 Definition:

> **Wrapping data (variables) and methods together and restricting direct access.**

### ✅ Benefits:

* Data protection
* Prevents misuse
* Easier to refactor

### 💡 Real-World:

Your **bank account balance** is private — you can only access it through methods (ATM/NetBanking).

### 🔧 Java Example:

```java
class BankAccount {
    private double balance; // 🔐 Private variable

    public void deposit(double amount) {
        if(amount > 0) balance += amount;
    }

    public double getBalance() {
        return balance;
    }
}
```

---

## 🧬 3. **Inheritance**

### 📌 Definition:

> **Acquiring properties and behavior from another class.**

### ✅ Benefits:

* Reusability
* Hierarchical modeling
* Code simplification

### 💡 Real-World:

**Dog** is an **Animal**, so it inherits legs, eyes, etc.

### 🔧 Java Example:

```java
class Animal {
    void eat() {
        System.out.println("Animal eats food");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Dog barks");
    }
}
```

✅ Usage:

```java
Dog d = new Dog();
d.eat();  // Inherited
d.bark(); // Own method
```

---

## 🧠 4. **Polymorphism**

### 📌 Definition:

> **One interface, many implementations. Two types:**

* **Compile-time** (Method Overloading)
* **Runtime** (Method Overriding)

### ✅ Benefits:

* Flexibility
* Extensibility
* Clean architecture (open/closed principle)

---

### ✅ Method Overloading (Compile-time)

```java
class Calculator {
    int add(int a, int b) { return a + b; }
    double add(double a, double b) { return a + b; }
}
```

---

### ✅ Method Overriding (Runtime)

```java
class Animal {
    void speak() { System.out.println("Animal sound"); }
}

class Cat extends Animal {
    @Override
    void speak() { System.out.println("Meow"); }
}
```

✅ Usage:

```java
Animal a = new Cat();  // Upcasting
a.speak(); // "Meow" → Runtime Polymorphism
```

---

## 🔁 Summary Diagram

```
       +---------------------------+
       |    4 Pillars of OOP       |
       +---------------------------+
       | 🎭 Abstraction            | → Hides complexity
       | 🔐 Encapsulation          | → Protects data
       | 🧬 Inheritance            | → Reuses code
       | 🧠 Polymorphism           | → Same interface, different behavior
       +---------------------------+
```

---

## 🧪 Best Practices for OOP Principles

| ✅ Principle   | ⚠️ Best Practice                                  |
| ------------- | ------------------------------------------------- |
| Encapsulation | Use `private` variables + `getter/setter`         |
| Abstraction   | Prefer `interfaces` for behavior contracts        |
| Inheritance   | Use only when there is true **is-a** relationship |
| Polymorphism  | Always program to interfaces for flexibility      |

---
[🏠 Back to Home](../..)