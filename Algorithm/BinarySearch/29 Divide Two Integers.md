# 29. Divide Two Integers
## Solution
```
class Solution {
    public int divide(int dividend, int divisor) {
        if(dividend == 1 << 31 && divisor == -1) { // 1 << 31 == -2 ^ 31
    		return (1 << 31) - 1;	//(1 << 31) - 1 == 2 ^ 31 - 1
    	}
    	int retval = 0;
    	
    	boolean sign = (dividend > 0) == (divisor > 0);
    	
    	dividend = Math.abs(dividend);
    	divisor = Math.abs(divisor);
    	System.out.println(divisor);
    	while(dividend - divisor >= 0) {
    		int count = 0;
    		
    		while(dividend - (divisor << 1 << count) >= 0) {
    			count++;
    		}

    		dividend -= divisor << count;
    		retval += 1 << count;
    	}
    	
        return (sign == true)? retval: -retval;
    }
}

```
### Time complexity: O(log(n))
#### Where n is length of nums
### Space complexity: O(1)