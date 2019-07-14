---
title: 构建乘积数组
date: 2019-04-04 10:50:00
img: https://gitee.com/wenguang0816/blogPic/raw/master/20190404-2.jpg
summary: 剑指 offer：51、构建乘积数组
categories: 剑指 offer
tags:
  - 数组
---
### [51\. 构建乘积数组](https://www.nowcoder.com/practice/94a4d381a68b47b7a8bed86f2975db46?tpId=13&tqId=11204&tPage=2&rp=2&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking)

### 题目描述
给定一个数组`A[0,1,...,n-1]`,请构建一个数组`B[0,1,...,n-1]`,其中B中的元素`B[i]=A[0]*A[1]*...*A[i-1]*A[i+1]*...*A[n-1]`。不能使用除法。

### 解题思路：
+ 思路1: 遍历数组，时间复杂度O(n)
+ 思路2: 

| B<sub>i</sub>   | A<sub>0</sub> | A<sub>1</sub> | A<sub>2</sub> | ... | A<sub>n-2</sub> | A<sub>n-1</sub> |
|-----------------|---------------|---------------|---------------|-----|-----------------|-----------------|
| B<sub>0</sub>   | **1**         | A<sub>1</sub> | A<sub>2</sub> | ... | A<sub>n-2</sub> | A<sub>n-1</sub> |
| B<sub>1</sub>   | A<sub>0</sub> | **1**         | A<sub>2</sub> | ... | A<sub>n-2</sub> | A<sub>n-1</sub> |
| B<sub>2</sub>   | A<sub>0</sub> | A<sub>1</sub> | **1**         | ... | A<sub>n-2</sub> | A<sub>n-1</sub> |
| B<sub>0</sub>   | ...           | ...           | ...           | ... | ...             | ...             |
| B<sub>n-2</sub> | A<sub>0</sub> | A<sub>1</sub> | A<sub>2</sub> | ... | **1**           | A<sub>n-1</sub> |
| B<sub>n-1</sub> | A<sub>0</sub> | A<sub>1</sub> | A<sub>2</sub> | ... | A<sub>n-2</sub> | **1**           |

通过观察，B<sub>i</sub>的值可以看作表格中每一行的乘积，下三角连乘易求得，上三角，从下向上也是连乘，所以我们可以先计算下三角中的连乘，再算上三角的连乘，将B<sub>i</sub>两部分相乘即可。

### 解答：

```cpp
// 解法1:
class Solution {
public:
    vector<int> multiply(const vector<int>& A) {
        int len = A.size();
        vector<int> B;
        for(int i = 0; i < len; ++i)
        {
            int bi = 1;
            for(int j = 0; j < len; ++j)
            {
                if(i == j)
                    continue;
                bi *= A[j]; 
            }
            B.push_back(bi);
        }
        return B;
    }
};

// 解法2:
class Solution {
public:
    vector<int> multiply(const vector<int>& A) {
        int len = A.size();
        vector<int> B(len);
        if(len <= 0)
            return B;
        B[0] = 1;
        // 计算下三角
        for(int i = 1; i < len; ++i)
        {
            B[i] = B[i-1] * A[i-1];
        }
        int tmp = 1;
        //计算上三角
        for(int i = len - 2; i >= 0; --i)
        {
            tmp *= A[i+1];
            B[i] *= tmp;
        }
        return B;
    }
};

```