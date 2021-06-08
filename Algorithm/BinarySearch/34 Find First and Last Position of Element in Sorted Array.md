# 34. Find First and Last Position of Element in Sorted Array
## Solution
```
class Solution {
    public int[] searchRange(int[] nums, int target) {
        int start = 0;
    	int end = nums.length - 1;
    	int[] retval = new int[2];
    	
    	while(start <= end) {
    		if(nums[(start + end) / 2] > target) {
    			end = (start + end) / 2 - 1;
    		}else{	//nums[(start + end) / 2] <= target
    			start = (start + end) / 2 + 1;
    		}
    	}
    	retval[1] = (end >= 0 && nums[end] == target) ?end : -1;
    	
    	if(retval[1] == -1) {
    		return new int[]{-1, -1};
    	}
    	
    	start = 0;
    	end = nums.length - 1;
    	
    	while(start <= end) {
    		if(nums[(start + end) / 2] < target) {
    			start = (start + end) / 2 + 1;
    		}else{	//nums[(start + end) / 2] <= target
    			end = (start + end) / 2 - 1;
    		}
    	}
    	retval[0] = start;
    	
		return retval;
    }
}
```
### Time complexity: O(log(n))
#### Where n is length of nums
### Space complexity: O(1)