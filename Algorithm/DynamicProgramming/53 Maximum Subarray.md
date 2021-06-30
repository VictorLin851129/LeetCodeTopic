# 53. Maximum Subarray
## Solution
```
class Solution {
    public int maxSubArray(int[] nums) {
        int[] dp = new int[nums.length];
    	
    	dp[0] = nums[0];
    	int maxVal = nums[0];
    	for(int i = 1; i < nums.length; i++) {
    		dp[i] = nums[i] + (dp[i - 1] > 0 ? dp[i - 1]: 0);
    		maxVal = Math.max(dp[i], maxVal);
    	}
    	
        return maxVal;
    }
}
```
### Time complexity: O(n)
#### Where n is length of nums
### Space complexity: O(1)