---
title: 二进制中1的个数
date: 2019-04-01 16:50:00
img: https://gitee.com/wenguang0816/blogPic/raw/master/20190401-4.jpg
summary: 剑指 offer：11、二进制中1的个数
categories: 剑指 offer
tags:
  - 位运算
  - 数学
---
### [11\. 二进制中1的个数](https://www.nowcoder.com/practice/8ee967e43c2c4ec193b040ea7fbb10b8?tpId=13&tqId=11164&tPage=1&rp=1&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking)

### 题目描述
输入一个整数，输出该数二进制表示中1的个数。其中负数用补码表示。

### 解题思路：
+ 思路1：直接去掉二进制中位置最靠后的1。假设`n=1100`，则`n-1=1011`，那么`n&(n-1)=1000`,位置最靠后的1被去掉。 时间复杂度O(M), M为1的个数
+ 思路2：利用标志位遍历int的32位; 时间复杂度O(1), 32次循环

**注：负数右移后，最高位补1，如果右移判断最低位将导致死循环** 

### 解答：

```cpp
// 方法1
class Solution {
public:
    int NumberOf1(int n) {
        int cnt = 0;
        while(n != 0)
        {
            n = n & (n-1);
            cnt++;
        }
        return cnt;
    }
};
// 方法2:
class Solution {
public:
     int  NumberOf1(int n) {
         int cnt = 0;
         int flag = 1;
         while(flag != 0)
         {
             if((n & flag) != 0)
                 ++cnt;
             flag = flag << 1;
         }
         return cnt;
     }
};
```