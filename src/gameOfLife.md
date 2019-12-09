#### 289 Game of Life
Leetcode question #289</br>
Technique use: 
```
class Solution {
    public void gameOfLife(int[][] board) {
        if (board.length == 0) return;
        
        for (int i = 0; i < board.length; i++) {
            for (int j = 0; j < board[i].length; j++) {
                int live = numOfLifeAround(board, i, j);
                if (live == 3) {
                    board[i][j] += 10;
                } else if (live == 2 && (board[i][j] == 1 || board[i][j] == 11)) { 
                    board[i][j] += 10;
                }
            }
        }
        
        for (int i = 0; i < board.length; i++) {
            for (int j = 0; j < board[i].length; j++) {
                board[i][j] /= 10; 
            }
        }
    }
    
    public int numOfLifeAround(int[][] board, int r, int c) {
        int live = 0;
        for (int i = r - 1; i <= r + 1; i++) {
            for (int j = c - 1; j <= c + 1; j++) {
                if (i == r && j == c) continue;
                if (i >= 0 && j >= 0 && i < board.length && j < board[i].length && board[i][j] % 10 == 1) {
                    live++;             
                }
            }
        }
        return live;
    }
}
```