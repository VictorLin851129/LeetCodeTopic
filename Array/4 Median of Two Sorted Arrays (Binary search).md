# 4. Median of Two Sorted Arrays (Binary search)
## Solution
```
class Solution {
    public double findMedianSortedArrays(int[] num1, int[] num2) {
        int totalCount = num1.length + num2.length;
        return (FindMid(num1, 0, num2, 0, (totalCount + 1) / 2) + FindMid(num1, 0, num2, 0, (totalCount + 2) / 2)) * 0.5;
    }
    
    private static int FindMid(int[] num1, int num1Index, int[] num2, int num2Index, int goalIndex) {
		if(num1Index >= num1.length) {
			return num2[num2Index + goalIndex - 1];
		}else if(num2Index >= num2.length) {
			return num1[num1Index + goalIndex - 1];
		}else if(goalIndex == 1) {
			return Math.min(num1[num1Index], num2[num2Index]);
		}
		
		int num1val = (num1Index + goalIndex / 2 - 1) < num1.length ? num1[num1Index + goalIndex / 2 - 1] : Integer.MAX_VALUE;
		int num2val = (num2Index + goalIndex / 2 - 1) < num2.length ? num2[num2Index + goalIndex / 2 - 1] : Integer.MAX_VALUE;
		if(num1val < num2val) {
			return FindMid(num1, num1Index + goalIndex / 2, num2, num2Index, goalIndex - goalIndex / 2);
		}else {
			return FindMid(num1, num1Index, num2, num2Index + goalIndex / 2, goalIndex - goalIndex / 2);
		}
	}
}
```
### Time complexity: O(log(n + m))
#### Where n is length of num1
#### Where m is length of num2
### Space complexity: O(1)