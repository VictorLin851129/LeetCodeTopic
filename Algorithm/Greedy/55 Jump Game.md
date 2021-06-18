# 55. Jump Game
## Solution
```
class Solution {
    public boolean canJump(int[] nums) {
        int n = nums.length - 1;
    	int cur = n;
    	
    	for(int i = cur - 1; i >= 0; i--) {
    		if(i + nums[i] >= cur) {
    			cur = i;
    		}
    	}
    	
        return cur == 0;
    }
}
```
### Time complexity: O(n)
#### Where n is length of nums
### Space complexity: O(1)