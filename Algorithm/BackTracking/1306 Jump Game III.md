# 1306. Jump Game III
## Solution
```
class Solution {
    public boolean canReach(int[] arr, int start) {
        boolean[] visited = new boolean[arr.length];
		return backTracking(arr, start, visited);
    }

	private static boolean backTracking(int[] arr, int start, boolean[] visited) {
		if(start < 0 || start >= arr.length || visited[start]) {
			return false;
		}
		if(arr[start] == 0) {
			return true;
		}
		
		visited[start] = true;
		if(backTracking(arr, start + arr[start], visited) || backTracking(arr, start - arr[start], visited)) {
			return true;
		}
		
		return false;
	}
}
```
### Time complexity: O(n)
#### Where n is length of arr
### Space complexity: O(n)
#### Where n is length of arr