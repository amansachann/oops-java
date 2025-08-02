# ⚡ Lambda Expression (Java 8)

---

## 🧠 What is a Lambda Expression?

### 📌 Definition:

> A **lambda expression** is a **short block of code** that takes in **parameters** and returns a **value**.  
> Lambda can be used **wherever a functional interface is expected**.

✅ Syntax:

```java
(parameters) -> expression
or
(parameters) -> { statements }
```

---

## 🎯 Functional Interface?

> A **Functional Interface** is an interface with **only one abstract method**.

✅ Example:

```java
@FunctionalInterface
interface Greeting {
    void sayHello(); // one abstract method
}
```

---

## 🧪 Basic Lambda Example

```java
Greeting g = () -> System.out.println("Hello, Aman! 👋");
g.sayHello();
```

✅ Output: `Hello, Aman! 👋`

---

## 📦 Syntax Variants

| 🧪 Syntax                                 | 💬 Meaning                       |
| ----------------------------------------- | -------------------------------- |
| `() -> System.out.println("Hi")`          | No parameters                    |
| `(a, b) -> a + b`                         | Multiple params, expression body |
| `(name) -> { System.out.println(name); }` | Single param, code block body    |

---

## ✅ Lambda with Parameters

```java
interface Calculator {
    int operate(int a, int b);
}

public class Test {
    public static void main(String[] args) {
        Calculator add = (a, b) -> a + b;
        Calculator mul = (a, b) -> a * b;

        System.out.println(add.operate(5, 3)); // 8
        System.out.println(mul.operate(5, 3)); // 15
    }
}
```

---

## 🧠 Why Use Lambdas?

| 🔥 Benefit               | ✅ Description                            |
| ------------------------ | ---------------------------------------- |
| Concise Code             | Removes boilerplate of anonymous classes |
| Functional Programming   | Enables passing behavior as data         |
| Improved Readability     | More expressive and declarative code     |
| Easy to use with Streams | Backbone of Java 8 Stream API            |

---

## 🧪 Lambda in Thread Example

```java
new Thread(() -> System.out.println("Thread running 🧵")).start();
```

✅ Equivalent to anonymous class but more concise!

---

## 🧪 Lambda with Collections

```java
List<String> names = Arrays.asList("Aman", "Raj", "Karan");

names.forEach(name -> System.out.println(name));
```

✅ Java 8 enhanced APIs support lambdas naturally.

---

## 🧪 Lambda with Comparator

```java
List<String> names = Arrays.asList("Banana", "Apple", "Mango");

names.sort((a, b) -> a.compareTo(b));
System.out.println(names);
```

---

## 🧪 Return Statement in Lambda

```java
Calculator sub = (a, b) -> {
    System.out.println("Subtracting...");
    return a - b;
};
System.out.println(sub.operate(10, 5)); // Output: 5
```

---

## 🧼 Best Practices

| ✅ Do’s                                     | ❌ Don’ts                                    |
| ------------------------------------------ | ------------------------------------------- |
| Use for short, expressive logic            | Don’t use for complex multi-line logic      |
| Leverage with Streams, functional APIs     | Avoid nesting lambdas inside lambdas deeply |
| Keep it pure (no side effects if possible) | Don’t modify external mutable state inside  |

---

## 🏁 Summary Table

| 📌 Feature    | Lambda Expression ⚡                |
| ------------- | ---------------------------------- |
| Introduced in | Java 8                             |
| Target        | Functional Interface               |
| Syntax        | `(params) -> expression`           |
| Used in       | Thread, Collections, Streams, etc. |
| Benefits      | Shorter, cleaner, functional code  |
| Works with    | Only 1-abstract-method interfaces  |

---

## 🧪 Functional Interfaces Java 8 provides

| Interface       | Signature           | Use case            |
| --------------- | ------------------- | ------------------- |
| `Runnable`      | `void run()`        | Threads             |
| `Callable<T>`   | `T call()`          | Concurrent tasks    |
| `Comparator<T>` | `int compare(T, T)` | Sorting             |
| `Consumer<T>`   | `void accept(T)`    | Streams             |
| `Function<T,R>` | `R apply(T)`        | Data transformation |
| `Predicate<T>`  | `boolean test(T)`   | Filtering           |
| `Supplier<T>`   | `T get()`           | Lazy initialization |

---

[🏠 Back to Home](../../README.md)