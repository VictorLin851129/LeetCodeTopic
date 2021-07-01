# 42. Trapping Rain Water
## Solution
```
class Solution {
    public int trap(int[] height) {
        if(height.length == 0) {
    		return 0;
    	}
        int[] dpL = new int[height.length];
    	int[] dpR = new int[height.length];
    	int retval = 0;
    	
    	dpL[0] = height[0];
    	for(int i = 1; i < height.length; i++) {
    		dpL[i] = Math.max(dpL[i - 1], height[i]);
    	}

    	dpR[height.length - 1] = height[height.length - 1];
    	for(int i = height.length - 2; i >= 0; i--) {
    		dpR[i] = Math.max(dpR[i + 1], height[i]);
            retval += Math.min(dpL[i], dpR[i]) - height[i];
    	}
    	
        return retval;
    }
}
```
### Time complexity: O(n)
#### Where n is length of height
### Space complexity: O(n)
#### Where n is length of height