# 260. Single Number III
## Solution
#### note: Integer.highestOneBit will cause problem, cause highest bit may be the sign of an integer, then (highBit & nums[i]) will always be negative
```
class Solution {
    public int[] singleNumber(int[] nums) {
        int twoXor = 0;
    	
    	for(int i = 0; i < nums.length; i++) {
    		twoXor ^= nums[i];
    	}
    	
    	int highBit = twoXor & (-twoXor);
    	int Firstnum = 0;
    	for(int i = 0; i < nums.length; i++) {
    		if((highBit & nums[i]) > 0) {
    			Firstnum ^= nums[i];
    		}
    	}
    	
        return new int[]{Firstnum, twoXor ^ Firstnum};
    }
}
```
### Time complexity: O(n)
#### Where n is length of nums
### Space complexity: O(1)