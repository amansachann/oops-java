# 🐉 Method Overloading

---

## 🧠 What is Method Overloading?

### 📌 **Definition:**

> **Method Overloading** means defining **multiple methods** in the **same class** with the **same name** but **different parameters** (number, type, or order).

---

## 🔧 Why Overload Methods?

| ✅ Use Case                                                   | 🔥 Benefit                                  |
| ------------------------------------------------------------ | ------------------------------------------- |
| Provide **multiple ways to perform an action**               | Flexibility for the caller                  |
| Avoid multiple confusing names like `addInt()`, `addFloat()` | Improves **readability** and **clean code** |
| Reuse method name for similar logic                          | Maintain logical grouping of operations     |

---

## 🔧 Syntax & Rules

```java
class Calculator {
    int add(int a, int b) {
        return a + b;
    }

    double add(double a, double b) {
        return a + b;
    }

    int add(int a, int b, int c) {
        return a + b + c;
    }
}
```

✅ Allowed Overload Variations:

* Different **number** of parameters
* Different **types** of parameters
* Different **order** of parameters

❌ **Return type alone is NOT enough** to overload:

```java
int sum(int a, int b)         ❌ Duplicate  
double sum(int a, int b)      ❌ Not allowed (only return type differs)
```

---

## 🔧 Example: Method Overloading

```java
class Printer {
    void print(String text) {
        System.out.println("Text: " + text);
    }

    void print(int number) {
        System.out.println("Number: " + number);
    }

    void print(String text, int copies) {
        for (int i = 0; i < copies; i++) {
            System.out.println("Print: " + text);
        }
    }
}
```

✅ Usage:

```java
Printer p = new Printer();
p.print("Hello");
p.print(100);
p.print("Report", 3);
```

---

## 🧠 Memory + Resolution

🧠 Java uses **compile-time binding** to determine which method to call based on:

* **Argument count**
* **Argument types**
* **Order of arguments**

So method overloading is also called **Compile-Time Polymorphism** ⚡

---

## 🧪 Real-World Analogy

Think of a restaurant menu:

* `order("Pizza")`
* `order("Burger", 2)`
* `order("Coffee", true)`

All are **orders**, just with different inputs → same concept, multiple ways to call!

---

## ⚔️ Method Overloading vs Method Overriding

| Feature         | 🔄 Overloading           | 🔁 Overriding               |
| --------------- | ------------------------ | --------------------------- |
| Class Level     | Same class               | Parent-child (inheritance)  |
| Binding Time    | Compile time             | Runtime                     |
| Return type     | Can be same or different | Must be same or subtype     |
| Access Modifier | No restriction           | Can widen, but not restrict |

---

## ⚠️ Common Mistakes

| ❌ Mistake                              | 🧠 Why It's Wrong                        |
| -------------------------------------- | ---------------------------------------- |
| Only return type differs               | Java can't differentiate at compile time |
| Ambiguous overloads with wrapper types | `int` vs `Integer`, can confuse JVM      |
| Using same params with different names | Not overload — just renaming variables   |

---

## ✅ Best Practices

| 💡 Tip                              | ✅ Reason                                        |
| ----------------------------------- | ----------------------------------------------- |
| Keep method behavior **related**    | Don't overload unrelated logic                  |
| Use for **optional parameters**     | Simulates default args (Java doesn't have them) |
| Prefer readability over overloading | Don’t confuse future maintainers                |

---

## 💡 Interview Question Example

🧠 **Q:** What is the output?

```java
class Demo {
    void show(int a) {
        System.out.println("int");
    }

    void show(Integer a) {
        System.out.println("Integer");
    }

    void show(long a) {
        System.out.println("long");
    }
}

new Demo().show(10); // 🔥 Output?
```

✅ Output:

```
int
```

➡️ Because **exact match wins** over widening or boxing.

---

## 🏁 Summary Table

| 🔧 Criteria               | ✅ Allowed for Overloading?       |
| ------------------------- | -------------------------------- |
| Different parameter count | ✅ Yes                            |
| Different parameter types | ✅ Yes                            |
| Different return types    | ❌ No (not alone)                 |
| Different parameter order | ✅ Yes                            |
| Different method name     | ❌ No (then it's not overloading) |

---

[🏠 Back to Home](../../README.md)