# 5. Longest Palindromic Substring
## Solution 1: DP programming
```
class Solution {
    public String longestPalindrome(String s) {
        boolean[][] check = new boolean[s.length()][s.length()];
        int start = 0;
        int end = 0;
    	
        for(int j = 0; j < s.length(); j++) {
        	for(int i = 0; i <= j; i++) {
        		if((s.charAt(i) == s.charAt(j)) && (j - i < 3 || check[i + 1][j - 1])) {
        			check[i][j] = true;
        			if(j - i > end - start) {
        				start = i;
        				end = j;
        			}
        		}
        	}
        }
    	return s.substring(start, end + 1);
    }
}
```
### Time complexity: O(n * n)
#### Where n is length of s
### Space complexity: O(n * n)
#### Where n is length of s
---
## Solution 2: Manacher's Algorithm
```
class Solution {
    public String longestPalindrome(String s) {
        char[] toEven = new char[2 * s.length() + 1];
    	toEven[0] = '#';
    	for(int i = 0; i < s.length(); i++) {
    		toEven[2 * i + 1] = s.charAt(i);
    		toEven[2 * i + 2] = '#';
    	}
    	
    	int central = 0;
    	int radius = 0;
    	int Max_Central = 0;
    	int Max_Radius = 0;
    	int[] PalindromicRange = new int[toEven.length];
    	
    	for(int i = 0; i < toEven.length; i++) {
    		if(central + radius > i) {
    			int j = central + radius - i + (central - radius);
    			PalindromicRange[i] = Math.min(PalindromicRange[j], central + radius - i);
    			
    		}else {
    			PalindromicRange[i] = 1;
    		}
    		
    		while(i - PalindromicRange[i] >= 0 && 
    				 i + PalindromicRange[i] < toEven.length && 
    				 toEven[i - PalindromicRange[i]] == toEven[i + PalindromicRange[i]]) {
    			PalindromicRange[i]++;
    		}
    		
    		if(i + PalindromicRange[i] > central + radius) {
    			central = i;
    			radius = PalindromicRange[i];
    		}
    		
    		if(Max_Radius < PalindromicRange[i]) {
    			Max_Central = i;
    			Max_Radius = PalindromicRange[i];
    		}
    		
    	}
    	
    	return s.substring((Max_Central - Max_Radius + 1) / 2, (Max_Central + Max_Radius - 1) / 2);
    }
}

```
### Time complexity: O(n)
#### Where n is length of s
### Space complexity: O(n)
#### Where n is length of s