# 🧑‍🧒 Single  Inheritance

---

## 🧠 What is Single Inheritance?

### 📌 **Definition:**

> In **Single Inheritance**, one class (**child/subclass**) **inherits** the properties (fields and methods) of **only one class** (**parent/superclass**).

---

## 👪 Real-Life Analogy

**Parent 👨‍👦 Child**
🧔 Parent: has surname, house
👦 Child: gets everything the parent has **+ their own stuff**

Just like that, **a child class inherits fields & methods from its parent class**!

---

## 🔧 Syntax

```java
class Parent {
    void showParent() {
        System.out.println("This is Parent class");
    }
}

class Child extends Parent {
    void showChild() {
        System.out.println("This is Child class");
    }
}
```

✅ Usage:

```java
Child c = new Child();
c.showParent(); // ✅ Inherited
c.showChild();  // ✅ Own method
```

---

## 🎯 Why Use Single Inheritance?

| ✅ Benefit         | 🔥 Description                          |
| ----------------- | --------------------------------------- |
| Code Reusability  | Reuse logic of existing class           |
| Maintainability   | Common logic lives in one place         |
| Logical hierarchy | Real-world modeling (is-a relationship) |
| Extensibility     | Add/modify features in subclass         |

---

## 🧱 Memory Diagram

```
Child object (in heap)
----------------------------
| showParent() ← inherited  |
| showChild()               |
----------------------------
```

---

## 🔧 Full Example: Animal → Dog

```java
class Animal {
    void eat() {
        System.out.println("Animal eats");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Dog barks");
    }
}
```

```java
public class Main {
    public static void main(String[] args) {
        Dog d = new Dog();
        d.eat();   // Inherited ✅
        d.bark();  // Own method ✅
    }
}
```

---

## ⚠️ Important Rules

| Rule                          | ✅ Explanation                                            |
| ----------------------------- | -------------------------------------------------------- |
| Use `extends` keyword         | For class-to-class inheritance                           |
| Only **one** parent class     | Java doesn't support multiple inheritance via classes ❌  |
| Private members not inherited | But can be accessed using **getters/setters** if defined |
| Constructors not inherited    | But parent constructor can be called via `super()`       |

---

## 🔁 Constructor Calling Order

```java
class A {
    A() {
        System.out.println("A’s constructor");
    }
}

class B extends A {
    B() {
        System.out.println("B’s constructor");
    }
}
```

✅ Output:

```
A’s constructor  
B’s constructor
```

➡️ **Parent constructor is always called first** (default or via `super()`)

---

## 💡 Real-World Use Case

### Example: `User` → `AdminUser`

```java
class User {
    String name;
    void login() {
        System.out.println(name + " logged in");
    }
}

class AdminUser extends User {
    void accessControlPanel() {
        System.out.println("Admin access granted");
    }
}
```

---

## 🔁 Summary Table

| 🔧 Feature              | 📘 Single Inheritance                |
| ----------------------- | ------------------------------------ |
| Keyword                 | `extends`                            |
| Max parent classes      | 1                                    |
| Child gets              | All **non-private** fields & methods |
| Constructor inheritance | ❌ No (but can call using `super()`)  |
| Reusability             | ✅ Yes                                |
| Relationship type       | IS-A (Dog IS-A Animal)               |

---

## ⚔️ Bonus: Single vs Multiple Inheritance (Java)

| Feature             | Single Inheritance | Multiple Inheritance (via classes) |
| ------------------- | ------------------ | ---------------------------------- |
| Supported in Java?  | ✅ Yes              | ❌ No (Ambiguity Problem)           |
| Implemented using   | `extends`          | ❌ Not allowed                      |
| Alternative in Java | Interfaces         | ✅ Multiple inheritance of type     |

---

[🏠 Back to Home](../../README.md)
