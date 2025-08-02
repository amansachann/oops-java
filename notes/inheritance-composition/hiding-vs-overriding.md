# 🍨 Hiding vs Overriding

---

## 🧠 What is Method Overriding?

### 📌 Definition:

> When a **subclass** provides a **specific implementation** of a **non-static** method already defined in its superclass using the **same name, return type, and parameters**.

✅ Achieves **runtime polymorphism**.

---

## 🧠 What is Method Hiding?

### 📌 Definition:

> When a **subclass defines a static method** with the **same signature** as a **static method in the superclass**, it's called **method hiding**, **not overriding**.

❌ No polymorphism — resolution happens at **compile time**.

---

## 🔧 Example: Overriding (Instance Method)

```java
class Parent {
    void show() {
        System.out.println("Parent show()");
    }
}

class Child extends Parent {
    @Override
    void show() {
        System.out.println("Child show()");
    }
}
```

```java
Parent p = new Child();
p.show(); // ✅ Output: Child show() – Overriding (runtime binding)
```

---

## 🔧 Example: Hiding (Static Method)

```java
class Parent {
    static void display() {
        System.out.println("Parent display()");
    }
}

class Child extends Parent {
    static void display() {
        System.out.println("Child display()");
    }
}
```

```java
Parent p = new Child();
p.display(); // ❌ Output: Parent display() – Hiding (compile-time binding)
```

---

## ⚖️ Overriding vs Hiding – Comparison Table

| Feature                   | Method Overriding 🔁          | Method Hiding 🎭                |
| ------------------------- | ----------------------------- | ------------------------------- |
| Method type               | Non-static (instance methods) | Static methods only             |
| Resolution time           | Runtime                       | Compile time                    |
| Achieves polymorphism?    | ✅ Yes                         | ❌ No                            |
| Annotations               | Use `@Override`               | ❌ No annotation used            |
| Can use `super.method()`? | ✅ Yes                         | ✅ Yes                           |
| Access via parent ref     | Executes child method         | Executes parent's static method |
| Real-world use            | Object behavior customization | Rarely used, can confuse        |

---

## 🚨 Common Mistakes & Gotchas

| Mistake ❌                            | Problem 💥                         |
| ------------------------------------ | ---------------------------------- |
| Using `@Override` on static method   | Compile-time error                 |
| Assuming static behaves like dynamic | Static methods are **class-level** |
| Forgetting that hiding ≠ overriding  | Can lead to unexpected outputs     |

---

## 🧪 Quick Test Code

```java
class Animal {
    static void run() { System.out.println("Animal runs"); }
    void eat() { System.out.println("Animal eats"); }
}

class Dog extends Animal {
    static void run() { System.out.println("Dog runs"); }  // Hiding
    @Override
    void eat() { System.out.println("Dog eats"); }         // Overriding
}

public class Test {
    public static void main(String[] args) {
        Animal a = new Dog();
        a.run();  // 👈 Animal runs (Hiding)
        a.eat();  // 👈 Dog eats (Overriding)
    }
}
```

---

## 🏁 Summary Table

| Feature             | Overriding             | Hiding                  |
| ------------------- | ---------------------- | ----------------------- |
| Method Type         | Non-static (instance)  | Static                  |
| Binding Type        | Runtime                | Compile-time            |
| Polymorphism        | ✅ Supported            | ❌ Not Supported         |
| Keyword Needed      | `@Override` (optional) | No annotation           |
| Inheritance         | ✅ Yes                  | ✅ Yes                   |
| Behavior via parent | Executes child version | Executes parent version |

---
[🏠 Back to Home](../..)