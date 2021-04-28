# 73. Set Matrix Zeroes
```
class Solution {
    public void setZeroes(int[][] matrix) {
        boolean col_zero = false, row_zero = false;
        
        for(int i = 0; i < matrix[0].length; i++) {
        	if(matrix[0][i] == 0) {
        		row_zero = true;
        		break;
        	}
        }
        
        for(int i = 0; i < matrix.length; i++) {
        	for(int j = 0; j < matrix[0].length; j++) {
        		if(i == 0 && j == 0 && matrix[i][j] == 0) {
        			col_zero = true;
        			row_zero = true;
        		}else if(j == 0 && matrix[i][j] == 0) {
        			col_zero = true;
        		}else {
        			if(matrix[i][j] == 0) {
        				matrix[i][0] = 0;
        				matrix[0][j] = 0;
        			}
        		}
        	}
        }
        
        for(int i = 1; i < matrix.length; i++) {
        	if(matrix[i][0] == 0) {
        		for(int j = 1; j < matrix[0].length; j++) {
            		matrix[i][j] = 0;
            	}
        	}
        }
        
        for(int i = 1; i < matrix[0].length; i++) {
        	if(matrix[0][i] == 0) {
	        	for(int j = 1; j < matrix.length; j++) {
	        		matrix[j][i] = 0;
	        	}
        	}
    	}
        

        if(col_zero) {
        	for(int i = 0; i < matrix.length; i++) {
        		matrix[i][0] = 0;
        	}
        }
        if(row_zero) {
        	for(int i = 0; i < matrix[0].length; i++) {
        		matrix[0][i] = 0;
        	}
        }
    }
}
```
### Time complexity: O(m * n)
#### Where n is row matrix
#### Where m is col matrix
### Space complexity: O(1)