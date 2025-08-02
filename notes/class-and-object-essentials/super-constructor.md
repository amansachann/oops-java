# 🪄 super() Constructor

---

## 🧠 What is `super()`?

### 📌 **Definition:**

> `super()` is a special call used **inside a child class constructor** to invoke the **parent class constructor**.

---

## 🎯 Why Use `super()`?

| 💥 Scenario                                            | 🎯 Purpose                                   |
| ------------------------------------------------------ | -------------------------------------------- |
| Parent has a **default constructor**                   | Java calls it automatically                  |
| Parent has a **parameterized constructor**             | You **must explicitly call** `super(...)`    |
| To run parent initialization logic                     | Ensure parent is fully set up before child   |
| To perform **constructor chaining across inheritance** | Essential for class hierarchy initialization |

---

## 🔧 Syntax

```java
super();           // Call default parent constructor
super(arg1, arg2); // Call parameterized parent constructor
```

---

## ⚠️ Golden Rule

> 🔴 `super()` must be the **first line** in the child constructor.
> If not, Java gives a **compile-time error**!

---

## 💡 Real-Life Analogy

👨‍👦 Child (subclass) calls Parent (superclass) constructor to set up inheritance — like calling your dad before using his bank account 😄

---

## 🔧 Example 1: Default `super()` call (No need to write it explicitly)

```java
class A {
    A() {
        System.out.println("Constructor of A");
    }
}

class B extends A {
    B() {
        System.out.println("Constructor of B");
    }
}

public class Main {
    public static void main(String[] args) {
        B obj = new B();
    }
}
```

✅ Output:

```
Constructor of A
Constructor of B
```

👉 Even though we didn’t write `super()`, Java called it **implicitly**.

---

## 🔧 Example 2: Calling Parameterized Constructor Using `super(...)`

```java
class A {
    A(String msg) {
        System.out.println("Parent says: " + msg);
    }
}

class B extends A {
    B() {
        super("Hello from B to A");
        System.out.println("Child constructor B");
    }
}
```

✅ Output:

```
Parent says: Hello from B to A
Child constructor B
```

---

## 🔧 Example 3: Constructor Chaining with `super(...)`

```java
class Animal {
    Animal(String name) {
        System.out.println("Animal name is: " + name);
    }
}

class Dog extends Animal {
    Dog() {
        super("Bulldog"); // must be the first statement
        System.out.println("Dog constructor called");
    }
}
```

✅ Output:

```
Animal name is: Bulldog
Dog constructor called
```

---

## ⚔️ super() vs this()

| Feature     | `this()`                              | `super()`                       |
| ----------- | ------------------------------------- | ------------------------------- |
| Calls...    | Another constructor in **same class** | Constructor in **parent class** |
| Used in...  | Constructor                           | Constructor                     |
| First line? | ✅ Must be 1st line                    | ✅ Must be 1st line              |
| Accesses... | Current class                         | Immediate superclass            |

---

## 🧭 Memory Flow Diagram

```
Dog obj = new Dog();

  → Dog() {
         super("Bulldog") → Animal(String)
     }

Memory Stack:
-------------------------
| Dog Object            |
-------------------------
       ↑ super
-------------------------
| Animal Object         |
-------------------------
```

---

## ✅ Best Practices

| 💡 Tip                                                                | ✅ Reason             |
| --------------------------------------------------------------------- | -------------------- |
| Always call `super(args)` if parent has no default constructor        | Avoid compile errors |
| Put `super()` as **first line only**                                  | Compiler requirement |
| Avoid logic before `super()`                                          | Will lead to error   |
| Use `super()` in multi-level inheritance to keep hierarchy consistent | Clean design pattern |

---

## 🧪 Interview Tip

🧠 **Q:** What happens if a parent class has only a parameterized constructor and the child does not call `super(...)`?

❌ **Compile-time error**
✅ You must explicitly call `super(...)` with matching arguments.

---

## 🏁 Final Summary

| 🔧 Use           | 🔍 Purpose                            |
| ---------------- | ------------------------------------- |
| `super()`        | Call default parent constructor       |
| `super(args...)` | Call parameterized parent constructor |
| Must be first    | Always the first line in constructor  |
| Used in subclass | Always from child to parent           |

---
[🏠 Back to Home](../..)