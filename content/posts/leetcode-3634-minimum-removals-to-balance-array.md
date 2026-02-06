---
date: '2026-02-06T09:51:25+08:00'
draft: false
title: 'Leetcode 3634 - Minimum Removals to Balance Array'
---
## Approach
Two pointers + sorting
## Complexity
+ Time complexity: `O(nlogn)`
    + The sorting takes `O(nlogn)`, and the two pointer process takes `O(n)`.
    + Using binary search or radix sort might optimize the execution time a little bit.
+ Space complexity: `O(n)` or `O(logn)`
    + This includes the stack space required by the sorting process, since built-in sorting implementations typically use a variant of quicksort or [timsort](https://en.wikipedia.org/wiki/Timsort).

Sorry 我不知道怎麼弄好 mathjax 的渲染 QwQ
## Code
```cpp
class Solution {
public:
    int minRemoval(vector<int>& nums, int k) {
        sort(nums.begin(), nums.end());
        int n = nums.size();
        int j = 0, ans = n;
        for (int i = 0; i < n; i++) {
            while (j < n && nums[j] <= 1LL*nums[i] * k) j++;
            ans = min(ans, n-j+i);
        }
        return ans;
    }
};
```
