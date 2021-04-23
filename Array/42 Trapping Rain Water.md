# 42. Trapping Rain Water
```
class Solution {
    public int trap(int[] height) {
        int retval = 0;
		
		int left = 0, right = height.length - 1;
		int left_max = 0, right_max = 0;
		
		while(left <= right) {
			if(left_max < right_max) {
				if(height[left] > left_max) {
					left_max = height[left];
				}else {
					retval += left_max - height[left];
				}
				left++;
			}else {
				if(height[right] > right_max) {
					right_max = height[right];
				}else {
					retval += right_max - height[right];
				}
				right--;
			}
		}
		
        return retval;
    }
}
```
### Time complexity: O(n)
#### Where n is length of height
### Space complexity: O(1)