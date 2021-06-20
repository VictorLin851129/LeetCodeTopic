# 56. Merge Intervals
## Solution
```
class Solution {
    public int[][] merge(int[][] intervals) {
        Arrays.parallelSort(intervals, (a1, a2) -> (a1[0] - a2[0]));
    	LinkedList<int[]> retval = new LinkedList<int[]>();
    	
    	for(int[] interval : intervals) {
    		if(retval.isEmpty() || retval.getLast()[1] < interval[0]) {
    			retval.add(interval);
    		}else{
    			retval.getLast()[1] = Math.max(retval.getLast()[1], interval[1]);
    		}
    	}
    	
    	return retval.toArray(new int[retval.size()][]);
    }
}
```
### Time complexity: O(nlog(n))
#### Where n is length of intervals
### Space complexity: O(n)
#### Where n is length of intervals