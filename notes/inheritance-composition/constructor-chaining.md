# 🔗 Constructor Chaining in Inheritance

---

## 🧠 What is Constructor Chaining in Inheritance?

### 📌 **Definition:**

> **Constructor Chaining** in inheritance means when a subclass constructor calls its **superclass constructor** either **implicitly** or **explicitly** using `super()`.

---

## 🔧 Key Rule:

> **Jab bhi subclass ka object banta hai**, sabse pehle **superclass constructor** call hota hai, **phir subclass ka**.
> Yeh chain top-to-bottom follow hoti hai. 🧗

---

## 🔧 Syntax

```java
class A {
    A() {
        System.out.println("A constructor");
    }
}

class B extends A {
    B() {
        super(); // 👈 Optional (added by default)
        System.out.println("B constructor");
    }
}
```

✅ Output:

```
A constructor  
B constructor
```

---

## 🔗 Constructor Chaining Flow

```
Object creation → Subclass constructor → super() → Parent constructor → Done
```

---

## ✅ Example: With Multiple Levels

```java
class A {
    A() {
        System.out.println("Constructor A");
    }
}

class B extends A {
    B() {
        System.out.println("Constructor B");
    }
}

class C extends B {
    C() {
        System.out.println("Constructor C");
    }
}
```

```java
C obj = new C();
```

✅ Output:

```
Constructor A  
Constructor B  
Constructor C
```

🧠 Even though we only created `C`, Java **automatically chains** all parent constructors!

---

## 🔥 Real-World Example: Employee → Manager → Director

```java
class Employee {
    Employee() {
        System.out.println("Employee created");
    }
}

class Manager extends Employee {
    Manager() {
        System.out.println("Manager created");
    }
}

class Director extends Manager {
    Director() {
        System.out.println("Director created");
    }
}
```

```java
Director d = new Director();
```

✅ Output:

```
Employee created  
Manager created  
Director created
```

---

## 🚨 Important Rules

| ⚠️ Rule                                           | ✅ Explanation                               |
| ------------------------------------------------- | ------------------------------------------- |
| `super()` must be first line in constructor       | Java requires it to initialize parent first |
| Default constructor is called automatically       | If no `super()` is written explicitly       |
| Parameterized `super(args)` must be manual        | For calling non-default constructors        |
| No-arg constructor needed if `super()` is missing | Else you'll get compile error               |

---

## 🔄 Using Parameterized `super()`

```java
class A {
    A(String msg) {
        System.out.println("A: " + msg);
    }
}

class B extends A {
    B() {
        super("Hello from B"); // 🔗 Calls A(String msg)
        System.out.println("B Constructor");
    }
}
```

✅ Output:

```
A: Hello from B  
B Constructor
```

---

## 💥 Constructor Chaining vs Method Overriding

| Concept 🔧           | Description                                  |
| -------------------- | -------------------------------------------- |
| Constructor Chaining | Always happens **top to bottom**             |
| Method Overriding    | Works **bottom up** (child overrides parent) |

---

## 🏁 Summary Table

| 🔧 Concept             | 📌 Description                       |
| ---------------------- | ------------------------------------ |
| `super()`              | Calls parent constructor             |
| Auto-invoked?          | ✅ Yes (default constructor only)     |
| Must be first line?    | ✅ Always                             |
| Constructor call order | Top (superclass) → Bottom (subclass) |
| Parameterized chaining | Use `super(args)` manually           |

---

[🏠 Back to Home](../../README.md)