# JavaScript uses 64-bit floating point numbers

JavaScript support only one number type, and that type is 64-bit floating point numbers. Under the hood, it uses IEEE 754 standard for floating-point arithmetic. As per the standard, number representation has three parts:

- sign
- fraction - the payload of the number
- exponent - controls how far and in which direction to move the decimal point in the fraction

Problem is in the binary representation of fractions, since computer can only store binary numbers. With binary division, numbers infinitely repeat. To store these number in 64 bit space, rounding must be applied. This is why we can get unexpected results for following calculations:

```
console.log(0.1 + 0.2);
console.log(0.1 + 0.2 == 0.3);
``` 

And the result will be:

```
0.30000000000000004
false
``` 
Resources
- https://www.codemag.com/article/1811041/JavaScript-Corner-Math-and-the-Pitfalls-of-Floating-Point-Numbers
- https://towardsdatascience.com/binary-representation-of-the-floating-point-numbers-77d7364723f1
