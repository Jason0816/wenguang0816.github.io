---
title: 二叉树的创建和遍历
date: 2019-05-11 00:00:00
img: https://upload-images.jianshu.io/upload_images/14484228-c68e683dea155b2d.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240
summary: 二叉树的创建和遍历
categories: 分享
tags:
  - 数据结构
  - 二叉树
---

## 二叉树相关概念
二叉树是一种常见的数据结构，二叉树的每个节点**最多有2个**孩子节点

### 二叉树形式
1. 满二叉树
   > 一个二叉树的所有非叶子节点都存在左右孩子，并且所有叶子节点都在同意层级上，则该树为满二叉树
   > ![满二叉树](https://upload-images.jianshu.io/upload_images/14484228-fa0842af007a91d2.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

2. 完全二叉树
   > 对一个有n个节点的二叉树，按层级顺序编号，则所有节点的编号从1到n。如果这个树所有的节点和同样深度的满二叉树的编号从1到n的节点位置相同，则这个二叉树为完全二叉树
   > ![完全二叉树](https://upload-images.jianshu.io/upload_images/14484228-09eafcf79007bb05.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 二叉树存储方式
1. 链式存储
   >  ![链式存储](https://upload-images.jianshu.io/upload_images/14484228-976d4832e0f48f9e.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
2. 数组存储
   >  ![数组存储](https://upload-images.jianshu.io/upload_images/14484228-c74f2777154b3004.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
   在数组存储中，如果父节点下标为`parent`， 那么他的左孩子节点下标为`2 * parent + 1`，右孩子节点下标为`2 * parent + 2`。

## 二叉树的遍历
二叉树遍历分为两个大类：深度优先遍历（DFS）和广度优先遍历（BFS）
以下树为例来讲述不同方式的遍历顺序
```
        实例二叉树
    	    3
    	   /  \
    	  2    8
    	 / \    \
    	9  10   11
```

### 深度优先遍历
1. 前序遍历（先序遍历）
   >二叉树前序遍历的输出顺序为：根节点、左节点、右节点

    则上例二叉树的前序遍历顺序为：`3 -> 2 -> 9 -> 10 -> 8 -> 11`
2. 中序遍历
   >二叉树中序遍历的输出顺序为：左节点、根节点、右节点

    则上例二叉树的中序遍历顺序为：`9 -> 2 -> 10 -> 3 -> 8 -> 11`
3. 后续遍历
   >二叉树后序遍历的输出顺序为：左节点、右节点、根节点

    则上例二叉树的中序遍历顺序为：`9 -> 10 -> 2 -> 11 -> 8 -> 3`
### 广度优先遍历
1. 层序遍历
   > 按照从根节点到叶子节点的层次关系，一层一层横向遍历各个节点

    则上例二叉树的层序遍历顺序为：`3 -> 2 -> 8 -> 9 -> 10 -> 11`

## 代码实现
```cpp
#include <iostream>
#include <vector>
#include <queue>
using namespace std;

struct TreeNode
{
    int val;
    struct TreeNode *left;
    struct TreeNode *right;
    TreeNode(int x) : val(x), left(nullptr), right(nullptr)
    {}
};

class BinaryTree
{
public:
    // 前序遍历创建二叉树
    TreeNode* createBinaryTree_1(vector<int> &array, int len, int& index);
    // 层序遍历创建二叉树
    TreeNode* createBinaryTree_2(vector<int> &array, int len, int index);
    // 前序遍历
    void preOrderTraveral(TreeNode *node);
    // 中序遍历
    void inOrderTraveral(TreeNode *node);
    // 后序遍历
    void postOrderTraveral(TreeNode *node);
    // 层序遍历
    void levelOrderTraveral(TreeNode *node);
    // 二叉树深度
    int TreeDepth(TreeNode *pRoot);
};

//前序遍历顺序创建二叉树
TreeNode* BinaryTree::createBinaryTree_1(vector<int> &array, int len, int& index)
{
    TreeNode *node = nullptr;
    if(index < len && array[index] != -1)
    {
        node = new TreeNode(array[index]);
        node->left = createBinaryTree_1(array, len, ++index);
        node->right = createBinaryTree_1(array, len, ++index);
    }
    return node;
}

// 层序遍历创建二叉树
TreeNode* BinaryTree::createBinaryTree_2(vector<int> &array, int len, int index)
{
    TreeNode *node = nullptr;
    if(index < len && array[index] != -1)
    {
        node = new TreeNode(array[index]);
        node->left = createBinaryTree_2(array, len, 2 * index + 1);
        node->right = createBinaryTree_2(array, len, 2 * index + 2);
    }
    return node;
}

// 前序遍历
void BinaryTree::preOrderTraveral(TreeNode *node)
{
    if(node == nullptr)
        return;
    cout << node->val << " ";
    preOrderTraveral(node->left);
    preOrderTraveral(node->right);
}

// 中序遍历
void BinaryTree::inOrderTraveral(TreeNode *node)
{
    if(node == nullptr)
        return;
    inOrderTraveral(node->left);
    cout << node->val << " ";
    inOrderTraveral(node->right);
}

// 后序遍历
void BinaryTree::postOrderTraveral(TreeNode *node)
{
    if(node == nullptr)
        return;
    postOrderTraveral(node->left);
    postOrderTraveral(node->right);
    cout << node->val << " ";
}

// 层序遍历
// 层序遍历需要借助队列来实现
void BinaryTree::levelOrderTraveral(TreeNode *node)
{
    queue<TreeNode *> qTreeNode;
    qTreeNode.push(node);
    while(!qTreeNode.empty())
    {
        TreeNode *pNode = qTreeNode.front();
        qTreeNode.pop();
        cout << pNode->val << " ";
        if(pNode->left != nullptr)
            qTreeNode.push(pNode->left);
        if(pNode->right != nullptr)
            qTreeNode.push(pNode->right);
    }
}

// 二叉树深度
int BinaryTree::TreeDepth(TreeNode *pRoot)
    {
        if(!pRoot)
            return 0;
        return max(TreeDepth(pRoot->left), TreeDepth(pRoot->right)) + 1;
    }

int main()
{
    // -1 代表节点为空
    // 按前序遍历顺序创建二叉树，并且遍历
    vector<int> array_1 {3, 2, 9, -1, -1, 10, -1, -1, 8, -1, 11};
    int len_1 = array_1.size();
    BinaryTree biTree;
    int index = 0;
    TreeNode *root_1 = biTree.createBinaryTree_1(array_1, len_1, index);
    cout << "PreOrderTraveral: ";
    biTree.preOrderTraveral(root_1);
    cout << endl;
    cout << "InOrderTraveral: ";
    biTree.inOrderTraveral(root_1);
    cout << endl;
    cout << "PostOrderTraveral: ";
    biTree.postOrderTraveral(root_1);
    cout << endl;
    cout << "LevelOrderTraveral: ";
    biTree.levelOrderTraveral(root_1);
    cout << endl;
    cout << "Tree_1's depth is: " << biTree.TreeDepth(root_1) << endl;

    // 按层序遍历顺序创建二叉树，并且遍历
    vector<int> array_2 {3, 2, 8, 9, 10, -1, 11};
    int len_2 = array_2.size();
    TreeNode *root_2 = biTree.createBinaryTree_2(array_2, len_2, 0);
    cout << "PreOrderTraveral: ";
    biTree.preOrderTraveral(root_2);
    cout << endl;
    cout << "InOrderTraveral: ";
    biTree.inOrderTraveral(root_2);
    cout << endl;
    cout << "PostOrderTraveral: ";
    biTree.postOrderTraveral(root_2);
    cout << endl;
    cout << "LevelOrderTraveral: ";
    biTree.levelOrderTraveral(root_2);
    cout << endl;
    cout << "Tree_2's depth is: " << biTree.TreeDepth(root_2) << endl;
}
```

**致谢：**本文部分文字和图片引自**程序员小灰**的新书**漫画算法**，为表感谢，特附上程序员小灰公众号二维码，大家快扫码学习新知识哈！
![程序员小灰](https://upload-images.jianshu.io/upload_images/14484228-2e504c60210295e1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

