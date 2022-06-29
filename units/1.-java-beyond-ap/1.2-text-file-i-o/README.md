# 1.2 Text File I/O

<mark style="color:red;">**I/O**</mark> stands for <mark style="color:red;">**Input/Output**</mark>

![Reading from a file (input)](https://www.seas.upenn.edu/\~cis1xx/resources/java/fileIO/io-ins.gif) ![Writing to a file (output)](https://www.seas.upenn.edu/\~cis1xx/resources/java/fileIO/io-outs.gif)

## Writing to a file

We will use the [`PrintWriter`](https://docs.oracle.com/javase/8/docs/api/java/io/PrintWriter.html) class in order to write text to files.  &#x20;

It's really nice because it allows us to use the `.print()`, `.println()`, and `.printf()` methods exactly like we do when printing to the screen using `System.out`.

```java
import java.io.PrintWriter; // import PrintWriter
import java.io.IOException; 

public class Example03 {
    public static void main(String[] args) {

        PrintWriter writer = null;
        try {
            writer = new PrintWriter("output.txt");
            writer.println("Writing to a file.");  
            writer.print("This is another line!");
            writer.println("  But this will be on the same line as the last.");  
        } catch (IOException e) {
            System.out.println(e.getMessage());
        }
        finally {
            writer.close();            
        }
    }
}
```

Compiling and running the`Example03.java` will create a new fill called `output.txt` in the working directory.  Here are the contents out `output.txt` (but you should compile and run the example yourself to make sure!)

#### Add another print statement of your choice, then compile and run Example03.java again.  What do you notice?

{% hint style="danger" %}
Writing to a file **overwrites** the file if it's already there.  For our purposes, that's probably OK. But keep it in mind!
{% endhint %}

#### Writing a list of names to a file

Here's another example demonstrating how the `PrintWriter` class really works just like System.out!

```java
import java.io.PrintWriter;
import java.io.IOException;

public class Example04 {
    public static void main(String[] args) {
        String[] names = {"Alice","Bob","Charles","Danielle"};

        PrintWriter writer = null;
        try {
            writer = new PrintWriter("outputnames.txt");
            for (String name : names) {
                writer.println(name);
            }
        } catch (IOException e) {
            System.out.println(e.getMessage());
        }
        finally {
            writer.close();            
        }
    }
}
```

## Reading from a file

The [`Scanner`](https://docs.oracle.com/javase/9/docs/api/java/util/Scanner.html) class has methods for reading user input (both files and from the keyboard). &#x20;

`Scanner` is in `java.util.Scanner`

```java
import java.io.File; // new import
import java.util.Scanner; 
import java.io.IOException;

public class Example05 {
    public static void main(String[] args) {

        Scanner scan = null;
        
        try {
            File file = new File("names.txt"); // create a File object!
            scan = new Scanner(file);
        } catch (IOException e) {
            System.out.println("File doesn't exist!");
            return; // stop the program if the file isn't there
        }
        
        // as long as there are more lines in the file keep going
        while (scan.hasNextLine()) { 
            System.out.println(scan.nextLine()); // print the next line
        }
        scan.close();
    }
}
```

{% hint style="info" %}
Notice on line 11, a `File` object is created.  Then on line 12, the `Scanner` is passed the `File` object. &#x20;

`Scanner` can actually be used to parse other things (strings, keyboard input, etc.)
{% endhint %}

Compile and run `Example05.java`.  Your output should look something like this:

```
1       Liam        Olivia
2       Noah        Emma
3       Oliver      Charlotte
4       Elijah      Amelia
5       James       Ava
6       William     Sophia
7       Benjamin        Isabella
8       Lucas       Mia
9       Henry       Evelyn
10      Theodore        Harper
```

### Scanner Methods

**Scanner** has quite a few methods, but we will primarily use:

> `String nextLine()`&#x20;
>
> Reads and returns the next line

> `String next()`&#x20;
>
> Reads and returns the next **token** (one word, or number)

> `double nextDouble()`&#x20;
>
> Reads and returns the next token as a `double`

> `int nextInt()`&#x20;
>
> Reads and returns the next token as an `int`

> `boolean hasNext()`&#x20;
>
> `boolean hasNextLine()`&#x20;
>
> `boolean hasNextInt()`&#x20;
>
> `boolean hasNextDouble()`&#x20;
>
> These return true if the next <mark style="color:red;">token</mark> is the indicated type and false otherwise.
>
> We will mostly use these as part of a while loop when we don't know how much data the file has.

{% hint style="info" %}
For now, we will say that a token is the next item in the file up to a space or newline.  This can be changed using the `useDelimiter` method.
{% endhint %}

#### Non-text File Example

```java
import java.util.Scanner;
import java.io.IOException;
import java.io.File;

public class Example06 {
    public static void main(String[] args) {

        Scanner scan = null;
        
        try {
            File file = new File("numbers.txt");
            scan = new Scanner(file);
        } catch (IOException e) {
            System.out.println("File doesn't exist!");
            return; // stop the program since the file isn't there
        }

        int total = 0;
        
        // as long as there is an integer, keep going
        while (scan.hasNextInt()) { 
            total += scan.nextInt(); // add the next integer to the total
        }
        scan.close();

        System.out.printf("Total: %d%n", total); // print Total: followed by 
                                                 // the value in the total 
                                                 // variable followed by
                                                 // a newline character
    }
}
```

Here is what is in `numbers.txt`

```
5
15
2
-3
18
-4
```

Compile and run `Example06.java`.  The output should be

`Total: 33`

## File I/O Reminders

{% hint style="warning" %}
* Enclose the file access in a `try` block and `catch` the `IOException` created if the file isn't found.
* Don't forget to **close** the `PrintWriter` and `Scanner` objects when you're _finished_ reading them.
* Writing to a file that already exists will erase the previous contents in the file (overwrite the file).
{% endhint %}
