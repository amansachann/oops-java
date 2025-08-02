# 🤞 Immutable Clasess

---

## 🧠 What Is an Immutable Class?

### 📌 Definition:

> An **immutable class** is a class whose **object state cannot be modified** after it is created.

✅ `String` class in Java is the most popular example of an **immutable class**.

---

## 🎯 Why Make a Class Immutable?

| ✅ Benefit               | 📘 Explanation                             |
| ----------------------- | ------------------------------------------ |
| 🔐 Thread-safe          | No sync issues because state never changes |
| 🧠 Predictable behavior | Once constructed, state is guaranteed      |
| ♻️ Hash-safe            | Great for `Map` keys & `Set` members       |
| 🔄 Easy caching         | Safe to reuse without side-effects         |
| ✔️ Cleaner design       | Promotes functional-style programming      |

---

## ✅ Steps to Make an Immutable Class

| 🔧 Rule                                  | ✅ Example                             |
| ---------------------------------------- | ------------------------------------- |
| 1. Make class `final`                    | So it can't be extended or modified   |
| 2. Make fields `private final`           | To prevent changes after construction |
| 3. No setter methods                     | Only getters (read-only)              |
| 4. Initialize fields via constructor     | All values set at object creation     |
| 5. Return deep copies for mutable fields | Defensive copies for safety           |

---

## 📦 Example: Immutable `Student` Class

```java
public final class Student {
    private final String name;
    private final int age;

    public Student(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }
}
```

✅ Usage:

```java
Student s = new Student("Aman", 22);
// s.age = 30; ❌ Not allowed
// s.setAge(30); ❌ No setter exists
```

---

## 🛡️ Defensive Copy for Mutable Fields

If you have mutable objects like `Date`, `List`, `Map`, etc., return a **copy**:

```java
public final class Order {
    private final Date orderDate;

    public Order(Date date) {
        this.orderDate = new Date(date.getTime()); // 🔐 Defensive copy
    }

    public Date getOrderDate() {
        return new Date(orderDate.getTime()); // 🔐 Return copy, not original
    }
}
```

---

## 🧠 How is `String` Immutable?

```java
String s1 = "hello";
String s2 = s1.toUpperCase();

System.out.println(s1); // hello
System.out.println(s2); // HELLO
```

➡️ `toUpperCase()` returns a **new String** — original `s1` not modified ✅

---

## 🚫 Common Mistakes

| ❌ Mistake                        | ⚠️ Why it's a Problem        |
| -------------------------------- | ---------------------------- |
| Exposing mutable fields directly | Can be changed outside class |
| Adding setter methods            | Breaks immutability          |
| Forgetting defensive copies      | Leaks internal state         |

---

## 🏁 Summary Table

| Feature              | Value                 |
| -------------------- | --------------------- |
| Class modifier       | `final`               |
| Fields               | `private final`       |
| Setter methods       | ❌ Not allowed         |
| Field initialization | ✅ In constructor      |
| Mutable fields       | Defensive copies used |
| Thread-safe          | ✅ Yes                 |

---
[🏠 Back to Home](../..)