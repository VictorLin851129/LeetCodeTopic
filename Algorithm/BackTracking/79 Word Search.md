# 79. Word Search
## Solution
```
class Solution {
    public boolean exist(char[][] board, String word) {
        for(int i = 0; i < board.length; i++) {
        	 for(int j = 0; j < board[0].length; j++) {
        		 if(backTracking(board, word, i, j, 0)) {
        			 return true;
        		 }
        	 }
         }
         return false;
	}

	private static boolean backTracking(char[][] board, String word, int row, int col, int index) {
		if(row < 0 || col < 0 || row >= board.length || col >= board[0].length || index >= word.length()) {
			return false;
		}
		if(board[row][col] != word.charAt(index)) {
			return false;
		}
		if(index == word.length() - 1) {
			return true;
		}
		board[row][col] = '*';
		boolean result = backTracking(board, word, row + 1, col, index + 1) || 
						backTracking(board, word, row, col + 1, index + 1) || 
						backTracking(board, word, row - 1, col, index + 1) || 
						backTracking(board, word, row, col - 1, index + 1);
		board[row][col] = word.charAt(index);
		return result; 
	}
}
```
### Time complexity: O(row * col * 4*l)
#### Where l is length of word
#### Where n and k is given
### Space complexity: O(1)