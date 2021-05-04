# 58. Length of Last Word
```
class Solution {
    public int lengthOfLastWord(String s) {
        int last = 0;
        
        int i = s.length() - 1;
    	while(i >= 0 && s.charAt(i) == ' ') {
    		i--;
    	}
    	while(i >= 0 && s.charAt(i) != ' ') {
    		last++;
    		i--;
    	}
        
        return last;
    }
}
```
### Time complexity: O(n)
#### Where n is length of s
### Space complexity: O(1)