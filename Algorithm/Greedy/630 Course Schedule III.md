# 630. Course Schedule III
## Solution
```
class Solution {
    public int scheduleCourse(int[][] courses) {
        PriorityQueue<Integer> courseDuration = new PriorityQueue<Integer>((a1, a2) -> (a2 - a1));
		
    	Arrays.sort(courses, ((a1, a2) -> (a1[1] - a2[1])));
    	int totalHour = 0;
    	for(int[] course : courses) {
    		if(totalHour + course[0] <= course[1]) {
    			totalHour += course[0];
	    		courseDuration.add(course[0]);
    		}else if(!courseDuration.isEmpty() && courseDuration.peek() > course[0]){
    			totalHour -= courseDuration.poll();
    			totalHour += course[0];
    			courseDuration.add(course[0]);
    		}
    	}
    	return courseDuration.size();
    }
}
```
### Time complexity: O(nlog(n))
#### Where n is length of courses
### Space complexity: O(n)
#### Where n is length of courses