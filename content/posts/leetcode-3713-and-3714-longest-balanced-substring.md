---
date: '2026-02-15T20:26:48+08:00'
draft: true
title: 'LeetCode 3713&3714 - Longest Balanced Substring I&II'
---
## LeetCode 3713 - Longest Balanced Substring I
### Problem
You are given a string `s` consisting of lowercase English letters.

A substring of `s` is called balanced if all distinct characters in the substring appear the same number of times.

Return the length of the longest balanced substring of `s`.
#### Constraints
+ 1 <= `s.length` <= 1000
+ `s` consists of lowercase English letters.

### Approach
Brute force.
### AC Code
```cpp
class Solution {
public:
    int longestBalanced(string s) {
        int n = s.length();

        int res = 0;
        for (int i = 0; i < n; i++) {
            unordered_map<char, int> mp;
            for (int j = i; j < n; j++) {
                mp[s[j]]++;
            
                int prev = -1, cnt = 0;
                bool ok = 1;
                for (auto i:mp) {
                    cnt++;
                    if (prev == -1) prev = i.second;
                    else {
                        if (i.second != prev) {
                            ok = 0;
                        }
                    }
                }
                if (ok) res = max(res, j-i+1);
            }
        }
        
        return res;
    }
};
```
---
## LeetCode 3714 - Longest Balanced Substring II
### Problem
You are given a string `s` consisting only of the characters `'a'`, `'b'`, and `'c'`.

A substring of `s` is called balanced if all distinct characters in the substring appear the same number of times.

Return the length of the longest balanced substring of `s`.
#### Constraints
+ 1 <= `s.length` <= 10^5
+ `s` contains only the characters `'a'`, `'b'`, and `'c'`.

### Approach
### AC Code
