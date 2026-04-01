---
date: '2026-04-01T09:52:33+08:00'
draft: false
title: 'Leetcode 2751 - Robot Collisions'
tags:
- 'LeetCode'
categories:
- 'LeetCode'
---
## Approach
將機器人的 index 依照位置排序，如果一個機器人往右衝就把它丟進 stack，反之，如果一個機器人往左衝，就一直跟 stack 裡面的機器人比較生命值，直到自己的生命值歸零/在較量中輸了或是 stack 已經清空。
## AC Code
```cpp
class Solution {
public:
    vector<int> survivedRobotsHealths(vector<int>& positions, vector<int>& healths, string directions) {
        int n = positions.size();
        vector<int> idx(n), res;
        stack<int> stack;

        for (int i = 0; i < n; i++) {
            idx[i] = i;
        }

        sort(idx.begin(), idx.end(), [&](int a, int b) { return positions[a] < positions[b]; });

        for (int cur:idx) {
            if (directions[cur] == 'R') {
                stack.push(cur);
            } else {
                while (!stack.empty() && healths[cur] > 0) {
                    int topIdx = stack.top();
                    stack.pop();

                    if (healths[topIdx] > healths[cur]) {
                        healths[topIdx]--;
                        healths[cur]=0;
                        stack.push(topIdx);
                    } else if (healths[topIdx] < healths[cur]) {
                        healths[cur]--;
                        healths[topIdx] = 0;
                    } else {
                        healths[topIdx]=0;
                        healths[cur]=0;
                    }
                }
            }
        }
        for (int i = 0; i < n; i++) {
            if (healths[i] > 0) {
                res.emplace_back(healths[i]);
            }
        }
        return res;
    }
};
```
## Happy April Fool's Day!
愚人節快樂，還蠻開心的，因為這是一年當中為我量身打造的節日，畢竟我本就是愚人:)
