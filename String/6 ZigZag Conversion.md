# 6. ZigZag Conversion
```
class Solution {
    public String convert(String s, int numRows) {
        if(numRows >= s.length() || numRows == 1) {
    		return s;
    	}
    	StringBuilder retval = new StringBuilder();
    	
    	int row = 0;
    	while(row < numRows) {
    		int front = (numRows - row)  * 2 - 2;
        	int rear = 2 * row;
    		int index = row;
    		do {
    			if(front != 0) {
	    			retval.append(s.charAt(index));
	    			index += front;
    			}
    			if(index < s.length() && rear != 0) {
	    			retval.append(s.charAt(index));
	    			index += rear;
    			}
    		}while(index < s.length());
			row++;
    	}
    	
    	return retval.toString();
    }
}
```
### Time complexity: O(n)
#### Where n is length of s
### Space complexity: O(n)
#### Where n is length of s