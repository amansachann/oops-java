# 🕹️ strictfp

---

## 🧠 What is `strictfp`?

> `strictfp` = Java ka “precision ka promise” 📏 — jitne mein divide karein, har jagah wahi milein! 😎

### 📌 Definition:

> `strictfp` (Strict Floating Point) is a Java keyword that **forces floating-point calculations (float, double)** to follow the **IEEE 754 standard** strictly.

---

### ✅ Syntax Usage:

```java
strictfp class MyCalculator { ... }
strictfp interface MathOps { ... }
strictfp methodName() { ... }
```

---

## 🔬 Why Use `strictfp`?

By default, **JVMs on different platforms** may handle floating-point calculations slightly differently (like extra precision on x86).
This can lead to **inconsistent results**.

### 🚫 Problem:

```java
double result = a / b;  // Different output on different CPUs!
```

### ✅ Solution:

```java
strictfp class Calculator {
    double compute(double a, double b) {
        return a / b; // Now guaranteed to follow IEEE 754 exactly
    }
}
```

---

## 📦 Where Can You Use `strictfp`?

| ✔️ Can Apply On | 🚫 Cannot Apply On |
| --------------- | ------------------ |
| Class           | Variable           |
| Interface       | Constructor        |
| Method          | Block (`{}` scope) |

---

## ⚙️ Example

```java
strictfp class PrecisionMath {
    public static void main(String[] args) {
        double a = 10.0 / 3.0;
        System.out.println(a);  // Output will be consistent across platforms
    }
}
```

---

## 🧪 Without strictfp (Platform Dependent)

```java
class NoStrict {
    public static void main(String[] args) {
        double result = 10.0 / 3.0;
        System.out.println(result); // May differ in 80-bit register CPUs
    }
}
```

---

## 🧠 IEEE 754 Standard (in short)

| Type   | Precision | Description                     |
| ------ | --------- | ------------------------------- |
| float  | 32-bit    | Single-precision floating point |
| double | 64-bit    | Double-precision floating point |

`strictfp` ensures Java **does not use 80-bit extended precision**, even if CPU supports it.

---

## 🧼 Best Practices

| ✅ Do’s                                          | ❌ Don’ts                                           |
| ----------------------------------------------- | -------------------------------------------------- |
| Use `strictfp` for math libraries               | Don’t use if platform-specific performance matters |
| Use for **cross-platform reproducibility**      | Avoid unnecessary use in non-float operations      |
| Use when comparing output with external systems | Don’t confuse it with rounding or formatting       |

---

## 🏁 Summary Table

| 📌 Feature     | `strictfp` Keyword ⚖️                     |
| -------------- | ----------------------------------------- |
| Applies to     | Class, Interface, Method                  |
| Not allowed on | Variable, Constructor, Code Block         |
| Controls       | Floating-point precision                  |
| Follows        | IEEE 754 standard                         |
| Use case       | Cross-platform deterministic calculations |

---
[🏠 Back to Home](../..)