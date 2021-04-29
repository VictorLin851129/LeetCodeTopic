# 18. 4Sum(kSum)
```
class Solution {
    public List<List<Integer>> fourSum(int[] nums, int target) {
        Arrays.sort(nums);
        
        return kSum(4, 0, nums, target);
    }
    public static List<List<Integer>> kSum(int k, int start, int[] nums, int target) {
		List<List<Integer>> ans = new ArrayList<List<Integer>>();
		if(nums.length < 2 || nums[start] * k > target || nums[nums.length - 1] * k < target) {
			return ans;
		}
		if(k == 2) {
			return twoSumList(start, nums, target);
		}
		
		for(int i = start; i < nums.length - k + 1; i++) {
			if(i == start || nums[i] != nums[i - 1]) {
				for(var set : kSum(k - 1, i + 1, nums, target - nums[i])) {
					set.add(nums[i]);
					ans.add(set);
				}
			}
		}
		
		return ans;
    }
    public static List<List<Integer>> twoSumList(int start, int[] nums, int target) {
		List<List<Integer>> res = new ArrayList<List<Integer>>();
        int left = start, right = nums.length - 1;
        
        while(left < right) {
        	List<Integer> ansChild = new ArrayList<Integer>();
        	if(nums[left] + nums[right] == target) {
        		ansChild.add(nums[left]);
        		ansChild.add(nums[right]);
        		res.add(ansChild);
        		while(left < nums.length - 1 && nums[left] == nums[left + 1]) {
        			left++;
        		}
        		left++;
        		while(right > start && nums[right] == nums[right - 1]) {
        			right--;
        		}
        		right--;
        	}else if(nums[left] + nums[right] < target) {
        		while(left < nums.length - 1 && nums[left] == nums[left + 1]) {
        			left++;
        		}
        		left++;
        	}else {
        		while(right > start && nums[right] == nums[right - 1]) {
        			right--;
        		}
        		right--;
        	}
        }
		
        return res;
    }
}
```
### Time complexity: O(n^(k - 1))
#### Where n is length of nums
#### Where k is the count in each list
### Space complexity: O(n)
#### Where n is length of nums