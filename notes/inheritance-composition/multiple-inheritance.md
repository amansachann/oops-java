# 🧑‍🧑‍🧒 Multiple Inheritance via interfaces

---

## 🧠 What is Multiple Inheritance?

### 📌 **Definition:**

> **Multiple Inheritance** means a class **inherits features from more than one parent**.

🛑 Java doesn't allow:

```java
class A {}
class B {}
class C extends A, B {} // ❌ Not allowed
```

✅ But allows:

```java
interface A {}
interface B {}
class C implements A, B {} // ✅ Perfectly valid
```

---

## 🤔 Why Java Doesn't Support Multiple Class Inheritance?

🔴 Ambiguity problem – what if both parent classes have same method?

```java
class A { void show() {} }
class B { void show() {} }
class C extends A, B {} // ❌ Which show() to call?
```

✅ Interfaces solve this by providing **no implementation**, just method signatures.

---

## ✅ Multiple Inheritance via Interfaces

### 🔧 Syntax:

```java
interface A {
    void methodA();
}

interface B {
    void methodB();
}

class C implements A, B {
    public void methodA() {
        System.out.println("A's method");
    }

    public void methodB() {
        System.out.println("B's method");
    }
}
```

---

## 🧪 Example: Printable + Showable

```java
interface Printable {
    void print();
}

interface Showable {
    void show();
}

class Document implements Printable, Showable {
    public void print() {
        System.out.println("Printing...");
    }

    public void show() {
        System.out.println("Showing...");
    }
}
```

✅ Usage:

```java
Document d = new Document();
d.print();  // ✅ From Printable
d.show();   // ✅ From Showable
```

---

## 💥 Default Method Conflict (Java 8+)

```java
interface A {
    default void show() {
        System.out.println("A’s show");
    }
}

interface B {
    default void show() {
        System.out.println("B’s show");
    }
}

class C implements A, B {
    public void show() {
        // Conflict resolved manually
        A.super.show(); // or B.super.show()
    }
}
```

✅ You **must override** if conflict occurs.

---

## 🎯 Real-World Example

```java
interface Drivable {
    void drive();
}

interface Flyable {
    void fly();
}

class FlyingCar implements Drivable, Flyable {
    public void drive() {
        System.out.println("Driving on road...");
    }

    public void fly() {
        System.out.println("Flying in air...");
    }
}
```

---

## ⚠️ Key Rules

| Rule ⚠️                                   | ✅ Explanation                    |
| ----------------------------------------- | -------------------------------- |
| `extends` for class-to-class              | `class A extends B`              |
| `implements` for interface-to-class       | `class A implements I1, I2`      |
| `extends` for interface-to-interface      | `interface C extends A, B`       |
| All interface methods must be implemented | Unless class is `abstract`       |
| Conflict in default methods?              | Must override & resolve manually |

---

## 🧠 POJO vs Interface-based Inheritance

| Feature               | POJO (Class) Inheritance | Interface Inheritance           |
| --------------------- | ------------------------ | ------------------------------- |
| Multiple inheritance  | ❌ Not allowed            | ✅ Allowed                       |
| Method implementation | ✅ Present                | ❌ (Until Java 8 default)        |
| Conflict possibility  | ❌ Avoided                | ⚠️ Resolved manually if default |

---

## 🏁 Summary Table

| 🔧 Feature               | ✅ Support in Java via Interface |
| ------------------------ | ------------------------------- |
| Multiple inheritance     | ✅ Yes                           |
| Keyword used             | `implements`                    |
| Can inherit multiple?    | ✅ Interfaces only               |
| Conflicts resolved using | `InterfaceName.super.method()`  |
| Use case                 | Spring, REST, Functional design |

---
[🏠 Back to Home](../../README.md)

