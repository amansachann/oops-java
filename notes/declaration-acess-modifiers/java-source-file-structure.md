# Java Source File Structure

- A java program can contain any number of classes, and when we compile that `.java` file, number of `.class` files generated would be equal to the number of classes present in that file.

- But at most only one class can be declared as `public`. Also if there is a public class then the name of that public class and your .java file should be same. Otherwise you would get compile time error.

- If there is no public class then we can give any name to our java source file.

```java
class A {

}

class B {

}

class C {

}
```

**Case-1:**
If there is no public class then we can use any name for java source file there are no restrictions.


**Case-2:**
If class B is declared as public then the name of the program should be `B.java`otherwise we will get compile-time error saying `class B is public, should be declared in a file named B.java`.

**Case-3:**
- If both B and C classes are declared as public and name of file is B.java then we'll get compile time error saying `class C is public, should be declared in a file named C.java`.
- It is highly recommended to take only one class for source file and the name of file should be same as class name. This approach improves readability and understandability of the code.


*This file is saved by name `Kajal.java`*

```java
class A {
    public static void main(String[] args) {
        System.out.println("A class main method is executed");
    }
}

class B {
    public static void main(String[] args) {
        System.out.println("B class main method is executed");
    }
}

class C {
    public static void main(String[] args) {
        System.out.println("C class main method is executed");
    }
}

class D {

}
```

- We can compile a java source file but not a particular class in that source file, and when we compile that source file for every class one `.class` file is generated.
- We can execute a class but not java source file, whenever we try to run a class corresponding class main method would be excuted.
- If the class won't contain main method then we will get Runtime Error saying `NoSuchMethodError: main`.
- If we are trying to execute a java class and if the corresponding `.class`file is not available then we will get runtime exception saying `ClassNotFoundException`.