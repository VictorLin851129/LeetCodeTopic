# 136. Single Number
## Solution
```
class Solution {
    public int singleNumber(int[] nums) {
        int retval = 0;
    	for(int i = 0; i < nums.length; i++) {
    		retval ^= nums[i];
    	}
    	
        return retval;
    }
}
```
### Time complexity: O(n)
#### Where n is length of nums
### Space complexity: O(1)