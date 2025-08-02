# 🍻 Overriding equals() & hashCode()
---

## 🧠 1. What is `equals()`?

### 📌 **Default behavior:**

```java
public boolean equals(Object obj) {
    return this == obj; // Reference comparison ❌
}
```

➡️ By default, **reference** (memory) compare karta hai, **not object content**.

### ✅ Why override?

> To compare object **data/values**, not references.

---

## 🔧 Example: Without Overriding

```java
class Student {
    String name;
    int age;

    Student(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```

```java
Student s1 = new Student("Aman", 22);
Student s2 = new Student("Aman", 22);

System.out.println(s1.equals(s2)); // ❌ false (ref compare)
```

---

## 🔧 Overriding `equals()`

```java
@Override
public boolean equals(Object obj) {
    if (this == obj) return true;
    if (obj == null || getClass() != obj.getClass()) return false;

    Student other = (Student) obj;
    return age == other.age && name.equals(other.name);
}
```

✅ Now:

```java
System.out.println(s1.equals(s2)); // ✅ true
```

---

## 🧠 2. What is `hashCode()`?

### 📌 **Definition:**

> Returns an `int` hash value of the object. Used in **HashMap**, **HashSet**, **Hashtable**.

### 🔐 Contract between `equals()` & `hashCode()`:

| Rule 🔒                           | Meaning 🧠                            |
| --------------------------------- | ------------------------------------- |
| If `a.equals(b)` is `true`        | Then `a.hashCode() == b.hashCode()` ✅ |
| If `a.hashCode() == b.hashCode()` | `equals()` **might** be true or false |

---

## ⚠️ If you override `equals()`, you **must override** `hashCode()` too!

---

## 🔧 Overriding `hashCode()`

```java
@Override
public int hashCode() {
    return Objects.hash(name, age);
}
```

📦 Full Class Example:

```java
class Student {
    String name;
    int age;

    Student(String name, int age) {
        this.name = name;
        this.age = age;
    }

    @Override
    public boolean equals(Object obj) {
        if (this == obj) return true;
        if (obj == null || getClass() != obj.getClass()) return false;

        Student other = (Student) obj;
        return age == other.age && name.equals(other.name);
    }

    @Override
    public int hashCode() {
        return Objects.hash(name, age);
    }
}
```

---

## 🧪 Use Case: HashSet

```java
Set<Student> set = new HashSet<>();

set.add(new Student("Aman", 22));
set.add(new Student("Aman", 22)); // Duplicate? Depends on equals + hashCode

System.out.println(set.size()); // ✅ 1 if correctly overridden
```

---

## 🎯 Best Practices

| Practice ✅                                         | Why?                                   |
| -------------------------------------------------- | -------------------------------------- |
| Always override `equals()` + `hashCode()` together | To follow contract 🔒                  |
| Use `Objects.equals()` & `Objects.hash()`          | Null-safe and clean                    |
| Avoid mutable fields in hash-based keys            | Mutation can break hashing             |
| Use IDE to auto-generate them                      | IntelliJ/Eclipse gives clean overrides |

---

## 🔍 equals() vs ==

| Feature      | `==`                        | `equals()`            |
| ------------ | --------------------------- | --------------------- |
| Type         | Operator                    | Method                |
| Compares     | References (memory address) | Values (custom logic) |
| Overridable? | ❌ No                        | ✅ Yes                 |

---

## 🏁 Summary Table

| Method       | Purpose                             | Override Required?                  |
| ------------ | ----------------------------------- | ----------------------------------- |
| `equals()`   | Compare object values               | ✅ Yes                               |
| `hashCode()` | Generate hash for hashing structure | ✅ Yes (if `equals()` is overridden) |

---

[🏠 Back to Home](../..)