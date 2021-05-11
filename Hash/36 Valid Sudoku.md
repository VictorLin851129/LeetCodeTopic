# 36. Valid Sudoku
```
class Solution {
    public boolean isValidSudoku(char[][] board) {
        for(int i = 0; i < board.length; i++) {
        	LinkedList<Character> row = new LinkedList<Character>();
        	LinkedList<Character> col = new LinkedList<Character>();
        	for(int j = 0; j < board[0].length; j++) {
        		//check col
        		if(board[i][j] != '.') {
	        		if(row.indexOf(board[i][j]) != -1) {
	        			return false;
	        		}
	        		row.add(board[i][j]);
        		}	
        		
        		//check row
        		if(board[j][i] != '.') {
	        		if(col.indexOf(board[j][i]) != -1) {
	        			return false;
	        		}
	        		col.add(board[j][i]);
        		}
        	}
        }
    	
    	for(int i = 0; i < 3; i++) {
    		for(int k = 0; k < 3; k++) {
    			LinkedList<Character> square = new LinkedList<Character>();
    			for(int j = 3 * i; j < 3 * i + 3; j++) {
    				for(int x = 3 * k; x < 3 * k + 3; x++) {
    					if(board[j][x] != '.') {
    		        		if(square.indexOf(board[j][x]) != -1) {
    		        			return false;
    		        		}
    		        		square.add(board[j][x]);
    	        		}	
    				}
    			}
    		}
    	}
    	
    	return true;
    }
}
```
### Time complexity: O(n)
#### Where n is length of board
### Space complexity: O(n)
#### Where n is length of board