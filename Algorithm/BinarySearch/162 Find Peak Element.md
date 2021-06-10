# 162. Find Peak Element
## Solution
```
class Solution {
    public int findPeakElement(int[] nums) {
        int start = 0;
    	int end = nums.length - 1;
    	
    	while(start < end) {
    		int mid = (start + end) / 2;
    		
    		if(nums[mid] < nums[mid + 1]){	//end max
    			start = mid + 1;
    		}else {
    			end = mid;
    		}
    	}
    	
        return start;
    }
}
```
### Time complexity: O(log(n))
#### Where n is length of nums
### Space complexity: O(1)