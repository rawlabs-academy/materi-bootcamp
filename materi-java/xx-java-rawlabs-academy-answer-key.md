# Java Answer Key
Java Answer Key of **Rawlabs Academy**

## Introduction Algorithm
### **Task**
A prime number is a natural number that is greater than 1, whose divisors are **1** and the **number itself**. The numbers **2** and **3** are **prime numbers**. The number 4 is not a prime number because it can be divided by 2.  *Create a function to determine whether the inputted number is a prime number or not using [Whimsical](https://whimsical.com)*. 

Example :
- Input: 3, Output: Prime Number
- Input: 7, Output: Prime Number
- Input: 10, Output: Not Prime Number

<p align="left">
  <img height="600px" src="../images/answer-key/java/introduction-algorithm.png"/>
</p>

## Basic Programming

### **Task 1**
Counts the number of characters in the form of vowels, consonants and total characters from the sentence *"Rahwlabs Academy"*.

**Input**: 
Rawlabs Academy

**Output**:
Vowels: 5
Consonants: 9
Total: 14

```java
public class VocalConsonant {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Input a text : ");
        String text = sc.nextLine();
        sc.close();

        int vowel = 0;
        int consonant = 0;

        for (int i = 0; i < text.length(); i++) {
            char c = Character.toLowerCase(text.charAt(i));
            
            if (c == ' ') continue;

            if (c == 'a' || c == 'i' || c == 'u' || c == 'e' || c == 'o') {
                vowel++;
            } else {
                consonant++;
            }
        }

        System.out.printf("Vowels: %d\n", vowel);
        System.out.printf("Consonants: %d\n", consonant);
        System.out.printf("Total: %d\n", vowel + consonant);
    }

}
```

### **Task 2**
**Palindrome** is a word, number, phrase, or other sequence of symbols that reads the same backwards as forwards. Write a program to detect whether a string is a palindrome or not.

Input: **katak** \
Output: Palindrome

Input: **mister** \
Output: Not Palindrome

Input: **kasur rusak** \
Output: Palindrome

```java
public class Palindrome {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Input a text : ");
        String text = sc.nextLine();
        sc.close();

        boolean isPalindrome = Boolean.TRUE;

        for (int i = 0; i < text.length(); i++) {
            int indexRight = (text.length() - 1) - i;
            char left = Character.toLowerCase(text.charAt(i));
            char right = Character.toLowerCase(text.charAt(indexRight));

            if (left != right) {
                isPalindrome = Boolean.FALSE;
                break;
            }
        }

        if (isPalindrome) {
            System.out.println("Palindrome");
        } else {
            System.out.println("Not Palindrome");
        }
    }

}
```

## Object Oriented Programming (OOP) - Basic
### **Task**
Define 5 classes freely related to the type of animal, plant or vehicle. Use encapsulation concepts such as public, protected and private according to analogy examples in the real world.

Example:
`Cat, Fish, Flower, Car, etc.`

Add instance variables and methods in each class created. Then create code to prove **encapsulation** is running as expected.

For example, can `Frog` access these `public`, `protected` or `private` variables? or other things that produce returns as expected.

```
.
└── main/
    └── participant/
        ├── MainParticipant.java
        ├── Mentee.java
        └── Person.java
    └── program/
        ├── BootcampProgram.java
        ├── Java.java
        └── MainProgram.java
    └── Main.java
```

**Package of** `main.participant`

```java
package main.participant;

public class Person {
    private String name;
    protected String gender;

    public void sayHello() {
        System.out.println("Hello I'm from public method. I can be called anywhere!");
    }

    protected void getHobby() {
        System.out.println("My hobby is coding. I can be called from sub-class");
    }

    // Setter Getter method
}
```

```java
package main.participant;

public class Mentee extends Person {
    private String bootcampProgram;

    // Setter Getter Method
}
```

```java
package main.participant;

public class MainParticipant {
    public static void main(String[] args) {
        Mentee mentee = new Mentee();

        /*
        This class can call directly the protected method of Person -> getHobby()
        Also can be direct access the gender attribute
         */
        mentee.getHobby();
        mentee.gender = "Male";

        System.out.println("Gender is = " + mentee.gender);
    }
}
```

Package of `main.program`

```java
package main.program;

public class BootcampProgram {
    private String programName;
    protected Integer batch;

    // Setter Getter method
}
```

```java
package main.program;

public class Java extends BootcampProgram {
    private Integer totalSyllabus;

    // Setter Getter method
}
```

```java
package main.program;

public class MainParticipant {
    public static void main(String[] args) {
        Mentee mentee = new Mentee();

        /*
        This class can call directly the protected method of Person -> getHobby()
        Also can be direct access the gender attribute
         */
        mentee.getHobby();
        mentee.gender = "Male";

        System.out.println("Gender is = " + mentee.gender);
    }
}
```

**Package of** `main`

```java
public class Main {
    public static void main(String[] args) {
        /*
        The protected method of BootcampProgram can't be direct accessed by Java because different package
        Should use setter and getter method
         */
        Java java = new Java();
        java.setProgramName("Backend Java");
        java.setBatch(1);
        java.setTotalSyllabus(30);

        System.out.println("Program Name = " + java.getProgramName());
        System.out.println("Batch = " + java.getBatch());
        System.out.println("Total Syllabus = " + java.getTotalSyllabus());

        System.out.println("==============================");

        Mentee mentee = new Mentee();
        /*
        Method sayHello() can be direct access because it has public modifier
         */
        mentee.sayHello();
        mentee.setBootcampProgram("Backend Java");
        mentee.setName("Calvin");
        mentee.setGender("Male");

        System.out.println("Mentee Name = " + mentee.getName());
        System.out.println("Gender = " + mentee.getGender());
        System.out.println("Bootcamp Program = " + mentee.getBootcampProgram());
    }
}
```