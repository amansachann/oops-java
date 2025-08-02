# = equals() Method

---

## 🧠 What is `equals()` in Java?

### 📌 Definition:

> The `equals()` method is used to **compare the contents (state)** of two objects, **not their memory addresses**.

👨‍🏫 Defined in:

```java
public boolean equals(Object obj)  // in java.lang.Object
```

🧪 Default behavior:

* Uses **==** → compares **reference/memory** (not field values)

```java
Student s1 = new Student();
Student s2 = new Student();
System.out.println(s1.equals(s2));  // ❌ false (different references)
```

---

## ✅ Why Override `equals()`?

> To check **meaningful equality** → same `id`, `name`, etc., not just if they point to same object.

---

## 🧑‍🎓 Example: Custom `equals()` Implementation

```java
class Student {
    int id;
    String name;

    Student(int id, String name) {
        this.id = id;
        this.name = name;
    }

    @Override
    public boolean equals(Object obj) {
        if (this == obj) return true; // same reference
        if (obj == null || getClass() != obj.getClass()) return false;

        Student s = (Student) obj;
        return this.id == s.id && this.name.equals(s.name);
    }
}
```

```java
Student s1 = new Student(1, "Aman");
Student s2 = new Student(1, "Aman");

System.out.println(s1.equals(s2));  // ✅ true (same content)
```

---

## 📌 equals() vs ==

| Feature            | `==` (Double Equals) | `equals()`                               |
| ------------------ | -------------------- | ---------------------------------------- |
| Compares           | Memory reference     | Object contents (logical equality)       |
| Type               | Operator             | Method                                   |
| Can be overridden? | ❌ No                 | ✅ Yes                                    |
| Default behavior   | Same reference check | Same reference check (unless overridden) |

---

## 🔐 With String (Already Overridden)

```java
String s1 = new String("hello");
String s2 = new String("hello");

System.out.println(s1 == s2);       // ❌ false (different objects)
System.out.println(s1.equals(s2));  // ✅ true (same characters)
```

---

## 🧱 equals() + hashCode() Combo

> **Whenever you override `equals()`, override `hashCode()` too**, especially when using HashMap/Set

```java
@Override
public int hashCode() {
    return Objects.hash(id, name);
}
```

✅ Ensures **contract is maintained** in hash-based collections

---

## 🔍 equals() Best Practices

| ✅ Do's                                   | ❌ Don'ts                                   |
| ---------------------------------------- | ------------------------------------------ |
| Use `@Override`                          | Don’t forget to also override `hashCode()` |
| Check for `null` and class compatibility | Don’t cast blindly                         |
| Compare meaningful fields only           | Don’t include transient/debug-only fields  |
| Use `Objects.equals()` for null safety   | Avoid direct string/int comparisons        |

---

## 🧩 Utility with `Objects.equals()`

```java
@Override
public boolean equals(Object obj) {
    if (this == obj) return true;
    if (!(obj instanceof Student s)) return false;
    return id == s.id && Objects.equals(name, s.name);
}
```

✅ Cleaner and null-safe

---

## 🧪 Real-World Analogy

> `==` ➤ "Are these **exact same smartphones**?"
> `equals()` ➤ "Do these phones have **same model, color, and specs**?"

---

## 🏁 Summary Table

| Feature            | `equals()` Method 📦                  |
| ------------------ | ------------------------------------- |
| Defined in         | `Object` class                        |
| Default behavior   | Reference check (like `==`)           |
| Can be overridden? | ✅ Yes                                 |
| Used for           | Logical comparison (content-based)    |
| Must pair with     | `hashCode()`                          |
| Commonly used in   | `Set`, `Map`, `List.contains()`, etc. |

---
[🏠 Back to Home](../../README.md)