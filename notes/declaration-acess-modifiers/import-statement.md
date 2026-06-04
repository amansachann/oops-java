# Import Statement

```java
public class Main {
    public static void main(String[] args) {
        ArrayList l = new ArrayList();
    }
}

```

```bash
Main.java:7: error: cannot find symbol
        ArrayList l = new ArrayList();
        ^
  symbol:   class ArrayList
  location: class Main
```

- We can resolve this problem using fully qualified name `java.util.ArrayList l = java.util.ArrayList();`. But problem with using fully qualified name everytime is it increases the length of the code reducing the readability.
  
- We can resolve this problem by using import statements.

```java
import java.util.ArrayList;

public class Main {
    public static void main(String[] args) {
        ArrayList l = new ArrayList();
    }
}
``` 

Hence whenever we are using import statement it is not required to use fully qualified names we can use short names directly. This approach decreases the length of code and increases readability.

## Types of Import Statements
There are 2 types of import statements:
1. Explicit class import 
2. Implicit class import


### Explicit class import
**Example:** `import java.util.ArrayList;`
- This type of import is highly recommended to use because it improves the readability of code.
- Best suitable for production code and your interviews.

### Implicit class import
**Example:** `import java.util.*;`
- This type of import is never recommended to use because it reduces the readability of code.
- Best suitable for competetive programming and non-serious kiddo projects.

```java
import java.util; ❌
import java.util.ArrayList.*; ❌
import java.util.*; ✅
import java.util.ArrayList; ✅
```

**Consider the following code:**
```java
class MyArrayList extends java.util.ArrayList {

}
```
- The code compiles fine even though we are not using import statements because we used fully qualified name.

- Whenever we are using fully qualified name it is not required to use import statement. Similarly whenever we are using import statements it is not required to use fully qualified name.

- Among both approaches always use import one because that is recommended.


```java
import java.util.*;
import java.sql.*;


class Test {
    public static void main(String[] args) {
        Date d = new Date();
    }
}
```

```bash
Main.java:7: error: reference to Date is ambiguous
        Date d = new Date();
        ^
  both class java.util.Date in java.util and class java.sql.Date in java.sql match
Main.java:7: error: reference to Date is ambiguous
```

- Always use explicit class import and don't import two classes with same name in the same java source file.



While resolving class names compiler will always give importance in following order:

1. Explicit class import
2. Classes present in current working directory
3. Implicit class import  

```java
import java.util.Date;
import java.sql.*;

class Test {

    public static void main(String[] args) {
        Date d = new Date();
    }
}
```

This code compiles fine and in this case util package Date would be considered.