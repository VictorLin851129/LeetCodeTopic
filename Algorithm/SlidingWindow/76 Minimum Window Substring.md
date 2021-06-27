# 76. Minimum Window Substring
## Solution
```
class Solution {
    class Pair{
        char C;
        int index;

        Pair(){
        }

        Pair(char c, int i){
            this.C = c;
            this.index = i;
        }
    }
    
    public String minWindow(String s, String t) {
        ArrayList<Pair> matchInt = new ArrayList<Pair>();
    	for(int i = 0; i < s.length(); i++) {
    		if(t.contains(String.valueOf(s.charAt(i)))) {
    			matchInt.add(new Pair(s.charAt(i), i));
    		}
    	}
    	
    	int requireCount = 0;
    	HashMap<Character, Integer> requirement = new HashMap<Character, Integer>();	//c, count
    	for(char c : t.toCharArray()) {
    		requirement.put(c, requirement.getOrDefault(c, 0) + 1);
    		requireCount++;
    	}

    	int alreadyMatch = 0;
    	HashMap<Character, Integer> duplicate = new HashMap<Character, Integer>();	//c, count
    	int left = 0;
    	int[] result = {-1, 0, 0};	//length, start, end
    	
    	for(int i = 0; i < matchInt.size(); i++) {
    		if(requirement.get(matchInt.get(i).C) > 0) {
    			requirement.put(matchInt.get(i).C, requirement.get(matchInt.get(i).C) - 1);
    			alreadyMatch++;
    		}else {
    			duplicate.put(matchInt.get(i).C, duplicate.getOrDefault(matchInt.get(i).C, 0) + 1);
    		}
    		
    		if(alreadyMatch == requireCount) {
    			if(result[0] == -1 || matchInt.get(i).index - matchInt.get(left).index + 1 < result[0]) {
    				result[0] = matchInt.get(i).index - matchInt.get(left).index + 1;
    				result[1] = matchInt.get(left).index;
    				result[2] = matchInt.get(i).index;
    				
    			}
    			requirement.put(matchInt.get(left).C, requirement.get(matchInt.get(left).C) + 1);
    			alreadyMatch--;
    			left++;
    		}
    		
    		while(left < i && duplicate.getOrDefault(matchInt.get(left).C, 0) > 0) {
    			duplicate.put(matchInt.get(left).C, duplicate.get(matchInt.get(left).C) - 1);
    			left++;
    		}
    	}
    	return result[0] == -1 ? "" : s.substring(result[1], result[2] + 1);
    }
}
```
### Time complexity: O(n + m)
#### Where n is length of s
#### Where m is length of t
### Space complexity: O(n + m)
#### Where n is length of s
#### Where m is length of t