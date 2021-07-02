# 416. Partition Equal Subset Sum
## Solution
```
class Solution {
    public boolean canPartition(int[] nums) {
        int sum = 0;
    	
    	for(int i : nums) {
    		sum += i;
    	}
    	
    	if(sum % 2 == 1) {
    		return false;
    	}
    	
    	sum /= 2;
    	
    	boolean[][] dp = new boolean[nums.length + 1][sum + 1];
    	
    	for(int i = 0; i <= nums.length; i++) {
    		dp[i][0] = true;
    	}
    	
    	for(int i = 1; i <= nums.length; i++) {
    		for(int j = 1; j <= sum; j++) {
    			dp[i][j] = j - nums[i - 1] >= 0 ? dp[i - 1][j] || dp[i - 1][j - nums[i - 1]] : dp[i - 1][j];
    		}
    	}
    	
        return dp[nums.length][sum];
    }
}
```
### Time complexity: O(n * m)
#### Where n is length of nums
#### Where m is half of total nums
### Space complexity: O(n * m)
#### Where n is length of nums
#### Where m is half of total nums