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

Abstract Class, Abstract Method, Inheritence and Polymorphism

---
<style scoped>
    p {
        font-size: 0.85rem;
    }
    ul {
        font-size: 0.8rem;
    }
</style>
# Abstract **Class** and **Method**
<div class="grid grid-cols-2 gap-4">
<div>

```java
abstract class ProgrammingLanguage {
    abstract void describe();
    
    public void print() {
        System.out.println("Coding is fun!");
    }
}

public class Java extends ProgrammingLanguage {
    @Override
    public void describe() {
        System.out.println("Java use OOP concept.");
    }
}
```
</div>
<div>

**Abstract Class** :
- Must be declared with `abstract` keyword
- Can have abstract and non-abstract method
- Can not be instantiated
- Can have *constructor* and static method also
- Can have final methods which will force the subclass not to change the body of the method
</div>
</div>

---
![bg right:40% 70%](../images/materi-java/oop/inheritance.png)
<style scoped>
    p {
        font-size: 0.85rem;
    }
    ul {
        font-size: 0.85rem;
    }
</style>
# Inheritence

**Object Fact** :
- Object are often very similar. They share common logic.
- But, they're not entirely the same

<hr>

> ***What if we put common logic in one class, and unique logic of every object in their own class? Is that save your life from creating bunch of code in one class***

---
### Inheritence **Analogy**

![h:400 center](../images/materi-java/oop/inheritance-analogy.png)

---
<style scoped>
    p {
        font-size: 0.85rem;
    }
    ul {
        font-size: 0.85rem;
    }
</style>
### Inheritence **Example**
<div class="grid grid-cols-2 gap-4">
<div>

```java
public class Human {
    private String name;

    public Human(String name) {
        this.name = name;
    }
    // Setter getter block
}

public class Employee {
    private String nik;

    public Employee(String name, String nik) {
        super(name);
        this.nik = nik;
    }
}
```
</div>
<div>

##### Pre save word **SUPER**
**SUPER** is used to returns a proxy object that delegates method all to a parent or sibling class of type.

**Method overriding** is used to overriding parent method
</div>
</div>