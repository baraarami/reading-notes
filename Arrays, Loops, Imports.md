# Packages and Import

Package = directory. Java classes can be grouped together in packages.

The first statement, other than comments, in a Java source file, must be the package declaration.

Package declaration syntax
The statement order is as follows. Comments can go anywhere.

1) Package statment (optional).
2) Imports (optional).
3) Class or interface definitions.


// This source file must be Drawing.java in the illustration directory.

package illustration;

import java.awt.*;

public class Drawing {
    . . .
}


 ## Common imports
import java.awt.; Common GUI elements. import java.awt.event.; The most common GUI event listeners. import javax.swing.; More common GUI elements. Note "javax". import java.util.; Data structures (Collections), time, Scanner, etc classes. import java.io.; Input-output classes. import java.text.; Some formatting classes. import java.util.regex.*; Regular expression classes.

## import FAQ
Q: I've imported java.awt., why do I also need java.awt.event.? A: The wildcard "*" only makes the classes in this package visible, not any of the subpackages.

Q: Why don't I need an import to use String, System, etc? A: All classes in the java.lang package are visible without an import.

Different types of loops in Java
j,bh

## Here are the types of loops that we can find in Java:
Simple for loop Enhanced for-each loop While loop Do-While loop

1) For - repeat by incrementing a counter

2) While - repeat while true

3) Do-While - first conditional evaluation happens after first iteration
