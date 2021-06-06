# 128. Longest Consecutive Sequence
## Solution
```
class Solution {
    class unionFindImpl {
        int[] nodes;
        int[] level;

        unionFindImpl(int n){
            nodes = new int[n];
            level = new int[n];
            for(int i = 0; i < n; i++) {
                nodes[i] = i;
                level[i] = 1;
            }
        }

        void union(int first, int second){
            int firstParent = find(first);
            int secondParent = find(second);

            if(firstParent != secondParent) {
                if(level[firstParent] < level[secondParent]) {
                    nodes[firstParent] = secondParent;
                }else if(level[firstParent] > level[secondParent]) {
                    nodes[secondParent] = firstParent;
                }else {
                    nodes[firstParent] = secondParent;
                    level[secondParent]++;
                }
            }
	    }
	
        int find(int kids) {
            ArrayList<Integer> changeParents = new ArrayList<Integer>();

            while(kids != nodes[kids]) {
                changeParents.add(kids);
                kids = nodes[kids];
            }

            for(int i : changeParents) {
                nodes[i] = kids;
            }

            return kids;
        }
    }
    
    public int longestConsecutive(int[] nums) {
        unionFindImpl uf = new unionFindImpl(nums.length);
    	
    	HashMap<Integer, Integer> numsMap = new HashMap<Integer, Integer>(); 
    	
    	//Union Find
    	for(int i = 0; i < nums.length; i++) {
    		if(!numsMap.containsKey(nums[i])) { // already process then skip
	    		if(numsMap.containsKey(nums[i] - 1)) { //consecutive with front 
	    			uf.union(i, numsMap.get(nums[i] - 1));
	    		}
	    		if(numsMap.containsKey(nums[i] + 1)) { //consecutive with rear 
	    			uf.union(i, numsMap.get(nums[i] + 1));
	    		}
	    		numsMap.put(nums[i], i);
    		}
    	}
    	
    	//Get Longest consecutive
    	int[] count = new int[nums.length];
    	int retval = 0;
    	
    	for(int i = 0; i < nums.length; i++) {
    		count[uf.find(i)]++;
    		if(count[uf.find(i)] > retval) {
    			retval = count[uf.find(i)];
    		}
    	}
    	
        return retval;
    }
}
```
### Time complexity: O(n)
#### Where n is length of nums
### Space complexity: O(n)
#### Where n is length of nums