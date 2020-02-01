---
title: 二叉树的深度
date: 2019-04-17 20:46:00
img: https://gitee.com/wenguang0816/blogPic/raw/master/20190417-2.jpg
summary: 剑指 offer：38、二叉树的深度
categories: 剑指 offer
tags:
  - 二叉树
  - 递归
  - 栈
---
### [38\. 二叉树的深度](https://www.nowcoder.com/practice/435fb86331474282a3499955f0a41e8b?tpId=13&tqId=11191&tPage=1&rp=1&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking)

### 题目描述
输入一棵二叉树，求该树的深度。从根结点到叶结点依次经过的结点（含根、叶结点）形成树的一条路径，最长路径的长度为树的深度。

### 解题思路：
+ 思路1: 使用递归思路，属于DFS（深度优先搜索），时间复杂度为`O(N)`，空间复杂度：在最糟糕的情况下，树是完全不平衡的，例如每个结点只剩下左子结点，递归将会被调用`N`次（树的高度），因此保持调用栈的存储将是`O(N)`。但在最好的情况下（树是完全平衡的），树的高度将是`log(N)`。因此，在这种情况下的空间复杂度将是`O(log(N))`。
+ 思路2: 使用迭代思路，引入一个栈，使用 DFS 策略访问每个结点，同时在每次访问时更新最大深度。时间复杂度为`O(N)`，空间复杂度将是`O(N)`。

### 解答：

```cpp
/*
struct TreeNode {
	int val;
	struct TreeNode *left;
	struct TreeNode *right;
	TreeNode(int x) :
			val(x), left(nullptr), right(nullptr) {
	}
};*/
// 解法1:
class Solution {
public:
    int TreeDepth(TreeNode* pRoot)
    {
        if(!pRoot)
            return 0;
        return max(TreeDepth(pRoot->left) + 1, TreeDepth(pRoot->right) + 1);
    }
};
// 解法2:
class Solution {
public:
    int TreeDepth(TreeNode* pRoot)
    {
        if(!pRoot)
            return 0;
        queue<TreeNode *> que;
        que.push(pRoot);
        int depth = 0;
        while(!que.empty())
        {
            // 队列中每次迭代都只存储了一层的元素
            int size = que.size();
            depth++;
            for(int i = 0; i < size; ++i)
            {
                TreeNode *node = que.front();
                que.pop();
                if(node->left)
                    que.push(node->left);
                if(node->right)
                    que.push(node->right);
            }
        }
        return depth;
    }
};
```