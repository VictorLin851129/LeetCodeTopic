# 40. Combination Sum II
## Solution: BackTracking
```
class Solution {
    public List<List<Integer>> combinationSum2(int[] candidates, int target) {
    ArrayList<List<Integer>> retval = new ArrayList<List<Integer>>();
		ArrayList<Integer> subRet = new ArrayList<Integer>();
		
		Arrays.parallelSort(candidates);
		backTracking(candidates, target, 0, subRet, retval);
		
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
			if(i > index && candidates[i] == candidates[i - 1]) {
				continue;
			}
			subRet.add(candidates[i]);
			backTracking(candidates, remain - candidates[i], i + 1, subRet, retval);
			subRet.remove(subRet.size() - 1);
		}
	}
}
```
### Time complexity: O(2^n) 
#### binomial theorem: 
$$ C_{0}^n + C_{1}^n + C_{2}^n + ... C_{n}^n = 2^n$$
where n is length of candidates

### Space complexity: O(n)
#### where n is length of candidates
