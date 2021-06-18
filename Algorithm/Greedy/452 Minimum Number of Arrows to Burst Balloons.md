# 452. Minimum Number of Arrows to Burst Balloons
## Solution
```
class Solution {
    public int findMinArrowShots(int[][] points) {
        //sort y-axis from small to large
    	Arrays.parallelSort(points, (a1, a2) -> Integer.compare(a1[1], a2[1]));
    	int preEnd = points[0][1];
    	int overlap = 0;
    	
    	for(int i = 1; i < points.length; i++) {
    		if(preEnd >= points[i][0]) {
    			//System.out.println(preEnd + " " + points[i][0]);
    			overlap++;
    			preEnd = Math.min(preEnd, points[i][1]);
    		}else {
    			preEnd = points[i][1];
    		}
    	}
    	
        return points.length - overlap;
    }
}
```
### Time complexity: O(n)
#### Where n is length of points
### Space complexity: O(1)