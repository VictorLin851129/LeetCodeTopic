# 63. Unique Paths II
## Solution
```
class Solution {
    public int uniquePathsWithObstacles(int[][] obstacleGrid) {
        int[][] dp = new int[obstacleGrid.length][obstacleGrid[0].length];
    	
    	for(int i = 0; i < obstacleGrid.length; i++) {
    		for(int j = 0; j < obstacleGrid[i].length; j++) {
    			if(obstacleGrid[i][j] != 1) {
	    			if(i == 0 || j == 0){
	    				if(i == 0 && j == 0){
	    					dp[i][j] = 1;
	    				}else if(i == 0 && j > 0 && obstacleGrid[i][j - 1] != 1) {
	    					dp[i][j] = dp[i][j - 1];
	    				}else if(i > 0 && j == 0 && obstacleGrid[i - 1][j] != 1) {
	    					dp[i][j] = dp[i - 1][j];
	    				}
	    			}else {
	    				dp[i][j] = dp[i - 1][j] + dp[i][j - 1];
	    			}
    			}
    		}
    	}
    	
        return dp[obstacleGrid.length - 1][obstacleGrid[0].length - 1];
    }
}
```
### Time complexity: O(m * n)
### Space complexity: O(m * n)