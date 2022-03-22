---
title: 191. Number of 1 Bits
weight: 3
bookToc: true
bookComments: true
---

# [191. Number of 1 Bits](https://leetcode.com/problems/number-of-1-bits/)
![Leetcode Easy](/images/leetcode_lvl_badges/easy.svg)

---

## Problem

Write a function that takes an unsigned integer and returns the number of '1' bits it has (also
known as the [Hamming weight](http://en.wikipedia.org/wiki/Hamming_weight)).

Note:

1. Note that in some languages, such as Java, there is no unsigned integer type. In this case, the
   input will be given as a signed integer type. It should not affect your implementation, as the
   integer's internal binary representation is the same, whether it is signed or unsigned.
2. In Java, the compiler represents the signed integers
   using [2's complement notation](https://en.wikipedia.org/wiki/Two%27s_complement). Therefore, in
   Example 3, the input represents the signed integer. -3.


### Example

#### Example 1:
```
Input: n = 00000000000000000000000000001011
Output: 3
Explanation: The input binary string 00000000000000000000000000001011 has a total of three '1' bits.
```

#### Example 2:
```
Input: n = 00000000000000000000000010000000
Output: 1
Explanation: The input binary string 00000000000000000000000010000000 has a total of one '1' bit.
```

#### Example 3:
```
Input: n = 11111111111111111111111111111101
Output: 31
Explanation: The input binary string 11111111111111111111111111111101 has a total of thirty one '1' bits.
```

### Constraints
- The input must be a `binary string` of length 32.

### Follow up 
If this function is called many times, how would you optimize it?

---

## Approach and Intuition

### 1. Naive approach

Using Integer class to get Binary representation

In java we've got `java.lang.Integer#toBinaryString` method which Returns a string representation of
the integer argument as an unsigned integer in base 2.

```java
public static String toBinaryString(int i) {
  return toUnsignedString0(i, 1);
}
```

We can get the binary string for the given input and iterate the string characters and countt he number of '1'

```java
 private int bruteForce(int n) {
     String binaryStr = Integer.toBinaryString(n);
     int count = 0;

     for (int i = 0; i < binaryStr.length(); i++) {
         if (binaryStr.charAt(i) == '1') {
             count++;
         }
     }
     
     return count;
 }

```

{{< hint warning >}}
{{< fontawesome "solid/circle-exclamation" >}} 
It is highly recommended not to use such approach as the interviewer would be interested in your bit manipulation skills.
What if you are asked to explain the idea behind `java.lang.Integer#toBinaryString` ?
{{< /hint >}}

### 2. Bitwise `AND` masking

Scan every bits of number and perform an `&` operation with LSB

Since we are dealing with Integer type data and there are 32 bits positions that we need to check in worst case.
So instead of converting the number to string, we can directly count the number of 1 bit.

Recalling the basics:
1. `LSB` represents the Least Significant Bits position(left most bit)
2. `Logical AND (&)` And operation results in true of the both the bits are high or set or true
3. `Logical Right Shift >>` Right shift operator divides the number by the 2 raised to power the number of time we shift the actual number i.e. for `a >> b`, it means we divide the number {{< katex >}} a {{< /katex >}} by {{< katex >}} 2^b{{< /katex >}}


If we perform the `&` operation over the LSB of number and check if it's `1` or `0` thereby increasing our count. Once done with LSB we can take that bit off the grid.

How do we remove the LSB from the original number once done performing operation over LSB? Answer is Logical Right Shift `>>` with 1.

And since there are only 32 bit position, we need to scan/perform 32 times and check if we get 1 in each time.

```java
 private int bitwiseOp(int n) {
     int count = 0;
     int len = 32;

     while (len-- >= 1) {
         if ((n & 1) == 1) {
             count++;
         }
         n >>= 1;
     }

     return count;
 }
```

`Time Complexity`: {{< katex >}} O(n) {{< /katex >}} where n would be 32 in worst case(all 32 bits
are 1), so asymptotically, it's almost constant time {{< katex >}} O(1) {{< /katex >}}

`Space Complexity`: {{< katex >}} O(1) {{< /katex >}} since we're not using any extra space

---

## Complete Solution

```java
public class Solution {

    // you need to treat n as an unsigned value
    public int hammingWeight(int n) {
        //return bruteForce(n);
        //return divisionMethod(n);
        return bitwiseOp(n);
    }

    private int bruteForce(int n) {
        String binaryStr = Integer.toBinaryString(n);
        int count = 0;

        for (int i = 0; i < binaryStr.length(); i++) {
            if (binaryStr.charAt(i) == '1') {
                count++;
            }
        }

        return count;
    }

    private int divisionMethod(int n) {
        int count = 0;

        // n > 0 will not work in case of negetive binary numbers
        // Use i: 0 to 31
        while (n > 0) {
            int rem = n % 2;

            if (rem == 1) {
                count++;
            }

            n = n / 2;
        }

        return count;
    }

    private int bitwiseOp(int n) {
        int count = 0;
        int len = 32;

        while (len-- >= 1) {
            if ((n & 1) == 1) {
                count++;
            }

            n >>= 1;
        }

        return count;
    }
}
```

---