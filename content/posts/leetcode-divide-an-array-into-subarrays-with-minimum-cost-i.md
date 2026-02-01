---
date: '2026-02-01T08:50:58+08:00'
draft: false
title: 'Leetcode 3010 - Divide an Array Into Subarrays With Minimum Cost I'
categories:
- LeetCode
---
## Approach
To minimize the total cost, we need to partition the array using the three smallest elements. However, since the first element is always included, the final answer is simply the first element plus the two smallest elements from the rest of the array.

In my code, I sort the array (excluding the first element) using built-in `sort()` function, but there might be other [methods](https://www.geeksforgeeks.org/dsa/find-k-smallest-elements-in-an-array/) with better time complexity. 
## Code
```cpp
class Solution {
public:
    int minimumCost(vector<int>& nums) {
        sort(nums.begin() + 1, nums.end());
        return nums[0] + nums[1] + nums[2];
    }
};
```
## uwu
我把 `richardlaiis.csie.org` (新的網址) 綁到 `richardlaiis.github.io` (原網址) 了，比我想像中的簡單很多～ 好希望趕快開學;)
