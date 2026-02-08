---
date: '2026-02-08T08:42:53+08:00'
draft: false
title: 'Leetcode 110 - Balanced Binary Tree'
categories:
- LeetCode
tags:
- LeetCode
---
## Approach
By definition, one binary tree is balanced if and only if its two subtree's depths' difference <= 1 and the two subtrees are both balanced. Hence, we can write the recursive function for `isBalanced()` and the function for the calculation of depth `depth()`.
## Code
```cpp
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    int depth(TreeNode* root) {
        if (!root) return 0;
        return max(depth(root->left), depth(root->right)) + 1;
    }
    bool isBalanced(TreeNode* root) {
        if (!root) return true;
        bool diffvalid = (abs(depth(root->left)-depth(root->right)) <= 1);
        return  diffvalid && isBalanced(root->left) && isBalanced(root->right);
    }
};
```
