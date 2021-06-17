# 127. Word Ladder
## Solution
```
class Solution {
    public int ladderLength(String beginWord, String endWord, List<String> wordList) {
        if(!wordList.contains(endWord)) {
    		return 0;
    	}
    	Set<String> setFront = new HashSet<String>();
    	Set<String> setRear = new HashSet<String>();
    	Set<String> visited = new HashSet<String>();
    	
    	setFront.add(beginWord);
    	setRear.add(endWord);
    	int level = 1;
    	
    	while(!setFront.isEmpty() && !setRear.isEmpty()) {
    		if(setFront.size() > setRear.size()) {
    			Set<String> swap = new HashSet<String>();
    			swap = setRear;
    			setRear = setFront;
    			setFront = swap;
    		}
    		level++;
    		Set<String> newSet = new HashSet<String>();
    		for(String oldString : setFront) {
    			char[] toChar = oldString.toCharArray();
    			for(int j = 0; j < toChar.length; j++) {
    				char origin = toChar[j];
    				for(char c = 'a'; c <= 'z'; c++) {
						toChar[j] = c;
						String newString = new String(toChar);
						if(setRear.contains(newString)) {
							return level;
						}
						if(wordList.contains(newString) && !visited.contains(newString)) {
							newSet.add(newString);
							visited.add(newString);
						}
    				}
    				toChar[j] = origin;
    			}
    		}
    		setFront = newSet;
    	}
    	
		return 0;
    }
}
```
### Time complexity: O(n ^ 2)
#### Where n is length of wordList
### Space complexity: O(n)
#### Where n is length of wordList