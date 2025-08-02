# 🐣 Anonymous Classes

---

## 🧠 What is an Anonymous Class?

### 📌 Definition:

> An **anonymous class** is an **unnamed class** that is **declared and instantiated at the same time**, typically used to provide **method implementation on the fly** for interfaces, abstract classes, or concrete classes.

---

## ✅ Syntax

```java
InterfaceType obj = new InterfaceType() {
    @Override
    public void methodName() {
        // implementation
    }
};
```

---

## 🧪 Example with Interface

```java
interface Greeting {
    void sayHello();
}

public class Test {
    public static void main(String[] args) {
        Greeting greet = new Greeting() {
            @Override
            public void sayHello() {
                System.out.println("Hello, Aman! 👋");
            }
        };

        greet.sayHello();  // ✅ Output: Hello, Aman! 👋
    }
}
```

---

## 🧪 Example with Abstract Class

```java
abstract class Animal {
    abstract void makeSound();
}

public class Test {
    public static void main(String[] args) {
        Animal dog = new Animal() {
            @Override
            void makeSound() {
                System.out.println("Woof 🐶");
            }
        };

        dog.makeSound();  // ✅ Output: Woof 🐶
    }
}
```

---

## 🧪 Example with Concrete Class

```java
class Printer {
    void print() {
        System.out.println("Printing...");
    }
}

public class Test {
    public static void main(String[] args) {
        Printer p = new Printer() {
            @Override
            void print() {
                System.out.println("Custom print logic 🖨️");
            }
        };

        p.print();  // ✅ Output: Custom print logic 🖨️
    }
}
```

---

## 📦 Real-World Use Case (e.g. GUI, Thread)

```java
new Thread(new Runnable() {
    @Override
    public void run() {
        System.out.println("Thread running 🧵");
    }
}).start();
```

✅ Commonly used in:

* Listeners (Swing, JavaFX)
* Threads
* Callbacks
* Strategy Pattern implementations

---

## ✅ Key Features

| 🔍 Feature               | ⚡ Anonymous Class               |
| ------------------------ | ------------------------------- |
| Named?                   | ❌ No                            |
| Can extend class?        | ✅ Yes                           |
| Can implement interface? | ✅ Yes                           |
| Access outer class?      | ✅ Yes                           |
| Access local vars?       | ✅ If final or effectively final |
| Use case                 | Short-term, one-time-use logic  |

---

## ⚖️ Anonymous vs Local Inner vs Lambda

| Feature                   | 🧩 Anonymous Class | 📦 Local Inner Class | 🧠 Lambda (Java 8+)     |
| ------------------------- | ------------------ | -------------------- | ----------------------- |
| Named?                    | ❌ No               | ✅ Yes                | ❌ No                    |
| Can extend abstract class | ✅ Yes              | ✅ Yes                | ❌ No                    |
| Can implement interface   | ✅ Yes              | ✅ Yes                | ✅ Yes (Functional only) |
| Syntax                    | Verbose            | Medium               | Concise                 |
| Scope                     | Block-local        | Method-local         | Block-local             |
| Java Version              | 1.1+               | 1.1+                 | 8+                      |

---

## 🧼 Best Practices

| ✅ Do's                                      | ❌ Don'ts                                     |
| ------------------------------------------- | -------------------------------------------- |
| Use for short, one-off implementations      | Don’t use for large/complex logic            |
| Use with functional interfaces (pre-Java 8) | Don’t return or expose it as class reference |
| Prefer Lambdas for functional interfaces    | Don’t try to add constructors (not allowed)  |

---

## 🏁 Summary Table

| 📌 Feature          | Anonymous Class ⚡                    |
| ------------------- | ------------------------------------ |
| Purpose             | One-time override of class/interface |
| Named?              | ❌ No                                 |
| Instantiation       | At the time of declaration           |
| Common use cases    | Event handlers, threads, callbacks   |
| Access outer class? | ✅ Yes                                |
| Access local vars?  | ✅ Final/effectively final only       |

---

[🏠 Back to Home](../../README.md)