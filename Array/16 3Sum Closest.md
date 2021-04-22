# 16. 3Sum Closest
```
class Solution {
    public static int threeSumClosest(int[] nums, int target) {
        int retval = nums[0] + nums[1] + nums[2];
		if(nums.length == 3) {
			return retval;
		}
		Arrays.parallelSort(nums);
        
		int closest = Math.abs(target - retval);
		for(int i = 0; i < nums.length - 2; i++) {
			if(i == 0 || nums[i] != nums[i - 1]) {
				int left = i + 1, right = nums.length - 1;
				while(left < right) {
					int temp = nums[i] + nums[left] + nums[right];
					if(temp == target) {
						return temp;
					}
					int dist = Math.abs(target - temp);
					if(closest > dist) {
						closest = dist;
						retval = temp;
					}
					if(target > temp) {
						left++;
					}else { 
						right--;
					}
				}
			}
		}
		
        return retval;
    }
}
```
### Time complexity: O(n * n)
#### Where n is length of nums
### Space complexity: O(1)