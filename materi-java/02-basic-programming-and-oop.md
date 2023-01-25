---
theme: gaia
_class: lead
paginate: true
backgroundColor: #fff
backgroundImage: url('https://marp.app/assets/hero-background.svg')
marp: true
---

![bg left:40% 60%](./../images/rawlabs-academy-logo.png)

# **Basic Programming and OOP**

Rawlabs Academy

---
# Tools and IDE
- JDK
- IDE

---
# Java Development Process

any

---
# Basic Programming

**Hello World!**

```java
public class Main {

    public static void main(String[] args) {
        System.out.println("Hello World!");
    }

}
```

---
<style scoped>
table {
    font-size: 0.8rem;
}
</style>
# Data Type (Integer)
| Data Type | Min | Max | Size | Default |
-----|------|-------|-------|-------|
byte | -128 | 127 | 1 byte | 0 |
short | -32,768 | 32,767 | 2 bytes | 0 |
int | -2,147,483,648 | -2,147,483,647 | 4 bytes | 0 |
long | -9,223,372,036, 854,755,808 | -9,223,372,036, 854,755,807 | 8 bytes | 0 |

---
# Data Type (Decimal)
| Data Type | Min | Max | Size | Default |
-----|------|-------|-------|-------|
float | 3.4e-038 | 34.e+038 | 4 bytes | 0 |
double | 1.7e-308 | 1.7e+308 | 8 bytes | 0 |

---
# Variable

**Declaration**
- `data_type variable_name = value`

**Example**
```java
int myInt;
long balance = 100000l;
String name = "Maverick";
double value = 1.71;

int age = 10;
byte ageAsByte = (byte) age;
```

---
<style scoped>
table {
    font-size: 0.8rem;
}
p {
    font-size: 0.8rem;
}
</style>
## Primitive & **Non** Primitive
**Primitive** default value is **0** but, **non primitive** is allow **nullable**;
| Data Type **Primitve** | Data Type **Non Primitive** |
|------|------|
| byte | Byte |
| short | Short |
| int | Integer |
| long | Long |
| float | Float |
| double | Double |
| char | Char |
| boolean | Boolean |

---
# Array

```java
char[] rawlabs = new char[] {'r','a','w','l','a','b','s'};

char[] rlabs = new char[7];
rlabs[0] = 'r';
rlabs[1] = 'a';
rlabs[2] = 'w';
rlabs[3] = 'l';
rlabs[4] = 'a';
rlabs[5] = 'b';
rlabs[6] = 's';
```

---
# Operator

| Operator | Symbol |
|------|:------:|
| Assignment | **=** |
| Arithmetic | **+ &nbsp; - &nbsp;  * &nbsp;  / &nbsp;  %** |
| Unary | **+ &nbsp; - &nbsp; ++ &nbsp; -- &nbsp; !** |
| Equality and Relational | **== &nbsp; != &nbsp; > &nbsp; >= &nbsp; < &nbsp; <=** |
| Conditional | **&& &nbsp; \|\|** |