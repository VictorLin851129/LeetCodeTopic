# 77. Combinations
## Solution
```
class Solution {
    public List<List<Integer>> combine(int n, int k) {
        ArrayList<List<Integer>> retval = new ArrayList<List<Integer>>();
    	ArrayList<Integer> subRet = new ArrayList<Integer>();
    	
    	backTracking(n, k, 0, subRet, retval);
    	
    	return retval;
    }

	private static void backTracking(int candidates, int target_length, int index, ArrayList<Integer> subRet, ArrayList<List<Integer>> retval) {
		
		if(subRet.size() == target_length) {
			retval.add(new ArrayList<Integer>(subRet));
			return;
		}
		
		for(int i = index; i < candidates; i++) {
			subRet.add(i + 1);
			backTracking(candidates, target_length, i + 1, subRet, retval);
			subRet.remove(subRet.size() - 1);
		}
	}
}

```
### Time complexity: O(n! / (k - 1)!)
#### Where n and k is given
### Space complexity: $$O( C_{k}^n)$$
#### Where n and k is given