---
title: LeetCode刷题：476.Number Complement
date: 2019-02-24 13:12:00
categories: LeetCode
tags:
  - LeetCode
---
#### [476\. Number Complement](https://leetcode-cn.com/problems/number-complement/)
Given a positive integer, output its complement number. The complement strategy is to flip the bits of its binary representation.

**Note:**
1.  The given integer is guaranteed to fit within the range of a 32-bit signed integer.
2.  You could assume no leading zero bit in the integer’s binary representation.

**Example 1:**

**Input:** `5`

**Output:** `2`

**Explanation:** The binary representation of 5 is 101 (no leading zero bits), and its complement is 010\. So you need to output 2.

**Example 2:**

**Input:** `1`

**Output:** `0`

**Explanation:** The binary representation of 1 is 1 (no leading zero bits), and its complement is 0\. So you need to output 0.
##### 解题思路：
题例中`5`的二进制为`101`，补数为`010`,补数可以通过`101 ^ 111`获得，所以首先获取与num相同二进制位数的`111`，通过判断`num`左移1位是否为空可以获得其位数，进而获取`mask`。
##### 解答：
```cpp
class Solution {
public:
    int findComplement(int num) {
        int mask = 2, tmp = num;
        while(tmp >>= 1)
        {
            mask <<= 1;  
        }
        return num ^ (mask-1);
    }
};
```