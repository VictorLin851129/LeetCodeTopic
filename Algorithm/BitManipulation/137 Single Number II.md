# 137. Single Number II
## Solution
```
class Solution {
    public int singleNumber(int[] nums) {
        //counter	input		result
    	// 0 0 			1		0 1
    	// 0 1			1		1 0
    	// 1 0			1		0 0
    	
    	int firstBit = 0;
    	int secondBit = 0;
    	
    	for(int i : nums) {
    		secondBit ^= firstBit & i;
    		firstBit ^= i;
    		
    		int mask = ~(firstBit & secondBit);
    		secondBit &= mask;
    		firstBit &= mask;
    	}
    	
        return firstBit;	//return firstBit cause the answer will only occur once
    }
}
```
### Time complexity: O(n)
#### Where n is length of nums
### Space complexity: O(1)