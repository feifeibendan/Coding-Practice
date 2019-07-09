#### Count number of island
Leetcode question #200</br>
Technique use: DFS
```
public int numIslands(char[][] grid) {
    if (grid.length == 0) return 0; //if grid length = 0, then two dimension is empty
        
    int ans = 0;
    for (int i = 0; i < grid.length; i++) {
        for (int j = 0; j < grid[i].length; j++) {
            if (grid[i][j] == '1') {
                ans++;
                markSurroundingIsland(grid, i, j, grid.length, grid[i].length);
            }
        }
    }
    return ans;
}
    
public void markSurroundingIsland(char[][] grid, int i, int j, int n, int m) {
    if (i < 0 || j < 0 || i >= n || j >= m || grid[i][j] != '1') return;
    grid[i][j] = '0';
    markSurroundingIsland(grid, i - 1, j, n, m);
    markSurroundingIsland(grid, i + 1, j, n, m);
    markSurroundingIsland(grid, i, j - 1, n, m);
    markSurroundingIsland(grid, i, j + 1, n, m);
}
```