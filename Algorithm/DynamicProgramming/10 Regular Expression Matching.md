# 10. Regular Expression Matching
## Solution
```
class Solution {
    public boolean isMatch(String s, String p) {
        Boolean[][]dp = new Boolean[s.length() + 1][p.length() + 1];
    	
        return helper(dp, s, 0, p, 0);
	}

	private static boolean helper(Boolean[][] dp, String s, int sIndex, String p, int pIndex) {
		if(dp[sIndex][pIndex] != null) {
			return dp[sIndex][pIndex];
		}

		if(pIndex == p.length()) {
			return sIndex == s.length();
		}
		
		boolean result = false;
		boolean first_match = sIndex < s.length() && (s.charAt(sIndex) == p.charAt(pIndex) || p.charAt(pIndex) == '.');
		
		if(pIndex + 1 < p.length() && p.charAt(pIndex + 1) == '*') {
			result = (first_match && helper(dp, s, sIndex + 1, p, pIndex)) ||
					helper(dp, s, sIndex, p, pIndex + 2);
		}else {
			result = first_match && helper(dp, s, sIndex + 1, p, pIndex + 1);
		}
		
		dp[sIndex][pIndex] = result;
		return dp[sIndex][pIndex];
	}
}

```
### Time complexity: O(m * n)
#### Where n is length of s
#### Where m is length of p
### Space complexity: O(m * n)
#### Where n is length of s
#### Where m is length of p