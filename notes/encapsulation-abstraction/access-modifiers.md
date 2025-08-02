# 🔭 Access Modifiers

---

## 🧠 What are Access Modifiers?

### 📌 Definition:

> **Access Modifiers** in Java define **visibility** or **scope** of classes, variables, constructors, and methods.

---

## 🧱 Types of Access Modifiers in Java

| Modifier     | Same Class | Same Package | Subclass (diff package) | Other Packages |
| ------------ | ---------- | ------------ | ----------------------- | -------------- |
| `public`     | ✅          | ✅            | ✅                       | ✅              |
| `protected`  | ✅          | ✅            | ✅                       | ❌              |
| *default* ✳️ | ✅          | ✅            | ❌                       | ❌              |
| `private`    | ✅          | ❌            | ❌                       | ❌              |

✳️ **Default** = No modifier specified

---

## 🔍 1. `public`

* Accessible **everywhere**
* Used for APIs, libraries, `main()` method, etc.

```java
public class Car {
    public void drive() {
        System.out.println("Driving...");
    }
}
```

✅ Usage:

```java
Car c = new Car();
c.drive(); // Accessible anywhere
```

---

## 🔐 2. `private`

* Accessible **only within the same class**
* Used to **hide implementation details** (encapsulation)

```java
public class BankAccount {
    private double balance;

    private void calculateInterest() {
        // Only accessible inside this class
    }
}
```

✅ Usage:

```java
BankAccount acc = new BankAccount();
// acc.balance ❌ NOT accessible
```

---

## 👪 3. `protected`

* Accessible:

    * Inside same class ✅
    * Inside same package ✅
    * In **subclass from other package** ✅

```java
package vehicles;

public class Vehicle {
    protected void startEngine() {
        System.out.println("Engine started");
    }
}
```

```java
package cars;

import vehicles.Vehicle;

class Car extends Vehicle {
    void test() {
        startEngine(); // ✅ Accessible via inheritance
    }
}
```

---

## 🏡 4. *Default* (Package-Private)

* No modifier = Default access
* Accessible **only within same package**

```java
class Person { // 👈 No modifier = default
    void walk() {
        System.out.println("Walking...");
    }
}
```

✅ Usage:

```java
// Same package? ✅ Accessible
// Different package? ❌ Not accessible
```

---

## 🎯 Use Case Summary

| Modifier    | When to Use ✅                                   |
| ----------- | ----------------------------------------------- |
| `public`    | When method/class should be globally accessible |
| `private`   | For internal logic, encapsulation               |
| `protected` | When you want subclass access (OOP use)         |
| *default*   | For package-level encapsulation                 |

---

## ⚠️ Quick Rules Recap

| Concept                                             | ✅ Rule                                   |
| --------------------------------------------------- | ---------------------------------------- |
| Class can only be `public` or *default*             | No `private/protected` top-level classes |
| Fields should be `private`                          | Use getters/setters for access 🔒        |
| Overridden method must have same or more visibility | Else compile error ❌                     |

---

## 🧠 Interview Tip

* 🔥 “Can a class be `private`?”  
  ❌ No! Only **nested classes** can be private.

* 🔥 “Can protected members be accessed without inheritance from another package?”  
  ❌ No! Only via subclass.

---

## 🏁 Final Summary Table

| Modifier     | Class | Package | Subclass | World |
| ------------ | ----- | ------- | -------- | ----- |
| `public`     | ✅     | ✅       | ✅        | ✅     |
| `protected`  | ✅     | ✅       | ✅        | ❌     |
| *default* ✳️ | ✅     | ✅       | ❌        | ❌     |
| `private`    | ✅     | ❌       | ❌        | ❌     |

---

[🏠 Back to Home](../..)
