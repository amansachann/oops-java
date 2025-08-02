# 🍹 transient Keyword

---

## 🧠 What is `transient` in Java?


> **`transient` = Java ka “yaad rakhne se inkaar” keyword 🧠❌ — jo kehde, *is field ko bhool ja JVM bhai!* 😎**



### 📌 Definition:

> `transient` is a **modifier used for fields** in a class that tells Java **not to serialize** that particular field when the object is being serialized. 💼❌📤

---

### ✅ Syntax:

```java
transient dataType variableName;
```

---

## 🔍 Why Use `transient`?

### 🎯 Purpose:

> To **exclude sensitive, temporary, or unnecessary data** from being written into a serialized file or stream.

---

## 📦 Real-Life Example

```java
import java.io.*;

class User implements Serializable {
    String username;
    transient String password;  // ❌ Will not be serialized

    User(String u, String p) {
        this.username = u;
        this.password = p;
    }
}
```

✅ Serialize the object:

```java
ObjectOutputStream out = new ObjectOutputStream(new FileOutputStream("user.ser"));
User u1 = new User("aman", "secret123");
out.writeObject(u1);
```

✅ Deserialize the object:

```java
ObjectInputStream in = new ObjectInputStream(new FileInputStream("user.ser"));
User u2 = (User) in.readObject();
System.out.println(u2.username);  // aman
System.out.println(u2.password);  // null ❗
```

---

## ⚠️ What Happens Internally?

* When Java serializes an object:

    * `transient` fields are **skipped**
    * They are **set to default values** after deserialization:

        * Objects → `null`
        * int → `0`
        * boolean → `false`
        * etc.

---

## 🔐 Common Use Cases

| 🧠 Use Case             | 💬 Reason to Use `transient`                         |
| ----------------------- | ---------------------------------------------------- |
| Passwords or Secrets    | Avoid writing sensitive data to disk                 |
| Derived/temporary data  | Can be recomputed; no need to persist                |
| Logger instances        | `transient Logger log = Logger.getLogger(...)`       |
| Non-serializable fields | Avoid `NotSerializableException` for 3rd-party types |

---

## 🧪 Can static fields be transient?

🔸 **Yes**, but it’s **meaningless** — because `static` fields are **never serialized anyway** (they belong to the class, not the instance).

---

## 🧼 Best Practices

| ✅ Do’s                                               | ❌ Don’ts                                                         |
| ---------------------------------------------------- | ---------------------------------------------------------------- |
| Use `transient` for fields you don't want to persist | Don’t forget to reinitialize them manually after deserialization |
| Combine with `Serializable` interface                | Don’t assume `transient` = secure encryption                     |
| Document why field is `transient`                    | Avoid using on `final` fields (unless reinitialized manually)    |

---

## 🏁 Summary Table

| 📌 Feature                | `transient` Keyword 🚫📦                  |
| ------------------------- | ----------------------------------------- |
| Applies to                | Instance variables (fields)               |
| Prevents                  | Serialization of that field               |
| Default after deserialize | Yes (null, 0, false, etc.)                |
| Works only with           | `Serializable` classes                    |
| Affects static fields?    | ❌ No (they are not serialized anyway)     |
| Common usage              | Passwords, cache, logging, derived values |

---

## 🛠️ Bonus Tip: Manual Initialization after Deserialization

```java
private void readObject(ObjectInputStream ois) throws IOException, ClassNotFoundException {
    ois.defaultReadObject();  // default deserialization
    this.password = "default@123";  // manually reset transient field
}
```
---
[🏠 Back to Home](../..)