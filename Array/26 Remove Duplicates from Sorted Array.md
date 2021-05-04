# 26. Remove Duplicates from Sorted Array
```
class Solution {
    public int removeDuplicates(int[] nums) {
        if(nums.length < 1) {
    		return 0;
    	}
        int temp = nums[0];  	
    	int index = 1;
    	
    	for(int i = 1; i < nums.length; i++) {
    		if(temp != nums[i]) {
    			temp = nums[i];
    			nums[index++] = temp;
    		}
    	}
    	
		return index;
    }
}
```
### Time complexity: O(n)
#### Where n is length of nums
### Space complexity: O(1)