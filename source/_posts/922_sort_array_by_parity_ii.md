---
title: LeetCode刷题：922.Sort Array By Parity II
date: 2019-02-24 13:27:00
categories: LeetCode
tags:
  - 数组
---
#### [922\. Sort Array By Parity II](https://leetcode-cn.com/problems/sort-array-by-parity-ii/)
Given an array `A` of non-negative integers, half of the integers in A are odd, and half of the integers are even.
Sort the array so that whenever `A[i]` is odd, `i` is odd; and whenever `A[i]` is even, `i` is even.
You may return any answer array that satisfies this condition.

**Example 1:**
>**Input:** `[4,2,5,7]`
>
>**Output:** `[4,5,2,7]`
>
>**Explanation:** `[4,7,2,5], [2,5,4,7], [2,7,4,5] would also have been accepted.`

**Note:**
1.  `2 <= A.length <= 20000`
2.  `A.length % 2 == 0`
3.  `0 <= A[i] <= 1000`
##### 解题思路：
1. 先将数组A按照奇偶分为两个数组odd和even，然后按照偶数、奇数的顺序依次插入到结果数组；
2. 思路和1类似，利用vector的`top()`取出栈顶元素和`pop()`删除栈顶元素；
##### 解答：
```cpp
// code 1:
// 80ms
class Solution {
public:
    vector<int> sortArrayByParityII(vector<int>& A) {
        vector<int> odd, even, result;
        for(auto vint = A.begin(); vint != A.end(); ++vint)
        {
            if((*vint) % 2 == 0)
                even.push_back(*vint);
            else
                odd.push_back(*vint);
        }
        size_t len = A.size();
        auto e = even.begin();
        auto o = odd.begin();
        for(auto i = 0; i < len; ++i)
        {
            if(i % 2 == 0)
            {
                result.push_back(*e);
                e++;
            }                
            else
            {
                result.push_back(*o);
                o++;
            }

        }
        return result;
    }
};
// code 2：
// 64ms
class Solution {
public:
    vector<int> sortArrayByParityII(vector<int>& A) 
    {
        stack<int> odd;
        stack<int> even;
        vector<int>::iterator iter;
        int a=0;//奇偶标志位
        for(iter=A.begin();iter!=A.end();iter++)
        {
            if(*iter%2==0)
                even.push(*iter);
            else
                odd.push(*iter);
        }
        for(iter=A.begin();iter!=A.end();iter++)
        {
              //top()取出栈顶元素，pop()删除栈顶元素；
              if(a==0)
              {
                *iter=even.top();
                 even.pop();
              }
            else
            {
                *iter=odd.top();
                 odd.pop();
            }
            a=1-a;//奇偶变换
        }
        return A;
    }
};
```