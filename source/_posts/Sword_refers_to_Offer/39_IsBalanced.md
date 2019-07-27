---
title: 平衡二叉树
date: 2019-07-27 18:00:00
img: https://gitee.com/wenguang0816/blogPic/raw/master/20190727-1.jpg
summary: 剑指 offer：39、平衡二叉树
categories: 剑指 offer
tags:
  - 递归
  - 二叉树
---
### [39\. 平衡二叉树](https://www.nowcoder.com/practice/8b3b95850edb4115918ecebdf1b4d222?tpId=13&tqId=11192&tPage=1&rp=1&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking)

### 题目描述
输入一棵二叉树，判断该二叉树是否是平衡二叉树。

### 解题思路：
> 平衡二叉树：Wiki:在计算机科学中，AVL树是最早被发明的自平衡二叉查找树。在AVL树中，任一节点对应的两棵子树的最大高度差为1，因此它也被称为高度平衡树。查找、插入和删除在平均和最坏情况下的时间复杂度都是O(logn)

我们可以通过递归的方式来获取二叉树每个节点的左右子树的深度，然后比较左右子树的深度，如果二者深度差值大于`1`，则可以判定该二叉树不是平衡二叉树，反之，该树为平衡二叉树。

如果从上向下进行判断，则会导致判断上层节点时，需要多次判断其下层节点。所以我们采用从下向上的方式进行判断，如果某节点出现左右子树深度差大于`1`，则可判定该树不是平衡二叉树。

### 解答：
```cpp
class Solution {
public:
    bool IsBalanced_Solution(TreeNode* pRoot) {
        return TreeDepth(pRoot) != -1;
    }
    int TreeDepth(TreeNode* pRoot)
    {
        if(pRoot == nullptr)
            return 0;
        int leftDepth = TreeDepth(pRoot->left);
        if(leftDepth == -1)
            return -1;
        int rightDepth = TreeDepth(pRoot->right);
        if(rightDepth == -1)
            return -1;
        // 如果两子树深度差大于1，则该树不是平衡二叉树，返回-1做标志
        return abs(leftDepth - rightDepth) > 1 ? -1 : max(leftDepth, rightDepth) + 1;
    }
};
```
