# 1004. Max Consecutive Ones III
## Solution
```
class Solution {
    public int longestOnes(int[] nums, int k) {
        int max_length = 0;
        for(int left = 0, right = 0, zero = 0; right < nums.length; right++){
            if(nums[right] == 0){
                zero++;
            }
            if(zero > k){
                while(nums[left] != 0){
                    left++;
                }
                left++;
                zero--;
            }
            if(right - left + 1 > max_length){
                max_length = right - left + 1;
            }
        }
        
        return max_length;
    }
}
```
### Time complexity: O(n)
#### Where n is length of nums
### Space complexity: O(1)