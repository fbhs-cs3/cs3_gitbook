# 2. Algorithm Analysis&#x20;

## Introduction

Let's start by considering the problem of making a grilled cheese sandwich. To make the sandwich:

1. Get the frying pan
2. Get the butter
   * Do we have butter?
     * If yes, put it in the pan.
     * If no, do we want to buy butter?
       * If yes, then go out and buy.
       * If no, stop
3. Turn on the stove, etc.

We are, for a given problem (making a grilled cheese), providing a step-by-step procedure for solving it.

{% hint style="info" %}
The formal definition of an <mark style="color:red;">algorithm</mark> can be stated as

> ### An algorithm is the step-by-step unambiguous instructions to solve a given problem.
{% endhint %}

#### There are two main criteria for judging an algorithm:

* Correctness (does the algorithm solve the problem?)
* Efficiency (how much resources does the algorithm take?)

### Why analyze algorithms?

There are many ways to get from city "A" to city "B".

* flight
* bus
* train
* walking
* etc

Depending on availability and convenience, we choose the one that works best for us.

#### Similarly, in CS, multiple algorithms are available for solving the same problem.

For example, **sorting**...

* insertion sort
* selection sort
* merge sort
* quick sort\*
* heap sort\*
* bogo sort\*\*
* pigeon hole sort\*\*

<mark style="color:red;">Algorithm analysis</mark> helps us determine which algorithm is most efficient in terms of time and space consumed.

The goal of the analysis of algorithms is to compare algorithms mainly in terms of <mark style="color:red;">**running time**</mark>**.**

<mark style="color:red;">**Running Time Analysis**</mark> is the process of determining how processing time increases as the size of the problem (input size) increases.

#### Common types of inputs:

* Size of an array
* Polynomial degree
* Number of elements in a matrix
* Number of bits in the binary representation of the input
* Vertices and edges in a graph
