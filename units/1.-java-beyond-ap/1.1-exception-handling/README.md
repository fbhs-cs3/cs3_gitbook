# 1.1 Exception Handling

## Definitions

#### **Exception handling** is one way to handle <mark style="color:red;">**runtime**</mark> <mark style="color:red;"></mark><mark style="color:red;">errors</mark>.

* Keeps the regular flow of the application uninterrupted
* Allows us to handle both expected and unexpected errors
* Keeps the program from **crashing** when the user does something unexpected

#### An <mark style="color:red;">**exception**</mark> is an unwanted or unexpected event which occurs during run time.

* Invalid user input
* Device failure
* Loss of network connection
* Out of memory
* Code errors (oops!)
* Trying to open an unavailable file

### The `Throwable` class

![All exception and error types are subclasses of the class Throwable](https://media.geeksforgeeks.org/wp-content/uploads/Exception-in-java1.png)

### Types of Exceptions

![There are different types of exceptions.](https://media.geeksforgeeks.org/wp-content/uploads/20220120111809/Group21-660x330.jpg)



#### **Built-in** Exceptions

These are available in Java libraries and are suitable for certain error situations.

* **Checked Exceptions**
  * Checked at compile-time by the compiler
* **Unchecked Exceptions**
  * Compiler does _not_ check these at compile time

#### **User-Defined** Exceptions

* Sometimes the built-in exceptions just don't cover it. In those cases, the user can define their own exceptions.

#### Example&#x20;

What is wrong with the code below?

```java
public class ExceptionExample {
    public static void main(String[] args) {
        String name = null;

        System.out.println(name.length());
    }
}
```

<details>

<summary>Click to see the answer</summary>

We get a `NullPointerException`

**Output:**

```
Exception in thread "main" java.lang.NullPointerException: Cannot invoke "String.length()" because "name" is null at Example01.main(Example01.java:6)
```

This is an <mark style="color:red;">**unchecked**</mark> exception (so, not a compile-error)

</details>

### Advantages of Exception Handling

* Easy identification of program code and error-handling code
* Meaningful error reporting
* Identifying error types
* Allows a program to keep running even when errors occur
* Keeps errors from spreading (ie. crashing other parts of a larger application)

## Handling Exceptions

In order to keep a program from crashing when it raises an exception, we must handle the exception.  We do this using a <mark style="color:red;">try-catch block</mark>.

```java
try {
    // block of code you think might raise an exception
} catch (ExceptionType1 exOb) {
    // exception handler for ExceptionType1
} catch (ExceptionType2 exOb) {
    // exception handler for ExceptionType2
}
// optional
finally {
    // block of code to execute after try block ends
}
```

**Important Notes**

* There can be more than one statement that might throw an exception. Put each statement within their own **try** block and provide separate exception handling within their own **catch** block.
* If an exception occurs within a **try** block, that exception is only handled by the **catch** block with the type of exception declared.
* For each **try** block there can be zero or more **catch** blocks, but **only one** `finally` block.
* The `finally` block is _optional_. It **always** executes whether an exception occurred or not.
* The `finally` block is usually used for clean up code like closing a file or a network connection.

### Try/Catch Example

```java
public class TryCatchExample {
    public static void main(String[] args) {
        String name = null;

        try {
            System.out.println(name.length()); // exception might occur here!
        } catch(NullPointerException exception) { // ONLY catches NullPointerException
            System.out.println("name is null!");
        }
    }
}
```

#### Output

`name is null!`
