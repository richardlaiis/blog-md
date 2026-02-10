---
date: '2026-02-10T09:34:51+08:00'
draft: false
title: 'Leetcode 3719 - Longest Balanced Subarray I'
tags:
- LeetCode
- murmur
categories:
- LeetCode
---
## Intuition
Just brute force as the hints said, but unfortunately I got TLE, so this method is too slow QAQ

而且這其實也是錯的，進到 inner loop 前也要把 `nums[i]` 加入 `odd` 或 `even`，我忘了加。
```cpp
class Solution {
public:
    int longestBalanced(vector<int>& nums) {
        int n = nums.size();
        int ans = 0;
        for (int i = 0; i < n-1; i++) {
            for (int j = i+1; j < n; j++) {
                unordered_set<int> odd, even;
                for (int k = i; k <= j; k++) {
                    if (nums[k] & 1) odd.insert(nums[k]);
                    else even.insert(nums[k]);
                }
                if (odd.size() == even.size()) ans = max(ans, j-i+1);
            }
        }
        return ans;
    }
};
```
## Approach
一樣是暴力，只是紀錄奇偶元素數量的 set 可以被沿用。（然後用 hash map 應該會跑得比較快，不過一樣可以過，所以我懶得改 :p）
## AC Code
```cpp
class Solution {
public:
    int longestBalanced(vector<int>& nums) {
        int n = nums.size();
        int ans = 0;
        for (int i = 0; i < n-1; i++) {
            unordered_set<int> odd, even;
            if (nums[i] & 1) odd.insert(nums[i]);
            else even.insert(nums[i]);

            for (int j = i+1; j < n; j++) {
                if (nums[j] & 1) odd.insert(nums[j]);
                else even.insert(nums[j]);
                if (odd.size() == even.size()) ans = max(ans, j-i+1);
            }
        }
        return ans;
    }
};
```
## untitled
怎麼這幾天的題目都有 `balanced` XD。

感覺自己確實有一點網路&手遊成癮了，不過最近把自己所有的社群軟體都卸載了，感覺心情有變得比較好，至少暫時停止了比較的心態，~~而且自己就算消失其實也沒有人會發現、或是想去關心吧，我沒有熟到這樣的朋友，真的早該習慣孑然一人的生活ㄌ~~。希望開學前能戒掉過度的使用網路，沒有這些有毒的多巴胺我一樣能過的很好，真的。

加油吧。
