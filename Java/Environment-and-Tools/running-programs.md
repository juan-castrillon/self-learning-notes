---
title: Running Programs
parent: Environment and tools
grand_parent: Java
nav_order: 4
---

# Running Programs on your computer

## Installing Java on your computer

In this topic, you will compile and run the simplest Hello World program on your computer. There is one prerequisite: you need to install JDK to develop Java applications. 

To check that the installation has been completed, let's check the version of Java by typing the following command in a terminal:

```
java -version
```

It outputs the version of Java that is installed on your computer. If it does not work correctly, open the installation instructions and try to set the path variable in your operating system.

## Writing a program
Let's write a simple program and then start it on your computer. To do that we will use a terminal.

Step 1. Create a file named Main.java using any text editor (such as TextPad or NotePad++ for Windows) and save it in a folder.

Step 2. Paste the following source code into this file:

```java
public class Main {

    public static void main(String[] args) {
        System.out.println("Hello, Java");
    }
}
```
The public class name must be the same as the file name.

## Compiling and running a program

To run the program, we will use a terminal installed in your OS. All the following commands need to be executed from within the same folder that the `.java` file is created.

Step 3. Compile the program using the following command in the terminal:

```
javac Main.java
```

The javac command asks the compiler to translate the source code into bytecode. The result of this command is a file named `Main.class`.

Step 4. Run the compiled program (make sure that your terminal is open in the same directory as your source file):

```
java -cp . Main
```

The java command starts a Java application. It does this by starting a JRE and invoking the main method inside the Main class.

The -cp parameter (classpath) specifies the location of user-defined classes and packages. The dot . means the current terminal directory. We will consider it in detail in the next topics.

> Note: you do not need to specify the .class extension when running a program.


The program should output the following text:

```
Hello, Java
```

> Since Java 11 it is possible to compile and run Java source code file using a single command java Main.java. It will compile the file in-memory, so it does not produce a .class file. Many developers don't know this small but interesting feature.