---
theme: gaia
_class: lead
paginate: true
backgroundColor: #fff
backgroundImage: url('https://marp.app/assets/hero-background.svg')
marp: true
style: @import url('https://unpkg.com/tailwindcss@^2/dist/utilities.min.css');
---

![bg left:40% 60%](./../images/rawlabs-academy-logo.png)

# **Object Oriented Programming**

Rawlabs Academy

---
<style scoped>
    p {
        text-align: center;
        font-size: 1.7rem;
    }
</style>
<!-- _class: lead -->
> Programming paradigm which provides a means of structuring program so that **properties** and **behaviour** are bundled into individual **objects**.

---
## Propeties
- Color
- Length
- Width

## Behavior
- Accelerate
- Break

---
## Properties
- Fur
- Leg
- Tail

## Behavior
- Make Sound
- Eat
- Jump

---
<style scoped>
    p {
        text-align: center;
        font-size: 1.7rem;
    }
</style>
<!-- _class: lead -->
> **Properties** determined by the values of its attributes

> **Behavior** determined by how the objects acts or reacts to requests

---
<!-- _class: lead -->
# OOP Fundamental Concept

---
# Encapsulation
***Basic encapsulation analogy:***
- Class
- Attributes
- Method

---
<style scoped>
    p {
        font-size: 0.85rem;
    }
    ul {
        font-size: 0.85rem;
    }
</style>
### Encapsulation - **Class**

**Class** is a *"template"*  or *"blueprint"* that is used to create object.
**"Special code"** template in Java to make object:
- Contain of:
    - Properties
    - Method
- Has an init method to initiate object

```java
public class Cat {
    private String name;
    private String color;
}
```
---
<style scoped>
    p {
        font-size: 0.85rem;
    }
    ul {
        font-size: 0.85rem;
    }
</style>
#### Make instance of Object
<div class="grid grid-cols-2 gap-4">
<div>

```java
public class Cat {
    private String name;
    private String color;

    // Constructor block
    public Cat(String name, String color) {
        this.name = name;
        this.color = color;
    }

    // Setter getter method
}

public static void main(String[] args) {
    Cat cat = new Cat("Peter", "White");
    cat.getName(); // Peter
    cat.getColor(); // White
}
```
</div>
<div>

An instance is a unique copy of a **Class** that representing an **Object**.
- All **classes** create **object**, and all **object** contain **characteristic** called **attribbutes**
- Use `new Object()` for creating new object in Java.

**Note:** You will never have to call the `new Object()` method; it gets called automatically when you create a new Cat object.
</div>
</div>
---
