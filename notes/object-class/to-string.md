# ✏️ toString() Method

---

## 🧠 What is `toString()` in Java?

### 📌 Definition:

> `toString()` is a method defined in **`java.lang.Object`** class that returns a **string representation** of an object.

🧪 Default implementation:

```java
public String toString() {
    return getClass().getName() + "@" + Integer.toHexString(hashCode());
}
```

🔍 Example (Default behavior):

```java
class Student {}

public class Test {
    public static void main(String[] args) {
        Student s = new Student();
        System.out.println(s);        // Student@6d06d69c
        System.out.println(s.toString()); // same as above
    }
}
```

---

## 🧾 Why Override `toString()`?

> To give **meaningful output** about the object’s state (field values), not just hash code.

---

## 🧑‍🎓 Custom Example: Override `toString()`

```java
class Student {
    int id;
    String name;

    Student(int id, String name) {
        this.id = id;
        this.name = name;
    }

    @Override
    public String toString() {
        return "Student{id=" + id + ", name='" + name + "'}";
    }
}
```

```java
public class Test {
    public static void main(String[] args) {
        Student s = new Student(101, "Aman");
        System.out.println(s); // 🟢 Student{id=101, name='Aman'}
    }
}
```

✅ Clean, readable, and debuggable output!

---

## 💼 Real-World Use Cases

| 🔍 Where Used                    | 📘 Why `toString()` is Important                       |
| -------------------------------- | ------------------------------------------------------ |
| Debugging/logging tools          | Shows object's state in logs                           |
| Printing objects directly        | `System.out.println(obj)` = calls `obj.toString()`     |
| Concatenating object with string | `"Hello " + obj` → calls `obj.toString()`              |
| Custom `Exception` messages      | `throw new Exception(obj.toString())`                  |
| Unit tests and reports           | `assertEquals(expected.toString(), actual.toString())` |

---

## 🧱 Best Practices

| ✅ Do's                                            | ❌ Don'ts                               |
| ------------------------------------------------- | -------------------------------------- |
| Override `toString()` in all domain/model classes | Don't keep default if class has fields |
| Include only necessary fields                     | Avoid printing sensitive data          |
| Use StringBuilder/String.format for formatting    | Don’t concatenate inefficiently        |
| Use `@Override` annotation                        | Avoid silent bugs                      |

---

## 🧠 With Lombok (for quick devs)

```java
import lombok.ToString;

@ToString
class Student {
    int id;
    String name;
}
```

✅ Lombok will auto-generate `toString()` for you!

---

## 🧪 Bonus: `toString()` and Inheritance

```java
class Person {
    String name;
    public String toString() {
        return "Person: " + name;
    }
}

class Employee extends Person {
    int empId;
    public String toString() {
        return super.toString() + ", Emp ID: " + empId;
    }
}
```

✅ You can call `super.toString()` to reuse parent logic.

---

## 🏁 Summary Table

| Feature          | `toString()` Method 🧾                  |
| ---------------- | --------------------------------------- |
| Defined in       | `java.lang.Object`                      |
| Returns          | String representation of object         |
| Default output   | `ClassName@hashCode`                    |
| Override purpose | To show field values (custom display)   |
| Called by        | `System.out.println(obj)` or `"" + obj` |

---

