# 89. Gray Code
## Solution
#### Formula : use Binary convert to Gray; keep first bit, then the following bit XOR with their next bit
```
class Solution {
    public List<Integer> grayCode(int n) {
        ArrayList<Integer> retval = new ArrayList<Integer>();
    	for(int i = 0; i < 1 << n; i++) {
    		retval.add(i ^ (i >> 1));
    	}
    	
        return retval;
    }
}
```
### Time complexity: O(1 << n)
#### Where n is given
### Space complexity: O((1 << n) - 1)