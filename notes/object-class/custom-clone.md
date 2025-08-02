# 👨‍💻 Custom Clone Implementation

---

## 🧠 What is Custom Clone?

> Custom Clone = Jab tu `clone()` method **manually override** karta hai to:

* Control what fields get cloned
* Create deep copies of nested objects
* Avoid shallow copy pitfalls

---

## 🧬 Scenario: `Student` has an `Address` field

```java
class Address implements Cloneable {
    String city;

    Address(String city) {
        this.city = city;
    }

    @Override
    protected Object clone() throws CloneNotSupportedException {
        return super.clone(); // simple shallow copy
    }
}
```

---

### ✅ Custom Clone in `Student` Class

```java
class Student implements Cloneable {
    int id;
    String name;
    Address address;

    Student(int id, String name, Address address) {
        this.id = id;
        this.name = name;
        this.address = address;
    }

    @Override
    public Student clone() {
        try {
            // Step 1: Shallow copy of Student object
            Student cloned = (Student) super.clone();
            
            // Step 2: Deep copy of nested Address object
            cloned.address = (Address) address.clone();

            return cloned;
        } catch (CloneNotSupportedException e) {
            throw new AssertionError(); // should never happen
        }
    }
}
```

---

## ✅ Test It

```java
public class Test {
    public static void main(String[] args) {
        Address addr1 = new Address("Delhi");
        Student s1 = new Student(101, "Aman", addr1);

        Student s2 = s1.clone(); // custom deep clone

        s2.name = "Rohit";
        s2.address.city = "Mumbai";

        System.out.println(s1.name);        // Aman ✅
        System.out.println(s1.address.city); // Delhi ✅
    }
}
```

✅ Output confirms that clone is **deep** — changes to `s2` don’t affect `s1`.

---

## 📊 Shallow vs Custom Deep Clone

| 🔍 Feature           | Shallow Clone (`super.clone()`) | Custom Clone (Deep)                    |
| -------------------- | ------------------------------- | -------------------------------------- |
| Nested object copy   | ❌ Only reference copied         | ✅ New object created for nested fields |
| Control over fields  | ❌ No (default behavior)         | ✅ Full control                         |
| Risk of mutation bug | ✅ High                          | ❌ Very low                             |
| Recommended for      | Simple flat objects             | Complex or nested objects              |

---

## 🧼 Best Practices for Custom Cloning

| ✅ Do’s                                      | ❌ Don’ts                                     |
| ------------------------------------------- | -------------------------------------------- |
| Always implement `Cloneable`                | Don’t forget to deep-clone mutable fields    |
| Override `clone()` properly                 | Don’t return `super.clone()` blindly         |
| Handle `CloneNotSupportedException` safely  | Don’t ignore nulls while copying references  |
| Use utility methods to clean up clone logic | Avoid using `clone()` for large object trees |

---

## 🧠 Alternative: Copy Constructor vs Custom Clone

| Feature          | Custom `clone()` 🔁   | Copy Constructor 🧱     |
| ---------------- | --------------------- | ----------------------- |
| Syntax           | `.clone()`            | `new Student(original)` |
| Standard usage   | Legacy, requires care | Modern & preferred      |
| Constructor call | ❌ No                  | ✅ Yes                   |
| Readability      | ❌ Lower               | ✅ Better                |

---

## 🧾 Optional Utility: Safe Clone Helper

```java
public class Cloner {
    public static <T extends Cloneable> T safeClone(T obj) {
        try {
            Method m = obj.getClass().getMethod("clone");
            return (T) m.invoke(obj);
        } catch (Exception e) {
            throw new RuntimeException("Clone failed", e);
        }
    }
}
```

---

## 🏁 Summary Table

| 🔑 Property            | Custom Clone 🧬                     |
| ---------------------- | ----------------------------------- |
| Required Interface     | `Cloneable`                         |
| Manual clone logic?    | ✅ Yes                               |
| Supports deep cloning? | ✅ Yes                               |
| Uses `super.clone()`?  | ✅ Often as base                     |
| Alternative available? | ✅ Copy constructor, builder pattern |
| Preferred for          | Complex objects with nested fields  |

---

[🏠 Back to Home](../..)