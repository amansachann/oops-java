# ✈️ Instance Blocks

---

## 🧠 What is an Instance Block in Java?

### 📌 **Definition:**

> An **Instance Block** (a.k.a. instance initializer block) is a block of code that runs **every time an object is created**, just **before the constructor** executes.

---

## 🔧 Syntax:

```java
class MyClass {
    {
        // instance block
        System.out.println("Instance block executed");
    }

    MyClass() {
        System.out.println("Constructor executed");
    }
}
```

✅ Output when you do:

```java
MyClass obj = new MyClass();
```

```
Instance block executed  
Constructor executed
```

---

## 🎯 Why Use Instance Blocks?

| ✅ Use Case                           | 🎯 Purpose                             |
| ------------------------------------ | -------------------------------------- |
| Common code across all constructors  | DRY (Don’t Repeat Yourself)            |
| Object-level pre-initialization      | Setup logic before constructor         |
| Anonymous or anonymous inner classes | Used where constructors aren’t allowed |

---

## 🧪 Example: Shared Pre-Logic for Constructors

```java
class Student {
    String name;
    int id;

    {
        System.out.println("Instance Block: Assigning ID");
        id = 100; // Default ID logic
    }

    Student(String name) {
        this.name = name;
        System.out.println("Constructor: Setting name");
    }

    void show() {
        System.out.println("Name: " + name + ", ID: " + id);
    }
}
```

```java
public class Main {
    public static void main(String[] args) {
        Student s1 = new Student("Aman");
        s1.show();
    }
}
```

✅ Output:

```
Instance Block: Assigning ID  
Constructor: Setting name  
Name: Aman, ID: 100
```

---

## ⚔️ Instance Block vs Constructor vs Static Block

| 🔧 Feature           | 💡 Instance Block            | 🔷 Constructor               | 🔶 Static Block                  |
| -------------------- | ---------------------------- | ---------------------------- | -------------------------------- |
| Runs when?           | Every time object is created | Every time object is created | When class is loaded             |
| Runs before what?    | Before constructor           | After instance block         | Before main(), before everything |
| Access `this`?       | ✅ Yes                        | ✅ Yes                        | ❌ No (no object yet)             |
| Access instance var? | ✅ Yes                        | ✅ Yes                        | ❌ No                             |

---

## 🔁 Multiple Instance Blocks?

✅ Yes, and they execute **in order of appearance** in the class.

```java
class Test {
    {
        System.out.println("Block 1");
    }

    {
        System.out.println("Block 2");
    }

    Test() {
        System.out.println("Constructor");
    }
}
```

🟢 Output:

```
Block 1  
Block 2  
Constructor
```

---

## ⚠️ Common Mistakes & Notes

| ❗ Mistake / Note                              | ✅ Explanation                                |
| --------------------------------------------- | -------------------------------------------- |
| Don’t access static members from `this` block | Not a compile error, but bad practice        |
| Runs even if constructor is empty             | Every time object is created                 |
| Not used much in modern code                  | Usually replaced by constructors or builders |

---

## 🧠 Real-World Use Case

Use instance block for **common object setup logic**, e.g.,

```java
class User {
    int id;
    static int counter = 1;

    {
        id = counter++; // Assign auto-increment ID to every new user
    }

    User() {}
}
```

---

## 🏁 Summary Table

| 🔧 Feature        | 📌 Description                 |
| ----------------- | ------------------------------ |
| Belongs to        | Object (not class)             |
| Runs when?        | On every `new` object creation |
| Runs before?      | Constructor                    |
| Access `this`?    | ✅ Yes                          |
| Multiple allowed? | ✅ Yes, executed top-down       |

---
[🏠 Back to Home](../..)