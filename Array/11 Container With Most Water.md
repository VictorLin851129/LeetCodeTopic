# 11. Container With Most Water
```
class Solution {
    public int maxArea(int[] height) {
        
		int ans = 0;
		int front = 0, rear = height.length - 1;
		
		while(front < rear) {
			int minHeight = Math.min(height[front], height[rear]);
			int area = minHeight * (rear - front);
			if(area > ans) {
				ans = area;
			}
//			if(height[front] == height[rear]) {
//				front++;
//				rear--;
//			}else if(height[front] > height[rear]) {
//				rear--;
//			}else {
//				front++;
//			}
			//Improve
            while (front < rear && height[front] <= minHeight) {
            	front++;
            }
            while (front < rear && height[rear] <= minHeight) {
            	rear--;
            }
		}
		
        return ans;
    }
}
```
### Time complexity: O(n)
#### Where n is length of height
### Space complexity: O(1)