---
theme: gaia
_class: lead
paginate: true
backgroundColor: #fff
backgroundImage: url('https://marp.app/assets/hero-background.svg')
marp: true
---

![bg left:40% 60%](./../images/rawlabs-academy-logo.png)

# **String, String Buffer and String Builder**

Rawlabs Academy

---
## What is **String**?
- String is **non-primitive** data type and it is also class which is under `java.lang` package.
- String is collection of characters
- Immutable
- Can create object without new keyword

---
## Why String is **Immutable**?
- String are **constants**, values can't be changed after they are created
- Because java uses the concept of **string literal**
- Suppose, fi one reference variable changes the value of the object, it will be affected to al the reference variables. That is why string objects are immutable in java.

---
### Example

```java
public class Main {
    public static void main(String[] args) {
        String s = "Java";
        s.concat(" Programming");
        System.out.println(s);
    }
}
```

Output : `Java`

The `concat()` method is append the string at the end. So, `String` are immutable objects.

---
![left h:580](../images/materi-java/strings/string-constant-pool.png)

---
### Cont...

```java
public class Main {
    public static void main(String[] args) {
        String s = "Java";
        s = s.concat(" Programming");
        System.out.println(s);
    }
}
```

Output : `Java Programming`

So, it assign it into the **reference variable**.