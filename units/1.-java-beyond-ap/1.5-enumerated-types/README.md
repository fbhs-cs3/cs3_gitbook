# 1.5 Enumerated Types

## `enum` Types

An **enum type** is a special data type that enables for a variable to be a set of predefined constants.

* The variable must be equal to one of the values that have been predefined for it.
* Because they are constants, the names of an enum type's fields are in uppercase letters.
* Common examples include compass directions and days of the week.

{% hint style="info" %}
#### **Enum types** should be used anytime you need to represent a fixed set of constants

* planets in our solar system
* days of the week
* data sets where you know all possible values at compile time
  * choices on a menu
  * command line flags
{% endhint %}

### Day enum

```java
public enum Day {
    SUNDAY, MONDAY, TUESDAY, WEDNESDAY,
    THURSDAY, FRIDAY, SATURDAY
}
```

Here I use the keyword `public` if there is going to be a file called `Day.java`.

Otherwise, if the enum is going to be included in a .java file of another class, drop the `public` (see `Example11.java below`)

```java
enum Day {
    SUNDAY, MONDAY, TUESDAY, WEDNESDAY,
    THURSDAY, FRIDAY, SATURDAY
}

public class Example11 {
    
    public static void describe(Day day) {
        switch (day) {
            case MONDAY:
                System.out.println("Mondays are bad.");
                break;

            case FRIDAY:
                System.out.println("Fridays are better.");
                break;

            case SATURDAY:
            case SUNDAY: 
                System.out.println("Weekends are best!");
                break; 

            default:
                System.out.println("Midweek days are ok.");
                break;
        }
    }

    public static void main(String[] args) {
        describe(Day.THURSDAY);
        describe(Day.MONDAY);
        describe(Day.FRIDAY);
        describe(Day.SUNDAY);
    }
}
```

{% hint style="warning" %}
The `enum` declaration defines a _class_

* The **enum** class body can include methods and other fields
* The compiler automatically adds some special methods when it creates an enum
  * They have a static `values` method that returns an array containing all of the values of the enum in the order they are declared
  * This method can be used in combination with a for-each loop to iterate over the values of an enum
{% endhint %}

### Planet enum

In the following example, `Planet` is an enum type that represents the planets in the solar system.

* They are defined with constant mass and radius properties.
* Each enum constant is declared with values for the mass and radius parameters.
* These values are passed to the constructor when the constant is created.

```java
enum Planet {
    MERCURY (3.303e+23, 2.4397e6),
    VENUS   (4.869e+24, 6.0518e6),
    EARTH   (5.976e+24, 6.37814e6),
    MARS    (6.421e+23, 3.3972e6),
    JUPITER (1.9e+27,   7.1492e7),
    SATURN  (5.688e+26, 6.0268e7),
    URANUS  (8.686e+25, 2.5559e7),
    NEPTUNE (1.024e+26, 2.4746e7);

    private final double mass;   // in kilograms
    private final double radius; // in meters
    Planet(double mass, double radius) {
        this.mass = mass;
        this.radius = radius;
    }
    private double mass() { return mass; }
    private double radius() { return radius; }

    // universal gravitational constant  (m3 kg-1 s-2)
    public static final double G = 6.67300E-11;

    double surfaceGravity() {
        return G * mass / (radius * radius);
    }
    double surfaceWeight(double otherMass) {
        return otherMass * surfaceGravity();
    }
}

public class Example12 {
    public static void main(String[] args) {
        double earthWeight = 150.0;
        double mass = earthWeight/Planet.EARTH.surfaceGravity();
        for (Planet p : Planet.values())
           System.out.printf("Your weight on %s is %f%n",
                             p, p.surfaceWeight(mass));
    }
}
```
