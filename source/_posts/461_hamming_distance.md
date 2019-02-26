---
title: LeetCode刷题：461.Hamming Distance
date: 2019-02-24 13:11:00
categories: LeetCode
tags:
  - LeetCode
---
#### [461\. Hamming Distance](https://leetcode-cn.com/problems/hamming-distance/)
The [Hamming distance](https://en.wikipedia.org/wiki/Hamming_distance) between two integers is the number of positions at which the corresponding bits are different.
Given two integers `x` and `y`, calculate the Hamming distance.

**Note:**
0 ≤ `x`, `y` < 2<sup>31</sup>.

**Example:**
```
Input: x = 1, y = 4
Output: 2
Explanation:
1   (0 0 0 1)
4   (0 1 0 0)
       ↑   ↑
The above arrows point to positions where the corresponding bits are different.
```
##### 解题思路：
n = x ^ y，两数对应位置若不相同，则n的相应位置置1
利用n = n & (n - 1)获取n中1的个数
##### 解答：
```
class Solution {
public:
    int hammingDistance(int x, int y) {
        int n = x^y, count = 0;
        while(n){
            count ++;
            n = n&(n-1);
        }
        return count;
    }
};
```