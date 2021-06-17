# 134. Gas Station
## Solution
```
class Solution {
    public int canCompleteCircuit(int[] gas, int[] cost) {
        int total = 0;
    	for(int i = 0; i < gas.length; i++) {
    		total += gas[i] - cost[i];
    	}
    	if(total < 0) {
    		return -1;
    	}
    	
    	int start = 0, tank = 0;
		for(int i = 0; i < gas.length; i++) {
			tank += gas[i] - cost[i];
			if(tank < 0) {
				start = i + 1;
				tank = 0;
			}
		}
    	
		return start;
    }
}

```
### Time complexity: O(n)
#### Where n is length of gas
### Space complexity: O(1)