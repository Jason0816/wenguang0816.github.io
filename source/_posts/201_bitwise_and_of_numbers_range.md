---
title: LeetCode刷题：201.Bitwise AND of Numbers Range
date: 2019-02-24 13:07:00
categories: LeetCode
tags:
  - LeetCode
---
#### [201\. Bitwise AND of Numbers Range](https://leetcode-cn.com/problems/bitwise-and-of-numbers-range/)
Given a range [m, n] where 0 <= m <= n <= 2147483647, return the bitwise AND of all numbers in this range, inclusive.

**Example 1:**

**Input:** `[5,7]`

**Output:** `4`

**Example 2:**

**Input:** `[0,1]`

**Output:** `0`

##### 解题思路：
通过观察可以知道5的二进制为**1**01，6的二进制为**1**10，7的二进制为**1**11，输出4的二进制为**1**00，可以发现，只要找到二进制的左边公共部分即可。
可以先建立一个32位都是1的mask，然后每次左移一位，比较m和n是否相同，不同再继续左移一位，直至相同，然后把m和mask相与即得最终结果。
##### 解答：
```
//方法1
class Solution {
public:
	int rangeBitwiseAnd(int m, int n) {
		unsigned int mask = UINT_MAX;
		while ((m & mask) != (n & mask)) {
			mask <<= 1;
		}
		return mask & m;
	}
};
//方法2
class Solution {
public:
    int rangeBitwiseAnd(int m, int n) {
        int cnt = 0;
        while(m!= n){
            m>>=1;
            n>>=1;
            ++cnt;
        }
        return m<<cnt;
    }
};
```