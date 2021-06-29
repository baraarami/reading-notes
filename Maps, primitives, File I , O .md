# FileIO
#### File handling
 the key function for working with files in Python is the open() function.
The open() function takes two parameters; filename, and mode, for example:
f = open("demofile.txt")
There are four different methods (modes) for opening a file:
"r" - Read - Default value. Opens a file for reading, error if the file does not exist
"a" - Append - Opens a file for appending, creates the file if it does not exist
"w" - Write - Opens a file for writing, creates the file if it does not exist
"x" - Create - Creates the specified file, returns an error if the file exists


# Exceptions
#### What are Exceptions?
Exceptions are events that are used to modify the flow of control through a program when the error occurs. Exceptions get triggered automatically on finding errors in Python.
I will give some example of exceptions:
Try/except: catch the error and recover from exceptions hoist by programmers or Python itself.
Try/finally: Whether exception occurs or not, it automatically performs the clean-up action.
Assert: triggers an exception conditionally in the code.
Raise: manually triggers an exception in the code.
#### Questions and Exercises

" #### Questions 
Is the following code legal?
try {
    
} finally {
    
}
What exception types can be caught by the following handler?
catch (Exception e) {
     
}
What is wrong with using this type of exception handler?
Is there anything wrong with the following exception handler as written? Will this code compile?
try {

} catch (Exception e) {
    
} catch (ArithmeticException a) {
    
}
Match each situation in the first list with an item in the second list.
int[] A;
A[0] = 0;
The JVM starts running your program, but the JVM can't find the Java platform classes. (The Java platform classes reside in classes.zip or rt.jar.)
A program is reading a stream and reaches the end of stream marker.
Before closing the stream and after reaching the end of stream marker, a program tries to read the stream again.
__error
__checked exception
__compile error
__no exception
#### Exercises
Add a readList method to ListOfNumbers.java. This method should read in int values from a file, print each value, and append them to the end of the vector. You should catch all appropriate errors. You will also need a text file containing numbers to read in.
Modify the following cat method so that it will compile.
public static void cat(File file) {
    RandomAccessFile input = null;
    String line = null;

    try {
        input = new RandomAccessFile(file, "r");
        while ((line = input.readLine()) != null) {
            System.out.println(line);
        }
        return;
    } finally {
        if (input != null) {
            input.close();
        }
    }
}   "






























