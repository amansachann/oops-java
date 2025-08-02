# ✋ Interface Static Methods

---

## 🧠 What is a Static Method in an Interface?

### 📌 Definition:

> A **static method** in an interface is a method that belongs to the **interface itself**, **not** to the objects or implementing classes.

✅ Static methods are called using `InterfaceName.methodName()`  
❌ They **cannot be overridden** by implementing classes.

---

## 🔧 Syntax

```java
interface MathUtils {
    static int square(int x) {
        return x * x;
    }
}
```

✅ Usage:

```java
int result = MathUtils.square(5);
System.out.println(result); // 25
```

---

## 🎯 Why Use Static Methods in Interface?

| ✅ Benefit                        | 📘 Explanation                                |
| -------------------------------- | --------------------------------------------- |
| Utility/Helper functions         | Like utility classes (`Collections`, etc.)    |
| No need to expose through object | Called directly via interface                 |
| Organize logic cleanly           | Interface = self-contained behavior set       |
| Framework internal logic         | Used in Stream API, Predicate, Function, etc. |

---

## 🛠️ Real Example

```java
interface StringUtils {
    static boolean isNullOrEmpty(String str) {
        return str == null || str.isEmpty();
    }
}
```

✅ Usage:

```java
System.out.println(StringUtils.isNullOrEmpty("")); // true
System.out.println(StringUtils.isNullOrEmpty("ChatGPT")); // false
```

---

## ❌ Static Methods ≠ Default Methods

| Feature             | `static` Method             | `default` Method             |
| ------------------- | --------------------------- | ---------------------------- |
| Called via          | Interface name              | Object of implementing class |
| Overridable?        | ❌ No                        | ✅ Yes                        |
| Purpose             | Utility/helper logic        | Default behavior for classes |
| Access to instance? | ❌ No (`this` not available) | ✅ Yes                        |

---

## 🧪 Class Cannot Override Interface Static Method

```java
interface A {
    static void greet() {
        System.out.println("Hello from A");
    }
}

class B implements A {
    // This will NOT override greet()
    static void greet() {
        System.out.println("Hello from B");
    }
}
```

✅ Usage:

```java
A.greet(); // Hello from A
B.greet(); // Hello from B
```

> **Note:** Both are separate static methods — no override occurs ❌

---

## ⚠️ Rules of Interface Static Methods

| ✅ Rule                            | 🚫 Restriction                         |
| --------------------------------- | -------------------------------------- |
| Must have body                    | Abstract static ❌ not allowed          |
| Called using interface name only  | `obj.staticMethod()` ❌                 |
| Cannot be inherited or overridden | Static methods are **not polymorphic** |
| No `this` or instance access      | Works just like static method in class |

---

## 🧪 Interface with Static + Default + Abstract

```java
interface Service {
    void execute(); // abstract

    default void log() {
        System.out.println("Default logging...");
    }

    static void helper() {
        System.out.println("Static utility from Service");
    }
}
```

---

## 🏁 Summary Table

| Feature          | Interface Static Method   |
| ---------------- | ------------------------- |
| Available since  | Java 8                    |
| Has method body? | ✅ Yes                     |
| Overridable?     | ❌ No                      |
| Called using     | `InterfaceName.method()`  |
| Use case         | Utilities, helper methods |
| Object required? | ❌ Not needed              |

---

## 🧱 Real-World Use: Java Streams

```java
List<String> names = Arrays.asList("Aman", "Bhavya");
Stream<String> s = names.stream(); // ✅ Called via interface
```

➡️ `stream()` internally uses static methods from the `Stream` interface.

---

[🏠 Back to Home](../..)