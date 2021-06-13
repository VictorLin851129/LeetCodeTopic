# 216. Combination Sum III
## Solution
```
class Solution {
    public List<List<Integer>> combinationSum3(int k, int n) {
        ArrayList<List<Integer>> retval = new ArrayList<List<Integer>>();
    	ArrayList<Integer> subRet = new ArrayList<Integer>();
    	int[] candidates = {1, 2, 3, 4, 5, 6, 7, 8, 9};
    	
    	backTracking(candidates, 0, n, k, subRet, retval);
    	
    	return retval;
    }

	private static void backTracking(int[] candidates, int index, int remain, int RemainCount, ArrayList<Integer> subRet, ArrayList<List<Integer>> retval) {
		if(RemainCount < 0 || remain < 0) {
			return;
		}
		if(remain == 0 && RemainCount == 0) {
			retval.add(new ArrayList<Integer>(subRet));
		}
		
		for(int i = index; i < candidates.length; i++) {
			subRet.add(candidates[i]);
			backTracking(candidates, i + 1, remain - candidates[i], RemainCount - 1, subRet, retval);
			subRet.remove(subRet.size() - 1);
		}
	}
}
```
### Time complexity: $$O(n*2^n)$$
#### Where n is length of 1-9(n is copy)
### Space complexity: $$O(2^n)$$
#### Where n is length of 1-9