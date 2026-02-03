---
date: '2026-02-03T09:06:58+08:00'
draft: false
title: 'LeetCode 3637 - Trionic Array I'
tags:
- LeetCode
- murmur
categories:
- LeetCode
---
## Approach
就是暴力題，所以才會被歸類在 Easy。只要紀錄每個區間的存在性以及當前的索引，並且細心判斷各種情況就行了，沒有使用到任何演算法知識。
## Code
```cpp
class Solution {
public:
    bool isTrionic(vector<int>& nums) {
        int cur = 1, n = nums.size();

        bool has = 0;
        while (cur < n && nums[cur] > nums[cur-1]) cur++, has = 1;
        if (!has || cur == n) return 0;
        
        has = 0;
        while (cur < n && nums[cur] < nums[cur-1]) cur++, has = 1;
        if (!has || cur == n) return 0;
        
        has = 0;
        while (cur < n && nums[cur] > nums[cur-1]) cur++, has = 1;
        if (!has || cur != n) return 0;
        return 1;
    }
};
```
## murmur
最近每天都好無聊，感覺自己正在變成一個更加無趣、更廢的一個存在，但或許這樣就不會再讓任何人失望了吧，我只要繼續埋頭努力就行了，不要再像以前一樣耽溺享樂，過度在意自己的感受;)

很希望趕快開學，就可以再次躋身忙碌之中，麻木比痛苦好太多了。
