# 🎏 Overriding toString()

---

## 🧠 What is `toString()` in Java?

### 📌 **Definition:**

> `toString()` is a method of the **Object class** in Java, used to return a **string representation of the object**.

### ⚠️ Default behavior:

```java
public class Student {}

Student s = new Student();
System.out.println(s);
```

✅ Output:

```
Student@7a81197d  // ClassName@HexHashCode ❌
```

---

## 🎯 Why Override `toString()`?

| ✅ Reason                | 💬 Description                                       |
| ----------------------- | ---------------------------------------------------- |
| Readable Output         | Convert object data into a **meaningful string**     |
| Debugging made easier   | Easy to print object states                          |
| Logging                 | Better logs with object detail                       |
| Framework compatibility | Many frameworks (e.g., Hibernate, Spring) rely on it |

---

## 🔧 Syntax: Overriding `toString()`

```java
class Student {
    String name;
    int age;

    Student(String name, int age) {
        this.name = name;
        this.age = age;
    }

    @Override
    public String toString() {
        return "Student{name='" + name + "', age=" + age + "}";
    }
}
```

✅ Usage:

```java
Student s = new Student("Aman", 22);
System.out.println(s);
```

✅ Output:

```
Student{name='Aman', age=22}
```

---

## 🧠 Points to Remember

| 🔍 Feature                 | ✅ Best Practice                       |
| -------------------------- | ------------------------------------- |
| Use `@Override` annotation | Ensures method is actually overridden |
| Return meaningful string   | Show important fields                 |
| Don’t return null          | Avoid NullPointerException in logging |

---

## 📦 toString() in JavaBeans

```java
public class Product {
    private String name;
    private double price;

    // constructor, getters, setters...

    @Override
    public String toString() {
        return "Product{name='" + name + "', price=" + price + "}";
    }
}
```

➡️ Useful in REST APIs, logs, debuggers, etc.

---

## 🔍 Bonus: IntelliJ / IDE Tip

👉 Most IDEs can auto-generate `toString()` method:

* IntelliJ:
  `Right-click → Generate → toString()`

* Eclipse:
  `Source → Generate toString()`

---

## ⚠️ Common Mistakes

| ❌ Mistake                 | 💥 Why it's wrong                        |
| ------------------------- | ---------------------------------------- |
| Not overriding            | Gives meaningless output                 |
| Returning fixed string    | Doesn’t reflect actual data              |
| Not including `@Override` | Could be a typo, won't override properly |
| Including sensitive info  | ⚠️ Avoid printing passwords/tokens       |

---

## 🏁 Summary Table

| Feature        | Description                  |
| -------------- | ---------------------------- |
| Method Name    | `toString()`                 |
| Belongs to     | `java.lang.Object`           |
| Return Type    | `String`                     |
| Default Output | `ClassName@Hashcode`         |
| Custom Output  | ✅ By overriding              |
| Common Usage   | Debugging, Logging, Printing |

---

[🏠 Back to Home](../../README.md)