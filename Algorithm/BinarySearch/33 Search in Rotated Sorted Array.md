# 33. Search in Rotated Sorted Array
## Solution
```
class Solution {
    public int search(int[] nums, int target) {
        int start = 0;
    	int end = nums.length - 1;
    	
    	while(start <= end) {
    		if(nums[(start + end) / 2] > target) {	//M > T
    			if((nums[start] <= nums[(start + end) / 2] && nums[start] <= target) 
    					|| (nums[start] > nums[(start + end) / 2] && nums[start] > target)) {
    				end = (start + end) / 2 - 1;
    			}else {
    				start = (start + end) / 2 + 1;
    			}
    		}else if(nums[(start + end) / 2] < target){ // M < T
    			if((nums[start] <= nums[(start + end) / 2] && nums[start] <= target) 
    					|| (nums[start] > nums[(start + end) / 2] && nums[start] > target)) {
    				start = (start + end) / 2 + 1;
    			}else {
    				end = (start + end) / 2 - 1;
    			}
    		}else {
    			return (start + end) / 2;
    		}
    	}
    	
        return -1;
    }
}
```
### Time complexity: O(log(n))
#### Where n is length of nums
### Space complexity: O(1)