---
date: '2026-03-22T09:15:31+08:00'
draft: false 
title: 'Leetcode 1886 - Determine Whether Matrix Can Be Obtained by Rotation'
tags:
- 'LeetCode'
- 'Murmur'
categories:
- 'LeetCode'
- 'Murmur'
---
## Problem Link
https://leetcode.com/problems/determine-whether-matrix-can-be-obtained-by-rotation/
## Solution
```cpp
class Solution {
public:
    bool equal(vector<vector<int>>& a, vector<vector<int>>& b) {
        int n = a.size();

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                if (a[i][j] != b[i][j]) return false;
            }
        }

        return true;
    }

    void rotate(vector<vector<int>>& matrix) {
        int n = matrix.size();
        reverse(matrix.begin(), matrix.end());
        for (int i = 0; i < n; i++) {
            for (int j = i+1; j < n; j++) {
                swap(matrix[i][j], matrix[j][i]);
            }
        }
    }

    bool findRotation(vector<vector<int>>& mat, vector<vector<int>>& target) {
        for (int i = 0; i < 4; i++) {
            if (equal(mat, target)) return true;
            rotate(mat);
        }
        return false;
    }
};
```

## untitled
很久沒有更新了，主要原因還是因為自己的惰性。這次的旋轉可以透過多開一個陣列存的方式實現。但如果要省空間，也可以 in-place 地做，一種方式是透過對稱性，先把整個矩陣上下翻轉，再沿著主對角線翻轉 (這是順時針，如果要逆時針就是先左右翻轉，再延主對角線翻轉)

另一個方法是詳解提供的，大概是把矩陣切成四個象限，然後針對一個象限每個元素進行移動 (一次動四個元素，完成一個循環)，用說的有點抽象。XD

最近開始寫日記了，我覺得這應該是個好習慣，應該能讓自己心中的矛盾減輕一些，想找人傾訴自己的悲傷，卻又因為知道不會有人願意/有義務聽，之於事情也不會有任何改善，總之我覺得，不可能有任何人真正地把我從孤獨的深淵中拉出來。至少文字可以讓我釋出腦中的一些 cache，把這些痛苦、枯燥、重複的每一天記錄下來，等到時間令我忘卻，能不再把往日舊事視作創傷，談笑風生地看著曾經記錄下來、100% 與我無關的文字。
