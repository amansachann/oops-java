# 🦾 Non-static Inner Class

---

## 🧠 What is a Non-static Inner Class?

### 📌 Definition:

> A **non-static inner class** is a class defined **inside another class** without the `static` keyword. It has an **implicit reference to the outer class instance**, allowing it to access **all members (even private)** of the outer class.

---

## ✅ Syntax

```java
class Outer {
    int outerData = 50;

    class Inner {
        void show() {
            System.out.println("Outer data: " + outerData);
        }
    }
}
```

---

### 🧪 Usage Example:

```java
public class Test {
    public static void main(String[] args) {
        Outer outer = new Outer();
        Outer.Inner inner = outer.new Inner(); // 💡 Syntax to create inner class
        inner.show(); // Output: Outer data: 50
    }
}
```

---

## 🔍 Key Characteristics

| 📌 Feature                      | 🔍 Description                             |
| ------------------------------- | ------------------------------------------ |
| Belongs to outer class instance | ✅ Yes                                      |
| Needs outer class instance      | ✅ Required to create                       |
| Can access outer class members  | ✅ All (even private)                       |
| Memory footprint                | 🔼 Higher (holds reference to outer class) |
| Compiled as                     | `Outer$Inner.class`                        |

---

## 📦 Real-World Analogy

> **Outer class** = Laptop 💻
> **Inner class** = Touchpad 🖱️
> Touchpad **needs the laptop** to function — it's not standalone!

---

## 🧬 Accessing Outer Class Fields

```java
class Outer {
    private String name = "Java";

    class Inner {
        void display() {
            System.out.println("Accessing outer: " + name);
        }
    }
}
```

✅ Inner class can access `private` members too!

---

## 🧪 Inner Class With Same Field Name

```java
class Outer {
    int x = 10;

    class Inner {
        int x = 20;

        void print() {
            System.out.println("Inner x: " + x);
            System.out.println("Outer x: " + Outer.this.x); // 🧠 Special syntax
        }
    }
}
```

---

## 🧾 Where It’s Used?

| 💡 Use Case                   | 🔍 Why Inner Class?                      |
| ----------------------------- | ---------------------------------------- |
| Event handling (Swing/JavaFX) | Needs access to outer UI components      |
| Data hiding (encapsulation)   | Keep tightly bound helper logic grouped  |
| Tree/Graph algorithms         | Helper classes bound to parent structure |

---

## ⚔️ Static vs Non-Static Inner Class

| Feature                    | 🧱 Non-static Inner Class    | 📦 Static Nested Class |
| -------------------------- | ---------------------------- | ---------------------- |
| Needs outer class instance | ✅ Yes                        | ❌ No                   |
| Access to outer members    | ✅ All (even private)         | ❌ Only static          |
| Memory footprint           | 🔼 Higher                    | 🔽 Lower               |
| Use case                   | Logic tied to outer instance | Utility/helper classes |

---

## 🧼 Best Practices

| ✅ Do's                                           | ❌ Don'ts                                        |
| ------------------------------------------------ | ----------------------------------------------- |
| Use for tightly-coupled logic with outer class   | Don't over-nest inner classes deeply            |
| Prefer `private` inner classes for encapsulation | Avoid inner classes for unrelated functionality |
| Keep inner classes small & focused               | Don’t expose inner class if not needed outside  |

---

## 🏁 Summary Table

| 🔑 Feature                | Non-static Inner Class 🔗      |
| ------------------------- | ------------------------------ |
| Belongs to                | Outer class instance           |
| Access to outer fields    | ✅ Yes (even private)           |
| Requires outer instance   | ✅ Always                       |
| Common use cases          | Event handlers, helper classes |
| Compilation               | `Outer$Inner.class`            |
| Outer reference available | ✅ via `Outer.this`             |

---

