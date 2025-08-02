# ⬆︎ Upcasting

---

## 🧠 What is Upcasting?

### 📌 Definition:

> **Upcasting** is when a **subclass object is assigned to a superclass reference**.  
> ✅ It is done **implicitly (automatically)** and enables **runtime polymorphism**.

🧬 Syntax:

```java
Parent ref = new Child();  // ✅ This is upcasting
```

---

## 🎯 Example: Animal → Dog

```java
class Animal {
    void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {
    void sound() {
        System.out.println("Dog barks 🐶");
    }

    void fetch() {
        System.out.println("Dog fetches stick");
    }
}
```

### ✅ Upcasting:

```java
Animal a = new Dog();  // 👈 Upcasting happens here
a.sound();             // Dog barks 🐶 (Runtime polymorphism)
```

### ❌ But can't do this:

```java
a.fetch(); // ❌ Compile-time error (fetch() is not in Animal)
```

---

## ⚙️ Why Use Upcasting?

| ✅ Advantage                  | 📘 Description                            |
| ---------------------------- | ----------------------------------------- |
| Enables runtime polymorphism | Decides method at runtime                 |
| Promotes abstraction         | Code depends on **parent**, not **child** |
| Reduces coupling             | Easily swap implementations               |
| Used in real frameworks      | e.g., Spring beans, JDBC, Hibernate, etc. |

---

## ✅ Implicit Casting (Auto)

```java
Dog d = new Dog();
Animal a = d;   // ✅ Upcasting (implicit)
```

## ❌ Downcasting Needs Explicit Cast

```java
Dog d = (Dog) a;  // ⛔ Only safe if 'a' actually refers to Dog
```

---

## 🧠 Real-World Analogy

> **TV Remote = Parent**,
> **Sony TV, LG TV = Child Classes**
> You can control both with the **same remote** (upcasted reference), but only basic functions.

---

## 🔥 Use Case: Polymorphic Arrays

```java
Animal[] zoo = new Animal[3];
zoo[0] = new Dog();     // Upcast
zoo[1] = new Cat();     // Upcast
zoo[2] = new Tiger();   // Upcast

for (Animal a : zoo) {
    a.sound(); // Calls overridden version 🐾
}
```

---

## 🧪 Can You Call Child-Specific Methods?

Not directly:

```java
Animal a = new Dog();
a.fetch(); // ❌ Compile error (method not in Animal)
```

👉 To access, you must **downcast**:

```java
Dog d = (Dog) a;
d.fetch(); // ✅
```

---

## 🛑 When Downcasting is Dangerous

```java
Animal a = new Animal();
Dog d = (Dog) a; // ❌ Runtime error: ClassCastException
```

⚠️ Always use `instanceof` check before downcasting:

```java
if (a instanceof Dog) {
    Dog d = (Dog) a;
    d.fetch(); // ✅ Safe
}
```

---

## 🏁 Summary Table

| Feature                  | Upcasting                         |
| ------------------------ | --------------------------------- |
| Type                     | Implicit (auto)                   |
| Direction                | Child → Parent                    |
| Access                   | Only parent methods/fields        |
| Used for                 | Polymorphism                      |
| Allows override?         | ✅ Yes (runtime dispatch)          |
| Calls child method?      | ✅ Yes (overridden methods only)   |
| Calls child-only method? | ❌ Not allowed without downcasting |

---

[🏠 Back to home](../../README.md)