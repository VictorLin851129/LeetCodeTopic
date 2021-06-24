# 5. Longest Palindromic Substring
## Solution
```
class Solution {
    public String longestPalindrome(String s) {
        boolean[][] dp = new boolean[s.length()][s.length()];
    	int start = 0;
    	int end = -1;
    	
    	for(int front = s.length() - 1; front >= 0; front--) {
    		for(int rear = s.length() - 1; rear >= front; rear--) {
    			if(s.charAt(front) == s.charAt(rear)) {
    				if((front + 1 < s.length() && rear - 1 >= 0  && dp[front + 1][rear - 1]) ||
    						(front == rear - 1 || front == rear)) {
    					dp[front][rear] = true;
    					if(rear - front > end - start) {
    						start = front;
    						end = rear;
    					}
    				}
    			}
    		}
    	}
        return s.substring(start, end + 1);
    }
}
```
### Time complexity: O(n ^ 2)
#### Where n is length of s
### Space complexity: O(n ^ 2)
#### Where n is length of s