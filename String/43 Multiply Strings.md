# 43. Multiply Strings
```
class Solution {
    public String multiply(String num1, String num2) {
       if(num1.equals("0") || num2.equals("0")) {
    		return "0";
    	}
    	StringBuilder retval = new StringBuilder();
    	
    	int[] num1Reverse = new int[num1.length()];
    	int[] num2Reverse = new int[num2.length()];
    	for(int i = num1.length() - 1, j = 0; i >= 0; i--, j++) {
    		num1Reverse[j] = num1.charAt(i) - '0';
    	}
    	
    	for(int i = num2.length() - 1, j = 0; i >= 0; i--, j++) {
    		num2Reverse[j] = num2.charAt(i) - '0';
    	}
    	int firstBit = 0;
    	int[] product = new int[num1.length() + num2.length()];
    	for(int i = 0; i < num1Reverse.length; i++) {
    		for(int j = 0; j < num2Reverse.length; j++) {
    			product[i + j] += num1Reverse[i] * num2Reverse[j];
    			if(product[i + j] != 0 && (i + j > firstBit)) {
    				firstBit = i + j;
    			}
    		}
    	}
    	
    	for(int i = 1; i <= firstBit; i++) {
    		int carry = product[i - 1] / 10;
    		product[i - 1] = product[i - 1] % 10;
    		product[i] += carry;
    	}
    	
    	for(; firstBit >= 0; firstBit--) {
    		retval.append(product[firstBit]);
    	}
    	
        return retval.toString();
    }
}
```
### Time complexity: O(n + m)
#### Where n is length of num1
#### Where m is length of num2
### Space complexity: O(n + m)
#### Where n is length of num1
#### Where m is length of num2