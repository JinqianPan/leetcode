# 1071. Greatest Common Divisor of Strings
There are two general ways to get the Greatest Common Divisor in math: Euclidean Algorithm and 更相减损术.

## Euclidean Algorithm
$gcd(a, b) = gcd(b, a \mod b), \text{ where } a > b \text{, and } a \mod b \neq 0$.

Proof:

$\text{Assume } d \text{ is the greatest common divisor of } a \text{ and } b \text{, where } a > b, a = d \times j, \text{ and } b = d \times i.$

$\text{ Also assume } a \div b = k \cdots r \text{, so that } a = b \times k + r $

$\rightarrow d \times j = d \times i \times k + r$

$\rightarrow r = d \times (j - i \times k)$

$d$ is also the gcd of $r$.

## 更相减损术
$gcd(a, b) = gcd(b, a - b), \text{ where } a > b \text{, and } a - b \neq 0$.

Proof:

$\text{Assume } d \text{ is the greatest common divisor of } a \text{ and } b \text{, where } a > b, a = d \times j, \text{ and } b = d \times i.$

$ a - b = d \times j - d \times i = d \times (j - i)$

So that $d$ is the gcd of $a-b$.