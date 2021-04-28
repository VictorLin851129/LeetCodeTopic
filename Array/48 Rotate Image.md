# 48. Rotate Image
```
class Solution {
    public static void rotate(int[][] matrix) {
    	transpose(matrix);
    	reverse(matrix);
    }
    
    public static void transpose(int[][] matrix) {
    	for(int i = 0; i < matrix.length; i++) {
    		for(int j = i; j < matrix[0].length; j++) {
    			if(i == j) {
    				continue;
    			}
    			int temp = matrix[i][j];
    			matrix[i][j] = matrix[j][i];
    			matrix[j][i] = temp;
    		}
    	}
    }
    
    public static void reverse(int[][] matrix) {
    	for(int[] row : matrix) {
    		for(int i = 0; i < row.length / 2; i++) {
    			int temp = row[i];
    			row[i] = row[row.length - i - 1];
    			row[row.length - i - 1] = temp;
    		}
    	}
    }
}
```
### Time complexity: O(n)
#### Where n is all cells in matrix
### Space complexity: O(1)