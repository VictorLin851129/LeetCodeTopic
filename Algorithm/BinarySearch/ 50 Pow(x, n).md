# 50. Pow(x, n)
## Solution
```
class Solution {
    public double myPow(double x, int n) {
        if(x == 0 || (n == 1 << 31 && x > 1)) {
    		return 0;
    	}
    	
    	if(n < 0) {
    		x = 1 / x;
    		n = -n;
    	}
    	
    	double retval = 1;
    	int bitN = n;
    	
    	while(bitN > 0) {
    		if((bitN & 1) == 1) {
    			retval *= x;
    		}
    		bitN = bitN >> 1;
    		x *= x;
    	}
    	
		return retval;
    }
}
```
### Time complexity: O(log(n))
#### Where n is length of n to bit
### Space complexity: O(1)