# ***240. Search a 2D Matrix II
## Solution 1: O(row * col)
```
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        int row = matrix.length;
    	int col = matrix[0].length;
        for(int rowS = 0; rowS < row; rowS++) {
    		if(matrix[rowS][0] > target) {
    			continue;
    		}
    		for(int colS = 0; colS < col; colS++) {
    			if(matrix[rowS][colS] > target) {
        			break;
        		}
    			if(matrix[rowS][colS] == target) {
    				return true;
    			}
    		}
    	}
    	return false;
    }
}
```
### Time complexity: O(row * col)
### Space complexity: O(1)
---
## Solution 2: O(row + col)
```
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        int row = 0;
    	int col = matrix[0].length - 1;
    	
    	while(row < matrix.length && col >= 0) {
	    	if(target == matrix[row][col]) {
	    		return true;
	    	}else if(target > matrix[row][col]) {
	    		row++;
	    	}else {
	    		col--;
	    	}
    	}
    	
    	return false;
    }
}
```
### Time complexity: O(row + col)
### Space complexity: O(1)
---
## Solution 3: O(log(row * col))
#### Check all Left diagonal part or Right diagonal part
```
class Solution {
    int[][] matrix;
	int target;
    public boolean searchMatrix(int[][] matrix, int target) {
        int rowS = 0, rowE = matrix.length - 1;
    	int colS = 0, colE = matrix[0].length - 1;
    	
    	this.matrix = matrix;
    	this.target = target;
    	
    	return helper(rowS, rowE, colS, colE);
    }
	private boolean helper(int rowS, int rowE, int colS, int colE) {
		if(rowS > rowE || colS > colE || rowS >= matrix.length || rowE < 0 || colS >= matrix[0].length || colE < 0) {
			return false;
		}
		int midRow = (rowS + rowE) / 2;
		int midCol = (colS + colE) / 2;
			
		if(target == matrix[midRow][midCol]) {
			return true;
		}else if(target < matrix[midRow][midCol]) {
			return helper(rowS, midRow - 1, colS, colE) || helper(rowS, rowE, colS, midCol - 1);
		}else {
			return helper(midRow + 1, rowE, colS, colE) || helper(rowS, rowE, midCol + 1, colE);
		}
	}
}
```
### Time complexity: O(log(row * col)
### Space complexity: O(1)
---
## Solution4:  O(log(row * col))
#### Only check left(include)-down & right(not include)-up when target < matrix[Row][midCol]
```
class Solution {
    int[][] matrix;
	int target;
    public boolean searchMatrix(int[][] matrix, int target) {
        int rowS = 0, rowE = matrix.length - 1;
    	int colS = 0, colE = matrix[0].length - 1;
    	
    	this.matrix = matrix;
    	this.target = target;
    	
    	return helper(rowS, rowE, colS, colE);
    }
	private boolean helper(int rowS, int rowE, int colS, int colE) {
		if(rowS > rowE || colS > colE) {
			return false;
		}
		int Row = rowS;
		int midCol = (colS + colE) / 2;
		
		
		while(Row <= rowE) {
			if(matrix[Row][midCol] < target) {
				Row++;
			}else if(matrix[Row][midCol] == target) {
				return true;
			}else {
				break;
			}
		}
		
		return helper(Row, rowE, colS, midCol - 1) || helper(rowS, Row - 1, midCol + 1, colE);
	}
}
```
### Time complexity: O(log(row * col)
### Space complexity: O(1)