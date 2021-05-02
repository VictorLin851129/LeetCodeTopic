# 28. Implement strStr() 
## Method 1
# KMP algorithm
```
class Solution {
     public int strStr(String haystack, String needle) {
         if(haystack.length() < needle.length()) {
	    	return -1;
	    }
	    int [] kmp_result = kmp(needle);
	    
	    int i = 0, j = 0;
	    
	    while(i < haystack.length() && j < needle.length()) {
	    	if(haystack.charAt(i) == needle.charAt(j)) {
	    		i++;
	    		j++;
	    	}else if(j > 0) {
	    		j = kmp_result[j - 1];
	    	}else {
	    		i++;
	    	}
	    }
	    
	    return j == needle.length() ? i - j : -1;
     }
    
    public static int[] kmp(String needle) {
		 int[] kmp_result = new int[needle.length()];
		 
		 int i = 1, j = 0;
		 
		 while(i < needle.length()) {
			 if(needle.charAt(i) == needle.charAt(j)) {
				 kmp_result[i] = j + 1;
				 i++;
				 j++;
			 }else if(j > 0) {
				 j = kmp_result[j - 1];
			 }else {
				 kmp_result[i] = 0;
				 i++;
			 }
		 }
		 
		 return kmp_result;
	 }
	 
}
```
### Time complexity: O(n + m) in average and worst case
#### Where n is length of haystack
#### Where m is length of needle
### Space complexity: O(m)
#### Where m is length of needle
---
## Method 2
```
class Solution {
    public int strStr(String haystack, String needle) {
        return haystack.indexOf(needle);
    }
}
```
### Time complexity: 
#### Average O(n + m), Worst O(m * n)
#### Where n is length of haystack
#### Where m is length of needle
### Space complexity: O(1)
