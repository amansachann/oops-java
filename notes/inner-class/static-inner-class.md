# ⛓️‍💥 Static Nested Class

---

## 🧠 What is a Static Nested Class?

### 📌 Definition:

> A **static nested class** is a nested class that is declared **static** inside another class. It **does not require an instance** of the outer class to be created.

```java
class Outer {
    static class StaticNested {
        void display() {
            System.out.println("Inside static nested class");
        }
    }
}
```

> 💡 **No reference to outer class instance is needed.**

---

## ✅ Key Characteristics

| 🔍 Feature                    | 📌 Description                               |
| ----------------------------- | -------------------------------------------- |
| Belongs to outer class        | ✅ Yes                                        |
| Needs outer class instance?   | ❌ No                                         |
| Can access outer class fields | ❌ Only static members                        |
| Can be `public`, `private`    | ✅ Yes (access modifier allowed)              |
| Useful for                    | Grouping logic, helpers, builders, constants |

---

## 🧪 Example

```java
class Car {
    String name = "Tesla";

    // 🚘 Static nested class
    static class Engine {
        void start() {
            System.out.println("Engine started");
        }
    }
}
```

### ✅ Usage:

```java
public class Test {
    public static void main(String[] args) {
        Car.Engine engine = new Car.Engine();  // ✅ No need to create Car
        engine.start();
    }
}
```

---

## 🔁 Access Rules

| What Static Nested Class Can Access    | Allowed? |
| -------------------------------------- | -------- |
| Static fields/methods of outer class   | ✅ Yes    |
| Instance fields/methods of outer class | ❌ No     |
| Private static members of outer class  | ✅ Yes    |
| Non-static outer class members         | ❌ No     |

```java
class Outer {
    static int x = 10;
    int y = 20;

    static class Inner {
        void print() {
            System.out.println(x); // ✅ OK
            // System.out.println(y); ❌ Compile-time error
        }
    }
}
```

---

## 📦 Real-World Use Case

```java
class Response {
    private int status;

    static class Builder {
        private int status;

        Builder setStatus(int status) {
            this.status = status;
            return this;
        }

        Response build() {
            Response res = new Response();
            res.status = this.status;
            return res;
        }
    }
}
```

✅ Builder pattern — **most common use** of static nested class 💯

---

## 🧱 Static vs Non-Static Nested Class (Inner Class)

| Feature                       | 🧱 Static Nested Class      | 🔄 Non-Static Inner Class    |
| ----------------------------- | --------------------------- | ---------------------------- |
| Requires outer class instance | ❌ No                        | ✅ Yes                        |
| Access outer class members    | ✅ Only static members       | ✅ All members (even private) |
| Memory footprint              | 🔽 Less                     | 🔼 More                      |
| Common use                    | Utility, constants, builder | Event handlers, callbacks    |

---

## 🧼 Best Practices

| ✅ Do's                                           | ❌ Don'ts                                      |
| ------------------------------------------------ | --------------------------------------------- |
| Use for logically grouping static helper classes | Don’t try to access instance members of outer |
| Use in Builder, Factory, or constant holder      | Don’t overuse — keep it clean and readable    |
| Make class `private static` if used internally   | Avoid nesting too deeply                      |

---

## 🏁 Summary Table

| 📌 Feature              | Static Nested Class 📦           |
| ----------------------- | -------------------------------- |
| Nested inside           | Outer class                      |
| Requires outer instance | ❌ No                             |
| Can access              | ✅ Static members of outer class  |
| Common use cases        | Builder pattern, helper, utils   |
| Visibility              | Can be `private`, `public`, etc. |
| JVM compiled file       | `Outer$Inner.class`              |

---
[🏠 Back to Home](../../README.md)