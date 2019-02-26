---
title: LeetCode刷题：231.Power of Two
date: 2019-02-24 13:08:00
categories: LeetCode
tags:
  - LeetCode
---
#### [231\. Power of Two](https://leetcode-cn.com/problems/power-of-two/)
**Example 1:**

**Input:** `1`

**Output:** `true `

**Explanation:** 2<sup>0</sup> = 1

**Example 2:**

**Input:** `16`

**Output:** `true`

**Explanation:** 2<sup>4</sup> = 16

**Example 3:**

**Input:** `218`

**Output:** `false`

##### 解题思路：
通过观察可知，如果一个数字为2的幂，那么这个数字中的二进制数中的最高位必为1，其它都为0，那么灵气减1，最高位变为0，其它位变为1。例如2<sup>3</sup>=8,其二进制形式为1000，那么8 - 1 = 7，7的二进制形式为0111，1000 & 0111 = 0；我们可以通过这个性质来判断该数字是否为2的幂。
##### 解答：
```
class Solution {
public:
    bool isPowerOfTwo(int n) {
        return (n > 0) && (! (n & (n - 1) ) );
    }
};
```