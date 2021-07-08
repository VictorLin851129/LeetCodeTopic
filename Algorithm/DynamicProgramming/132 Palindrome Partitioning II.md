# 132. Palindrome Partitioning II
## Solution 1
```
class Solution {
    public int minCut(String s) {
        boolean[][] isPalindrome = new boolean[s.length()][s.length()];
    	int[] minCut = new int[s.length()];
    	
    	for(int i = 0; i < s.length(); i++) {
    		minCut[i] = i;
    		for(int j = 0; j <= i; j++) {
    			if(s.charAt(i) == s.charAt(j) &&
    					(i - j <= 2 || isPalindrome[i - 1][j + 1])) {
    				isPalindrome[i][j] = true;
    				minCut[i] = Math.min(minCut[i], j - 1 >= 0 ? minCut[j - 1] + 1: 0);
    			}
    		}
    	}
        
        return minCut[s.length() - 1];
    }
}
```
### Time complexity: O(n^2)
#### Where n is length of s
### Space complexity: O(n^2)
#### Where n is length of s