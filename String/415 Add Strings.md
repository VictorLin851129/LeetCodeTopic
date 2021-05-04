# 415. Add Strings
```
class Solution {
    public String addStrings(String num1, String num2) {
       StringBuilder str = new StringBuilder();
        int carry = 0;
        int i = num1.length() - 1, j = num2.length() - 1;
        while(i >=0 || j >= 0) {
        	int num1Int = (i >= 0 ? num1.charAt(i) - '0' : 0);
        	int num2Int = (j >= 0 ? num2.charAt(j) - '0' : 0);
        	
        	int temp = num1Int + num2Int + carry;
        	if(temp >= 10) {
        		str.append(temp - 10);
        		carry = 1;
        	}else {
        		str.append(temp);
        		carry = 0;
        	}
        	i--;
        	j--;
        }
        
        if(carry == 1) {
        	str.append(1);
        }
        
        return str.reverse().toString();
    }
}
```
### Time complexity: O(n)
#### Where n is max of length between num1 and num2
### Space complexity: O(n)
#### where n is max of length between num1 and num2