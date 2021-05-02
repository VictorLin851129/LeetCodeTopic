# 67. Add Binary
```
class Solution {
    public String addBinary(String a, String b) {
        int i = a.length() - 1, j = b.length() - 1;
    	StringBuilder retval = new StringBuilder();
    	
    	int carry = 0;
    	int sum = 0;
    	while(i >= 0 || j >= 0) {
    		int aInt = i >= 0 ? a.charAt(i) - '0' : 0;
    		int bInt = j >= 0 ? b.charAt(j) - '0' : 0;
    		sum = aInt + bInt + carry;
    		retval.append(Integer.toString(sum % 2));
    		carry = sum / 2;
    		i--;
    		j--;
    	}
    	
    	if(carry == 1){
    		retval.append('1');
    	}
    	
        return retval.reverse().toString();
    }
}
```
### Time complexity: O(n)
#### Where n is max length between a and b
### Space complexity: O(n)
#### Where n is max length between a and b