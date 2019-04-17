---
title: 二叉树的镜像
date: 2019-04-17 21:48:00
img: https://upload-images.jianshu.io/upload_images/14484228-01341b258b1fd7de.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
summary: 剑指 offer：18、二叉树的镜像
categories: 剑指 offer
tags:
  - 二叉树
  - 递归
  - 栈
---
### [18\. 二叉树的镜像](https://www.nowcoder.com/practice/564f4c26aa584921bc75623e48ca3011?tpId=13&tqId=11171&tPage=1&rp=1&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking)

### 题目描述
操作给定的二叉树，将其变换为源二叉树的镜像。

### 输入描述
```
二叉树的镜像定义：源二叉树 
    	    8
    	   /  \
    	  6   10
    	 / \  / \
    	5  7 9 11
    	镜像二叉树
    	    8
    	   /  \
    	  10   6
    	 / \  / \
    	11 9 7  5
```

### 解题思路：
使用递归思路，先交换根节点的两个子节点，再交换子节点的两个子节点

### 解答：

```cpp
/*
struct TreeNode {
	int val;
	struct TreeNode *left;
	struct TreeNode *right;
	TreeNode(int x) :
			val(x), left(NULL), right(NULL) {
	}
};*/
class Solution {
public:
    void Mirror(TreeNode *pRoot) {
        if(!pRoot)
            return;
        TreeNode *tmp = pRoot->left;
        pRoot->left = pRoot->right;
        pRoot->right = tmp;
        Mirror(pRoot->left);
        Mirror(pRoot->right);
    }
};
```