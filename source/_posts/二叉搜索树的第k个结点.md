---
title: 二叉搜索树的第k个结点
date: 2020-02-09 22:46:54
tags:
---

给定一棵二叉搜索树，请找出其中的第k小的结点。例如， （5，3，7，2，4，6，8）    中，按结点数值大小顺序第三小结点的值为4。

中序，root不压栈、设为c

```cpp
/*
struct TreeNode {
    int val;
    struct TreeNode *left;
    struct TreeNode *right;
    TreeNode(int x) :
            val(x), left(NULL), right(NULL) {
    }
};
*/
class Solution {
public:
    TreeNode* KthNode(TreeNode* pRoot, int k)
    {
        TreeNode *c = pRoot;
        stack<TreeNode*> s;
        while (c != nullptr || s.size() > 0)
        {
            while (c != nullptr)
            {
                s.push(c);
                c = c->left;
            }
            c = s.top();
            s.pop();
            k--;
            if (k == 0)
            {
                return c;
            }
            c = c->right;
        }
        return nullptr;
    }
};
```
