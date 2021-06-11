# 46. Permutations
## Solution
```
class Solution {
    public List<List<Integer>> permute(int[] nums) {
       ArrayList<List<Integer>> retval = new ArrayList<List<Integer>>();
    	ArrayList<Integer> subRet = new ArrayList<Integer>();
    	
    	backTracking(nums, 0, subRet, retval);
    	
    	return retval;
    }

	private static void backTracking(int[] nums, int index, ArrayList<Integer> subRet, ArrayList<List<Integer>> retval) {
		if(subRet.size() == nums.length) {
			retval.add(new ArrayList<Integer>(subRet));
			return;
		}
		
		for(int i = index; i < nums.length; i++) {
			if(subRet.contains(nums[i])) {
				continue;
			}
			subRet.add(nums[i]);
			backTracking(nums, index, subRet, retval);
			subRet.remove(subRet.size() - 1);
		}
	}
}
```
### Time complexity: O(n!)
#### Where n is length of nums
### Space complexity: O(n * (n - 1))
#### Where n is length of nums