# ✨ Static Blocks in Java

---

## 🧠 What is a Static Block in Java?

### 📌 **Definition:**

> A **static block** is a block of code enclosed in `{}` and marked with the `static` keyword.
> 
> It runs **once** when the class is **loaded into memory**, before any constructor or method.

---

## 🔧 Syntax:

```java
class MyClass {
    static {
        // static initialization code here
    }
}
```

---

## 🎯 Key Use Cases

| ✅ Use Case                      | 🔥 Purpose                          |
| ------------------------------- | ----------------------------------- |
| Initialize **static variables** | Complex or dynamic static values    |
| Load configuration              | Read from file/db/environment       |
| Register drivers (like JDBC)    | Automatically load once per app run |
| One-time setup logic            | Logging, counters, cache, etc.      |

---

## 🔧 Example: Static Block Execution

```java
class Demo {
    static int value;

    static {
        System.out.println("Static block running...");
        value = 100;
    }

    static void show() {
        System.out.println("Value = " + value);
    }
}
```

```java
public class Main {
    public static void main(String[] args) {
        Demo.show();  // Static block runs before this line
    }
}
```

✅ Output:

```
Static block running...
Value = 100
```

---

## 🧠 Behind the Scenes: Execution Order

| 🚀 Event        | 🧠 Happens When                      |
| --------------- | ------------------------------------ |
| Static block    | When class is **loaded into memory** |
| Static variable | Also during class loading            |
| Constructor     | When object is **created**           |

---

## 🔁 Multiple Static Blocks

Yes! You can define **multiple static blocks** — they execute **in the order they appear**.

```java
class Test {
    static {
        System.out.println("Block 1");
    }

    static {
        System.out.println("Block 2");
    }
}
```

✅ Output:

```
Block 1  
Block 2
```

---

## ⚔️ Static Block vs Constructor

| Feature              | 🔷 Static Block                        | 🔶 Constructor                  |
| -------------------- | -------------------------------------- | ------------------------------- |
| Runs when            | Class is loaded                        | Object is created               |
| Runs how many times? | **Once** (per class load)              | Every time an object is created |
| Access `this`?       | ❌ No (no object context)               | ✅ Yes                           |
| Used for             | Static variable setup, config, logging | Object-level initialization     |

---

## 💡 Real-World Use Case: Load Config or Register JDBC Driver

```java
class Config {
    static Properties props;

    static {
        props = new Properties();
        try {
            FileInputStream in = new FileInputStream("config.properties");
            props.load(in);
            System.out.println("Config loaded");
        } catch (Exception e) {
            System.out.println("Failed to load config");
        }
    }
}
```

---

## ⚠️ Important Notes

| ⚠️ Rule                              | ✅ Explanation                            |
| ------------------------------------ | ---------------------------------------- |
| Runs only once                       | When class is loaded into JVM            |
| No object reference allowed (`this`) | Because it runs before object is created |
| Static blocks run before `main()`    | JVM loads class before calling `main()`  |

---

## 🧪 Trick Question (Asked in Interviews)

🧠 **Q:** Will static block run if you don’t create object or call method?

```java
class Hello {
    static {
        System.out.println("Hello Static Block");
    }
}

public class Main {
    public static void main(String[] args) {
        Hello h = null;
    }
}
```

✅ **Yes!** Static block runs because `Hello` class gets **loaded** into memory.

---

## 🏁 Summary Table

| 🔧 Feature           | 📌 Description                  |
| -------------------- | ------------------------------- |
| Runs when?           | Class is loaded                 |
| Runs how many times? | Once per class (not per object) |
| Purpose              | Static setup / init / config    |
| Can use `this`?      | ❌ No                            |
| Called before        | `main()` and constructor        |

---

[🏠 Back to Home](../..)
