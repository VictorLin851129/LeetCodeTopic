# 14. Longest Common Prefix
```
class Solution {
    public String longestCommonPrefix(String[] strs) {
        if(strs.length == 1) {
    		return strs[0];
    	}
    	
        String retval = strs[0];
        
        for(int i = 1; i < strs.length; i++) {
        	while(!strs[i].startsWith(retval)) {
        		retval = retval.substring(0, retval.length() - 1);
        	}
        	if(retval.isEmpty()) {
        		return "";
        	}
        }
        
        return retval;
    }
}
```

### Time complexity: O(n)
#### Where n is the total of characters in strs array
### Space complexity: O(n)
#### Where n is length of string in strs[0]