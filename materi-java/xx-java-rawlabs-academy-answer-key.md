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

## Abstract, Inheritence Polymorphism (OOP)
### Task
Create a simple calculator application with addition, subtraction, division and multiplication functions. 

Take advantage of the `input()` function in Java to `enter the desired 2 numbers` and **1 number in the form of an operation choice**. 

Print the result of the operation at the end of the section like demo on the next slide.

```java
public class MainClass {
    public static void main(String[] args) {
        Calculator calc = new Calculator();
        calc.openCalculator();
    }
}

class Calculator extends InputOutput implements Arithmetic {

    @Override
    public Integer sum(int a, int b) {
        return a + b;
    }

    @Override
    public Integer subtract(int a, int b) {
        return a - b;
    }

    @Override
    public Integer multiply(int a, int b) {
        return a * b;
    }

    @Override
    public Integer divide(int a, int b) {
        return a / b;
    }

    @Override
    void openCalculator() {
        System.out.println(this.header);
        System.out.println("1: Open Calculator");
        System.out.println("99: Exit");
        System.out.print("Input Choice : ");
        int menu = input.nextInt();
        if (menu == 1) {
            inputValueCalculator();
        }
    }

    @Override
    void inputValueCalculator() {
        System.out.println(header);
        System.out.print("Input value 1 : ");
        int a = input.nextInt();
        System.out.print("Input value 2 : ");
        int b = input.nextInt();
        menuCalculator(a, b);
    }

    @Override
    void menuCalculator(int a, int b) {
        System.out.println(header);
        System.out.println("1. Add Value");
        System.out.println("2. Subtract Value");
        System.out.println("3. Multiply Value");
        System.out.println("4. Divide Value");
        System.out.println(header);
        System.out.println("Select operation : ");
        Integer n = input.nextInt();
        Integer result = 0;
        if (n == 1) {
            result = sum(a, b);
        } else if (n == 2) {
            result = subtract(a, b);
        } else if (n == 3) {
            result = multiply(a, b);
        } else if (n == 4) {
            result = divide(a, b);
        } else {
            System.out.println("Invalid Menu");
            return;
        }
        outputValueCalculator(n, result);
    }

    @Override
    void outputValueCalculator(int menu, int result) {
        System.out.println(header);
        System.out.println("Operation : " + menu);
        System.out.println("Result : " + result);
    }

}

abstract class InputOutput {

    protected String header = "+++++++++++++ CALCULATOR +++++++++++++";
    protected Scanner input = new Scanner(System.in);

    abstract void openCalculator();
    abstract void inputValueCalculator();
    abstract void menuCalculator(int a, int b);
    abstract void outputValueCalculator(int menu, int result);

}

interface Arithmetic {

    Integer sum(int a, int b);
    Integer subtract(int a, int b);
    Integer multiply(int a, int b);
    Integer divide(int a, int b);

}
```

### Task

- `Vehicle` is a parent of all existing classes. And have property:
    - `name` : for object name
    - `isUseEngine` : flag object if has engine or not
- `Bike`, `Car` and `Bus` is a child from `Vehicle`
- Class `Bike`
    - `wheelCount` : number of wheels owned
- Class `Car`
    - `wheelCount`
    - `engineType` : type of engine
- Class `Bus`
    -  `wheelCount`
    - `isPrivateBus` : flag bus is private or public
- Every class have method `identifyMySelf()` that **overrides** from `Vehicle` to print out like demo on the next slide

```java
public class MainClass {
    public static void main(String[] args) {
        Vehicle pedalBike = new Bike("Pedal Bike", Boolean.FALSE, 2);
        pedalBike.identityMyself();
        System.out.println();

        Vehicle motorBike = new Bike("Motor Bike", Boolean.TRUE, 2);
        motorBike.identityMyself();
        System.out.println();

        Vehicle cityCar = new Car("City Car", Boolean.TRUE, 4, "4 Cylinder");
        cityCar.identityMyself();
        System.out.println();

        Vehicle sportCar = new Car("Sport Car", Boolean.TRUE, 4, "12-V Cylinder");
        sportCar.identityMyself();
        System.out.println();

        Vehicle transBus = new Bus("Public Bus", Boolean.TRUE, 6, Boolean.FALSE);
        transBus.identityMyself();
        System.out.println();

        Vehicle schoolBus = new Bus("Private Bus", Boolean.TRUE, 6, Boolean.TRUE);
        schoolBus.identityMyself();
        System.out.println();
    }
}

class Vehicle {
    protected String name;
    protected boolean isUseEngine;

    public Vehicle(String name, boolean isUseEngine) {
        this.name = name;
        this.isUseEngine = isUseEngine;
    }

    public void identityMyself() {
        System.out.println("Hi I'm Parent of All Vehicles, My name is " + this.name + ", My Engine Status is '" + (this.isUseEngine ? "with engine" : "no engine") + "'");
    }
}

class Bike extends Vehicle{

    protected Integer wheelCount;

    public Bike(String name, boolean isUseEngine, Integer wheelCount) {
        super(name, isUseEngine);
        this.wheelCount = wheelCount;
    }

    @Override
    public void identityMyself() {
        System.out.println("Hi I'm Bike , My name is " + this.name + ", My Engine Status is '"
                + (this.isUseEngine ? "with engine" : "no engine") + "', I have " + this.wheelCount + " Wheel(s)");
    }
}

class Bus extends Vehicle {

    protected Integer wheelCount;
    protected boolean isPrivateBus;

    public Bus(String name, boolean isUseEngine, Integer wheelCount, boolean isPrivateBus) {
        super(name, isUseEngine);
        this.wheelCount = wheelCount;
        this.isPrivateBus = isPrivateBus;
    }

    @Override
    public void identityMyself() {
        System.out.println("Hi I'm Bus [" + (this.isPrivateBus ? "Private Bus" : "Public Bus") + "] , My name is "
                + this.name + ", My Engine Status is '" + (this.isUseEngine ? "with engine" : "no engine")
                + "', I have " + this.wheelCount + " Wheel(s)");
    }
}

class Car extends Vehicle {

    protected Integer wheelCount;
    protected String engineType;

    public Car(String name, boolean isUseEngine, Integer wheelCount, String engineType) {
        super(name, isUseEngine);
        this.wheelCount = wheelCount;
        this.engineType = engineType;
    }

    @Override
    public void identityMyself() {
        System.out.println("Hi I'm Car , My name is " + this.name + ", My Engine Status is '"
                + (this.isUseEngine ? "with engine" : "no engine") + "', I have " + this.wheelCount
                + " Wheel(s), My Engine Type = " + this.wheelCount);
    }
}
```

### Task
- `Animal` is a parent of all existing classes. And have property:
    - `name` : object name
    - `foodType` : type of food
    - `isSharpTeeth` : flag teeth is sharp or blunt
- `Herbivor`, `Carnivor` and `Omnivor` is a child from `Animal`
- Class `Herbivor`
    - Should eat plants
    - Should have blunt teeth
- Class `Carnivor`
    - Should eat meat
    - Should have sharp teeth
- Every class have method `identifyMySelf()` that **overrides** from `Animal` to print out like demo on the next slide

```java
public class MainClass {
    public static void main(String[] args) {
        Animal animal = new Animal("Animal", "All", "Sharp and Blunt");
        animal.identityMySelf();
        System.out.println();

        Animal herbivor = new Herbivor("Cow");
        herbivor.identityMySelf();
        System.out.println();

        Animal carnivor = new Carnivor("Tiger");
        carnivor.identityMySelf();
        System.out.println();

        Animal omnivor = new Omnivor("Cat");
        omnivor.identityMySelf();
        System.out.println();
    }
}

class Animal {
    protected String name;
    protected String foodType;
    protected String toothType;

    public Animal(String name, String foodType, String toothType) {
        this.name = name;
        this.foodType = foodType;
        this.toothType = toothType;
    }

    public void identityMySelf() {
        System.out.println("Hi I'm Parent of All Animal, My name is " + this.name);
    }
}

class Herbivor extends Animal {
    public Herbivor(String name) {
        super(name, "Plants", "Blunt");
    }

    @Override
    public void identityMySelf() {
        System.out.println("Hi I'm Herbivor , My Name is " + this.name + ", My Food is '"
                + this.foodType + "', I have " + this.toothType + " teeth");
    }
}

class Carnivor extends Animal {
    public Carnivor(String name) {
        super(name, "Meat", "Sharp");
    }

    @Override
    public void identityMySelf() {
        System.out.println("Hi I'm Carnivor , My Name is " + this.name + ", My Food is '"
                + this.foodType + "', I have " + this.toothType + " teeth");
    }
}

class Omnivor extends Animal {
    public Omnivor(String name) {
        super(name, "Meat and Plants", "Sharp and Blunt");
    }

    @Override
    public void identityMySelf() {
        System.out.println("Hi I'm Omnivor , My Name is " + this.name + ", My Food is '"
                + this.foodType + "', I have " + this.toothType + " teeth");
    }
}
```