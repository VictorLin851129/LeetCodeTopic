# 81. Search in Rotated Sorted Array II
## Solution
```
class Solution {
    public boolean search(int[] nums, int target) {
        int start = 0;
    	int end = nums.length - 1;
    	
    	while(start <= end) {
    		int mid = (start + end) / 2;
    		
    		if(nums[mid] == target) {
    			return true;
    		}
    		
    		if(nums[start] == nums[mid]) {
    			start++;
    			continue;
    		}
    		
    		boolean TargetSide = SideCheck(nums[start], target);	//true 1 part, false other part
    		boolean MidSide = SideCheck(nums[start], nums[mid]);
    		
    		if(TargetSide ^ MidSide) {	//xor true if only one of them are true
    			if(nums[start] > target) {
    				start = mid + 1;
    			}else {
    				end = mid - 1;
    			}
    		}else {
    			
    			if(target > nums[mid]) {
    				start = mid + 1;
    			}else {
    				end = mid - 1;
    			}
    		}
    	}
    	
		return false;
    }

	private static boolean SideCheck(int start, int element) {
		return start <= element;		//if start == target we just need to get start 
	}
}
```
### Time complexity: O(log(n))
#### Where n is length of nums
### Space complexity: O(1)