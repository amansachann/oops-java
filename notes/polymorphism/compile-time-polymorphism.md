# 🧑‍💻 Compile-Time Polymorphism 

---

## 🧠 What is Compile-Time Polymorphism?

### 📌 Definition:

> **Compile-Time Polymorphism** means the method call is **resolved by the compiler at compile time** based on the **method signature** (method name + parameters).

✅ Also called: **Method Overloading**

---

## 🧬 Real-World Example

🛒 Suppose ek **payment** method hai:

* `pay(int amount)`
* `pay(int amount, String method)`

📞 Depending on how you call, different version run hota hai:

```java
Payment p = new Payment();
p.pay(500);                    // Debit
p.pay(500, "Credit Card");     // Credit
```

---

## 🔧 Method Overloading = Compile-Time Polymorphism

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

✅ Usage:

```java
Calculator c = new Calculator();
System.out.println(c.add(2, 3));          // int + int
System.out.println(c.add(2.5, 4.1));      // double + double
System.out.println(c.add(1, 2, 3));       // 3 int params
```

---

## 🧠 Why Use Compile-Time Polymorphism?

| ✅ Advantage        | 📘 Description                              |
| ------------------ | ------------------------------------------- |
| Code readability   | Same method name, different behavior        |
| Cleaner API design | One method name for similar logic           |
| Flexibility        | Accepts different number/types of inputs    |
| Performance        | Resolved at compile time → Faster execution |

---

## ⚙️ Overloading Can Be Based On:

| Type                | Example                                  |
| ------------------- | ---------------------------------------- |
| Number of arguments | `sum(int a, int b)` vs `sum(int a)`      |
| Type of arguments   | `sum(int, int)` vs `sum(double, double)` |
| Order of arguments  | `sum(int, float)` vs `sum(float, int)`   |

---

## ❌ What Is *Not* Considered Overloading?

| Invalid Overloading Attempt   | Why? ❌                                          |
| ----------------------------- | ----------------------------------------------- |
| Only changing return type     | Not allowed — return type not part of signature |
| Changing only parameter names | Parameter names don’t matter                    |

```java
int sum(int a, int b);
double sum(int x, int y); // ❌ Compile error
```

---

## 🧪 Static Methods Can Also Be Overloaded

```java
class Printer {
    static void print(String s) {
        System.out.println("String: " + s);
    }

    static void print(int i) {
        System.out.println("Int: " + i);
    }
}
```

✅ Usage:

```java
Printer.print("Hello");
Printer.print(42);
```

---

## 🧠 Is Constructor Overloading Polymorphism?

✅ YES! Constructor overloading is **compile-time polymorphism** too:

```java
class Person {
    Person(String name) { }
    Person(String name, int age) { }
}
```

---

## 🏁 Summary Table

| Feature                 | Value                              |
| ----------------------- | ---------------------------------- |
| Type                    | Compile-Time Polymorphism          |
| Also Known As           | Method Overloading                 |
| Resolved When?          | Compile time                       |
| Basis                   | Number, type, or order of params   |
| Return type considered? | ❌ No                               |
| Constructor support?    | ✅ Yes                              |
| Runtime flexibility?    | ❌ No (that's runtime polymorphism) |

---
[🏠 Back to Home](../..)
