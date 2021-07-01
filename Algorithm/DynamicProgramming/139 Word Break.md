# 139. Word Break
## Solution
```
class Solution {
    public boolean wordBreak(String s, List<String> wordDict) {
        boolean[] dp = new boolean[s.length() + 1];
    	
    	dp[0] = true;
    	for(int i = 1; i <= s.length(); i++) {
    		for(String word : wordDict) {
    			if(i >= word.length() && dp[i - word.length()] && s.substring(i - word.length(), i).equals(word)) {
    				dp[i] = true;
    				break;
    			}
    		}
    	}
    	
    	return dp[s.length()];
    }
}
```
### Time complexity: O(n * m)
#### Where n is length of s
#### Where m is length of wordDict
### Space complexity: O(n)
#### Where n is length of s