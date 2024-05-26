# Introduction

Core Java refers to the foundational features and libraries of the Java programming language that are used for building general-purpose applications. Below is a cheat sheet covering essential concepts and practical use cases in Core Java.

# Basic Syntax

- Hello World:
```
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

# Data Types

- Primitive Data Types:

```
int myNum = 5;               // Integer (whole number)
float myFloatNum = 5.99f;    // Floating point number
char myLetter = 'D';         // Character
boolean myBool = true;       // Boolean
```

- Wrapper Classes:
```
Integer myInt = 5;
Float myFloat = 5.99f;
Character myChar = 'D';
Boolean myBoolean = true;
```

# Control Flow

- If-Else:
```
if (condition) {
    // code block
} else if (condition) {
    // code block
} else {
    // code block
}
```

- Switch:
```
int day = 4;
switch (day) {
    case 1:
        System.out.println("Monday");
        break;
    case 2:
        System.out.println("Tuesday");
        break;
    default:
        System.out.println("Invalid day");
        break;
}
```

# Loops:

- For Loop:
```
for (int i = 0; i < 5; i++) {
    System.out.println(i);
}
```

- While Loop:
```
int i = 0;
while (i < 5) {
    System.out.println(i);
    i++;
}
```

- Do-While Loop:
```
int i = 0;
do {
    System.out.println(i);
    i++;
} while (i < 5);
```

# Arrays

- One-Dimensional Array:
```
int[] myArray = {1, 2, 3, 4, 5};
```

- Two-Dimensional Array:
```
int[][] my2DArray = {
    {1, 2, 3},
    {4, 5, 6}
};
```

# Methods

- Method Definition:
```
public static void myMethod() {
    // code block
}
```

- Method with Parameters:
```
public static void myMethod(String fname) {
    System.out.println(fname + " Refsnes");
}
```

- Method with Return Value:
```
public static int addNumbers(int a, int b) {
    return a + b;
}
```

# Object-Oriented Programming

- Classes and Objects:
```
public class MyClass {
    int x = 5;
}

public class Main {
    public static void main(String[] args) {
        MyClass myObj = new MyClass();
        System.out.println(myObj.x);
    }
}
```

- Constructors:
```
public class MyClass {
    int x;

    public MyClass() {
        x = 5;
    }
}
```

- Inheritance:
```
class Animal {
    public void animalSound() {
        System.out.println("The animal makes a sound");
    }
}

class Dog extends Animal {
    public void animalSound() {
        System.out.println("The dog says: bow wow");
    }
}
```

- Polymorphism:
```
class Animal {
    public void animalSound() {
        System.out.println("The animal makes a sound");
    }
}

class Dog extends Animal {
    public void animalSound() {
        System.out.println("The dog says: bow wow");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal myAnimal = new Dog();
        myAnimal.animalSound();
    }
}
```

- Abstract Classes and Methods:
```
abstract class Animal {
    public abstract void animalSound();
    public void sleep() {
        System.out.println("Zzz");
    }
}

class Dog extends Animal {
    public void animalSound() {
        System.out.println("The dog says: bow wow");
    }
}
```

- Interfaces:
```
interface Animal {
    public void animalSound();
    public void sleep();
}

class Dog implements Animal {
    public void animalSound() {
        System.out.println("The dog says: bow wow");
    }
    public void sleep() {
        System.out.println("Zzz");
    }
}
```

# Exception Handling

- Try-Catch:
```
try {
    int[] myNumbers = {1, 2, 3};
    System.out.println(myNumbers[10]);
} catch (Exception e) {
    System.out.println("Something went wrong.");
}
```

- Finally:
```
try {
    int[] myNumbers = {1, 2, 3};
    System.out.println(myNumbers[10]);
} catch (Exception e) {
    System.out.println("Something went wrong.");
} finally {
    System.out.println("The 'try catch' is finished.");
}
```

- Throw:
```
public class Main {
    static void checkAge(int age) {
        if (age < 18) {
            throw new ArithmeticException("Access denied - You must be at least 18 years old.");
        } else {
            System.out.println("Access granted - You are old enough!");
        }
    }

    public static void main(String[] args) {
        checkAge(15);
    }
}
```

# Collections Framework

- ArrayList:
```
import java.util.ArrayList;

public class Main {
    public static void main(String[] args) {
        ArrayList<String> cars = new ArrayList<String>();
        cars.add("Volvo");
        cars.add("BMW");
        cars.add("Ford");
        System.out.println(cars);
    }
}
```

- HashMap:
```
import java.util.HashMap;

public class Main {
    public static void main(String[] args) {
        HashMap<String, String> capitalCities = new HashMap<String, String>();

        // Add keys and values (Country, City)
        capitalCities.put("England", "London");
        capitalCities.put("Germany", "Berlin");
        capitalCities.put("Norway", "Oslo");
        capitalCities.put("USA", "Washington DC");
        System.out.println(capitalCities);
    }
}
```

- HashSet:
```
import java.util.HashSet;

public class Main {
    public static void main(String[] args) {
        HashSet<String> cars = new HashSet<String>();
        cars.add("Volvo");
        cars.add("BMW");
        cars.add("Ford");
        System.out.println(cars);
    }
}
```

# Streams

- Filtering and Iterating:
```
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class Main {
    public static void main(String[] args) {
        List<String> strings = Arrays.asList("abc", "", "bc", "efg", "abcd", "", "jkl");
        List<String> filtered = strings.stream().filter(string -> !string.isEmpty()).collect(Collectors.toList());
        System.out.println(filtered);
    }
}
```

- Map and Collect:
```
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class Main {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(3, 2, 2, 3, 7, 3, 5);
        List<Integer> squaresList = numbers.stream().map(i -> i * i).distinct().collect(Collectors.toList());
        System.out.println(squaresList);
    }
}
```

# File I/O

- Reading a File:
```
import java.io.File;
import java.io.FileNotFoundException;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        try {
            File myObj = new File("filename.txt");
            Scanner myReader = new Scanner(myObj);
            while (myReader.hasNextLine()) {
                String data = myReader.nextLine();
                System.out.println(data);
            }
            myReader.close();
        } catch (FileNotFoundException e) {
            System.out.println("An error occurred.");
            e.printStackTrace();
        }
    }
}
```

- Writing to a File:
```
import java.io.FileWriter;
import java.io.IOException;

public class Main {
    public static void main(String[] args) {
        try {
            FileWriter myWriter = new FileWriter("filename.txt");
            myWriter.write("Files in Java might be tricky, but it is fun enough!");
            myWriter.close();
            System.out.println("Successfully wrote to the file.");
        } catch (IOException e) {
            System.out.println("An error occurred.");
            e.printStackTrace();
        }
    }
}
```

# Concurrency

- Creating a Thread by Extending Thread Class:
```
public class Main extends Thread {
    public void run() {
        System.out.println("This code is running in a thread");
    }

    public static void main(String[] args) {
        Main thread = new Main();
        thread.start();
    }
}
```

- Creating a Thread by Implementing Runnable Interface:
```
public class Main implements Runnable {
    public void run() {
        System.out.println("This code is running in a thread");
    }

    public static void main(String[] args) {
        Main obj = new Main();
        Thread thread = new Thread(obj);
        thread.start();
    }
}
```

# Java 8 Features

- Lambda Expressions:
```
interface StringFunction {
    String run(String str);
}

public class Main {
    public static void main(String[] args) {
        StringFunction exclaim = (s) -> s + "!";
        StringFunction ask = (s) -> s + "?";
        printFormatted("Hello", exclaim);
        printFormatted("Hello", ask);
    }

    public static void printFormatted(String str, StringFunction format) {
        String result = format.run(str);
        System.out.println(result);
    }
}
```

- Streams API:
```
import java.util.Arrays;
import java.util.List;

public class Main {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(2, 3, 4, 5);
        List<Integer> squares = numbers.stream().map(x -> x * x).collect(Collectors.toList());
        System.out.println(squares);
    }
}
```

- Optional:
```
import java.util.Optional;

public class Main {
    public static void main(String[] args) {
        Optional<String> optional = Optional.of("Hello");
        optional.ifPresent(System.out::println);
    }
}
```

# Resources
- [Java SE Documentation](https://docs.oracle.com/javase/8/docs/api/)
- [Java Tutorials](https://www.javatpoint.com/java-tutorial)
- [Java 8 Features](https://www.javatpoint.com/java-8-features)

This cheat sheet provides a comprehensive overview of core Java concepts, covering basic syntax, object-oriented programming, collections, streams, and file I/O, among other essential topics. 
