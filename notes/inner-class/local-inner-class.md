# 🏡 Local Inner Class

---

## 🧠 What is a Local Inner Class?

### 📌 Definition:

> A **Local Inner Class** is a class defined **inside a method, constructor, or block** of an outer class.
> Yeh class **sirf us method ke scope mein accessible** hoti hai — matlab pure encapsulation! 🔐

---

## ✅ Syntax

```java
class Outer {
    void outerMethod() {
        // 👇 Local Inner Class inside a method
        class Local {
            void msg() {
                System.out.println("Inside Local Inner Class");
            }
        }

        Local local = new Local();
        local.msg();
    }
}
```

---

### 🧪 Usage:

```java
public class Test {
    public static void main(String[] args) {
        Outer outer = new Outer();
        outer.outerMethod();  // ✅ Output: Inside Local Inner Class
    }
}
```

---

## 🔍 Key Features

| 🔍 Feature                       | ✅ Description                                       |
| -------------------------------- | --------------------------------------------------- |
| Defined inside                   | A method, constructor, or block                     |
| Scope                            | Only within the block/method where defined          |
| Access outer class members?      | ✅ Yes (including private)                           |
| Access method's local variables? | ✅ Only if they are **final or effectively final**   |
| Modifiers allowed                | ❌ Cannot use access modifiers (`public`, `private`) |
| Compilation                      | Named like `Outer$1Local.class` internally          |

---

## 🧪 Example with Local Variable

```java
class Outer {
    void process() {
        int x = 100; // effectively final

        class Local {
            void display() {
                System.out.println("x = " + x); // ✅ allowed
            }
        }

        Local local = new Local();
        local.display();
    }
}
```

> ❗ If `x` is modified after declaration, it will throw **compilation error** because it's no longer "effectively final".

---

## 🧾 Real-Life Use Case

```java
class Button {
    void setOnClickListener() {
        class OnClickHandler {
            void onClick() {
                System.out.println("Button clicked!");
            }
        }

        new OnClickHandler().onClick();
    }
}
```

✅ Useful in UI logic, encapsulated callbacks, short-lived event handling

---

## 🧼 Best Practices

| ✅ Do's                                               | ❌ Don'ts                                         |
| ---------------------------------------------------- | ------------------------------------------------ |
| Use for **short-lived helper logic**                 | Don’t over-complicate with too many inner levels |
| Keep class small & focused                           | Avoid modifying captured local variables         |
| Leverage to group logic that should not escape scope | Don’t return or expose Local Inner Class outside |

---

## ⚖️ Local Inner Class vs Other Inner Classes

| Feature               | 🧱 Local Inner Class | 🔗 Non-static Inner | 📦 Static Nested |
| --------------------- | -------------------- | ------------------- | ---------------- |
| Defined inside        | Method/block         | Class               | Class            |
| Needs outer instance  | ✅ Yes                | ✅ Yes               | ❌ No             |
| Can access local vars | ✅ Yes (final only)   | ❌ No                | ❌ No             |
| Scope                 | Method-local         | Outer class-wide    | Outer class-wide |
| Use case              | Short callbacks      | Logic tied to outer | Utility grouping |

---

## 🏁 Summary Table

| 📌 Feature                 | Local Inner Class 💡                         |
| -------------------------- | -------------------------------------------- |
| Scope                      | Inside method/block                          |
| Access to outer class      | ✅ Yes                                        |
| Access to method variables | ✅ If final/effectively final                 |
| Modifiers allowed?         | ❌ None (`public`, `private` not allowed)     |
| Common use cases           | Event listeners, helper logic, tight scoping |
| Compilation                | `Outer$1Local.class`                         |

---

[🏠 Back to Home](../../README.md)