# ⛔ Final Variables

---

## 🧠 What is a Final Variable?

### 📌 Definition:

> A **`final` variable** is a variable whose **value cannot be changed** once it is assigned.
> It becomes a **constant reference** after initialization.

---

## ✅ Syntax

```java
final int MAX_USERS = 100;
```

❗ Attempting to reassign:

```java
MAX_USERS = 200;  // ❌ Compile-time error
```

---

## 📦 Types of Final Variables

| 🔢 Type                 | 📌 Description                                                    |
| ----------------------- | ----------------------------------------------------------------- |
| Final Local Variable    | Declared inside method/block                                      |
| Final Instance Variable | Non-static member (must be initialized via constructor)           |
| Final Static Variable   | Shared across all instances (must be initialized in static block) |

---

## 🧪 Examples

### 🔹 Final Local Variable

```java
void calculate() {
    final int rate = 10;
    System.out.println(rate);
    // rate = 20; ❌ Not allowed
}
```

---

### 🔹 Final Instance Variable

```java
class User {
    final String name;

    User(String name) {
        this.name = name;  // ✅ Must assign here
    }
}
```

---

### 🔹 Final Static Variable

```java
class Config {
    static final int MAX_CONNECTIONS;

    static {
        MAX_CONNECTIONS = 50; // ✅ Must assign in static block
    }
}
```

---

## 🧠 Final Reference Variables (Objects)

```java
final List<String> names = new ArrayList<>();
names.add("Aman");  // ✅ Allowed (modifying contents)
names = new ArrayList<>();  // ❌ Not allowed (changing reference)
```

> 📌 `final` stops reassignment of the **reference**, not modification of the **object itself**

---

## 📛 What if You Don't Initialize?

| Type                    | Result                                                 |
| ----------------------- | ------------------------------------------------------ |
| Final Local Variable    | ❌ Compilation Error if not initialized                 |
| Final Instance Variable | ✅ OK if initialized in **all constructors**            |
| Final Static Variable   | ✅ OK if initialized in **static block** or declaration |

---

## ⚔️ Final vs Const (C++ Style)

| Feature    | `final` in Java                     | `const` in C++               |
| ---------- | ----------------------------------- | ---------------------------- |
| Immutable? | ✅ After assignment                  | ✅ Constant value             |
| Primitive  | ✅ Fully immutable                   | ✅ Fully immutable            |
| Object ref | 🔐 Reference fixed, content mutable | 🔐 Reference & content fixed |

---

## 🧼 Best Practices

| ✅ Do’s                                         | ❌ Don’ts                                       |
| ---------------------------------------------- | ---------------------------------------------- |
| Use `final` for constants                      | Don’t leave final fields uninitialized         |
| Prefer naming constants in UPPER\_SNAKE\_CASE  | Don’t confuse with immutability of object data |
| Combine with `static` for class-wide constants | Don’t overuse where mutability is needed       |

---

## 🔐 Constant Convention in Java

```java
public class Constants {
    public static final double PI = 3.14159;
}
```

✅ Use: `Constants.PI`

---

## 🏁 Summary Table

| 📌 Feature           | Final Variable 💎                        |
| -------------------- | ---------------------------------------- |
| Syntax               | `final int x = 10;`                      |
| Value re-assignable? | ❌ No                                     |
| Used with objects?   | ✅ Reference is final, content is mutable |
| Must be initialized? | ✅ Yes (at declaration or in constructor) |
| Static final combo?  | ✅ For constants (e.g. `MAX_LIMIT`)       |

---
[🏠 Back to Home](../..)