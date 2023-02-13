# Java Answer Key
Java Answer Key of **Rawlabs Academy**

## Table of Contents
- [01 - Introduction Algorithm](#01---introduction-algorithm)
- [02 - Basic Programming](#02---basic-programming)
- [03 - Basic Object Oriented Programming](#03---basic-object-oriented-programming)
-  [04 - Abstract Inheritence Polymorphism](#04---abstract-inheritence-polymorphism)
- [05 - Enumeration](#05---enumeration)
- [06 - Array](#06---array)
- [07 - Iterrable and Collection](#07---iterrable-and-collection)
- [08 - Collection List](#08---collection-list)
- [09 - Collection Set](#09---collection-set)
- [10 - Collection Map](#10---collection-map)
- [11 - Java Generic Method and Generic Class](#11---java-generic-method-and-generic-class)
- [12 - String Buffer and String Builder](#12---string-buffer-and-string-builder)
- [13 - Lambda Expression](#13---lambda-expression)


## 01 - Introduction Algorithm
### **Task**
A prime number is a natural number that is greater than 1, whose divisors are **1** and the **number itself**. The numbers **2** and **3** are **prime numbers**. The number 4 is not a prime number because it can be divided by 2.  *Create a function to determine whether the inputted number is a prime number or not using [Whimsical](https://whimsical.com)*. 

Example :
- Input: 3, Output: Prime Number
- Input: 7, Output: Prime Number
- Input: 10, Output: Not Prime Number

<p align="left">
  <img height="600px" src="../images/answer-key/java/introduction-algorithm.png"/>
</p>

## 02 - Basic Programming

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

## 03 - Basic Object Oriented Programming
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

    // Setter Getter method
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

## 04 - Abstract Inheritence Polymorphism
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

## 05 - Enumeration
### Task

Create a method to check **Boba drink** payment if the payment is less than the price then throw a custom exception. And make validation if the selected **Boba menu** does not match the enum, then throw a custom exception with a message. 

**Note**: Take advantage of user input

```text
Input Boba menu : Boba Tea
Input Size : REGULAR
Input payment : 10000

Exception in thread "main" InvalidAmountException: Your amount is less than price!
```

```text
Input Boba menu : Boba Tea
Input Size: EXTRA_LARGE

Exception in thread "main" InvalidBobaSizeException: Invalid boba size!
Available boba size: [REGULAR, LARGE]
```

File `BobaSize.java`
```java
public enum BobaSize {
    REGULAR(12000),
    LARGE(15000);

    private final Integer price;

    BobaSize(Integer price) {
        this.price = price;
    }

    public Integer getPrice() {
        return price;
    }

}
```

File `InvalidAmountException.java`
```java
public class InvalidAmountException extends RuntimeException {
    public InvalidAmountException(String message) {
        super(message);
    }
}
```

File `InvalidBobaSizeException.java`
```java
public class InvalidBobaSizeException extends RuntimeException {
    public InvalidBobaSizeException(String message) {
        super(message);
    }

    @Override
    public String getMessage() {
        return super.getMessage() + "\nAvailable boba size: " + Arrays.toString(BobaSize.values());
    }
}
```

File `Main.java`
```java
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Input Boba menu : ");
        String bobaMenu = sc.nextLine();

        System.out.print("Input Size : ");
        String size = sc.nextLine();

        BobaSize bobaSize;

        try {
            bobaSize = BobaSize.valueOf(size);
        } catch (Exception e) {
            System.out.println();
            throw new InvalidBobaSizeException("Invalid boba size!");
        }

        System.out.print("Input Payment : ");
        Integer amount = sc.nextInt();
        sc.close();

        if (amount <= bobaSize.getPrice()) {
            System.out.println();
            throw new InvalidAmountException("Your amount is less than price!");
        }

    }
}
```

## 06 - Array
### Task 1 - Check **Prime Number**
Given an array `[2, 4, 8, 7, 9, 13, 11, 29, 18, 29, 34, 15, 17]`, create a function to check whether the numbers in the array are **prime** or not.

Expected Output:
- When prime number, print **x is Prime Number**.
- When not prime number, print **x is not Prime Number**.

```java
public class Main {

    static boolean isPrimeNumber(Integer number) {
        if (number == 1) {
            return false;
        }
        for (int i = 2; i < number; i++) {
            if (number%i == 0) {
                return false;
            }
        }
        return true;
    }

    public static void main(String[] args) {
        int[] arr = {2, 4, 8, 7, 9, 13, 11, 29, 18, 29, 34, 15, 17};
        for (int i = 0; i < arr.length; i++) {
            int number = arr[i];
            if (isPrimeNumber(number)) System.out.println(number + " is Prime Number");
            else System.out.println(number + " is not Prime Number");
        }
    }
}
```

### Task 2 - Play with **Asterisk**
Write a program to print the **asterisk triangle** as shown below.

**Input:** 5

**Output:**
```bash
    * 
   * * 
  * * * 
 * * * * 
* * * * *
```

```java
public class Main {

    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        System.out.print("Input : ");
        int total = input.nextInt();

        for (int i = 1; i <= total; i++) {
            for (int j = total-1; j >= i; j--) {
                System.out.print(' ');
            }
            for (int k = 1; k <= i; k++) {
                System.out.print("* ");
            }
            System.out.println();
        }
    }

}
```

### Task 3 - **Multiply Table**

Write program to print table of multiply based on user input as shown below.

**Input :** 6

**Output :**
```bash
1	2	3	4	5	6	
2	4	6	8	10	12	
3	6	9	12	15	18	
4	8	12	16	20	24	
5	10	15	20	25	30	
6	12	18	24	30	36
```

```java
public class Main {

    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        System.out.print("Input : ");
        int total = input.nextInt();

        for (int i = 1; i <= total; i++) {
            for (int j = 1; j <= total; j++) {
                Integer result = i * j;
                System.out.print(result + "\t");
            }
            System.out.println();
        }
    }

}
```

### Task 4 - **Searching** (Bonus)
Given `Person` data

| NIK | Name |
|:----|:-----|
| 0001 | Calvin |
| 0002 | Joe |
| 0003 | Maverick |
| 0004 | Kirito |
| 0005 | Andrew |

Write program to search `Person` by `name` **OR** by `nik`.

Test Case
- Input : `Joe`, Output : `Found data [Joe 0002]`
- Input : `0004`, Output : `Found data at [Kirito 0004]`
- Input : `Any`, Output : `Data not found`

```java
public class Main {

    static class Person {
        private String name;
        private String nik;

        public Person(String name, String nik) {
            this.name = name;
            this.nik = nik;
        }
        
        // Getter and Setter method
    }

    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        System.out.print("Input : ");
        String searchKey = input.nextLine();

        Person calvin = new Person("Calvin", "001");
        Person joe = new Person("Joe", "002");
        Person maverick = new Person("Maverick", "003");
        Person kirito = new Person("Kirito", "004");
        Person andrew = new Person("Andrew", "005");

        Person[] people = {calvin, joe, maverick, kirito, andrew};
        String result = "Data not found!";

        for (int i = 0; i < people.length; i++) {
            Person person = people[i];
            if (searchKey.equalsIgnoreCase(person.getName()) ||
                    searchKey.equalsIgnoreCase(person.getNik())) {
                result = "Found data [" + person.getName() + " " + person.getNik() + "]";
            }
        }

        System.out.println(result);
    }
}
```

## 07 - Iterrable and Collection
### Task

Make a summary for `Iterable` and `Collection` material and provide examples of implementation other than those contained in the material.

Implementation includes :
- While loop
- Foreach loop
- Implementation methods of `Iterable` and `Collection`

```java
public class Main {

    public static void main(String[] args) {
        Collection<Mentee> mentees = List.of(
                new Mentee("Calvin", "Male"),
                new Mentee("Maverick", "Male"),
                new Mentee("Cassandra", "Female")
        );

        System.out.println("Use iterator");
        Iterator<Mentee> iter = mentees.iterator();
        while (iter.hasNext()) {
            Mentee mentee = iter.next();
            System.out.println("Name : " + mentee.getName() + ", Gender : " + mentee.getGender());
        }

        System.out.println();
        System.out.println("Use foreach");
        for (Mentee mentee : mentees) {
            System.out.println("Name : " + mentee.getName() + ", Gender : " + mentee.getGender());
        }

    }

    public static class Mentee {
        private String name;
        private String gender;

        public Mentee(String name, String gender) {
            this.name = name;
            this.gender = gender;
        }

        // Getter and Setter method
    }

}
```

## 08 - Collection List
### Task - **Array Merge**
Make a program to combine 2 arrays, then insert several objects into the array in the middle with the index entered.

```java
public class Main {

    public static void main(String[] args) {
        List<String> data1 = List.of("One", "Two", "Three");
        List<String> data2 = List.of("Four", "Five");

        List<String> result = new ArrayList<>(data1);
        result.addAll(data2);
        System.out.println(result);
    }

}
```
 
### Task - **Play with Parking Area**
It is known that there is a parking lot that only contains 1 motorcycle in each row. Make a program to manage the parking lot so that it fills the farthest parking lot with the parking gate first and the motorbike closest to the parking gate can exit first.

```java
public class Main {

    public static void main(String[] args) {
        Stack<String> motor = new Stack<>();
        Scanner sc = new Scanner(System.in);
        String type;
        do {
            System.out.print("Input Type\n1. Motor Masuk\n 2. Motor Keluar\n99. Exit\nMasukkan Pilihan : ");
            type = sc.nextLine();

            if ("1".equalsIgnoreCase(type)) {
                System.out.print("Input plat nomor : ");
                String plat = sc.nextLine();
                motor.push(plat);
            } else if ("2".equalsIgnoreCase(type)) {
                System.out.println("Motor keluar : " + motor.peek());
                motor.pop();
            }

            System.out.println("Data motor : " + motor);
        } while (!"99".equalsIgnoreCase(type));
    }

}
```

## 09 - Collection Set
### Task - **Array Merge**

Create a program to merge 2 arrays that given and don't have the same name in the data that was merged. And then print out the **descendance data also**.

**Note :** Do not use Brute Force

Sample Test Case :
- input : `['kazuya', 'jin', 'lee']` and `['kazuya', 'feng']`
    output : `['kazuya', 'jin', 'lee', 'feng']`
- input: `['jin', 'lee', 'leo']` and `['kazuya', 'panda', 'leo']`
    output : `['jin', 'lee', 'leo', 'kazuya', 'panda']`

```java
public class Main {

    public static void main(String[] args) {
        List<String> data1 = List.of("kazuya", "jin", "lee");
        List<String> data2 = List.of("kazuya", "feng");

        Set<String> result = new HashSet<>(data1);
        result.addAll(data2);

        System.out.println(result);
    }

}
```

## 10 - Collection Map
### Task 1 - **Array Appears Once**

Create a method that functions to identify numbers that appear once from a string that is input. String contains a collection of numbers.

**Test Case :**
- Input : `"76523752"`
  Output : `[6, 3]`
- Input : `"1122"`
  Output: `[]`

```java
public class Main {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String number = "";

        System.out.print("Input number : ");
        number = sc.nextLine();

        Map<Integer, Integer> map = new HashMap<>();
        List<Integer> result = new ArrayList<>();

        String[] arr = number.split("");

        for (String v : arr) {
            Integer num = Integer.valueOf(v);
            if (map.get(num) == null) {
                map.put(num, 1);
            } else {
                map.put(num, map.get(num) + 1);
            }
        }

        System.out.println(map);

        for (Map.Entry<Integer, Integer> entry : map.entrySet()) {
            if (entry.getValue() == 1) {
                result.add(entry.getKey());
            }
        }

        System.out.println(result);
    }

}
```

### Task 2 - **Array Unique**

Create a method to identify the unique value between 2 array.

**Test Case :**
- Input : `[1, 2, 3, 4]` and `[1, 3, 5, 10, 16]`
  Output : `[2, 4, 5, 10, 16]`
- Input : `[3, 8]` and `[2, 8]`
  Output : `[3, 2]`

```java
public class Main {

    public static void main(String[] args) {
        List<Integer> data1 = List.of(1, 2, 3, 4);
        List<Integer> data2 = List.of(1, 3, 5, 10, 16);

        List<Integer> merge = new ArrayList<>(data1);
        merge.addAll(data2);

        Map<Integer, Integer> m = new HashMap<>();

         for (Integer v : merge) {
             m.merge(v, 1, Integer::sum);
         }

         List<Integer> unique = new ArrayList<>();
         for (Map.Entry<Integer, Integer> entry : m.entrySet()) {
             if (entry.getValue() == 1) {
                 unique.add(entry.getKey());
             }
         }

        System.out.println(unique);
    }

}
```

### Task 3 - **Search Book**

Create class `BookPriceList` and have fields are `name`,  `price` and `discount`. Add some **object** and **value** of that class.

Create method to check discount and calculate the final price of the book you are looking for.

```text
Input book which you want to check : java
Book name : Java from Zero to Hero
Discount : 15%
Price : IDR xxx,-
```

**Note :** `Price` is represent the **final price** after discount.

File `Book.java`
```java
public class Book {

    private String name;
    private Integer price;
    private Integer disc;

    public Book(String name, Integer price, Integer disc) {
        this.name = name;
        this.price = price;
        this.disc = disc;
    }

    // Getter and Setter method
}
```

File `Main.java`
```java
public class Main {

    public static void main(String[] args) {
        Book java = new Book("Java", 30000, 10);
        Book pyhton = new Book("Python", 24000, 20);
        Book javascript = new Book("Javascript", 70000, 15);
        Book kotlin = new Book("Kotlin", 120000, 25);

        Map<String, Book> map = new HashMap<>();
        map.put(java.getName().toLowerCase(), java);
        map.put(pyhton.getName().toLowerCase(), pyhton);
        map.put(javascript.getName().toLowerCase(), javascript);
        map.put(kotlin.getName().toLowerCase(), kotlin);

        try {
            Scanner sc = new Scanner(System.in);
            System.out.print("Input book which you want to check : ");
            String search = sc.nextLine().toLowerCase();

            Book book = map.get(search);
            System.out.println("Book name : " + book.getName());
            System.out.println("Price : " + book.getPrice());
            System.out.println("Discount : " + book.getDisc());

            Double disc = Double.valueOf((100-book.getDisc()) * 0.01);

            Double price = disc * book.getPrice();
            System.out.println("Final Price: IDR " + price);
        } catch (Exception e) {
            System.out.println("Book not found!");
        }
    }

}
```

## 11 - Java Generic Method and Generic Class
### Task - **Array Unique**
Create a method to identify the unique value between 2 array of different type using single **generic method**.

**Test Case :**
- Input : `[1, 2, 3, 4]` and `[1, 3, 5, 10, 16]`
  Output : `[2, 4, 5, 10, 16]`
- Input : `["one", "two"]` and `["two", "six"]`
  Output : `["one", "six"]`

```java
public class Main {

    public static <E> List<E> arrayUnique(List<E> list1, List<E> list2) {
        List<E> data = new ArrayList<>(list1);
        data.addAll(list2);

        Map<E, Integer> m = new HashMap<>();
        for (E v : data) {
            m.merge(v, 1, Integer::sum);
        }

        List<E> unique = new ArrayList<>();
        for (Map.Entry<E, Integer> entry : m.entrySet()) {
            if (entry.getValue() == 1) {
                unique.add(entry.getKey());
            }
        }
        return unique;
    }

    public static void main(String[] args) {
        List<Integer> integers = arrayUnique(List.of(1, 2, 3, 4), List.of(1, 3, 5, 10, 16));
        System.out.println(integers);

        List<String> strings = arrayUnique(List.of("one", "two"), List.of("two", "six"));
        System.out.println(strings);
    }
}
```

### Task - **Generic Class**
Create class using **generic class**. The class must have attributes `responseCode`, `responseDesc`, `timestamp` and `data`. The `data` is generic type that can be used for `String`, `Integer`, `Object`, `List`, etc.

```text
responseCode: SUCCESS
responseDesc: Success
timestamp: 2023-02-13T21:48:27.870496
data: Hello World
```

```text
responseCode: SUCCESS
responseDesc: Success
timestamp: 2023-02-13T21:50:05.087440
data: [Calvin, Joe, Cassandra]
```

```java
public class Main {

    public static void main(String[] args) {
        BaseResponse<String> response1 = new BaseResponse<>("SUCCESS", "Success", LocalDateTime.now(), "Hello World");
        System.out.println("responseCode: " + response1.getResponseCode());
        System.out.println("responseDesc: " + response1.getResponseDesc());
        System.out.println("timestamp: " + response1.getTimestamp());
        System.out.println("data: " + response1.getData());

        System.out.println();
        BaseResponse<List<String>> response2 = new BaseResponse<>("SUCCESS", "Success", LocalDateTime.now(), List.of("Calvin", "Joe", "Cassandra"));
        System.out.println("responseCode: " + response2.getResponseCode());
        System.out.println("responseDesc: " + response2.getResponseDesc());
        System.out.println("timestamp: " + response2.getTimestamp());
        System.out.println("data: " + response2.getData());
    }

}
```

## 12 - String Buffer and String Builder
### Task

Create method to print log like following below using string builder. **Note :** `Calvin` is inputed name, `2023-02-13T10:30:00.000` is represent today.

```text
================= RAWLABS ID ====================
> Learning Java is Fun
> We will learn spring boot soon
> Today is 2023-02-13T10:30:00.000
> My name is Calvin, I have learn String Builder in Java
> My Hobbies is Coding and Learning
=================================================
```

```java
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Input your name: ");
        String name = sc.nextLine();
        sc.close();

        LocalDateTime today = LocalDateTime.now();

        StringBuilder sb = new StringBuilder();
        sb.append("================= RAWLABS ID ====================\n");
        sb.append("> Learning Java is Fun\n");
        sb.append("> We will learn spring boot soon\n");
        sb.append("> Today is ");
        sb.append(today);
        sb.append("\n");
        sb.append("> My name is ");
        sb.append(name);
        sb.append(", ");
        sb.append("I have learn String Builder in Java\n");
        sb.append("> My Hobbies is Coding and Learning\n");
        sb.append("=================================================\n");

        System.out.println(sb);
    }
}
```

## 13 - Lambda Expression
### Task - **Play with Data**
It is known with the following data :

| Name | Interest | GPA | Status |
|:-----|:--------:|:---:|:------:|
| Calvin | Mobile | 3.5 | **PASSED** |
| Joe | Backend | 4.0 | **PASSED** |
| Albert | Web | 3.8 | **PASSED** |
| Maverick | Backend | 2.9 | **NOT_PASSED** |
| Andra | Backend | 2.5 | **PASSED** |
| Cassandra | Mobile | 3.0 | **PASSED** |


- Get list of cumlaude students, GPA should be greater than equal to **3.5** GPA
- Group student by status
- Count interest, how many took the `Mobile`, `Backend` or `Web` interest.
- Order students by name **ascending** order
- Order students by GPA **descending** order

File `Student.java`
```java
public class Student {
    private String name;
    private String interest;
    private Double gpa;
    private String status;

    public Student(String name, String interest, Double gpa, String status) {
        this.name = name;
        this.interest = interest;
        this.gpa = gpa;
        this.status = status;
    }

    // Getter and Setter method
}
```

File `Main.java`
```java
public class Main {
    public static void main(String[] args) {
        List<Student> students = List.of(
                new Student("Calvin", "Mobile", 3.5, "PASSED"),
                new Student("Joe", "Backend", 4.0, "PASSED"),
                new Student("Albert", "Web", 3.8, "PASSED"),
                new Student("Maverick", "Backend", 2.9, "NOT_PASSED"),
                new Student("Andra", "Backend", 2.5, "NOT_PASSED"),
                new Student("Cassandra", "Mobile", 3.0, "PASSED")
        );

        // Get list cumlaude
        List<Student> cumlaudeStudents = students
                .stream()
                .filter(v -> v.getGpa() >= 3.5)
                .collect(Collectors.toList());
        System.out.println(cumlaudeStudents);

        // Group by status
        Map<String, List<Student>> groupByStatus = students
                .stream()
                .collect(Collectors.groupingBy(v -> v.getStatus().toLowerCase()));
        System.out.println(groupByStatus);

        // Count by Interest
        Map<String, Long> countInterest = students
                .stream()
                .collect(Collectors.groupingBy(v -> v.getInterest().toLowerCase(), Collectors.counting()));
        System.out.println(countInterest);

        // Bonus Order by Name Ascending
        List<Student> orderByNameAscending = students
                .stream()
                .sorted(Comparator.comparing(Student::getName))
                .collect(Collectors.toList());
        orderByNameAscending.forEach(v -> System.out.println(v.getName()));

        System.out.println();

        // Order by GPA
        List<Student> orderByGPADescending = students
                .stream()
                .sorted(Comparator.comparing(Student::getGpa).reversed())
                .collect(Collectors.toList());
        orderByGPADescending.forEach(v -> System.out.println(v.getName() + " :: " + v.getGpa()));

    }
}
```