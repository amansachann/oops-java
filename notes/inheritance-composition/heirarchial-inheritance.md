# 🧑‍🧒‍🧒 Hierarchical Inheritance

---

## 🧠 What is Hierarchical Inheritance?

### 📌 **Definition:**

> In **Hierarchical Inheritance**, **multiple subclasses** inherit from a **single superclass**.

📚 Java mein:

```java
    Parent
     /   \
Child1  Child2
```

---

## 👪 Real-Life Analogy

👨‍👧‍👦 **Parent** has 2 kids → 👧 Daughter and 👦 Son

* Dono same **surname**, same **culture**, alag **hobbies**
* Similarly, multiple classes inherit from a **common parent**

---

## 🔧 Syntax

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

class Cat extends Animal {
    void meow() {
        System.out.println("Cat meows");
    }
}
```

✅ Usage:

```java
Dog d = new Dog();
d.eat();   // inherited from Animal
d.bark();  // Dog's own method

Cat c = new Cat();
c.eat();   // inherited from Animal
c.meow();  // Cat's own method
```

---

## 🧱 Memory Diagram

```
           Animal
          /      \
       Dog       Cat
```

🧠 `Dog` and `Cat` **both get access** to Animal's methods and fields individually.

---

## 🎯 Why Use Hierarchical Inheritance?

| ✅ Benefit                 | 🔥 Description                                           |
| ------------------------- | -------------------------------------------------------- |
| Common logic at one place | Superclass handles shared methods/fields                 |
| Code reusability          | Reduce code duplication                                  |
| Real-world modeling       | One entity → many types (e.g., `Shape → Circle, Square`) |
| Easier maintenance        | Update in one class affects all children                 |

---

## 🧪 Real-World Example: Shape → Rectangle, Circle

```java
class Shape {
    void draw() {
        System.out.println("Drawing shape...");
    }
}

class Circle extends Shape {
    void area() {
        System.out.println("Area = πr²");
    }
}

class Rectangle extends Shape {
    void area() {
        System.out.println("Area = l × b");
    }
}
```

✅ Usage:

```java
Circle c = new Circle();
c.draw();  // from Shape
c.area();  // Circle’s own

Rectangle r = new Rectangle();
r.draw();  // from Shape
r.area();  // Rectangle’s own
```

---

## 🔁 Constructor Flow (Each object only goes upward)

```java
class Vehicle {
    Vehicle() {
        System.out.println("Vehicle constructor");
    }
}

class Car extends Vehicle {
    Car() {
        System.out.println("Car constructor");
    }
}

class Bike extends Vehicle {
    Bike() {
        System.out.println("Bike constructor");
    }
}
```

✅ Output (on `new Car()`):

```
Vehicle constructor  
Car constructor
```

---

## ⚠️ Important Points

| 🔧 Rule                       | ✅ Explanation                     |
| ----------------------------- | --------------------------------- |
| Use `extends` for each child  | All children extend same parent   |
| No cross-child inheritance    | `Car` can't access `Bike` methods |
| Common logic goes in parent   | `eat()`, `draw()`, `login()` etc. |
| Use `super()` for constructor | Constructor chaining to parent    |

---

## 💡 Java Inheritance Types Recap

| 🧬 Type      | 🔧 Description             | ✅ Java Support        |
| ------------ | -------------------------- | --------------------- |
| Single       | One child → One parent     | ✅ Yes                 |
| Multilevel   | A → B → C chain            | ✅ Yes                 |
| Hierarchical | One parent → Many children | ✅ Yes                 |
| Multiple     | One child ← Many parents   | ❌ No (use interfaces) |
| Hybrid       | Combo of above types       | ❌ Not directly        |

---

## 🏁 Summary Table

| 🔧 Feature              | 📌 Description                         |
| ----------------------- | -------------------------------------- |
| Inheritance type        | One superclass → many subclasses       |
| Common methods location | Superclass                             |
| Access to sibling logic | ❌ Not allowed                          |
| Keyword                 | `extends` for each child               |
| Use case                | Shared behavior across different types |

---
[🏠 Back to Home](../..)

