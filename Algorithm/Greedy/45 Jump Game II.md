# 45. Jump Game II
## Solution
```
class Solution {
    public int jump(int[] nums) {
        if(nums.length == 1) {
    		return 0;
    	}
    	int cur = 0;
    	int jump = 1;
    	while(cur + nums[cur] < nums.length - 1) {
    		int max = 0;
    		int maxIndex = 0;
    		for(int i = cur + 1; i <= cur + nums[cur];i++) {
    			if(nums[i] != 0 && i + nums[i] >= maxIndex) {
    				maxIndex = i + nums[i];
    				max = i;
    			}
    		}
    		cur = max;
    		jump++;
    	}
    	
        return jump;
    }
}

```
### Time complexity: O(n)
#### Where n is length of nums
### Space complexity: O(1)