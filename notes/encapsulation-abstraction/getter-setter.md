# 🍡 Getters & Setters

---

## 🧠 What Are Getters and Setters?

### 📌 Definition:

> * A **getter** is a method used to **retrieve** (get) the value of a private field.
> * A **setter** is a method used to **set/change** the value of a private field.

✅ Yeh dono milke **encapsulation** implement karte hain.

---

## 💡 Why Use Getters and Setters?

| ✅ Reason                    | 📘 Explanation                                 |
| --------------------------- | ---------------------------------------------- |
| 🔒 Encapsulation            | Hide internal data (make fields `private`)     |
| ✅ Control Access            | Add validation, logging before setting/getting |
| 🔄 Flexible Changes         | Change internal logic without breaking API     |
| 🧪 Easy Testing & Debugging | Can intercept changes in data                  |
| 📦 Frameworks Compatibility | Required by JavaBeans, Spring, etc.            |

---

## 🔧 Syntax

```java
public class Student {
    private String name;
    private int age;

    // Getter for name
    public String getName() {
        return name;
    }

    // Setter for name
    public void setName(String name) {
        this.name = name;
    }

    // Getter for age
    public int getAge() {
        return age;
    }

    // Setter for age
    public void setAge(int age) {
        if (age > 0) { // 👈 You can add validation
            this.age = age;
        }
    }
}
```

---

## ✅ Usage Example

```java
Student s = new Student();
s.setName("Aman");
s.setAge(22);

System.out.println(s.getName()); // Aman
System.out.println(s.getAge());  // 22
```

---

## 🧱 JavaBean Standard (🚨 Interview Favorite)

> A **JavaBean** is a class that:

* Has **private fields**
* Has **public no-arg constructor**
* Has **public getters & setters**

```java
public class Product {
    private String name;
    private double price;

    public Product() {} // No-arg constructor ✅

    public String getName() { return name; }
    public void setName(String name) { this.name = name; }

    public double getPrice() { return price; }
    public void setPrice(double price) { this.price = price; }
}
```

---

## 🔐 Getters and Setters = Controlled Access

You can:

* Add **validation** in setter (e.g., age must be > 0)
* Add **formatting/logging** in getter
* Make **getter only** (read-only) or **setter only** (write-only)

---

## ⚙️ IDE Auto-Generate

In IntelliJ/Eclipse:

* Right-click → **Generate** → **Getter and Setter**

⚡ Fastest way to implement clean code!

---

## ⚠️ Best Practices

| Practice ✅                     | Why?                                  |
| ------------------------------ | ------------------------------------- |
| Keep fields `private`          | Encapsulation 🔐                      |
| Use standard `getX()`/`setX()` | JavaBean compliance                   |
| Validate in `setters`          | Prevent invalid state                 |
| Avoid heavy logic in `getters` | Keep them fast & safe                 |
| Immutable? Skip `setters`      | Use only getters for read-only fields |

---

## 🏁 Summary Table

| Concept      | Role                           |
| ------------ | ------------------------------ |
| `getter`     | Reads a private field value    |
| `setter`     | Modifies a private field value |
| Used for     | Encapsulation, JavaBeans, APIs |
| Access Level | Always `public`                |
| Field Level  | Always `private`               |

---

