# 154. Find Minimum in Rotated Sorted Array II
## Solution
```
class Solution {
    public int findMin(int[] nums) {
        int start = 0;
    	int end = nums.length - 1;
    	
    	while(start < end) {
    		if(nums[start] < nums[end]) {
    			return nums[start];
    		}
    		
    		int mid = (start + end) / 2;
    		if(nums[start] == nums[mid]) {
    			start++;
    			continue;
    		}
    		
    		if(nums[mid] > nums[end]) {
    			start = mid + 1;
    		}else {
    			end = mid;
    		}
    	}
    	
		return nums[start];
    }
}
```
### Time complexity: O(log(n))
#### Where n is length of nums
### Space complexity: O(1)