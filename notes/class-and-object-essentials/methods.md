# 🎮 Methods in Java

---
## 🧠 What is a Method in Java?

### 📌 **Definition:**

> A **method** is a block of code that performs a specific task and can be called whenever needed.

✅ Think of it as a **function** inside a **class**.

---

## 🧾 Syntax of a Method

```java
returnType methodName(parameters) {
    // method body
    return value;
}
```

---

## 🔧 Example

```java
class Calculator {
    int add(int a, int b) {
        return a + b;
    }
}
```

---

## 🧩 Types of Methods in Java

| 🔢 Type                 | 🧠 Description                                              | 💡 Example                              |
| ----------------------- | ----------------------------------------------------------- | --------------------------------------- |
| 🧱 Instance Methods     | Belong to object (non-static)                               | `obj.display()`                         |
| 🏢 Static Methods       | Belong to class, called without object                      | `ClassName.method()`                    |
| 📬 Parameterized Method | Accept input arguments                                      | `void greet(String name)`               |
| 🎁 Return Type Method   | Returns a value after execution                             | `int getAge()`                          |
| 🧪 Void Method          | Performs action, doesn’t return value                       | `void printMessage()`                   |
| ♻️ Overloaded Method    | Same name, different parameters (compile-time polymorphism) | `add(int, int)` & `add(double, double)` |

---

## 🧱 1. Instance Method

```java
class Student {
    String name;

    void greet() {
        System.out.println("Hello, " + name);
    }
}
```

```java
Student s = new Student();
s.name = "Aman";
s.greet(); // Output: Hello, Aman
```

---

## 🏢 2. Static Method

```java
class MathUtil {
    static int square(int x) {
        return x * x;
    }
}
```

```java
int result = MathUtil.square(5); // 25
```

---

## 🎯 3. Method with Parameters and Return Type

```java
class Calculator {
    int multiply(int a, int b) {
        return a * b;
    }
}
```

---

## ♻️ 4. Method Overloading

```java
class Calculator {
    int add(int a, int b) {
        return a + b;
    }

    double add(double a, double b) {
        return a + b;
    }
}
```

---

## 🧠 Behind the Scenes: Memory Allocation

| 🔍 Area        | 🧠 What’s Stored                       |
| -------------- | -------------------------------------- |
| 🔢 Stack       | Local variables, method calls (frames) |
| 💾 Heap        | Object instances                       |
| 📦 Method Area | Static methods, static variables       |

---

## 🧪 Example Using All Types

```java
class Employee {
    String name;
    static String company = "Google";

    void setName(String n) { // Instance method
        name = n;
    }

    void display() {
        System.out.println("Name: " + name + ", Company: " + company);
    }

    static void companyPolicy() {
        System.out.println("Company policy: Work 5 days/week");
    }
}
```

```java
Employee e1 = new Employee();
e1.setName("Aman");
e1.display();
Employee.companyPolicy(); // Static method
```

---

## 📌 Best Practices

| ✅ Practice                                            | 💥 Why It Matters                                 |
| ----------------------------------------------------- | ------------------------------------------------- |
| Use **meaningful names**                              | Improves readability (`calculateSalary`)          |
| Keep **methods short**                                | Single Responsibility Principle (SRP)             |
| Follow **camelCase naming**                           | Java convention: `getDetails()`, `printInvoice()` |
| Make **static** if no object state is used            | Saves memory, improves performance                |
| Use **`final`** for methods you don’t want overridden | Inheritance control                               |

---

## 🧭 Summary Diagram

```
         +------------------------+
         |       Method           |
         +------------------------+
         | 🔢 Instance Method      |
         | 🏢 Static Method        |
         | 🎁 Return Type         |
         | 📬 Parameterized       |
         | ♻️ Overloaded Method    |
         +------------------------+
```

---
[🏠 Back to Home](../../README.md)