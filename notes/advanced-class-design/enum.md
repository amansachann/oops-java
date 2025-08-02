# 🏀 Enum with Fields & Methods

---

## 🧠 What is an Enum in Java?
> **Enums** = Java ke "intelligent constants" 🧠 — secure, readable, and powerful! 💪
### 📌 Basic Idea:

> `enum` is a special Java type used to define **a group of named constants**.  
> But unlike other languages, **Java enums are classes** internally! ✅

---

## 🧱 Enum with Fields, Constructor & Methods

```java
enum Planet {
    MERCURY(3.303e+23, 2.4397e6),
    VENUS(4.869e+24, 6.0518e6),
    EARTH(5.976e+24, 6.37814e6);

    private final double mass;     // in kilograms
    private final double radius;   // in meters

    // 🛠 Constructor (only private allowed)
    Planet(double mass, double radius) {
        this.mass = mass;
        this.radius = radius;
    }

    // 📦 Methods
    public double mass() { return mass; }
    public double radius() { return radius; }

    public double surfaceGravity() {
        final double G = 6.67300E-11;
        return G * mass / (radius * radius);
    }
}
```

---

## ✅ How to Use:

```java
public class Test {
    public static void main(String[] args) {
        for (Planet p : Planet.values()) {
            System.out.printf("%s: Gravity = %.2f%n", p, p.surfaceGravity());
        }
    }
}
```

---

## 🧪 Output Example:

```
MERCURY: Gravity = 3.70
VENUS: Gravity = 8.87
EARTH: Gravity = 9.80
```

---

## 📌 Key Features of Enum with Fields & Methods

| 🔍 Feature           | ✅ Supported in Java Enum                                      |
| -------------------- | ------------------------------------------------------------- |
| Fields               | ✅ Yes (final recommended)                                     |
| Constructor          | ✅ Yes (must be `private`)                                     |
| Methods              | ✅ Yes                                                         |
| Overriding methods   | ✅ Yes (even `toString()`)                                     |
| Implement interfaces | ✅ Yes (even custom interfaces)                                |
| Inheritance          | ❌ Cannot extend classes (implicitly extends `java.lang.Enum`) |

---

## 🧪 Enum with Custom `toString()`

```java
enum Level {
    LOW("Low Priority"), MEDIUM("Medium Priority"), HIGH("High Priority");

    private final String label;

    Level(String label) {
        this.label = label;
    }

    @Override
    public String toString() {
        return this.label;
    }
}
```

✅ Usage:

```java
System.out.println(Level.HIGH);  // Output: High Priority
```

---

## 🎯 Enum with Abstract Method

```java
enum Operation {
    PLUS {
        public double apply(double a, double b) { return a + b; }
    },
    MINUS {
        public double apply(double a, double b) { return a - b; }
    };

    public abstract double apply(double a, double b);
}
```

✅ Usage:

```java
System.out.println(Operation.PLUS.apply(5, 3));  // Output: 8.0
```

---

## 🧼 Best Practices

| ✅ Do's                                   | ❌ Don'ts                                    |
| ---------------------------------------- | ------------------------------------------- |
| Use fields for related data per constant | Don’t make constructors public/protected    |
| Keep enums immutable                     | Avoid large business logic in enums         |
| Use for fixed set of known constants     | Don’t use if constants are dynamic/changing |

---

## 🏁 Summary Table

| 📌 Feature               | ✅ Enum with Fields & Methods            |
| ------------------------ | --------------------------------------- |
| Constructor allowed?     | ✅ Yes, only private                     |
| Can have fields?         | ✅ Yes                                   |
| Can have methods?        | ✅ Yes (static, instance, abstract)      |
| Can override methods?    | ✅ Yes (e.g., `toString()`, abstract)    |
| Can extend a class?      | ❌ No (already extends `java.lang.Enum`) |
| Can implement interface? | ✅ Yes                                   |

---

[🏠 Back to Home](../..)