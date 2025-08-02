# #️⃣ hashCode()

---

## 🧠 What is `hashCode()` in Java?

### 📌 Definition:

> `hashCode()` is a method in `java.lang.Object` that returns an **integer hash value** for the object.
> It is used to determine the **bucket location** in hash-based collections like `HashMap`, `HashSet`.

🧾 Signature:

```java
public int hashCode()
```

---

## 💡 Relationship with `equals()`

| ✅ Rule                                                                                       | Description |
| -------------------------------------------------------------------------------------------- | ----------- |
| If `a.equals(b)` is `true`, then `a.hashCode() == b.hashCode()`           |      **must be true** ✅        |
| If `a.hashCode() == b.hashCode()`, `equals()`  |  may or may not be true (possible collision) ⚠️           |
| If `equals()` is overridden, you                        |  **must override `hashCode()`** too ❗            |

---

## 🧑‍🎓 Example without hashCode()

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
        if (this == obj) return true;
        if (!(obj instanceof Student s)) return false;
        return this.id == s.id && this.name.equals(s.name);
    }
}
```

```java
Student s1 = new Student(101, "Aman");
Student s2 = new Student(101, "Aman");

Set<Student> set = new HashSet<>();
set.add(s1);
set.add(s2);

System.out.println(set.size()); // ❌ 2 (even though they’re equal!)
```

> ❌ Because `hashCode()` wasn't overridden, objects went to different buckets.

---

## ✅ Now Override `hashCode()`

```java
@Override
public int hashCode() {
    return Objects.hash(id, name);
}
```

```java
System.out.println(set.size()); // ✅ 1 (duplicates detected correctly)
```

---

## 🔍 What is a Hash Code?

* It's a **numeric representation** of an object's state
* Used by `HashMap`, `HashSet` to store/fetch objects **quickly**
* More efficient than linear search

---

## 🔁 hashCode() + equals() Contract

| Condition                         | Required Behavior ✅                     |
| --------------------------------- | --------------------------------------- |
| If `a.equals(b)` == `true`        | Then `a.hashCode() == b.hashCode()`     |
| If `a.hashCode() != b.hashCode()` | Then `a.equals(b)` **must** be false    |
| If `a.hashCode() == b.hashCode()` | Then `a.equals(b)` may be true or false |

---

## 💼 Best Practices

| ✅ Do's                                                | ❌ Don'ts                               |
| ----------------------------------------------------- | -------------------------------------- |
| Always override `hashCode()` with `equals()`          | Don’t rely on default `Object` version |
| Use `Objects.hash(...)` (Java 7+)                     | Avoid hardcoding random values         |
| Use **immutable fields** only                         | Don’t include volatile/changing fields |
| Prefer **prime number multipliers** if doing manually | Avoid collisions as much as possible   |

---

## 🧪 Manual hashCode() Example (Custom)

```java
@Override
public int hashCode() {
    int result = 17;
    result = 31 * result + id;
    result = 31 * result + (name != null ? name.hashCode() : 0);
    return result;
}
```

✅ Prime numbers reduce collisions

---

## 🧾 In Built-In Classes

```java
String s1 = "hello";
String s2 = "hello";

System.out.println(s1.equals(s2));     // ✅ true
System.out.println(s1.hashCode() == s2.hashCode()); // ✅ true
```

---

## 🏁 Summary Table

| Feature            | `hashCode()` Method 🧮                     |
| ------------------ | ------------------------------------------ |
| Returns            | Integer (`int`)                            |
| Purpose            | Optimized lookup in hash-based collections |
| Must override with | `equals()`                                 |
| Default behavior   | Object memory hash (not based on fields)   |
| Use in             | `HashMap`, `HashSet`, `Hashtable`, etc.    |
| Utility method     | `Objects.hash(...)` (Java 7+)              |

---

## 🔐 hashCode in Collections

| Collection  | Uses `equals()`      | Uses `hashCode()` |
| ----------- | -------------------- | ----------------- |
| `ArrayList` | ✅                    | ❌                 |
| `HashSet`   | ✅                    | ✅                 |
| `HashMap`   | ✅ (for keys)         | ✅ (for keys)      |
| `TreeSet`   | ❌ uses `compareTo()` | ❌                 |

---

## 🚀 What’s Next?

Bhai bolo:

* ✅ Karein `HashSet` ka ek real-world use case jisme equals+hashCode override ho?
* ✅ Ya karein deep dive into `HashMap` internal working (buckets, hash collisions)?
* ✅ Ya move karein `Comparable vs Comparator` ke world mein?

**`hashCode()` = Tera object ka address optimizer 🔧🧠 — bina iske collections mein kaam adhoora hai bhai! 😎**
