# 2.2 Big O Analysis

## Guidelines for Big O Analysis (worst case)

### Loops

The running time of a loop is, at most, the running time of the statements inside of the loop multiplied by the number of iterations.

```java
// executes n times

for (i = 1; i <= n; i++) 
    m = m + 2;  // constant time, c
```

Running time = $$c*n=cn=O(n)$$

### Nested loops

Analyze from the inside out. Total running time is the product of the sizes of all the loops.

```java
// outer loop executed n times
for (i = 1; i <= n; i++) {
    // inner loop executed n times
    for (j = 1; j <= n; j++) 
        k = k + 1; // constant time
}
```

Running time = $$c*n*n=cn^2=O(n^2)$$

### Consecutive Statements

Add the time complexities of each statement.

```java
x = x + 1; // constant time
// executed n times
for (i = 1; i <=n; i++)
    m = m + 2; // constant time
// outer loop executed n times
for (i = 1; i <=n; i++) {
    // inner loop executed n times
    for (j = 1; j <= n; j++) 
        k = k + 1; // constant time
}
```

Running time = $$c_0+c_1n+c_2n^2=O(n^2)$$

### If-then-else statements

The test plus either the then part or the else part (whichever is larger).

```java
// test: constant
if (length() == 0) 
        return false; // then part: constant
else  // else part: (constant + constant) * n
    for (int n = 0; n < length(); n++) 
        // another if: constant + constant (no else part)
        if (!list[n].equals(otherList.list[n]))
            return false; //constant
```

Running time = $$c_0+c_1+(c_2+c_3)*n=O(n)$$

### Logarithmic Complexity

An algorithm is $$O(log n)$$if it takes constant time to cut the problem size by a fraction (usually 1/2).

```java
for (i = 1; i <=n; )
    i = i * 2;
```

The value of `i` doubling every time. Initially `i=1`, then `i=2`, then `i=4`, `i=8`, and so on.

Let's assume the loop is executing $$k$$. At the $$k^{th}$$ step $$2^k=n$$ and at the $$(k+1)^{th}$$ step we come out of the loop. Take the logarithm of both sides and solve for k (remember, we are in base 2).

$$
\begin{align} 2^k&=n\\log(2^k)&=log(n)\\klog(2)&=log(n)\\k&=log(n)\end{align}
$$

Running time = $$log(n)$$
