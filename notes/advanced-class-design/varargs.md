# 📨 Varargs(...)

---

## 🧠 What is Varargs?

> **Varargs** = Java ka “flexible guest list” 🧑‍🤝‍🧑 — kitne bhi aayein, sab welcome! 😎

### 📌 Definition:

> **Varargs (variable arguments)** allow a method to accept **zero or more arguments** of a specified type.
> Introduced in **Java 5** for simplifying method calls with dynamic number of parameters.

---

## ✅ Syntax

```java
returnType methodName(datatype... variableName)
```

### Example:

```java
public void printNames(String... names) {
    for (String name : names) {
        System.out.println(name);
    }
}
```

✅ Call with any number of arguments:

```java
printNames("Aman", "Raj", "Karan");
printNames(); // also valid!
```

---

## 🧪 Behind the Scenes (Internally)

* Varargs is just **syntactic sugar**.
* Java treats it as an **array parameter**.

```java
public void printNames(String... names);
// is same as:
public void printNames(String[] names);
```

---

## 🔒 Rules of Varargs

| ✅ Rule                     | 📌 Description                                   |
| -------------------------- | ------------------------------------------------ |
| Only one varargs in method | Can’t use multiple varargs in same method        |
| Must be the last parameter | Varargs must come **after all fixed parameters** |
| Can accept zero arguments  | Safe to call with 0 arguments                    |

```java
// ✅ Valid
void log(String level, String... messages);

// ❌ Invalid
void wrong(String... msgs, int code); // Compile error
```

---

## 🎯 Real-Life Example: Sum Calculator

```java
public int sum(int... numbers) {
    int total = 0;
    for (int num : numbers) {
        total += num;
    }
    return total;
}

sum();               // Output: 0
sum(1, 2, 3);        // Output: 6
sum(10, 20, 30, 40); // Output: 100
```

---

## 🧱 Combining with Fixed Params

```java
public void greet(String greeting, String... names) {
    for (String name : names) {
        System.out.println(greeting + ", " + name);
    }
}

greet("Hello", "Aman", "Karan"); // ✅
```

---

## 📦 Use Cases

| 🔥 Scenario                  | ✅ Why Varargs?                        |
| ---------------------------- | ------------------------------------- |
| Logging frameworks           | Variable-length messages              |
| SQL query builders           | Variable WHERE conditions             |
| Custom print/debug utilities | Flexible argument list                |
| Aggregator functions         | Like `sum`, `multiply`, `joinStrings` |

---

## 🧼 Best Practices

| ✅ Do’s                                    | ❌ Don’ts                                            |
| ----------------------------------------- | --------------------------------------------------- |
| Use for truly optional/multiple arguments | Don’t overuse if fixed parameters are enough        |
| Combine with fixed params for clarity     | Don’t put varargs in the middle of parameter list   |
| Inside method, treat like an array        | Don’t assume at least 1 value will always be passed |

---

## 🏁 Summary Table

| 📌 Feature              | 🔥 Varargs (`...`)                     |
| ----------------------- | -------------------------------------- |
| Introduced in           | Java 5                                 |
| Purpose                 | Accept zero or more values dynamically |
| Internally treated as   | Array                                  |
| Position in parameter   | Must be last                           |
| Allowed with overloads? | ✅ Yes                                  |
| Only one per method?    | ✅ Yes                                  |

---
[🏠 Back to Home](../..)