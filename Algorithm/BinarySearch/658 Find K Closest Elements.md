# 658. Find K Closest Elements
## Solution
```
class Solution {
    public List<Integer> findClosestElements(int[] arr, int k, int x) {
        int left = 0;
    	int right = arr.length - k;
    	
    	while(left < right) {
    		int mid = (left + right) / 2;
    		
    		if(x - arr[mid] > arr[mid + k] - x) {
    			left = mid + 1;
    		}else {
    			right = mid;
    		}
    	}
    	
    	ArrayList<Integer> retval = new ArrayList<Integer>();
    	for(int i = left; i < left + k; i++) {
    		retval.add(arr[i]);
    	}
    	
        return retval;
    }
}
```
### Time complexity: O(log(n) + k)
#### Where n is length of arr
### Space complexity: O(k)