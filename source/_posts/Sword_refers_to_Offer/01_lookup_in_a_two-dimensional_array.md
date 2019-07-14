---
title: 二维数组中的查找
date: 2019-04-01 15:20:00
img: https://gitee.com/wenguang0816/blogPic/raw/master/20190401-2.jpg
summary: 剑指 offer：1、二维数组中的查找
categories: 剑指 offer
tags:
  - 查找
  - 数组
---
### [1\. 二维数组中的查找](https://www.nowcoder.com/practice/abc3fe2ce8e146608e868a70efebf62e?tpId=13&tqId=11154&tPage=1&rp=1&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking)

### 题目描述
在一个二维数组中（每个一维数组的长度相同），每一行都按照从左到右递增的顺序排序，每一列都按照从上到下递增的顺序排序。请完成一个函数，输入这样的一个二维数组和一个整数，判断数组中是否含有该整数。

### 解题思路：
+ 思路1: 暴力破解法，遍历整个二维数组，查看目标值是否在数组中; 时间复杂度O(M * N)
+ 思路2: 由题意可知，数组从左向右，从上到下递增，因此可以从右上角的数字开始查找，该数左边的数都比它小，下边的数都比它大(从左下角查找也可以); 时间复杂度O(M + N)

### 解答：

```cpp
// 解法1:
class Solution {
public:
    bool Find(int target, vector<vector<int> > array) {
        int row = array.size();
        int col = array[0].size();
        for(int i = 0; i < row; ++i)
        {
            for(int j = 0; j < col; ++j)
            {
                if(target == array[i][j])
                    return true;
            }
        }
        return false;
    }
};

// 解法2:
// 从右上角开始查找
class Solution {
public:
    bool Find(int target, vector<vector<int> > array) {
        int row = array.size();
        int col = array[0].size();
        // 从右上角开始查找
        int r = 0;
        int c = col - 1;
        while(r < row && c >= 0)
        {
            if(array[r][c] == target)
                return true;
            else if(target > array[r][c])
                ++r;
            else
                --c;
        }
        return false;
    }
};

// 解法3:
// 从左下角开始查找
class Solution {
public:
    bool Find(int target, vector<vector<int> > array) {
        int row = array.size();
        int col = array[0].size();
        // 从左下角开始查找
        int r = row - 1;
        int c = 0;
        while(r >= 0 && c < col)
        {
            if(array[r][c] == target)
                return true;
            else if(target > array[r][c])
                ++c;
            else
                --r;
        }
        return false;
    }
};
```