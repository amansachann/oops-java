# 🚼 Multilevel Inheritance

---

## 🧠 What is Multilevel Inheritance?

### 📌 **Definition:**

> In **Multilevel Inheritance**, a class inherits from another class, which itself inherits from another class.
> Matlab:
> `Class C` → inherits `Class B` → which inherits `Class A`

---

## 👪 Real-Life Analogy

👴 **Grandfather** → 👨 **Father** → 👦 **Son**

* Son inherits both Father’s & Grandfather’s features!
* In Java: `Son` class inherits both **Father** and **Grandfather** methods ✅

---

## 🔧 Syntax

```java
class A {
    void showA() {
        System.out.println("Class A");
    }
}

class B extends A {
    void showB() {
        System.out.println("Class B");
    }
}

class C extends B {
    void showC() {
        System.out.println("Class C");
    }
}
```

✅ Usage:

```java
C obj = new C();
obj.showA(); // inherited from A
obj.showB(); // inherited from B
obj.showC(); // defined in C
```

---

## 🧱 Memory Hierarchy

```
     [ C object ]
         ↑
       Class B
         ↑
       Class A
```

🧠 All methods of A → accessible to B
All methods of A + B → accessible to C

---

## 🔁 Constructor Calling Order

```java
class A {
    A() { System.out.println("A Constructor"); }
}

class B extends A {
    B() { System.out.println("B Constructor"); }
}

class C extends B {
    C() { System.out.println("C Constructor"); }
}
```

```java
C obj = new C();
```

✅ Output:

```
A Constructor  
B Constructor  
C Constructor
```

🎯 **Parent constructors run from top to bottom** (A → B → C)

---

## 🎯 Why Use Multilevel Inheritance?

| ✅ Benefit                           | 🔥 Description                               |
| ----------------------------------- | -------------------------------------------- |
| Code Reusability at multiple levels | Each class reuses and extends previous logic |
| Easy hierarchy modeling             | e.g., Employee → Manager → Director          |
| Progressive enhancement             | Add features at each inheritance layer       |

---

## ⚠️ Important Rules

| ⚠️ Rule                                   | ✅ Explanation                                   |
| ----------------------------------------- | ----------------------------------------------- |
| Use only one parent at a time             | Java doesn’t support multiple class inheritance |
| `super()` used to call parent constructor | Always at top of constructor                    |
| Private members not inherited             | Access via getters/setters only                 |

---

## 💡 Real-World Example: Organization Hierarchy

```java
class Employee {
    void work() {
        System.out.println("Employee works");
    }
}

class Manager extends Employee {
    void manage() {
        System.out.println("Manager manages team");
    }
}

class Director extends Manager {
    void strategize() {
        System.out.println("Director makes strategy");
    }
}
```

✅ Usage:

```java
Director d = new Director();
d.work();       // from Employee
d.manage();     // from Manager
d.strategize(); // own method
```

---

## 🧪 Java Inheritance Types Recap

| 📘 Type      | 🔧 Description                   | ✅ Supported in Java?       |
| ------------ | -------------------------------- | -------------------------- |
| Single       | One class inherits one class     | ✅ Yes                      |
| Multilevel   | Chain of inheritance (A → B → C) | ✅ Yes                      |
| Hierarchical | One parent → many children       | ✅ Yes                      |
| Multiple     | One class inherits from multiple | ❌ No (but interfaces)      |
| Hybrid       | Mix of multiple types            | ❌ No (only via interfaces) |

---

## 🏁 Summary Table

| 🔧 Feature                 | 📌 Multilevel Inheritance               |
| -------------------------- | --------------------------------------- |
| Keyword                    | `extends`                               |
| Constructor order          | Top-down (A → B → C)                    |
| Private members inherited? | ❌ No (use getters/setters)              |
| Use case                   | Class chains (Employee → Manager → CEO) |
| Superclass access          | ✅ Direct access to all ancestors        |

---

[🏠 Back to Home](../../README.md)