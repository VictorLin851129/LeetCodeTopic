# 84. Largest Rectangle in Histogram
```
class Solution {
    public int largestRectangleArea(int[] heights) {
       int retval = 0;
        
        int[] left_less = new int[heights.length];
        int[] right_less = new int[heights.length];
        left_less[0] = -1;
        right_less[heights.length - 1] = heights.length;
        
        for(int i = 1; i < heights.length; i++) {
        	int index = i - 1;
        	while(index >= 0 && heights[i] <= heights[index]) {
        		index = left_less[index];
        	}
        	left_less[i] = index;
        }
        
        for(int i = heights.length - 2; i >= 0; i--) {
        	int index = i + 1;
        	while(index < heights.length && heights[i] <= heights[index]) {
        		index = right_less[index];
        	}
        	right_less[i] = index;
        }
        
        for(int i = 0; i < heights.length; i++) {
        	retval = Math.max(retval, heights[i] * (right_less[i] - left_less[i] - 1));
        }
        
        return retval;
    }
}
```
### Time complexity: O(n)
#### Where n is length of heights
### Space complexity: O(n)
#### Where n is length of heights