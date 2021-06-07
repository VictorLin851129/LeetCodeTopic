# 35. Search Insert Position
## Solution
```
class Solution {
    public int searchInsert(int[] nums, int target) {
        int start = 0;
    	int end = nums.length - 1;
    	
    	while(start <= end) {
    		if(nums[(start + end) / 2] > target) {
    			end = (start + end) / 2 - 1;
    		}else if(nums[(start + end) / 2] < target) {
    			start = (start + end) / 2 + 1;
    		}else {
    			return (start + end) / 2;
    		}
    	}
    	
		return start;
    }
}
```
### Time complexity: O(log(n))
#### Where n is length of nums
### Space complexity: O(1)