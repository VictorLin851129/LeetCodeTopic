# 85. Maximal Rectangle
```
class Solution {
   
    public int maximalRectangle(char[][] matrix) {
        if(matrix.length < 1 || matrix[0].length < 1) {
    		return 0;
    	}
    	int retval = 0;
    	
    	int[] col = new int[matrix[0].length];
    	
    	for(char[] row : matrix){
    		for(int i = 0; i < row.length; i++) {
    			if(row[i] == '1') {
    				col[i]++;
    			}else {
    				if(col[i] > 0) {
    					col[i] = 0;
    				}
    			}
    		}
    		int[] left_min = new int[col.length], right_min = new int[col.length];
            left_min[0] = -1;
            right_min[col.length - 1] = col.length;
            
            for(int i = 1; i < col.length; i++) {
            	int index = i - 1;
            	while(index >= 0 && col[i] <= col[index]) {
            		index = left_min[index];
            	}
            	left_min[i] = index;
            }
            
            for(int i = col.length - 2; i >= 0; i--) {
            	int index = i + 1;
            	while(index < col.length && col[i] <= col[index]) {
            		index = right_min[index];
            	}
            	right_min[i] = index;
            }
            
            
            for(int i = 0; i < col.length; i++) {
            	retval = Math.max(retval, col[i] * (right_min[i] - left_min[i] - 1));
            }
    	}
    	
        return retval;
    }
}
```
### Time complexity: O(n*m)
#### Where n is length of column
#### Where m is length of row
### Space complexity: O(n)
#### Where n is length of column