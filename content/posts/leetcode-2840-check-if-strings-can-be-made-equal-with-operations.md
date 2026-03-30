---
date: '2026-03-30T19:51:27+08:00'
draft: false
title: 'Leetcode 2840 - Check if Strings Can Be Made Equal With Operations'
---
## Approach
+ Use hash table to record the frequency of each character of s1 and s2.
+ Note that only the position with same parity can be swapped, if two strings' sets of odd-position charaters are the same, they must can be permuted using finite number of transpositions.
## Code
```cpp
class Solution {
public:
    bool checkStrings(string s1, string s2) {
        int n = s1.length();
        vector<int> s1_odd(26, 0), s1_even(26, 0), s2_odd(26, 0), s2_even(26, 0);
        for (int i = 0 ; i < n; i++) {
            if (i & 1) {
                s1_odd[s1[i]-'a']++;
                s2_odd[s2[i]-'a']++;
            } else {
                s1_even[s1[i]-'a']++;
                s2_even[s2[i]-'a']++;
            }
        }

        for (int i = 0; i < 26; i++) {
            if (s1_odd[i] != s2_odd[i] || s1_even[i] != s2_even[i]) return false;
        }

        return true;
    }
};
```
