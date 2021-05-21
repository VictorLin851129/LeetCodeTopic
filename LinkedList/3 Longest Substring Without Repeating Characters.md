# 3. Longest Substring Without Repeating Characters
## Solution
```
class Solution {
    public int lengthOfLongestSubstring(String s) {
       HashMap<Character, Integer> map = new HashMap<Character, Integer>();
    	
    	int max = 0;
    	
    	for(int i = 0, j = 0; i < s.length(); i++) {
    		if(map.containsKey(s.charAt(i))) {
    			j = Math.max(j, map.get(s.charAt(i)) + 1);
    		}
    		max = Math.max(max, i - j + 1);
    		map.put(s.charAt(i), i);
    	}
    	
    	return max;
    }
    
}
```
### Time complexity: O(n)
#### Where n is length of s
### Space complexity: O(n)
#### Where n is length of s