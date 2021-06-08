# 69. Sqrt(x)
## Solution
```
class Solution {
    public int mySqrt(int x) {
        if(x <= 1) {
    		return x;
    	}
    	int start = 1;
    	int end = x / 2;	
    	
    	while(start <= end) {
    		int mid = (start + end) / 2;
    		long pow = (long)mid * mid;
    		if(pow == x){
    			return mid;
    			
    		}else if(pow < x){
    			start = mid + 1;
    		}else if(pow > x) {
    			end = mid - 1;
    		}
    	}
    	
		return Math.min(start, end);
    }
}
```
### Time complexity: O(log(n))
#### Where n is length of nums
### Space complexity: O(1)