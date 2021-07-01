# 32. Longest Valid Parentheses
## Solution
```
class Solution {
    public int longestValidParentheses(String s) {
        int[] dp = new int[s.length()];
    	int retval = 0;
    	
    	for(int i = 0; i < s.length(); i++) {
    		if(i > 0 && s.charAt(i) == ')') {
    			if(s.charAt(i - 1) == '(') {
    				if(i - 2 >= 0) {
    					dp[i] += dp[i - 2] + 2;
    				}else {
    					dp[i] += 2;
    				}
    			}else {
    				if(i - 1 - dp[i - 1] >= 0) {
    					if(s.charAt(i - 1 - dp[i - 1]) == '(') {
    						if(i - 1 - dp[i - 1] <= 1) {
    							dp[i] += dp[i - 1] + 2;
    						}else {
    							dp[i] += dp[i - 1] + dp[i - 1 - dp[i - 1] - 1] + 2;
    						}
    					}
    				}
    			}
    			
    			if(dp[i] > retval) {
    				retval = dp[i];
    			}
    		}
    	}
    	
        return retval;
    }
}
```
### Time complexity: O(n)
#### Where n is length of s
### Space complexity: O(n)
#### Where n is length of s