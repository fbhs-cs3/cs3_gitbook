# 1.3 Do-While Loops

## Do-While Loop

Suppose we want to write a program that has the user enter an integer until they enter a zero.

**Algorithm:**

1. Ask the user to enter a number
2. If it's 0, stop
3. Otherwise, go back to step 1

Notice that the first step **has** to happen at least once, then it depends on whether the type a 0 or not.

{% hint style="info" %}
<mark style="color:red;">**do-while**</mark> loops ensure that the loop body executes _at least_ once.
{% endhint %}

```java
do {

    // loop body

} while (booleanCondition);
```

The code inside of the loop body will execute **before** `booleanCondition` is checked.

## Keyboard Input

Let's revisit the <mark style="color:red;">`Scanner`</mark> class one more time:

```java
import java.util.Scanner;

public class Example07 {
    public static void main(String[] args) {
        Scanner kb = new Scanner(System.in); // System.in is the keyboard

        System.out.print("Enter an integer followed by the <enter> key: ");
        int n = kb.nextInt(); // read in an integer

        System.out.println("You entered " + n);
    }
}
```

Compile and run `Example07.java`. &#x20;

{% hint style="danger" %}
If the user doesn't type in an `int`, this happens:

```
Enter an integer followed by the <enter> key: h
Exception in thread "main" java.util.InputMismatchException
        at java.base/java.util.Scanner.throwFor(Scanner.java:939)
        at java.base/java.util.Scanner.next(Scanner.java:1594)
        at java.base/java.util.Scanner.nextInt(Scanner.java:2258)
        at java.base/java.util.Scanner.nextInt(Scanner.java:2212)
        at Example09.main(Example09.java:8)
```

What needs to be done to address this?
{% endhint %}
