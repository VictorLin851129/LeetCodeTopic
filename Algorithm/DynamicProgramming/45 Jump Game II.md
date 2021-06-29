# 45. Jump Game II
## Solution
```
class Solution {
    public int jump(int[] nums) {
        int[] dp = new int[nums.length];
    	dp[0] = 0;
    	
    	for(int i = 1; i < nums.length; i++) {
    		for(int j = i - 1; j >= 0; j--) {
    			if(nums[j] + j >= i) {
    				dp[i] = dp[j] + 1;
    			}
    		}
    	}
    	
    	return dp[nums.length - 1];
    }
}
```
### Time complexity: O(n * n)
#### Where n is length of nums
### Space complexity: O(n)
#### Where n is length of nums