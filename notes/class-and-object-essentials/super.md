# 🚀 super Keyword in Java

---

## 🧠 What is `super` in Java?

### 📌 **Definition**:

> `super` is a reference variable used to refer to the **immediate parent class object**.

---

## 🎯 Use Cases of `super`

| 🔢 # | 🔧 Usage             | 🧠 What It Does                    |
| ---- | -------------------- | ---------------------------------- |
| 1️⃣  | `super()`            | Calls parent class **constructor** |
| 2️⃣  | `super.variableName` | Accesses **parent class variable** |
| 3️⃣  | `super.methodName()` | Calls **parent class method**      |

---

## 🧬 Inheritance Recap

```java
class Animal {
    String color = "Brown";

    void sound() {
        System.out.println("Animal makes sound");
    }

    Animal() {
        System.out.println("Animal constructor called");
    }
}

class Dog extends Animal {
    Dog() {
        super(); // calls Animal()
        System.out.println("Dog constructor called");
    }

    void printColor() {
        System.out.println(super.color); // accesses Animal's color
    }

    void sound() {
        super.sound(); // calls Animal's sound()
        System.out.println("Dog barks");
    }
}
```

✅ Output:

```
Animal constructor called
Dog constructor called
Brown
Animal makes sound
Dog barks
```

---

## 🔧 Example 1: `super()` → Calling Parent Constructor

```java
class A {
    A() {
        System.out.println("Constructor of A");
    }
}

class B extends A {
    B() {
        super(); // explicitly calls A's constructor
        System.out.println("Constructor of B");
    }
}
```

> ⚠️ If not written, Java **automatically inserts** `super()` as the first line of child constructor
> 
> ✅ But if parent has **parameterized constructor**, you **must call it explicitly**

---

## 🔧 Example 2: Accessing Parent Variable

```java
class A {
    int x = 10;
}

class B extends A {
    int x = 20;

    void show() {
        System.out.println("Child x = " + x);
        System.out.println("Parent x = " + super.x); // Access parent variable
    }
}
```

---

## 🔧 Example 3: Calling Parent Method

```java
class Animal {
    void speak() {
        System.out.println("Animal speaks");
    }
}

class Dog extends Animal {
    void speak() {
        super.speak();  // Call parent method
        System.out.println("Dog barks");
    }
}
```

---

## ⚠️ Rules of `super`

| ❗ Rule                                           | ✅ Explanation                            |
| ------------------------------------------------ | ---------------------------------------- |
| `super()` must be first statement in constructor | Just like `this()`, or compilation fails |
| Can't use `super` in static methods              | Because it refers to object, not class   |
| Can only access **immediate** parent             | `super.super` ❌ not allowed in Java      |
| Use when parent has **same method/field**        | Helps resolve **naming conflict**        |

---

## 🧠 Memory Diagram

```
Dog d = new Dog();

→ Dog() calls super() → Animal()

Memory Stack:
----------------------
| Dog Object          |
| color = "Brown"     |
| sound() → Dog       |
----------------------
         ↑
       super
         ↓
----------------------
| Animal Object       |
| color = "Brown"     |
| sound() → Animal    |
----------------------
```

---

## 🔥 Real-Life Analogy

| 👪 Concept       | 🧠 Example                      |
| ---------------- | ------------------------------- |
| Inheritance      | Son inherits traits from Father |
| `super()`        | Son calls Father’s constructor  |
| `super.method()` | Son calls Father’s advice       |
| `super.variable` | Accesses Father’s property      |

---

## ✅ Best Practices

| 💡 Tip                                                                 | ⚠️ Reason                                |
| ---------------------------------------------------------------------- | ---------------------------------------- |
| Use `super()` **explicitly** when parent has parameterized constructor | Avoid errors                             |
| Use `super` to resolve naming conflicts                                | Improves clarity                         |
| Don't overuse `super.method()`                                         | Prefer overridden behavior unless needed |
| Use `@Override` with overridden methods                                | Compiler checks correctness              |

---

## 🧪 Mini Practice

```java
class Person {
    String name = "John";

    void greet() {
        System.out.println("Hello from Person");
    }
}

class Student extends Person {
    String name = "Aman";

    void greet() {
        super.greet(); // Parent greet()
        System.out.println("Hello from Student");
    }

    void showNames() {
        System.out.println("Child name: " + name);
        System.out.println("Parent name: " + super.name);
    }
}
```

---

## 🏁 Summary Table

| 🔧 Syntax        | 🎯 Purpose                            |
| ---------------- | ------------------------------------- |
| `super()`        | Call parent constructor               |
| `super(args...)` | Call parent parameterized constructor |
| `super.var`      | Access parent variable                |
| `super.method()` | Call parent method                    |

---
[🏠 Back to Home](../../README.md)