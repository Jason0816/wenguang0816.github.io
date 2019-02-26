---
title: LeetCode刷题：344.Reverse String
date: 2019-02-24 13:10:00
categories: LeetCode
tags:
  - LeetCode
---
#### [344\. Reverse String](https://leetcode-cn.com/problems/reverse-string/)
Write a function that takes a string as input and returns the string reversed.

**Example 1:**

**Input:** "hello"

**Output:** "olleh"

**Example 2:**

**Input:** "A man, a plan, a canal: Panama"

**Output:** "amanaP :lanac a ,nalp a ,nam A"
##### 解题思路：
+ 思路1： 通过`s.length()`获取`s`的字符长度，然后通过下标访问`s`，将`s`中的字符从尾到头拼接到`result`上，得到返回结果。
+ 思路2： 利用`reverse`函数，`reverse(beg, end)`会将区间`(beg, end)`之间的元素全部逆转。
##### 解答：
```
// code 1: 
// 4ms
class Solution {
public:
    string reverseString(string s) {
        string result = "";
        auto len = s.length();
        while(len > 0)
        {
            result += s[len - 1];
            --len;
        }
        return result;
    }
};
// code 2:
// 4ms
class Solution {
public:
    string reverseString(string s) {
        reverse(s.begin(),s.end());
        return s;
    }
};
```