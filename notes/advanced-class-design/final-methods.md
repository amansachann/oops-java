# ⚠️ Final Methods 

---

## 🧠 What is a Final Method?

### 📌 Definition:

> A `final` method is a method that **cannot be overridden** in a subclass.
> It is declared using the `final` keyword.

```java
class Vehicle {
    final void start() {
        System.out.println("Vehicle starting...");
    }
}
```

---

## 🚫 Attempt to Override — Error Example

```java
class Car extends Vehicle {
    @Override
    void start() {  // ❌ ERROR!
        System.out.println("Car starting...");
    }
}
```

🛑 **Output:** `Cannot override the final method from Vehicle`

---

## ✅ Why Use Final Methods?

| 🔐 Use Case                         | 📌 Reason                               |
| ----------------------------------- | --------------------------------------- |
| Secure critical logic               | Prevents subclasses from breaking rules |
| API design                          | Avoid misuse of core framework methods  |
| Performance optimization hint (JVM) | JVM may inline final methods            |
| Immutable design pattern            | Ensures fixed behavior                  |

---

## 🧪 Real-World Example

```java
class Bank {
    final double getInterestRate() {
        return 7.5;
    }
}

class SBI extends Bank {
    // ❌ This would be illegal:
    // double getInterestRate() { return 8.5; }
}
```

✅ Subclasses can’t tamper with critical financial logic 🔒💰

---

## ⚖️ Final Method vs Non-Final Method

| Feature     | `final` Method 🔒          | Normal Method 🔄        |
| ----------- | -------------------------- | ----------------------- |
| Overridable | ❌ No                       | ✅ Yes                   |
| Used for    | Safety & integrity         | Flexibility & extension |
| Common in   | Immutable/API/base classes | Most regular classes    |

---

## 🔬 With Abstract or Static?

| Combination          | Valid? | Notes                                      |
| -------------------- | ------ | ------------------------------------------ |
| `final` + `abstract` | ❌ No   | Contradiction: abstract needs override     |
| `final` + `static`   | ✅ Yes  | Static methods can't be overridden anyway  |
| `final` + `private`  | ✅ Yes  | Private methods can't be overridden either |

---

## 🧼 Best Practices

| ✅ Do’s                                   | ❌ Don’ts                                       |
| ---------------------------------------- | ---------------------------------------------- |
| Use `final` when you want fixed behavior | Don’t make all methods final unnecessarily     |
| Combine with `template method` pattern   | Don’t mark abstract methods final (invalid)    |
| Clearly document why method is final     | Avoid using final in low-level temporary logic |

---

## 🏁 Summary Table

| 📌 Feature              | Final Method 🔒              |
| ----------------------- | ---------------------------- |
| Syntax                  | `final void methodName() {}` |
| Overridable in subclass | ❌ No                         |
| Use case                | Restrict behavior change     |
| Allowed with static?    | ✅ Yes                        |
| Allowed with abstract?  | ❌ No (compilation error)     |
| JVM optimization?       | ✅ May help inline the method |

---
[🏠 Back to Home](../..)