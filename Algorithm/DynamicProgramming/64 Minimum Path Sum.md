# 64. Minimum Path Sum
## Solution
```
class Solution {
    public int minPathSum(int[][] grid) {
        int[][] dp = new int[grid.length][grid[0].length];
	    	
			for(int i = 0; i < grid.length; i++) {
				for(int j = 0; j < grid[0].length; j++) {
					if(i == 0 || j == 0){
						if(i == 0 && j == 0){
							dp[i][j] = grid[i][j];
						}else if(i == 0 && j > 0) {
							dp[i][j] = dp[i][j - 1] + grid[i][j];
						}else if(i > 0 && j == 0) {
							dp[i][j] = dp[i - 1][j] + grid[i][j];
						}
					}else {
						dp[i][j] = Math.min(dp[i - 1][j] + grid[i][j], dp[i][j - 1] + grid[i][j]);
					}
				}
			}
			
			return dp[grid.length - 1][grid[0].length - 1];
    }
}
```
### Time complexity: O(m * n)
#### Where m is grid[0].length
#### Where n is grid.length
### Space complexity: O(m * n)