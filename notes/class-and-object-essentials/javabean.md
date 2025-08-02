# 🫘 JavaBean Standards

---

## 🧠 What is a JavaBean?

### 📌 **Definition:**

> A **JavaBean** is a **reusable software component** in Java that follows **specific coding conventions** and can be **easily managed/configured** by frameworks or tools.

---

## ✅ JavaBean Standards (Rules)

| 🔧 Rule                                                 | 📌 Description                                        |
| ------------------------------------------------------- | ----------------------------------------------------- |
| 1️⃣ Must be a **public class**                          | So that it can be accessed from outside packages      |
| 2️⃣ Must have a **public no-arg constructor**           | Required for frameworks/tools to instantiate the bean |
| 3️⃣ Must have **private fields**                        | Data hiding (encapsulation)                           |
| 4️⃣ Must provide **public getters/setters**             | Access fields using `getX()` / `setX()` methods       |
| 5️⃣ Must be **serializable** (optional but recommended) | For saving/transferring JavaBeans over network        |

---

## 🔧 Syntax Example: JavaBean Structure

```java
import java.io.Serializable;

public class Student implements Serializable {
    private String name;
    private int age;

    public Student() {} // No-arg constructor ✅

    // Getter and Setter for name
    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    // Getter and Setter for age
    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}
```

---

## 🧱 Breakdown

| 🔧 Element          | ✅ Reason                                             |
| ------------------- | ---------------------------------------------------- |
| `private` fields    | 🛡️ Encapsulation, access via methods only           |
| `getX()` / `setX()` | 🔍 Standard accessors and mutators (naming matters!) |
| `Serializable`      | 💾 Save/load across network or file                  |
| No-arg constructor  | 🧱 Used by Spring, Hibernate, reflection, etc.       |

---

## 🧪 Getter/Setter Naming Convention

| 🧠 Field Name        | Getter       | Setter               |
| -------------------- | ------------ | -------------------- |
| `name`               | `getName()`  | `setName(String)`    |
| `age`                | `getAge()`   | `setAge(int)`        |
| `isActive` (boolean) | `isActive()` | `setActive(boolean)` |

---

## 🔁 Real-World Use: Spring Framework

Spring uses JavaBeans as **POJOs** (Plain Old Java Objects) to represent:

* Entities (like `User`, `Product`, `Order`)
* DTOs
* Form data models
* REST payloads

Framework automatically sets values using:

```java
bean.setX(request.getParameter("x"));
```

---

## ⚠️ Common Mistakes

| ❌ Mistake                 | 🧠 Why It's Wrong                           |
| ------------------------- | ------------------------------------------- |
| Public fields             | Violates encapsulation                      |
| Missing setters           | Read-only bean — can’t modify values        |
| No default constructor    | Frameworks can’t instantiate                |
| Wrong getter/setter names | Reflection-based tools won’t recognize them |

---

## 💡 Bonus: Difference Between POJO and JavaBean

| Feature            | POJO                  | JavaBean                      |
| ------------------ | --------------------- | ----------------------------- |
| Full form          | Plain Old Java Object | JavaBean (reusable component) |
| No-arg constructor | Optional              | ✅ Required                    |
| Private fields     | Optional              | ✅ Required                    |
| Getters/Setters    | Optional              | ✅ Required                    |
| Serializable       | Optional              | ✅ Recommended                 |

---

## ✅ Summary Table

| 🔧 JavaBean Rule           | ✅ Required?    |
| -------------------------- | -------------- |
| Public class               | ✅ Yes          |
| Private member variables   | ✅ Yes          |
| Public no-arg constructor  | ✅ Yes          |
| Public getters and setters | ✅ Yes          |
| Serializable (implements)  | 🔄 Recommended |

---

[🏠 Back to Home](../..)