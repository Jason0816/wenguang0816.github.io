---
title: LeetCode刷题：709.To Lower Case
date: 2019-02-24 13:19:00
categories: LeetCode
tags:
  - LeetCode
---
#### [709\. To Lower Case](https://leetcode-cn.com/problems/to-lower-case/)
Implement function ToLowerCase() that has a string parameter str, and returns the same string in lowercase.
**Example 1:**
>**Input:** "Hello"
>
>**Output:** "hello"

**Example 2:**
>**Input:** "here"
>
>**Output:** "here"

**Example 3:**
>**Input:** "LOVELY"
>
>**Output:** "lovely"

##### 解题思路：
利用C++ tolower()函数；
##### 解答：
```cpp
class Solution {
public:
    string toLowerCase(string str) {
        for(auto &letter : str)
        {
            letter = tolower(letter);
        }
        return str;
    }
};
```