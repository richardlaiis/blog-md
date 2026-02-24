---
date: '2026-02-24T16:56:02+08:00'
draft: false
title: 'Leetcode 1022 - Sum of Root to Leaf Binary Numbers'
---
今天用Python寫 :p
## Code
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    ans = 0
    def traverse(self, root, cur):
        if not root:
            return
        if not root.left and not root.right:
            cur = cur<<1 | root.val
            self.ans += cur
            return
        self.traverse(root.left, cur<<1 | root.val)
        self.traverse(root.right, cur<<1 | root.val)
    def sumRootToLeaf(self, root: Optional[TreeNode]) -> int:
        self.traverse(root, 0)
        return self.ans
```
