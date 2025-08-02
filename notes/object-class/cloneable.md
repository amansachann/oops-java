# 🚀 Cloneable

---

## 🧠 What is `Cloneable` in Java?

### 📌 Definition:

> `Cloneable` is a **marker interface** (no methods) in `java.lang` package that **enables an object to be cloned using `Object.clone()`**.

🧾 Declaration:

```java
public interface Cloneable {}
```

---

## ❓ Why is it Required?

* If your class **does NOT implement** `Cloneable` and you call `clone()`, Java will throw:

  ❌ `CloneNotSupportedException`

---

## 🧪 Basic Example

```java
class Student implements Cloneable {
    int id;
    String name;

    Student(int id, String name) {
        this.id = id;
        this.name = name;
    }

    @Override
    public Object clone() throws CloneNotSupportedException {
        return super.clone(); // Uses Object's protected clone()
    }
}
```

```java
public class Test {
    public static void main(String[] args) throws CloneNotSupportedException {
        Student s1 = new Student(101, "Aman");
        Student s2 = (Student) s1.clone();

        System.out.println(s1 == s2);          // false ✅
        System.out.println(s1.name.equals(s2.name)); // true ✅
    }
}
```

---

## 🚫 Without Cloneable?

```java
class Student {
    int id;
    String name;

    public Object clone() throws CloneNotSupportedException {
        return super.clone(); // ❌ throws CloneNotSupportedException
    }
}
```

> ❌ You'll get exception if class doesn't `implements Cloneable`

---

## 🧬 Cloneable = Shallow Copy Enabler

| Feature     | Description                           |
| ----------- | ------------------------------------- |
| Type        | Marker interface (no methods)         |
| Package     | `java.lang`                           |
| Used with   | `Object.clone()`                      |
| Enables     | Shallow copy by default               |
| Needed for  | Avoiding `CloneNotSupportedException` |
| Does NOT do | Deep copy (you handle that manually)  |

---

## 🧼 Best Practices

| ✅ Do's                                        | ❌ Don'ts                                    |
| --------------------------------------------- | ------------------------------------------- |
| Always implement `Cloneable` to use `clone()` | Don’t use `clone()` without implementing it |
| Override `clone()` and make it `public`       | Don't rely on `super.clone()` for deep copy |
| Handle `CloneNotSupportedException`           | Don’t assume all classes are cloneable      |
| Prefer **Copy Constructors** or Builders      | Don’t overuse `clone()` in complex systems  |

---

## 🧱 Real-Life Analogy

> `Cloneable` = **“Authorized for Xerox”** stamp 📜  
> Only marked objects (classes) are allowed to be cloned legally by `clone()`! ✅

---

## 🔍 Cloneable vs Serializable

| Feature          | `Cloneable` 🧬     | `Serializable` 📦            |
| ---------------- | ------------------ | ---------------------------- |
| Purpose          | Enables cloning    | Enables object serialization |
| Type             | Marker interface   | Marker interface             |
| Common Use       | Object duplication | Save/load objects            |
| Companion Method | `clone()`          | `ObjectOutputStream`, etc.   |

---

## 🏁 Summary Table

| 🔑 Property            | 🧬 `Cloneable` Interface           |
| ---------------------- | ---------------------------------- |
| Type                   | Marker interface (no methods)      |
| In package             | `java.lang`                        |
| Used with              | `Object.clone()`                   |
| Needed to              | Avoid `CloneNotSupportedException` |
| Default clone type     | Shallow copy                       |
| Alternative            | Copy constructor, builder pattern  |
| Java version available | Since Java 1.0                     |

---

## ⚠️ Important Note (Java 9+)

* `clone()` is considered **legacy** now ⚠️
* Prefer **copy constructors** and **immutable design**
* But still useful in some scenarios and frameworks

---

