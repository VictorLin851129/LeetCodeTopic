# 130. Surrounded Regions
## Solution
```
class Solution {
    
    class Point{
		int x;
		int y;
		Point(){
			
		}
		
		Point(int x, int y){
			this.x = x;
			this.y = y;
		}
	}
    
    public void solve(char[][] board) {
        int rowBound = board.length;
    	int colBound = board[0].length;
    	Queue<Point> queue = new LinkedList<Point>();
    	
    	//|****| check all 'o' boarder 
    	for(int i = 0; i < rowBound; i++) {
    		if(board[i][0] == 'O') {
    			board[i][0] = '*';
    			queue.add(new Point(i, 0));
    		}
    		if(board[i][colBound - 1] == 'O') {
    			board[i][colBound - 1] = '*';
    			queue.add(new Point(i, colBound - 1));
    		}
    	}
    	
    	//----
    	//****
    	//----
    	for(int i = 0; i < colBound; i++) {
    		if(board[0][i] == 'O') {
    			board[0][i] = '*';
    			queue.add(new Point(0, i));
    		}
    		if(board[rowBound - 1][i] == 'O') {
    			board[rowBound - 1][i] = '*';
    			queue.add(new Point(rowBound - 1, i));
    		}
    	}
    	
    	//check if boarder's neighbors are 'O'
    	while(!queue.isEmpty()) {
    		Point first = queue.remove();
    		
    		if(first.x > 0 && board[first.x - 1][first.y] == 'O') {//left
    			board[first.x - 1][first.y] = '*';
    			queue.add(new Point(first.x - 1, first.y));
    		}
    		if(first.x < rowBound - 1 && board[first.x + 1][first.y] == 'O') {//right
    			board[first.x + 1][first.y] = '*';
    			queue.add(new Point(first.x + 1, first.y));
    		}
    		if(first.y > 0 && board[first.x][first.y - 1] == 'O') {//up
    			board[first.x][first.y - 1] = '*';
    			queue.add(new Point(first.x, first.y - 1));
    		}
    		if(first.y < colBound - 1 && board[first.x][first.y + 1] == 'O') {//down
    			board[first.x][first.y + 1] = '*';
    			queue.add(new Point(first.x, first.y + 1));
    		}
    	}
    	
    	
    	for(int i = 0; i < rowBound; i++) {
    		for(int j = 0; j < colBound; j++) {
    			if(board[i][j] == 'O') {
    				board[i][j] = 'X';
    			}else if(board[i][j] == '*') {
    				board[i][j] = 'O';
    			}
    		}
    	}
    }
}
```
### Time complexity: O(row * col)
### Space complexity: at most O(boarder)
#### where boarder is 2 * row + 2 * col - 4