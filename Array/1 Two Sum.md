# 1. Two Sum
```
class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> goal = new HashMap<Integer, Integer>();
		int[] ans = new int[2];
		
		for(int i = 0; i < nums.length; i++) {
			if(goal.containsKey(nums[i])) {
				return new int[] {goal.get(nums[i]),i};
			}
			goal.put(target - nums[i], i);
		}
		
		throw null;
    }
}
```
### Time complexity: O(n)
#### Where n is length of nums
### Space complexity: O(n)
#### Where n is length of nums