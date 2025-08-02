# 🌀 clone() 

---

## 🧠 What is `clone()` in Java?

### 📌 Definition:

> The `clone()` method is used to **create an exact copy** (shallow or deep) of an object.

🧾 Declared in:

```java
protected Object clone() throws CloneNotSupportedException
```

✅ Returns a **new object** with **same field values** as the original

---

## 🚨 Prerequisites to Use `clone()`

| Requirement                                           | Description                               |
| ----------------------------------------------------- | ----------------------------------------- |
| ✅ Class must implement `Cloneable`                    | Marker interface (no methods)             |
| ✅ Override `clone()` method                           | Because original is `protected` in Object |
| ⚠️ Otherwise, you'll get `CloneNotSupportedException` |                                           |

---

## 🧪 Basic Example – Shallow Cloning

```java
class Student implements Cloneable {
    int id;
    String name;

    Student(int id, String name) {
        this.id = id;
        this.name = name;
    }

    @Override
    public Object clone() throws CloneNotSupportedException {
        return super.clone(); // shallow copy
    }
}
```

```java
public class Test {
    public static void main(String[] args) throws CloneNotSupportedException {
        Student s1 = new Student(101, "Aman");
        Student s2 = (Student) s1.clone();

        System.out.println(s1 == s2);        // false ✅ different objects
        System.out.println(s1.name.equals(s2.name)); // true ✅ same content
    }
}
```

---

## 🧪 What is Shallow Copy?

* Primitive fields: ✅ copied by value
* Object fields: ❌ only reference copied (not deep structure)

```java
class Address {
    String city;
}

class Person implements Cloneable {
    int age;
    Address addr;

    public Object clone() throws CloneNotSupportedException {
        return super.clone();  // shallow clone
    }
}
```

> If you modify `addr.city`, it will affect both objects. ⚠️

---

## 🧬 Deep Cloning Example

```java
class Address implements Cloneable {
    String city;

    Address(String city) {
        this.city = city;
    }

    @Override
    protected Object clone() throws CloneNotSupportedException {
        return super.clone();
    }
}

class Person implements Cloneable {
    int age;
    Address addr;

    Person(int age, Address addr) {
        this.age = age;
        this.addr = addr;
    }

    @Override
    public Object clone() throws CloneNotSupportedException {
        Person cloned = (Person) super.clone();
        cloned.addr = (Address) addr.clone(); // deep copy
        return cloned;
    }
}
```

✅ Now both objects have **independent Address objects**.

---

## 🧾 clone() vs new

| `clone()`                             | `new`                            |
| ------------------------------------- | -------------------------------- |
| No constructor call                   | Constructor is called            |
| Fast (bitwise copy in shallow clone)  | Slightly slower (field-by-field) |
| Risk of shared references             | Always fresh objects             |
| Can lead to bugs if not done properly | More predictable                 |

---

## ⚠️ Common Pitfalls

* If `Cloneable` is not implemented → ❌ `CloneNotSupportedException`
* `clone()` only does **shallow copy** unless you override it deeply
* Object references may still be shared unless deep copied
* `clone()` is tricky and sometimes **not recommended** — use **copy constructors** or **builder pattern** instead

---

## 🧼 Best Practices

| ✅ Do’s                                     | ❌ Don’ts                                     |
| ------------------------------------------ | -------------------------------------------- |
| Implement `Cloneable`                      | Don’t forget it, or you'll get exceptions    |
| Override `clone()` and make it `public`    | Don’t expose raw `super.clone()` if unsafe   |
| Use deep copy for mutable objects          | Don’t use shallow copy if fields are objects |
| Document clearly if class supports cloning | Don’t rely on default clone in complex cases |

---

## 🏁 Summary Table

| Feature          | `clone()` Method 🔁                         |
| ---------------- | ------------------------------------------- |
| Defined in       | `Object` class                              |
| Return type      | `Object`                                    |
| Must implement   | `Cloneable` interface                       |
| Throws           | `CloneNotSupportedException` if not handled |
| Default behavior | Shallow copy                                |
| For deep copy    | Must override manually                      |
| Alternatives     | Copy constructor, Builder pattern           |

---

[🏠 Back to Home](../..)