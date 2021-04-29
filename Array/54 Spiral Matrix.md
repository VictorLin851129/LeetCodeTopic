# 54. Spiral Matrix
```
class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {
        List<Integer> ans = new ArrayList<Integer>();
    	int left_wall = 0, right_wall = matrix[0].length - 1;
    	int up_wall = 0, down_wall = matrix.length - 1;
    	
    	while(left_wall <= right_wall && up_wall <= down_wall) {
    		for(int i = left_wall; i <= right_wall; i++) {
    			ans.add(matrix[up_wall][i]);
    		}
    		for(int i = up_wall + 1; i <= down_wall; i++) {
    			ans.add(matrix[i][right_wall]);
    		}
    		
    		for(int i = right_wall - 1; up_wall != down_wall && i >= left_wall; i--) {
    			ans.add(matrix[down_wall][i]);
    		}
    		for(int i = down_wall - 1; left_wall != right_wall && i > up_wall; i--) {
    			ans.add(matrix[i][left_wall]);
    		}
    		
    		left_wall++;
    		right_wall--;
    		up_wall++;
    		down_wall--;
    	}
    	
        return ans;
    }
}
```
### Time complexity: O(n)
#### Where n is cells' count in matrix
### Space complexity: O(n)
#### Where n is cells' count in matrix