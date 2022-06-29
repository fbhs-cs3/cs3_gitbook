# 1.6 Bitwise Operators

## Integer Types in Java

First off, recall that in Java, has multiple primitive types that represent integer values:

* `long` - 64-bit integer
* `int` - 32-bit integer
* `short` - 16-bit integer
* `byte` - 8-bit integer

We can manipulate data in these types at the _<mark style="color:red;">bit</mark>_ level using <mark style="color:red;">bitwise operators</mark>.

## Bitwise Operators

* `>>` bit shift right
* `<<` bit shift left
* `&` bitwise AND
* `|` bitwise OR
* `^` bitwise XOR

### Bit Shift Operators

`>>` and `<<` are used to _shift_ the bits to the left or right a certain number of places.

```java
System.out.println(15 >> 2);  // 3
```

> This means, take the integer value `15` (or `1111`) and shift the bits to the right 2 places, filling in with 0s on the left.
>
> This results in `0011` or `3`

Like wise `<<` means to shift the bits to the left:

```java
System.out.println(15 << 2);  // 60
```

> Take `1111` and shift the bits to the left 2 places
>
> This result is `111100` or `60`

#### <mark style="color:red;">The</mark> <mark style="color:red;"></mark><mark style="color:red;">**math**</mark> <mark style="color:red;"></mark><mark style="color:red;">behind bit shift</mark>

To better understand what's happening, let's look for a pattern:

```java
32 >> 1  // 100000 >> 1 == 10000 == 16
16 >> 1  //  10000 >> 1 ==  1000 ==  8
 8 >> 1  //   1000 >> 1 ==   100 ==  4
 4 >> 1  //    100 >> 1 ==    10 ==  2
 2 >> 1  //     10 >> 1 ==     1 ==  1
 1 >> 1  //      1 >> 1 ==     0 ==  0
```

Bit shifting to the right by 1 has the same result as dividing by 2.  That is,&#x20;

> `x >> 1 == x / 2`

We can actually generalize this pattern and the following statement is true:

> `x >> n == x / (Math.pow(2, n))`

So if bit shifting to the right is dividing by 2, what would bit shifting left do?

```java
1 << 1 //   1 << 1 ==  10 == 2
2 << 1 //  10 << 1 == 100 == 4
4 << 1 // 100 << 1 = 1000 == 8
...
```

and so on.   So we can see that bit shifting left multiplies by 2, that is

> `x << 1 == x * 2`

{% hint style="info" %}
Bit Shift Summary

`(x >> n) == x / (Math.pow(2, n))`

and

`(x << n) == x * (Math.pow(2, n))`
{% endhint %}

### Bitwise AND (&)

1. Write each operand in binary
2. Go bit by bit through both numbers, if both bits are 1, the result is 1, otherwise the result is 0
3. Convert the result back to decimal

#### Example

```java
15 & 6 == 6
```

Why?

```
  1111 
& 0110
  ----
  0110
```



**Another Example**

```java
25 & 10 == 8
```

Why?

```
  11001 
& 01010
  ----
  01000
```

### **Bitwise** OR (|)

1. Write each operand in binary
2. Go bit by bit through both numbers, if either bit is 1, the result is 1 otherwise the result is 0
3. Convert the result back to decimal

**Example**

```java
15 | 6 == 15
```

Why?

```
  1111
| 0110
  ----
  1111
```

### **Bitwise** XOR (^)

1. Write each operand in binary
2. Go bit by bit through both numbers, if _exactly_ one of the bits is 1, the result is 1, otherwise the result is 0
3. Convert the result back to decimal

**Example**

```java
15 ^ 6 == 7
```

Why?

```
  1111
^ 0110
  ----
  1001
```



## So what's it used for?

While bitwise operators more than likely aren't going to be something that you use in every program, they do have some use cases where they are needed to improve performance and/or reduce errors.

* Low-level device control
* Error detection and correction algorithms
* Data compression
* Encryption
* Optimization

### Get Green from an RGB color

```java
// arithmetic
(rgb / 256) % 256
```

```java
//bitwise
(rgb >> 8) & 0xFF
```

Both do the same thing, but the second will generally be _faster_.

### Check if a number is **even**

```java
(x & 1 == 0)
```

This solution relies on two things:

* 2 equates to 0001
* The rightmost number for all odd numbers greater than 2 is 1

Any time the final bit evaluates to 1, you know that it matched and is, therefore, an odd number. If it instead evaluates to 0, you know that no numbers matched and therefore it’s even.

### Convert characters to uppercase and lowercase

You can convert any character, `ch`, to the opposite case using `ch ^= 32`

This is because the binary representation of lowercase and uppercase letters are nearly identical, with only 1 bit of difference.

`'A' == 65 (1000001)` and `'a' == 97 (1100001)`

```
 1000001        65
^0100000       ^32
 -------        --
 1100001        97
```
