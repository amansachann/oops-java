# 👐 Shallow Copy & Deep Copy

---

## 🧠 Basic Definitions

| Type             | Definition                                                                   |
| ---------------- | ---------------------------------------------------------------------------- |
| **Shallow Copy** | Copies **object reference** of nested objects — not actual nested objects 🪞 |
| **Deep Copy**    | Copies the **entire object along with all nested objects** 🎯                |

---

## 🧪 Real Example

```java
class Address {
    String city;
}

class Person implements Cloneable {
    String name;
    Address address;

    public Person(String name, Address address) {
        this.name = name;
        this.address = address;
    }

    // 🔁 Shallow Copy
    public Object clone() throws CloneNotSupportedException {
        return super.clone();  // Just reference copied
    }
}
```

```java
Person p1 = new Person("Aman", new Address("Delhi"));
Person p2 = (Person) p1.clone();

p2.address.city = "Mumbai";
System.out.println(p1.address.city); // ❌ Output: Mumbai (p1 also changed!)
```

🛑 Problem: Both `p1` and `p2` share **same Address object**

---

## 🧬 Deep Copy Example

```java
class Address implements Cloneable {
    String city;

    public Address(String city) {
        this.city = city;
    }

    public Object clone() throws CloneNotSupportedException {
        return super.clone(); // Copy Address
    }
}

class Person implements Cloneable {
    String name;
    Address address;

    public Person(String name, Address address) {
        this.name = name;
        this.address = address;
    }

    // ✅ Deep Copy
    public Object clone() throws CloneNotSupportedException {
        Person p = (Person) super.clone();
        p.address = (Address) address.clone(); // Deep copy nested object
        return p;
    }
}
```

```java
Person p1 = new Person("Aman", new Address("Delhi"));
Person p2 = (Person) p1.clone();

p2.address.city = "Mumbai";
System.out.println(p1.address.city); // ✅ Output: Delhi (no effect on p1)
```

---

## 📊 Shallow vs Deep Copy: Comparison Table

| 🔍 Feature              | 🪞 Shallow Copy                                        | 🎯 Deep Copy                                   |
| ----------------------- | ------------------------------------------------------ | ---------------------------------------------- |
| Primitive fields        | ✅ Copied by value                                      | ✅ Copied by value                              |
| Object/reference fields | ❌ Reference copied only                                | ✅ New object created recursively               |
| Nested object changes   | 🔄 Reflect in both copies                              | 🔐 Only affect the copied object               |
| Memory usage            | 🔽 Less (references shared)                            | 🔼 More (fully duplicated)                     |
| Performance             | ⚡ Fast                                                 | 🐢 Slower (due to recursion)                   |
| Clone method            | `super.clone()` only                                   | Manual deep copy of fields                     |
| Use case                | When object is immutable or nested fields don’t change | When full isolation is needed (defensive copy) |
| Safer?                  | ❌ Risk of unintended side effects                      | ✅ Safer for independent copies                 |

---

## 🛠 Real-Life Analogy

| Scenario     | Analogy 🔍                                             |
| ------------ | ------------------------------------------------------ |
| Shallow Copy | Xerox of document with reference to attachments 📄➡️📎 |
| Deep Copy    | Xerox of document with attachments also copied 📄📎📄  |

---

## 💼 Best Practices

| ✅ When to Use Shallow Copy                     | ✅ When to Use Deep Copy                        |
| ---------------------------------------------- | ---------------------------------------------- |
| For immutable or stateless objects             | For mutable/nested objects                     |
| When nested fields are not meant to be changed | When you want full independence in object copy |
| For performance-sensitive situations           | For correctness-sensitive situations           |

---

## 🧾 Bonus: Deep Copy via Serialization (Alt Technique)

```java
// Serialize the object to byte stream and deserialize to get deep copy
```

✔️ Works well when all objects are `Serializable`, but slower.

---

## 🏁 Summary

| 📌 Aspect          | 🪞 Shallow Copy     | 🎯 Deep Copy                      |
| ------------------ | ------------------- | --------------------------------- |
| Reference copied   | ✅ Yes               | ❌ No (new object)                 |
| Data copied deeply | ❌ No                | ✅ Yes                             |
| Performance        | ⚡ Faster            | 🐢 Slower                         |
| Use case           | Lightweight cloning | Safe, full duplication            |
| Implementation     | `super.clone()`     | Manual recursion or serialization |

---

