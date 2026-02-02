---
date: '2026-02-02T08:52:21+08:00'
draft: false
title: 'Leetcode 1509 - Minimum Difference Between Largest and Smallest Value in Three Moves'
tags:
- LeetCode
- murmur
categories:
- LeetCode
---
## Approach
有 4 種方式去移除三個元素，在將陣列由小至大排序後：
1. 移除前三個元素
2. 移除前兩個元素，以及尾端一個元素
3. 移除第一個元素，以及尾端兩個元素
4. 移除最後面三個元素

而這四種 case 最大最小值的 difference 很容易就可以推出來了，如程式碼所示。
## Code
```cpp
class Solution {
public:
    int minDifference(vector<int>& nums) {
        sort(nums.begin(), nums.end());

        int n = nums.size();
        if (n <= 4) return 0;

        int res = 2e9;
        for (int l = 0, r = n-4; l < 4; l++, r++) {
            res = min(res, nums[r]-nums[l]);
        }

        return res;
    }
};
```
## untitled
> 常常，我們誰不都是老犯同一個毛病，以一種自以為是並且蠻橫的方式去愛眼前的人，卻不知道眼前的人所渴望的，有時候不過是一個善意的牽引，一場低調的擺渡和一份體貼的成全，就好像我們根本不知道，張國榮在決定放棄對紅塵聲色的眷戀從酒店墜下之前，是如何地將自己關押在情緒的寒流裡哆嗦，在風光背後，摸索著比黑暗更黑暗的黑暗，卻永遠等不到詭異的天色，也許很快就會破曉。── 范俊奇《鏤空與浮雕》(星之全蝕)

