---
title: LeetCode刷题：191.Number of 1 Bits
date: 2019-02-24 13:06:00
categories: LeetCode
tags:
  - LeetCode
---
### [191\. Number of 1 Bits](https://leetcode-cn.com/problems/number-of-1-bits/)
Write a function that takes an unsigned integer and return the number of '1' bits it has (also known as the [Hamming weight](http://en.wikipedia.org/wiki/Hamming_weight)).

**Example 1:**

**Input:** `00000000000000000000000000001011`

**Output:** `3`

**Explanation:** The input binary string **00000000000000000000000000001011** has a total of three '1' bits.

**Example 2:**

**Input:** `00000000000000000000000010000000`

**Output:** `1`

**Explanation:** The input binary string **00000000000000000000000010000000** has a total of one '1' bit.

**Example 3:**

**Input:** `11111111111111111111111111111101`

**Output:** `31`

**Explanation:** The input binary string **11111111111111111111111111111101** has a total of thirty one '1' bits.

**Note:**
*   Note that in some languages such as Java, there is no unsigned integer type. In this case, the input will be given as signed integer type and should not affect your implementation, as the internal binary representation of the integer is the same whether it is signed or unsigned.
*   In Java, the compiler represents the signed integers using [2's complement notation](https://en.wikipedia.org/wiki/Two%27s_complement). Therefore, in **Example 3** above the input represents the signed integer `-3`.

**Follow up**:
If this function is called many times, how would you optimize it?
##### 解题思路：
+ 思路1：除2取余法，末尾为1，除2取余后为1，末尾为0，除2取余后为0
+ 思路2：与1相与，直接判定末位是否为1
+ 思路3：直接去掉二进制中位置最靠后的1。假设`n=1100`，则`n-1=1011`，那么`n&(n-1)=1000`,位置最靠后的1被去掉。
##### 解答：
```cpp
//方法1
class Solution {
public:
    int hammingWeight(uint32_t n) {
        int cnt = 0;
        while(n != 0)
        {
            cnt += n % 2;
            n >>= 1;
        }
        return cnt;
    }
};
//方法2
class Solution {
public:
    int hammingWeight(uint32_t n) {
        int cnt = 0;
        while(n != 0)
        {
            cnt += n & 1;
            n >>= 1;
        }
        return cnt;
    }
};
//方法3
class Solution {
public:
    int hammingWeight(uint32_t n) {
        int cnt = 0;
        while(n != 0)
        {
            n = n & (n-1);
            cnt++;
        }
        return cnt;
    }
};
```