# 1071. Greatest Common Divisor of Strings
There are two general ways to get the Greatest Common Divisor in math: Euclidean Algorithm and 更相减损术.

## Euclidean Algorithm
$gcd(a, b) = gcd(b, a \mod b), \text{ where } a > b \text{, and } a \mod b \neq 0$.

Proof:

$\text{Assume } d \text{ is the greatest common divisor of } a \text{ and } b \text{, where } a > b, a = d \times j, \text{ and } b = d \times i.$

$\text{ Also assume } a \div b = k \cdots r \text{, so that } a = b \times k + r $

$\quad\rightarrow d \times j = d \times i \times k + r$

$\quad\rightarrow r = d \times (j - i \times k)$

$d$ is also the gcd of $r$.

## 更相减损术
$gcd(a, b) = gcd(b, a - b), \text{ where } a > b \text{, and } a - b \neq 0$.

Proof:

$\text{Assume } d \text{ is the greatest common divisor of } a \text{ and } b \text{, where } a > b, a = d \times j, \text{ and } b = d \times i.$

$a - b = d \times j - d \times i = d \times (j - i)$

So that $d$ is the gcd of $a-b$.

## Code
In this question, we get the two string, so the other trick part is how to move the gcd string from given strings.

```python
class Solution(object):
    def gcdOfStrings(self, str1, str2):
        """
        :type str1: str
        :type str2: str
        :rtype: str
        """
        def GCD(str1, str2):
            if len(str2) > len(str1):
                tmp_str = str1
                str1 = str2
                str2 = tmp_str
            
            if str2 == '':
                return str1

            if str1[0: len(str2)] == str2:
                return GCD(str1[len(str2):], str2)
            else:
                return ''
        
        return GCD(str1, str2)

```

### Complexity
Time complexity:

Space complexity:

```python
class Solution(object):
    def gcdOfStrings(self, str1: str, str2: str) -> str:
        if str1+str2!=str2+str1:
            return ""
        a=len(str1)
        b=len(str2)
        if a<b:
            a,b = b,a
        while b:
            a,b=b,a%b
        return str2[:a]
```

### Complexity
Time complexity:

Space complexity: