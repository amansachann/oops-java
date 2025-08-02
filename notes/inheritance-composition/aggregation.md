# 🍬 Aggregation

---

## 🧠 What is Aggregation?

### 📌 **Definition:**

> **Aggregation** is a **HAS-A relationship** where one class **uses another class** as a **part**, but:

* Both objects can **exist independently**
* It represents a **"whole-part"** relationship

🧾 Example:

* A **University has Students**
* But if the university closes, students still exist ✅

---

## 👨‍🏫 Real-Life Analogy

* A **Library HAS-A Books**
* Books can exist even outside the library
  ➡️ This is **Aggregation** (weak HAS-A)

---

## 🔧 Syntax

```java
class Student {
    String name;

    Student(String name) {
        this.name = name;
    }

    void display() {
        System.out.println("Student: " + name);
    }
}

class College {
    String name;
    List<Student> students; // Aggregation

    College(String name, List<Student> students) {
        this.name = name;
        this.students = students;
    }

    void showCollegeDetails() {
        System.out.println("College: " + name);
        for (Student s : students) {
            s.display();
        }
    }
}
```

✅ Usage:

```java
Student s1 = new Student("Aman");
Student s2 = new Student("Ravi");

List<Student> studentList = List.of(s1, s2);
College clg = new College("IIT Kanpur", studentList);

clg.showCollegeDetails();
```

---

## 💡 Aggregation vs Composition

| Feature             | Aggregation (💡 Weak HAS-A)    | Composition (🔒 Strong HAS-A)        |
| ------------------- | ------------------------------ | ------------------------------------ |
| Object dependency   | ❌ Part can exist without whole | ✅ Part **can’t exist independently** |
| Lifetime of objects | Independent                    | Tightly bound                        |
| Object ownership    | Shared                         | Owned                                |
| Example             | University → Students          | Car → Engine                         |
| Coupling            | Loosely coupled                | Tightly coupled                      |

---

## 🔍 When to Use Aggregation?

| ✅ Use Case                                 | Example                          |
| ------------------------------------------ | -------------------------------- |
| One object uses another temporarily        | Teacher uses Marker              |
| Part can be shared across multiple objects | Multiple Depts share a Professor |
| Objects shouldn’t own each other tightly   | Company ↔ Employee               |

---

## 📦 UML Representation

In UML Class Diagrams:

* **Aggregation** is shown using a **hollow diamond**:

```
College ◇─── Student
```

* **Composition** is shown using a **filled diamond**:

```
Car ◆─── Engine
```

---

## 🧠 Key Points

| Concept 🔧           | Detail 📘                            |
| -------------------- | ------------------------------------ |
| Type of relationship | HAS-A (weak)                         |
| Object lifetime      | Independent                          |
| Keyword              | No special keyword — just references |
| Best for             | Loose part-whole modeling            |

---

## 🧪 Real-World Example: Department ↔ Teacher

```java
class Teacher {
    String name;
    Teacher(String name) { this.name = name; }
}

class Department {
    String deptName;
    List<Teacher> teachers;

    Department(String deptName, List<Teacher> teachers) {
        this.deptName = deptName;
        this.teachers = teachers;
    }
}
```

➡️ Even if `Department` is deleted, `Teacher` objects can live on.

---

## 🏁 Summary Table

| Feature            | Aggregation                 |
| ------------------ | --------------------------- |
| Relationship type  | HAS-A (Weak)                |
| Object dependency  | ❌ No (objects independent)  |
| Lifetime control   | No                          |
| Used in real world | Yes – e.g., Teams & Players |
| UML symbol         | ◇ Hollow Diamond            |

---
[🏠 Back to Home](../..)