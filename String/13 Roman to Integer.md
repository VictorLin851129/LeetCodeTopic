# 13. Roman to Integer
```
class Solution {
    public int romanToInt(String s) {
        int retval = 0;
        
        for(int i = s.length() - 1; i >= 0; i--) {
        	switch(s.charAt(i)) {
        	case 'I':
        		retval += retval >= 5 ? -1 : 1;
        		break;
        	case 'V':
        		retval += 5;
        		break;
        	case 'X':
        		retval += retval >= 50 ? -10 : 10;
        		break;
        	case 'L':
        		retval += 50;
        		break;
        	case 'C':
        		retval += retval >= 500 ? -100 : 100;
        		break;
        	case 'D':
        		retval += 500;
        		break;
        	case 'M':
        		retval += 1000;
        		break;
        	}
        }
        
        return retval;
    }
}
```
### Time complexity: O(n)
#### Where n is length of s
### Space complexity: O(1)