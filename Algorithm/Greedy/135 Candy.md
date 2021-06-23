# 135. Candy
## Solution
```
class Solution {
    public int candy(int[] ratings) {
        int retval = 0;
		
		int[] leftToRight = new int[ratings.length];
		leftToRight[0] = 1;
		for(int i = 1; i < leftToRight.length; i++) {
			if(ratings[i] > ratings[i - 1]) {
				leftToRight[i] = 1 + leftToRight[i - 1];
			}else {
				leftToRight[i] = 1;
			}
		}
		
		int[] rightToLeft = new int[ratings.length];
		rightToLeft[ratings.length - 1] = 1;
		for(int i = ratings.length - 2; i >= 0;  i--) {
			if(ratings[i] > ratings[i + 1]) {
				rightToLeft[i] = 1 + rightToLeft[i + 1];
			}else {
				rightToLeft[i] = 1;
			}
		}
		
		for(int i = 0; i < leftToRight.length; i++) {
			retval += Math.max(leftToRight[i], rightToLeft[i]);
		}
		
		return retval;
    }
}
```
### Time complexity: O(n)
#### Where n is length of ratings
### Space complexity: O(n)
#### Where n is length of ratings