# 🤿 Polymorphic Paramaters

---

## 🧠 What are Polymorphic Parameters?

### 📌 Definition:

> A **polymorphic parameter** is a method parameter that accepts a **superclass or interface type**, so that **any subclass object** can be passed to it.

✅ This allows **method reuse** for **multiple types of objects**  
✅ Achieved via **runtime polymorphism (dynamic method dispatch)**

---

## 🔧 Syntax Example

```java
class Animal {
    void sound() {
        System.out.println("Generic animal sound");
    }
}

class Dog extends Animal {
    void sound() {
        System.out.println("Dog barks 🐶");
    }
}

class Cat extends Animal {
    void sound() {
        System.out.println("Cat meows 🐱");
    }
}
```

### 🧪 Polymorphic Parameter in Action

```java
class AnimalTrainer {
    void train(Animal a) {
        a.sound();  // runtime polymorphism
    }
}
```

```java
public class Test {
    public static void main(String[] args) {
        AnimalTrainer t = new AnimalTrainer();
        t.train(new Dog());  // Dog barks 🐶
        t.train(new Cat());  // Cat meows 🐱
    }
}
```

🧠 `train(Animal a)` — yeh ek **polymorphic parameter** hai!

---

## 🎯 Real-World Analogy

> 🎤 **Speaker = Polymorphic Parameter**
> You can plug in **Phone, Laptop, TV** (subclasses) into the **same AUX port** (superclass/interface)
> And output is decided by what you plug in → runtime behavior! 🔊

---

## ✅ Why Use Polymorphic Parameters?

| ✅ Benefit                     | 📘 Explanation                                         |
| ----------------------------- | ------------------------------------------------------ |
| Enables runtime polymorphism  | Behavior decided at runtime                            |
| Promotes code reuse           | Same method handles multiple object types              |
| Follows Open/Closed principle | Easy to extend with new subtypes without changing code |
| Cleaner API                   | Fewer method overloads, better abstraction             |

---

## 💡 Used in All Java APIs

```java
public void print(Object o)         // Object is polymorphic
public boolean add(Collection c)    // Accepts any type of collection
public void setLayout(LayoutManager m)
```

---

## 🧱 With Interfaces Example

```java
interface Shape {
    void draw();
}

class Circle implements Shape {
    public void draw() { System.out.println("Drawing Circle 🟠"); }
}

class Rectangle implements Shape {
    public void draw() { System.out.println("Drawing Rectangle 🟥"); }
}

class Painter {
    void paint(Shape s) {
        s.draw();  // polymorphic call
    }
}
```

```java
Painter p = new Painter();
p.paint(new Circle());    // Drawing Circle 🟠
p.paint(new Rectangle()); // Drawing Rectangle 🟥
```

---

## 🏁 Summary Table

| Feature  | Polymorphic Parameter 🧬                 |
| -------- | ---------------------------------------- |
| Type     | Parent class or interface                |
| Supports | Subclass object as argument              |
| Calls    | Overridden methods (dynamic dispatch)    |
| Benefits | Flexibility, reusability, cleaner design |
| Used in  | Java APIs, Frameworks, Design Patterns   |

---

## 🚀 Best Practices

* ✅ Prefer **parent class or interface** as parameter type  
* ✅ Use **abstract methods** to enforce child behavior  
* ✅ Avoid overloading for each child — use polymorphic parameter  
* ✅ Keep method **focused on common behavior**, not child-specific logic  

---
[🏠 Back to Home](../..)