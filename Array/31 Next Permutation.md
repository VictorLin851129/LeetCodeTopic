# 31. Next Permutation
```
class Solution {
    public void nextPermutation(int[] nums) {
        int front = 0;
		for(front = nums.length - 1; front > 0; front--) {
		   if(nums[front] > nums[front - 1]) {
			   break;
		   }
        }
        
		if(front > 0) {
			front--;
			int rear = 0;
			for(rear = nums.length - 1; rear > 0; rear--) {
				if(nums[rear] > nums[front]) {
					break;				
				}
			}
			swap(nums, front, rear);
			front++;
		}

		reverse(nums, front);
    }
	
	public static void swap(int[] nums, int front, int rear) {
		int temp = nums[front];
		nums[front] = nums[rear];
		nums[rear] = temp;
	}
	
	public static void reverse(int[] nums, int front) {
		int rear = nums.length - 1;
		
		while(front < rear) {
			swap(nums, front++, rear--);
		}
	}
}
```
### Time complexity: O(n)
#### Where n is length of nums
### Space complexity: O(1)