# 44. Wildcard Matching
## Solution
```
class Solution {
    public boolean isMatch(String s, String p) {
        int pLastMatch = -1;
    	int sLastMatch = -1;
    	int pIndex = 0;
    	int sIndex = 0;
    	while(sIndex < s.length()) {
    		if(pIndex < p.length() && (s.charAt(sIndex) == p.charAt(pIndex) || p.charAt(pIndex) == '?')) {
    			sIndex++;
    			pIndex++;
    		}else if(pIndex < p.length() && p.charAt(pIndex) == '*') {
    			while(pIndex < p.length() && p.charAt(pIndex) == '*') {
    				pLastMatch = pIndex;
    				pIndex++;
    			}
    			sLastMatch = sIndex;
    		}else if(pLastMatch != -1) {
    			pIndex = pLastMatch;
    			sIndex = sLastMatch + 1;
    			sLastMatch = sIndex;
    			pIndex++;
    		}else {
    			return false;
    		}
    	}
    	
    	while(pIndex < p.length()) {
    		if(p.charAt(pIndex) == '*') {
    			pIndex++;
    		}else {
    			return false;
    		}
    	}
    	
        return true;
    }
}
```
### Time complexity: O(n + m)
#### Where n is length of s
#### Where m is length of p
### Space complexity: O(n + m)
#### Where n is length of s
#### Where m is length of p