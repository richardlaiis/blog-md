---
date: '2026-02-09T09:17:27+08:00'
draft: false
title: 'Leetcode 1382 - Balance a Binary Search Tree'
---
## 題目連結
https://leetcode.com/problems/balance-a-binary-search-tree/
## Approach
對原本的二元搜尋樹進行中序遍歷，把每個元素存入陣列中，如此一來陣列中的元素會是由小到大排序的。接著用遞迴的方式由這個陣列重建出一棵平衡的二元搜尋樹，就做好了。
## Code
```cpp
class Solution {
private:
    void dfs(TreeNode* root, vector<int>& arr) {
        if (!root) return;
        dfs(root->left, arr);
        arr.emplace_back(root->val);
        dfs(root->right, arr);
    }
    TreeNode* toBST(vector<int>&arr, int start, int end) {
        if (start > end) return NULL;
        int mid = (start + end) / 2;
        TreeNode* res = new TreeNode(arr[mid]);
        res->left = toBST(arr, start, mid-1);
        res->right = toBST(arr, mid+1, end);
        return res;
    }
public:
    TreeNode* balanceBST(TreeNode* root) {
        vector<int> arr;
        dfs(root, arr);
        return toBST(arr, 0, arr.size() - 1);
    }
};
```
