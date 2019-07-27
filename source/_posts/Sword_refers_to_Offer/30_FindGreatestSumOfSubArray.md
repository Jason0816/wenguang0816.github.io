---
title: 连续子数组的最大和
date: 2019-07-25 20:00:00
img: https://gitee.com/wenguang0816/blogPic/raw/master/20190725-1.jpg
summary: 剑指 offer：30、连续子数组的最大和
categories: 剑指 offer
tags:
  - 数组
  - 动态规划
---
### [30\. 连续子数组的最大和](https://www.nowcoder.com/practice/459bd355da1549fa8a49e350bf3df484?tpId=13&tqId=11183&tPage=1&rp=1&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking)

### 题目描述
HZ偶尔会拿些专业问题来忽悠那些非计算机专业的同学。今天测试组开完会后,他又发话了:在古老的一维模式识别中,常常需要计算连续子向量的最大和,当向量全为正数的时候,问题很好解决。但是,如果向量中包含负数,是否应该包含某个负数,并期望旁边的正数会弥补它呢？例如:{6,-3,-2,7,-15,1,2,2},连续子向量的最大和为8(从第0个开始,到第3个为止)。给一个数组，返回它的最大连续子序列的和，你会不会被他忽悠住？(子向量的长度至少是1)

### 解题思路：
这里补充一个例子来帮助更好的理解题意：
> 输入数组为{1, -2, 3, 10, -4, 7, 2, -5}，和最大的子数组为{3, 10, -4, 7, 2}，因此该子数组的和为`18`。(子数组并不需要从第一个开始，即不需要从`1`开始)

我们可以运用动态规划的思想来解决这个问题。我们用`f(i)`来表示以数组中第`i`个元素结尾的子数组的最大和，那么我们可以得到以下公式：
  ```python
  f(i) = array[i]           # i = 0或者f(i-1) < 0
  f(i) = f(i-1) + array[i]  # i != 0并且f(i-1) >= 0
  ```
  这个公式的含义为：当`f(i-1) < 0`即以第`i-1`个元素为结尾的子数组的最大和小于`0`时，我们如果将这个小于`0`的和与`array[i]`相加，就会导致结果比`array[i]`要小，所以我们舍弃以第`i-1`为结尾的子数组和，取`f(i) = array[i]`。反之，如果`f(i-1) >= 0`，我们取`f(i) = f(i-1) + array[i]`


### 解答：
```cpp
class Solution {
public:
    int FindGreatestSumOfSubArray(vector<int> array) {
        int len = array.size();
        if(len <= 0)
            return 0;
        int sum = array[0];
        int tempsum = array[0];
        for(int i = 1; i < len; ++i)
        {
            tempsum = (tempsum < 0) ? array[i] : tempsum + array[i];
            sum = (tempsum > sum) ? tempsum : sum;
        }
        return sum;
    }
};
```
