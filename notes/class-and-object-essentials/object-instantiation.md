# 📦 Object Instantiation

---

## 🧠 What is Object Instantiation?

### 📌 \*\*Definition:

> **Object instantiation** is the process of **creating a real object (instance)** from a **class blueprint** using the `new` keyword.

---

## 🔧 Syntax

```java
ClassName obj = new ClassName(); // 🧱 Basic object creation
```

🧾 Example:

```java
Student s1 = new Student();
```

✅ Here:

| Part        | Meaning                         |
| ----------- | ------------------------------- |
| `Student`   | Class name (type)               |
| `s1`        | Reference variable              |
| `new`       | Allocates memory for the object |
| `Student()` | Calls the constructor           |

---

## 🔧 Step-by-Step: What Happens Internally?

1. JVM **allocates memory** in heap for `Student` object
2. JVM **calls the constructor** (like `Student()`)
3. JVM **assigns the address** to `s1` reference in stack

---

## 🧠 Memory Diagram

```
Stack (Reference)          Heap (Object)
+----------------+         +----------------------+
| s1             | ----->  | name = null          |
| (Student ref)  |         | id = 0               |
+----------------+         +----------------------+
```

---

## ✅ Different Ways to Instantiate an Object

| Method 💡                          | Example                                  | Use Case                                   |
| ---------------------------------- | ---------------------------------------- | ------------------------------------------ |
| Using `new` keyword                | `new Student()`                          | ✅ Most common                              |
| Using `newInstance()` (reflection) | `Class.forName("Student").newInstance()` | 🔁 Dynamic object creation                 |
| Using **clone()** method           | `Student s2 = (Student) s1.clone();`     | 🔄 Copy of existing object                 |
| Using **Deserialization**          | Reading object from stream/file          | 🔄 Re-create object from saved state       |
| Using **Factory Methods**          | `User.createAdminUser()`                 | 🚀 Control creation logic (design pattern) |

---

## 🔧 Example: Basic Instantiation

```java
class Car {
    String brand = "Honda";
    int speed = 0;

    void drive() {
        System.out.println(brand + " is driving at " + speed + " km/h");
    }
}
```

```java
public class Main {
    public static void main(String[] args) {
        Car c1 = new Car();      // 🆕 Object creation
        c1.speed = 60;
        c1.drive();              // Honda is driving at 60 km/h
    }
}
```

---

## 💡 Real-World Analogy

**Class** = Recipe
**Object** = Cake
You can bake multiple cakes from the same recipe — same as creating multiple objects from a class!

---

## 📦 Object Creation Using Parameterized Constructor

```java
class Student {
    String name;

    Student(String name) {
        this.name = name;
    }

    void greet() {
        System.out.println("Hi, I’m " + name);
    }
}
```

```java
Student s1 = new Student("Aman");
s1.greet(); // Hi, I’m Aman
```

---

## ⚠️ Common Mistakes

| Mistake ❌                              | Explanation 🧠                  |
| -------------------------------------- | ------------------------------- |
| Forgetting `new` keyword               | Object is not created           |
| Not initializing fields after creation | May get default/null values     |
| Accessing object before creation       | Leads to `NullPointerException` |

---

## 🔥 Interview Tip

🧠 **Q:** What's the difference between object and class?

| Class                   | Object                               |
| ----------------------- | ------------------------------------ |
| Blueprint or template   | Real instance created from the class |
| No memory for variables | Occupies memory in heap              |
| Cannot be directly used | Actual working entity                |

---

## 🏁 Summary Table

| 🔧 Element         | 📌 Meaning                  |
| ------------------ | --------------------------- |
| `new`              | Allocates memory for object |
| Constructor        | Initializes the object      |
| Reference Variable | Points to object memory     |
| Heap               | Where objects are stored    |
| Stack              | Stores reference variables  |

---

[🏠 Back to Home](../../README.md)
