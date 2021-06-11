# 39. Combination Sum
## Solution 1: BackTracking
```
class Solution {
    public List<List<Integer>> combinationSum(int[] candidates, int target) {
        ArrayList<List<Integer>> retval = new ArrayList<List<Integer>>();
    	ArrayList<Integer> subRet = new ArrayList<Integer>();
    	int index = 0;
    	//Arrays.parallelSort(candidates);
    	backTracking(candidates, target, index, subRet, retval);
    	
		return retval;
	}

	private void backTracking(int[] candidates, int remain, int index, ArrayList<Integer> subRet, ArrayList<List<Integer>> retval) {
		if(remain < 0) {
			return;
		}else if(remain == 0) {
			retval.add(new ArrayList<Integer>(subRet));
			return;
		}
		
		for(int i = index; i < candidates.length; i++) {
			subRet.add(candidates[i]);
			backTracking(candidates, remain - candidates[i], i, subRet, retval);
			subRet.remove(subRet.size() - 1);
		}
	}
}
```
### Time complexity: O(2^n) 
#### binomial theorem: 
$$ C_{0}^n + C_{1}^n + C_{2}^n + ... C_{n}^n = 2^n$$
where n is length of candidates

### Space complexity: O(1)
---
## Solution 2: DP
```
class Solution {
    public List<List<Integer>> combinationSum(int[] candidates, int target) {
        ArrayList<List<List<Integer>>> dp = new ArrayList<List<List<Integer>>>();
    	for(int i = 1; i <= target; i++) {
    		ArrayList<List<Integer>> retval = new ArrayList<List<Integer>>();
    		for(int j = 0; j < candidates.length; j++) {
    			if(candidates[j] > i) {
    				continue;
    			}
    			if(candidates[j] == i) {
    				retval.add(new ArrayList<Integer>(Arrays.asList(i)));
    			}else{
    				for(List<Integer> list : dp.get(i - candidates[j] - 1)) {
    					if(candidates[j] <= list.get(0)) {
    						ArrayList<Integer> subRet = new ArrayList<Integer>();
	    					subRet.add(candidates[j]);
		    				subRet.addAll(list);
		    				retval.add(subRet);
    					}
    				}
    			}
    		}
    		dp.add(retval);
    	}
		return dp.get(target - 1);
    }
}
```
### Time complexity: O(2^n)
### Space complexity: O(1)