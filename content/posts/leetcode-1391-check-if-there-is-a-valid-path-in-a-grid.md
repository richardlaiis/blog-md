---
date: '2026-04-27T13:07:28+08:00'
draft: false
title: 'Leetcode 1391 - Check if There Is a Valid Path in a Grid'
---
## Approach
BFS，但在做的時候需要去**確認下一格是否有與當前的格子連接**。
## Code
```cpp
class Solution {
public:
    bool hasValidPath(vector<vector<int>>& grid) {
        int m = grid.size();
        int n = grid[0].size();
        
        vector<vector<pair<int,int>>> dir(7);
        dir[1] = {{0, -1}, {0, 1}}; // l, r
        dir[2] = {{-1, 0}, {1, 0}}; // u, d
        dir[3] = {{0, -1}, {1, 0}}; // l, d
        dir[4] = {{0, 1}, {1, 0}}; // r, d
        dir[5] = {{0, -1}, {-1, 0}}; // l, u
        dir[6] = {{0, 1}, {-1, 0}}; // r, u

        queue<pair<int,int>> q;
        vector<vector<bool>> vis(m, vector<bool>(n, 0));

        q.push({0, 0});
        vis[0][0] = 1;

        while (!q.empty()) {
            auto [r, c] = q.front();
            q.pop();

            if (r == m-1 && c == n-1) return true;
            for (auto [dr, dc]:dir[grid[r][c]]) {
                int nr = r+dr;
                int nc = c+dc;
                if (nr < 0 || nc < 0 || nr >= m || nc >= n || vis[nr][nc]) {
                    continue;
                }

                for (auto [bdr, bdc]:dir[grid[nr][nc]]) {
                    int rr = nr+bdr; // reverse check
                    int rc = nc+bdc;
                    if (rr == r && rc == c) {
                        vis[nr][nc] = 1;
                        q.push({nr, nc});
                    }
                }
            }
        }

        return false;
    }
};
```
## murmur
好久沒更新了，我覺得自己情緒控管還是有待加強，太容易被某些事情激怒或弄哭了。或許哭不是件壞事，但生氣絕對是百害而無一利，因為我生氣的對象通常也是我很敬愛的人，而就算自己不傷人，也依然會被人尖銳的言語所刺傷。所以至少不要在別人面前生氣，最好不要展露任何情緒比較好。
