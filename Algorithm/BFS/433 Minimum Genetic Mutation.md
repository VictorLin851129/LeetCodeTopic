# 433. Minimum Genetic Mutation
## Solution
```
class Solution {
    public int minMutation(String start, String end, String[] bank) {
       
        char[] type = {'A', 'C', 'G', 'T'};
    	Set<String> setFront = new HashSet<String>();
    	Set<String> setRear = new HashSet<String>();
    	ArrayList<String> dict = new ArrayList<String>();
    	for(String s : bank) {
    		dict.add(s);
    	}
    	
        if(dict.size() == 0 || !dict.contains(end)) {
    		return -1;
    	}
        
    	int level = 1;
    	
    	setFront.add(start);
    	setRear.add(end);
    	
    	while(!setFront.isEmpty() && !setRear.isEmpty()){
    		if(setFront.size() > setRear.size()) {
    			Set<String> temp  = setRear;
    			setRear = setFront;
    			setFront = temp;
    		}
    		level++;
    		Set<String> newSet = new HashSet<String>();
    		for(String s : setFront) {
    			char[] Sc = s.toCharArray();
    			for(int i = 0; i < Sc.length; i++) {
    				char origin = Sc[i];
    				for(char t : type) {
    					Sc[i] = t;
    					String newString = new String(Sc);
    					if(setRear.contains(newString)) {
    						return level - 1;
    					}
    					if(t != origin && dict.contains(newString)) {
    						newSet.add(newString);
    						dict.remove(newString);
    					}
    				}
    				Sc[i] = origin;
    			}
    		}
    		setFront = newSet;
    	}
    	
		return -1;
    }
}

```
### Time complexity: worst case O(n^2)
#### Where n is length of bank
### Space complexity: worst case O(k)
#### Where k is length of bank