# 47. Permutations II
## Solution
```
class Solution {
    public List<List<Integer>> permuteUnique(int[] nums) {
     ArrayList<List<Integer>> retval = new ArrayList<List<Integer>>();
        
        boolean[] used = new boolean[nums.length];
        Arrays.sort(nums);
        backTracking(nums, new ArrayList<Integer>(), retval, used);
            
        return retval;
    }
    
    private static void backTracking(int[] nums, ArrayList<Integer> subRet, ArrayList<List<Integer>> retval, boolean[] used){
    	if(subRet.size() > nums.length) {
    		return;
    	}
        if(nums.length == subRet.size()) {
        	retval.add(new ArrayList<Integer>(subRet));
        	return;
        }
        
        
        for(int i = 0; i < nums.length; i++) {
        	if(used[i]) {
        		continue;
        	}
        	if(i > 0 && nums[i] == nums[i - 1] && !used[i - 1]) {
        		continue;
        	}
        	used[i] = true;
        	subRet.add(nums[i]);
        	backTracking(nums, subRet, retval, used);
        	used[i] = false;
        	subRet.remove(subRet.size() - 1);
        }
    }
}
```
### Time complexity: $$O(\sum_{k=1}^nP_{k}^{n})$$
#### Where n and k is given
### Space complexity: O(n! / (k1! * k2!... )
#### Where n is length of nums
#### Where k is duplicate value in nums