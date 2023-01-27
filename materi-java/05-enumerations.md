---
theme: gaia
_class: lead
paginate: true
backgroundColor: #fff
backgroundImage: url('https://marp.app/assets/hero-background.svg')
marp: true
---

![bg left:40% 60%](./../images/rawlabs-academy-logo.png)

# **Enumeration and Exception**

Rawlabs Academy

---
<!-- _class: lead -->
# What is **Enumeration**?

An **Enums** or **Enumerations** is a special *"class"* that represents a group of constants (unchangeable variables, like **final** variables).

---
**Final variables**
```java
public class Level {
    public static final String LOW = "LOW";
    public static final String MEDIUM = "MEDIUM";
    public static final String HIGH = "HIGH";
}
```

**Enum**
```java
public enum Level {
    LOW, 
    MEDIUM, 
    HIGH;
}
```

---
<style scoped>
    p {
        font-size: 0.85rem;
    }
</style>
### Why use Java **Enums**?
Enum was introduced to **replace the use of int constant**.

```java
public class Size {
    public static final int SMALL = 1;
    public static final int MEDIUM = 2;
    public static final int LARGE = 3;
    public static final int EXTRA_LARGE = 4;
}
```

Can be simplify using enums.
```java
public enum Size {
    SMALL, MEDIUM, LARGE, EXTRA_LARGE;
}
```

---
### Java Enum - **Basic Usage**

```java
public enum PizzaSize {
    SMALL, MEDIUM, LARGE, EXTRA_LARGE;
}

public class Main {
    public static void main(String[] args) {
        System.out.println(PizzaSize.MEDIUM);
        System.out.println(PizzaSize.LARGE);
    }
}
```

---
### Java Enum in **Switch Statement**

```java
public static void main(String[] args) {
    PizzaSize myPizza = PizzaSize.LARGE;
    switch(myPizza) {
        case PizzaSize.SMALL:
            System.out.println("I bought small pizza");
            break;
        case PizzaSize.MEDIUM:
            System.out.println("I bought medium pizza");
            break;
        case PizzaSize.LARGE:
            System.out.println("I bought large pizza");
            break;
    }
}
```

---
<style scoped>
    p {
        font-size: 0.85rem;
    }
</style>
### Methods of Java Enum
- `ordinal()` : returns the position of an enum constant
- `compareTo()` : compare the enum constants based on their ordinal value
- `toString()` : returns string representation
- `name()` : returns defined name in a string form
- `valueOf()` : takes a string and return an enum constant having the same string name
- `values()` : return an array of enum type containing all the enum constants

---
### Enum with **Predefined Value**
```java
public enum Color {
    RED("#F44336"),
    GREEN("#43A047"),
    BLUE("#0277BD");

    private final String hex;

    private Color(String hex) {
        this.hex = hex;
    }

    public String getHex() {
        return this.hex;
    }
}
```
---
<!-- _class: lead -->
# Exception
![h:300 center](../images/materi-java/enum-and-exceptions/error.png)

---
