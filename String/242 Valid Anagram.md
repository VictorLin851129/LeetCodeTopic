# 242. Valid Anagram
## Method 1
```
class Solution {
    public boolean isAnagram(String s, String t) {
        if(s.length() != t.length())
    		return false;
       char[] sChar = s.toCharArray();
    	char[] tChar = t.toCharArray();
    	Arrays.sort(sChar);
    	Arrays.sort(tChar);
    	
    	for(int i = 0; i < sChar.length; i++) {
    		if(sChar[i] != tChar[i]) {
    			return false;
    		}
    	}
    	
    	return true;
    }
}
```
### Time complexity: O(n * log(n))
#### Where n is length of s/t
### Space complexity: O(n)
#### Where n is length of s/t
---
## Method 2
```
class Solution {
    public boolean isAnagram(String s, String t) {
        
        int[] sChar = new int[26];
    	int[] tChar = new int[26];
    	
    	for(char c : s.toCharArray()) {
    		sChar[c - 'a']++;
		}
    	
    	for(char c : t.toCharArray()) {
    		tChar[c - 'a']++;
		}
	
    	for(int i = 0; i < sChar.length; i++) {
    		if(sChar[i] != tChar[i])
    			return false;
    	}
    	return true;
    }
}
```
### Time complexity: O(n)
#### Where n is length of Max(s, t)
### Space complexity: O(1)
