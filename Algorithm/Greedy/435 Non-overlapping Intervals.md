# 435. Non-overlapping Intervals
## Solution
```
class Solution {
    public int eraseOverlapIntervals(int[][] intervals) {
        //sort y-axis from small to large
    	Arrays.parallelSort(intervals, (a1, a2) -> a1[1] - a2[1]);
    	int preEnd = intervals[0][1];
    	int overlap = 0;
    	
    	for(int i = 1; i < intervals.length; i++) {
    		if(preEnd > intervals[i][0]) {
    			overlap++;
    			preEnd = Math.min(preEnd, intervals[i][1]);
    		}else {
    			preEnd = intervals[i][1];
    		}
    	}
    	
        return overlap;
    }
}
```
### Time complexity: O(nlogn)
#### Where n is length of intervals
### Space complexity: O(1)