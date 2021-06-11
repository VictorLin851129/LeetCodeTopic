# 90. Subsets II
## Solution
```
class Solution {
    public List<List<Integer>> subsetsWithDup(int[] nums) {
ArrayList<List<Integer>> retval = new ArrayList<List<Integer>>();
    	ArrayList<Integer> subRet = new ArrayList<Integer>();
    	Arrays.parallelSort(nums);
    	backTracking(nums, 0, subRet, retval);
    	
    	return retval;
    }

	private static void backTracking(int[] nums, int index, ArrayList<Integer> subRet, ArrayList<List<Integer>> retval) {
		retval.add(new ArrayList<Integer>(subRet));
		
		for(int i = index; i < nums.length; i++) {
			if(i > index && nums[i] == nums[i - 1]) {
				continue;
			}
			subRet.add(nums[i]);
			backTracking(nums, i + 1, subRet, retval);
			subRet.remove(subRet.size() - 1);
		}
	}
}
```
### Time complexity: $$O((n - k) * (2^n - 2^k))$$
#### Where n is length of nums(first n is copy)
#### where k is the duplicate counts
### Space complexity: $$O(2^n - 2 ^ k)$$
#### Where n is length of nums