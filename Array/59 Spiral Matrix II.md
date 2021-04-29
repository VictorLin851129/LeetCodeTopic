# 59. Spiral Matrix II
```
class Solution {
    public int[][] generateMatrix(int n) {
        int[][] retval = new int[n][n];
        int count = 1;
        int left_wall = 0, right_wall = n - 1;
        int up_wall = 0, down_wall = n - 1;
        
        while(left_wall <= right_wall && up_wall <= right_wall) {
        	for(int i = left_wall; i <= right_wall; i++) {
        		retval[up_wall][i] = count++;
        	}
        	for(int i = up_wall + 1; i <= down_wall; i++) {
        		retval[i][right_wall] = count++;
        	}
        	
        	for(int i = right_wall - 1; up_wall != down_wall && i >= left_wall; i--) {
        		retval[down_wall][i] = count++;
        	}
        	for(int i = down_wall - 1; right_wall != left_wall && i > up_wall; i--) {
        		retval[i][left_wall] = count++;
        	}
        	
        	left_wall++;
        	right_wall--;
        	up_wall++;
        	down_wall--;
        }

        return retval;
    }
}
```
### Time complexity: O(n)
#### Where n is cells' count in matrix
### Space complexity: O(n)
#### Where n is cells' count in matrix