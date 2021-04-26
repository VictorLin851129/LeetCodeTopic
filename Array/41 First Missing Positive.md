# 41. First Missing Positive
```
class Solution {
    public int firstMissingPositive(int[] nums) {
         int retval = 0;
        
        int[] count = new int[nums.length + 1];
        for(int i : nums) {
        	if(i < nums.length + 1 && i > 0) {
        		count[i]++;
        	}
        }
        
        
        for(retval = 1; retval < count.length; retval++) {
        	if(count[retval] < 1) {
        		return retval;
        	}
        }
        
        return retval;
    }
}
```
### Time complexity: O(n)
#### Where n is length of nums
### Space complexity: O(n)
#### Where n is length of nums