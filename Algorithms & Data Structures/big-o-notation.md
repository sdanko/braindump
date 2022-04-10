# Big O Notation

Big O notation is used to describe the performance or complexity of an algorithm. It is essentially measuring the rate-of-growth in time, for an algorithm, with reference to the size of input. Big O favors the worst-case performance scenario and will always assume the upper limit where the algorithm will perform the maximum number of iterations. Here are some orders of growth:

## O(1)

0(1) describes an algorithm that will always execute in the same time (or space) regardless of the size of the input data set.

## O(N)

O(N) describes an algorithm whose performance will grow linearly and in direct proportion to the size of the input data set.

## O(N²)

O(N²) represents an algorithm whose performance is directly proportional to the square of the size of the input data set. This is common with algorithms that involve nested iterations over the data set. Deeper nested iterations will result in O(N³), O(N⁴) etc.

## O(2^N)

O(2^N) denotes an algorithm whose growth doubles with each addition to the input data set. An example of an O(2^N) function is the recursive calculation of Fibonacci numbers.

## O(log n)

Example is binary search. The iterative halving of data sets described in the binary search example produces a growth curve that peaks at the beginning and slowly flattens out as the size of the data sets increase e.g. an input data set containing 10 items takes one second to complete, a data set containing 100 items takes two seconds, and a data set containing 1,000 items will take three seconds. 

Resources:
- https://rob-bell.net/2009/06/a-beginners-guide-to-big-o-notation
