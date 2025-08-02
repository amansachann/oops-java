# 📄 Copy Constructor

---

## 🧠 What is a Copy Constructor?

### 📌 Definition:

> A **copy constructor** is a constructor that takes **an object of the same class** as a parameter and **copies its field values** to create a **new object**.

---

## ✅ Syntax:

```java
class ClassName {
    // fields...

    // Copy constructor
    ClassName(ClassName other) {
        // Copy fields from `other`
    }
}
```

---

## 🧑‍🎓 Example:

```java
class Student {
    int id;
    String name;

    // Constructor
    Student(int id, String name) {
        this.id = id;
        this.name = name;
    }

    // ✅ Copy Constructor
    Student(Student other) {
        this.id = other.id;
        this.name = other.name;
    }
}
```

```java
public class Test {
    public static void main(String[] args) {
        Student s1 = new Student(101, "Aman");
        Student s2 = new Student(s1); // Copy constructor call

        System.out.println(s1 == s2);         // false ✅ Different objects
        System.out.println(s1.name.equals(s2.name)); // true ✅ Same content
    }
}
```

---

## 🧬 Deep Copy with Copy Constructor

```java
class Address {
    String city;

    Address(String city) {
        this.city = city;
    }

    Address(Address other) {
        this.city = other.city;
    }
}

class Person {
    String name;
    Address address;

    Person(String name, Address address) {
        this.name = name;
        this.address = address;
    }

    // ✅ Deep Copy Constructor
    Person(Person other) {
        this.name = other.name;
        this.address = new Address(other.address); // Deep copy
    }
}
```

> ✅ Now modifying `address.city` in one object **won’t affect** the other.

---

## ✅ Copy Constructor vs clone()

| Feature              | `Copy Constructor` 🧱 | `clone()` 🔁                       |
| -------------------- | --------------------- | ---------------------------------- |
| Requires Interface?  | ❌ No                  | ✅ Needs `Cloneable`                |
| Constructor Call?    | ✅ Yes                 | ❌ No (direct memory copy)          |
| Default Behavior     | You define it         | Shallow copy                       |
| Deep Copy Supported? | ✅ Yes (customizable)  | ❌ Must override manually           |
| Checked Exception?   | ❌ No                  | ✅ `CloneNotSupportedException`     |
| Readability          | ✅ Clear               | ❌ Less intuitive                   |
| Recommended?         | ✅ YES                 | ❌ Not recommended (complex, risky) |

---

## 🔥 Real-Life Analogy

> 🧬 `clone()` = **Photocopy machine** (copies everything — even if it’s junk)  
> 🧱 `Copy Constructor` = **Human-made copy** (you decide what to copy, what to ignore)

---

## 🧼 Best Practices

| ✅ Do's                                                | ❌ Don'ts                                      |
| ----------------------------------------------------- | --------------------------------------------- |
| Use for immutable or deep copying                     | Don't just assign object references (shallow) |
| Call copy constructors recursively for nested objects | Avoid mixing copy constructor with clone()    |
| Always make fields `final` if possible                | Don't forget to copy critical fields          |

---

## 🏁 Summary Table

| Feature           | Copy Constructor 📦         |
| ----------------- | --------------------------- |
| Type              | Constructor                 |
| Input             | Object of same class        |
| Use case          | Create copy with same state |
| Default provided? | ❌ No (you write it)         |
| Shallow or Deep?  | ✅ You decide                |
| Exceptions?       | ❌ None                      |
| Recommended?      | ✅ Yes — clean and safe      |

---

[🏠 Back to Home](../../README.md)