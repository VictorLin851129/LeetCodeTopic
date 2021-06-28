# 131. Palindrome Partitioning
## Solution
```
class Solution {
    public List<List<String>> partition(String s) {
        List<List<String>> retval = new ArrayList<List<String>>();
    	boolean [][] dp = new boolean[s.length()][s.length()];
        
    	backTracking(0, dp, new ArrayList<String>(), retval, s);
    	
    	return retval;
    }

	private static void backTracking(int start, boolean[][] dp, ArrayList<String> subRet, List<List<String>> retval, String s) {
		if(start == s.length()) {
			retval.add(new ArrayList<>(subRet));
			return;
		}
		for(int end = start; end < s.length(); end++) {
			if((s.charAt(start) == s.charAt(end) &&
					(end - start < 3 || dp[start + 1][end - 1]))){
				dp[start][end] = true;
				subRet.add(s.substring(start, end + 1));
				backTracking(end + 1, dp, subRet, retval, s);
				subRet.remove(subRet.size() - 1);
			}
		}
    }
}
```
### Time complexity: O(n * 2 ^ n)
#### Where n is length of s
### Space complexity: O(n * n)
#### Where n is length of s