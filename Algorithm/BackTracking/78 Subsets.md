# 78. Subsets
## Solution
```
class Solution {
    public List<List<Integer>> subsets(int[] nums) {
        ArrayList<List<Integer>> retval = new ArrayList<List<Integer>>();
    	ArrayList<Integer> subRet = new ArrayList<Integer>();
    	
    	backTracking(nums, 0, subRet, retval);
    	
    	return retval;
    }

	private static void backTracking(int[] nums, int index, ArrayList<Integer> subRet, ArrayList<List<Integer>> retval) {
		retval.add(new ArrayList<Integer>(subRet));
		
		for(int i = index; i < nums.length; i++) {
			subRet.add(nums[i]);
			backTracking(nums, i + 1, subRet, retval);
			subRet.remove(subRet.size() - 1);
		}
	}
}
```
### Time complexity: $$O(n*2^n)$$
#### Where n is length of nums(first n is copy)
### Space complexity: $$O(2^n)$$
#### Where n is length of nums