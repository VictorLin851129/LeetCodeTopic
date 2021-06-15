# 37. Sudoku Solver
## Solution
```
class Solution {
    public void solveSudoku(char[][] board) {
        backTracking(board);
	}

	private static boolean backTracking(char[][] board) {
		for(int i = 0; i < board.length; i++) {
			for(int j = 0; j < board[0].length; j++) {
				if(board[i][j] != '.') {
					continue;
				}
				for(char c = '1'; c <= '9'; c++) {
					if(isValid(board, i, j, c)) {
						board[i][j] = c;
						if(!backTracking(board)) {
							board[i][j] = '.';
						}else {
							return true;
						}
					}
				}
				return false;
			}
		}
		return true;
	}

	private static boolean isValid(char[][] board, int row, int col, char c) {
		for(int i = 0; i < board.length; i++) {
			if(i != col && board[row][i] == c) {
				return false;
			}
			if(i != row && board[i][col] == c) {
				return false;
			}
			if((row / 3 * 3 + i / 3 != row) && (col / 3 * 3 + i % 3 != col) 
					&& board[row / 3 * 3 + i / 3][col / 3 * 3 + i % 3] == c) {
				return false;
			}
		}
		return true;
	}
}
```