#### Unique Path
Leetcode question #62</br>
Technique use: DFS, DP

```
class Solution {
    public int uniquePaths(int m, int n) {
        return dfs(0, 0, m, n);
    }
    
    public int dfs(int x, int y, int m, int n) {
        if (x == m - 1 && y == n - 1) return 1;
        if (x < m - 1 && y < n - 1) {
            return dfs(x + 1, y, m, n) + dfs(x, y + 1, m, n);
        }
        if (x < m - 1) {
            return dfs(x + 1, y, m, n);
        }
        if (y < n - 1) {
            return dfs(x, y + 1, m, n);
        }
        return 0;
    }
}
```

```
public int uniquePaths(int m, int n) {
    if (m == 0 || n == 0) return 0;
    int[][] dp = new int[m][n];
    //column
    for (int i = 0; i < m; i++) {
        dp[i][0] = 1;
    }
    //row
    for (int i = 0; i < n; i++) {
        dp[0][i] = 1;
    }
        
    for (int i = 1; i < m; i++) {
        for (int j = 1; j < n; j++) {
            dp[i][j] = dp[i - 1][j] + dp[i][j - 1];
        }
    }
    return dp[m - 1][n - 1];
}
```

