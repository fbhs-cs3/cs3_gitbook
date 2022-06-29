# 1.4 Ternary Operator & Switch/Case

## The Ternary Operator

The operators you have worked with so far have all been either <mark style="color:red;">**binary**</mark> <mark style="color:red;"></mark><mark style="color:red;">operators</mark> or <mark style="color:red;">**unary**</mark> <mark style="color:red;"></mark><mark style="color:red;">operators</mark>**.  B**inary operators have **2** operands, and unary operators have **1.**

| binary operators | unary operators |
| :--------------: | :-------------: |
|         +        |        ++       |
|         -        |        --       |
|        \*        |        !        |
|        &&        |                 |
|       \|\|       |                 |

#### The <mark style="color:red;">**ternary**</mark> operator has **3** operands:

> (condition) ? (thing to return if true) : thing to return if false)

{% hint style="info" %}
The `?` and the `:` make up the ternary operator
{% endhint %}

The ternary operator is essentially a **shortcut** for an if/else statement:

```java
String result;
if (x > 0) 
    string = "greater!";
else
    string = "less!";
```

is equivalent to

```java
String result = (x > 0) ? "greater!" : "less!";
```

{% hint style="warning" %}
While you can use _nested_ ternary operators, it is generally **avoided** because it ends up making your code **more complex**.
{% endhint %}

```java
// create a variable
int n1 = 2, n2 = 9, n3 = -11;

// nested ternary operator
// to find the largest number
int largest = (n1 >= n2) ? ((n1 >= n3) ? n1 : n3) : ((n2 >= n3) ? n2 : n3);
System.out.println("Largest Number: " + largest);
```



## **Switch/Case** statements

* The <mark style="color:red;">**switch**</mark> statement evaluates its expression, then executes all statements that follow the matching `case` label until `break` is reached.
* Unlike _if-then_ and _if-then-else_ statements, the **switch** statement can have a number of possible execution paths.
* A **switch** works with the byte, short, char, and int primitive data types. It also works with _enumerated_ types, the _String_ class, and wrapper classes (Integer, Double, etc.)
* The body of a **switch** statement is known as a _switch block_.
* A statement in the **switch** block can be labeled with one or more `case` or `default` labels.

```java
public class Example08 {
    public static void main(String[] args) {

        int month = 8;
        String monthString;
        switch (month) {
            case 1:  monthString = "January";
                     break;
            case 2:  monthString = "February";
                     break;
            case 3:  monthString = "March";
                     break;
            case 4:  monthString = "April";
                     break;
            case 5:  monthString = "May";
                     break;
            case 6:  monthString = "June";
                     break;
            case 7:  monthString = "July";
                     break;
            case 8:  monthString = "August";
                     break;
            case 9:  monthString = "September";
                     break;
            case 10: monthString = "October";
                     break;
            case 11: monthString = "November";
                     break;
            case 12: monthString = "December";
                     break;
            default: monthString = "Invalid month";
                     break;
        }
        System.out.println(monthString);
    }
}
```

{% hint style="warning" %}
The `break` statements are necessary because without them, statements in switch blocks **fall through**: All statements after the matching case label are executed in sequence, regardless of the expression of subsequent case labels, until a `break` statement is encountered.
{% endhint %}

### Switch Fall Through

The next example shows how statements in a switch block fall through.

The program displays the month corresponding to the integer `month` and the months that follow in the year.

```java
import java.util.ArrayList;

public class Example09 {

    public static void main(String[] args) {
        ArrayList<String> futureMonths =
            new ArrayList<String>();

        int month = 8;

        switch (month) {
            case 1:  futureMonths.add("January");
            case 2:  futureMonths.add("February");
            case 3:  futureMonths.add("March");
            case 4:  futureMonths.add("April");
            case 5:  futureMonths.add("May");
            case 6:  futureMonths.add("June");
            case 7:  futureMonths.add("July");
            case 8:  futureMonths.add("August");
            case 9:  futureMonths.add("September");
            case 10: futureMonths.add("October");
            case 11: futureMonths.add("November");
            case 12: futureMonths.add("December");
                     break;
            default: break;
        }

        if (futureMonths.isEmpty()) {
            System.out.println("Invalid month number");
        } else {
            for (String monthName : futureMonths) {
               System.out.println(monthName);
            }
        }
    }
}
```

Compile and run `Example09.java`.   Your output should look like this:

> August&#x20;
>
> September&#x20;
>
> October&#x20;
>
> November&#x20;
>
> December

{% hint style="info" %}
Technically the final `break` isn't required because the switch statement is over at that point, but having it there is recommended to make modifying the code easier and less error prone.
{% endhint %}

{% hint style="info" %}
The `default` section handles all values that are not explicitly handled by one of the `case` conditions.
{% endhint %}

### Multiple Case Labels

The next example shows how a statement can have multiple `case` labels.

The code calculates the number of days in a particular month.

```java
class Example10 {
    public static void main(String[] args) {

        int month = 2;
        int year = 2000;
        int numDays = 0;

        switch (month) {
            case 1: case 3: case 5:
            case 7: case 8: case 10:
            case 12:
                numDays = 31;
                break;
            case 4: case 6:
            case 9: case 11:
                numDays = 30;
                break;
            case 2:
                if (((year % 4 == 0) && 
                     !(year % 100 == 0))
                     || (year % 400 == 0))
                    numDays = 29;
                else
                    numDays = 28;
                break;
            default:
                System.out.println("Invalid month.");
                break;
        }
        System.out.println("Number of Days = "
                           + numDays);
    }
}
```

## So what to use?

Deciding whether to use `if-else`, **ternary**, or `switch-case` is based on readability and the expression that the statement is testing.

* Ternary operators can be more readable than if/else but really only make sense if you want to assign a value based on the condition.
* `if`-`else` statements can test expressions based on ranges of values or conditions (&&, ||)
* `switch` statements test expressions based on a single integer, enumerated value, or String.
