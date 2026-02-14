---
date: '2026-02-14T16:50:10+08:00'
draft: false
title: 'Leetcode 799 - Champagne Tower'
tags:
- LeetCode
- murmur
categories:
- LeetCode
---
## Solution
試著模擬一次倒下所有香檳後的過程。不過這作法基本上是參考官解的，但對我來說蠻神奇的，因此選擇發上來紀錄一下。
## Code
```cpp
class Solution {
public:
    double champagneTower(int poured, int query_row, int query_glass) {
        vector<vector<double>> glasses(101, vector<double>(101));
        glasses[0][0] = poured;
        for (int r = 0; r <= query_row; r++) {
            for (int c = 0; c <= query_glass; c++) {
                double rest = (glasses[r][c] - 1.0) / 2.0;
                if (rest > 0) {
                    glasses[r+1][c] += rest;
                    glasses[r+1][c+1] += rest;
                }
            }
        }
        return min(1.0, glasses[query_row][query_glass]);
    }
};
```
## 26/2/11~26/2/14
不知道第幾次和家人環島了，感覺很開心，因為可以住旅館、吃早餐的buffet(如果有的話)、到處吃當地小吃，以及欣賞絕美的海景。不過玩四天我們一家四口花了 10000 多，感覺好燒錢 QAQ 儘管家裡人在吃的層面都盡量省了。

最近發現到自己已經再也沒辦法純粹地去享受那些快樂了，我滿腦子裡想的都是責任、錢途，還有令人害怕的未來。對，我其實害怕未來，因為自己真的很弱小，或許有天會變得真的孤身一人，卻沒有活下去的勇氣。所以我才更需要變得更強大，才能讓我所愛的那些人沒有後顧之憂地活著，從責任中掙脫，不管活著再痛苦也是我的選擇，不過我其實也不希望自己痛苦，那就變得麻木吧，不要期待/信任自己、他人和任何好事，只要清楚自己做的事是有意義的就行了。

前幾天聽到很好聽、頗具深意的一首歌:  [R.I.P - Language of the Lost ft. Kasane Teto SV (SynthV Original Song)](https://youtu.be/1xEfMnXyGkA?si=W0IeL_6lG1LOcUnG)，我很喜歡裡頭的歌詞，應該之後有空會想翻譯為繁體中文看看，不知道自己為什麼這麼想，明明是沒有意義的事情XD

晚安。
