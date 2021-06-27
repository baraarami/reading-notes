# Packages and Import
Package = directory. Java classes can be grouped together in packages. A package name is the same as the directory (folder) name which contains the .java files. You declare packages when you define your Java program, and you name the packages you want to use from other libraries in an import statement.

Package declaration
The first statement, other than comments, in a Java source file, must be the package declaration.

Following the optional package declaration, you can have import statements, which allow you to specify classes from other packages that can be referenced without qualifying them with their package.

Default package. Altho all Java classes are in a directory, it's possible to omit the package declaration. For small programs it's common to omit it, in which case Java creates what it calls a default package. Sun recommends that you do not use default packages.

Package declaration syntax
The statement order is as follows. Comments can go anywhere.

Package statment (optional).
Imports (optional).
Class or interface definitions.
// This source file must be Drawing.java in the illustration directory.

package illustration;

import java.awt.*;

public class Drawing {
    . . .
}
Imports: three options
The JOptionPane class is in the swing package, which is located in the javax package. The wildcard character (*) is used to specify that all classes with that package are available to your program. This is the most common programming style.

import javax.swing.*;  // Make all classes visible altho only one is used.

class ImportTest {
    public static void main(String[] args) {
        JOptionPane.showMessageDialog(null, "Hi");
        System.exit(0);
    }
}
Classes can be specified explicitly on import instead of using the wildcard character.

import javax.swing.JOptionPane;  // Make a single class visible.

class ImportTest {
    public static void main(String[] args) {
        JOptionPane.showMessageDialog(null, "Hi");
        System.exit(0);
    }
}
Alternately we can the fully qualified class name without an import.

class ImportTest {
    public static void main(String[] args) {
        javax.swing.JOptionPane.showMessageDialog(null, "Hi");
        System.exit(0);
    }
}
Common imports
There are 166 packages containing 3279 classes and interfaces in Java 5. However, only a few packages are used in most programming. GUI programs typically use at least the first three imports.

import java.awt.*;	Common GUI elements.
import java.awt.event.*;	The most common GUI event listeners.
import javax.swing.*;	More common GUI elements. Note "javax".
import java.util.*;	Data structures (Collections), time, Scanner, etc classes.
import java.io.*;	Input-output classes.
import java.text.*;	Some formatting classes.
import java.util.regex.*;	Regular expression classes.
import FAQ
###### *Q: Does importing all classes in a package make my object file (.class or .jar) larger?
###### *A: No, import only tells the compiler where to look for symbols.

###### *Q: Is it less efficient to import all classes than only the classes I need?
###### *A: No. The search for names is very efficient so there is no effective difference.

###### *Q: Doesn't it provide better documentation to import each class explicitly?
###### *A: This shows good intentions, but ...

It's hard to remember to remove classes when they are no longer used, so the import list is surprisingly often wrong. It can seriously slow down reading because unusual or unexpected class imports make me look for that class, only to discover that it must have been used in an earlier version.
Explicit class imports permit accidentally defining classes with names that conflict with the standard library names. This is very bad. Using "*" to import all classes prevents this dangerous naming accident.
It's annoying to always update this list, altho if you use NetBeans, fixing the list is only a click away (see below).
Q: I've imported java.awt.*, why do I also need java.awt.event.*?
A: The wildcard "*" only makes the classes in this package visible, not any of the subpackages.

###### *Q: Why don't I need an import to use String, System, etc?
###### *A: All classes in the java.lang package are visible without an import.

###### *Q: Is the order of the imports important?
###### *A: No. Group them for readability.

NetBeans creates packages by default
The project name is used as the default package name, but you can change it.
A directory / folder is created with this project name. This directory name is the name of your package.
A package declaration is automatically inserted into each new source file it creates.
When you build a main project, the double-clickable .jar file uses this project/package/directory name.
NetBeans will create your imports
If you forgot to write import statements, or don't remember which package a class is in, no problem. Just right click on the source file and choose Fix Imports. It will add all necessary import statements.

Static imports in Java 5
Java 5 added an import static option that allows static variables (typically constants) to be referenced without qualifying them with a class name. For example, after

import static java.awt.Color;
It would then be possible to write

   Color background = RED;
instead of

   Color background = Color.RED;
Adding this "feature" wasn't the best idea because it leads to name pollution and confusion about which class constants come from. Even Sun (see References below) basically advises not to use it!



# A Guide to Java Loops

## 1. Overview
In this article, we'll look at a core aspect of the Java language – executing a statement or a group of statements repeatedly – using loops.

 ## 2. Intro to Loops
In programming languages, looping is a feature which facilitates the execution of a set of instructions until the controlling Boolean-expression evaluates to false.

Java provides different types of loops to fit any programming need. Each loop has its own purpose and a suitable use case to serve.

Here are the types of loops that we can find in Java:

Simple for loop
Enhanced for-each loop
While loop
Do-While loop

## 3. For Loop
A for loop is a control structure that allows us to repeat certain operations by incrementing and evaluating a loop counter.

For a detailed example, have a look at the dedicated post: Java For Loop.

## 4. While Loop
The while loop is Java's most fundamental loop statement. It repeats a statement or a block of statements while its controlling Boolean-expression is true.

For a detailed example, have a look at the dedicated post: Java While Loop.

## 5. Do-While Loop
The do-while loop works just like the while loop except for the fact that the first condition evaluation happens after the first iteration of the loop.


## freestar
For a detailed example, have a look at the dedicated post: Java Do-While Loop.

 ## 6. Conclusion
In this quick tutorial, we showed the different types of loops that are available in the Java programming language.

We also saw how each loop serves a particular purpose given a suitable use case. We discussed the circumstances that are suitable for a given loop implementation.




