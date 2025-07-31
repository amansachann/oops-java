# 👒 Composition

---

## 🧠 What is Composition in Java?

### 📌 **Definition:**

> **Composition** is an OOP technique where one class contains a **reference to another class**, implying a **HAS-A** relationship.

🧾 Example:

* A **Car** has an **Engine**
* A **Person** has an **Address**

---

## 🆚 Inheritance vs Composition

| Feature      | Inheritance (`IS-A`)             | Composition (`HAS-A`)            |
| ------------ | -------------------------------- | -------------------------------- |
| Relationship | `Car IS-A Vehicle`               | `Car HAS-A Engine`               |
| Reusability  | Achieved via extension           | Achieved via containment         |
| Flexibility  | ❌ Less flexible (tight coupling) | ✅ More flexible (loose coupling) |
| Usage        | Compile-time hierarchy           | Runtime collaboration            |
| Good for     | "is a" modeling                  | "has a" modeling                 |

---

## 🔧 Syntax Example

```java
class Engine {
    void start() {
        System.out.println("Engine started");
    }
}

class Car {
    // Composition: Car has-a Engine
    Engine engine = new Engine();

    void drive() {
        engine.start();
        System.out.println("Car is moving...");
    }
}
```

✅ Usage:

```java
Car c = new Car();
c.drive();
```

🧾 Output:

```
Engine started  
Car is moving...
```

---

## 👪 Real-Life Example: Person → Address

```java
class Address {
    String city;
    String state;

    Address(String city, String state) {
        this.city = city;
        this.state = state;
    }

    void display() {
        System.out.println(city + ", " + state);
    }
}

class Person {
    String name;
    Address address; // HAS-A relationship

    Person(String name, Address address) {
        this.name = name;
        this.address = address;
    }

    void showDetails() {
        System.out.print(name + " lives in ");
        address.display();
    }
}
```

```java
Address addr = new Address("Kanpur", "UP");
Person p = new Person("Aman", addr);
p.showDetails();
```

✅ Output:

```
Aman lives in Kanpur, UP
```

---

## 🔍 Advantages of Composition

| ✅ Benefit            | 🧠 Description                            |
| -------------------- | ----------------------------------------- |
| Loose coupling       | Change one class without affecting others |
| Reusability          | Use composed class elsewhere              |
| Better encapsulation | Implementation details hidden             |
| Flexibility          | Dynamic behavior changes at runtime       |
| No diamond problem   | Unlike multiple inheritance               |

---

## ⚠️ Composition Tips & Best Practices

| Tip 💡                             | Reason ✅                                |
| ---------------------------------- | --------------------------------------- |
| Use private fields for composition | Follow encapsulation                    |
| Inject via constructor             | Encourages immutability & testing       |
| Avoid deep composition chains      | Increases complexity                    |
| Prefer interfaces for dependencies | More flexibility, helps mocking/testing |

---

## 💡 Composition in Frameworks

### ✅ Spring Framework:

* Beans are **composed via dependency injection**.

```java
@Service
class OrderService {
    private final PaymentService paymentService;

    OrderService(PaymentService paymentService) {
        this.paymentService = paymentService;
    }
}
```

➡️ `OrderService HAS-A PaymentService` — pure composition 😎

---

## 🏁 Summary Table

| Feature               | Composition (HAS-A) |
| --------------------- | ------------------- |
| Relationship type     | HAS-A               |
| Implemented using     | Object references   |
| Reusability           | ✅ High              |
| Flexibility           | ✅ High              |
| Coupling              | Loose               |
| Replaces inheritance? | Sometimes, YES 👍   |

---

[🏠 Back to Home](../../README.md)