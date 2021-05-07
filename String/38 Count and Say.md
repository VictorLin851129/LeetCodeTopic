# 38. Count and Say
```
class Solution {
    public String countAndSay(int n) {
       StringBuilder retval = new StringBuilder();
    	retval.append(1);
    	for(int i = 1; i < n; i++) {
    		StringBuilder temp = new StringBuilder();
    		char tempC = retval.charAt(0);
    		int count = 1;
    		int index = 1;
    		while(index < retval.length()) {
    			if(retval.charAt(index) != tempC) {
    				temp.append(count);
    				temp.append(tempC);
    				tempC = retval.charAt(index);
    				count = 1;
    			}else {
    				count++;
    			}
    			index++;
    		}
    		temp.append(count);
			temp.append(tempC);
    		retval = temp;
    	}
        
        return retval.toString();
    }
}
```

### Time complexity: O(n * k)
#### Where n is given
#### Where k is the length of the largest sequence till n
### Space complexity: O(k)
#### where k is the length of the largest sequence till n