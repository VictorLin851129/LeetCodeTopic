# 30. Substring with Concatenation of All Words
## Solution 1: Sliding Window
```
class Solution {
    public List<Integer> findSubstring(String s, String[] words) {
        ArrayList<Integer> retval = new ArrayList<Integer>();
    	
    	HashMap<String, Integer> GoalMap = new HashMap<String, Integer>();
    	for(String str : words) {
    		GoalMap.put(str, GoalMap.getOrDefault(str, 0) + 1);
    	}
    	
    	int wordLen = words[0].length();
    	int totalWord = words.length;
    	int StrLen = s.length();
    	int WindowSize = totalWord * wordLen;
    	
    	for(int i = 0; i < wordLen; i++) {
    		HashMap<String, Integer> windowMap = new HashMap<String, Integer>();
    		int exceed = 0;
    		for(int j = i, start = i; j + wordLen <= StrLen && start + WindowSize <= StrLen; j += wordLen) {
    			String newWord = s.substring(j, j + wordLen);
    			
    			if(!GoalMap.containsKey(newWord)) {
    				windowMap.clear();
    				start = j + wordLen;
    				exceed = 0;
    			}else {
    				if(j + wordLen - start > WindowSize) {
    					String preWord = s.substring(start, start + wordLen);
    					int count = windowMap.get(preWord);
    					if(count > GoalMap.get(preWord)) {
    						windowMap.put(preWord, count - 1);
    						exceed--;
    					}else if(count == 1) {
    						windowMap.remove(preWord);
    					}else {
    						windowMap.put(preWord, count - 1);
    					}
    					start += wordLen;
    				}
    				
    				windowMap.put(newWord, windowMap.getOrDefault(newWord, 0) + 1);
    				if(windowMap.get(newWord) > GoalMap.get(newWord)) {
    					exceed++;
    				}
    				
    				if(exceed == 0 && start + WindowSize == j + wordLen) {
    					retval.add(start);
    				}
    			}
    		}
    	}
    	
		return retval;
    }
    
}
```
### Time complexity: O(n * wl)
#### Where n is length of s
#### Where wl is word length
### Space complexity: O(n * wl)
#### Where n is length of words array
#### Where wl is word length
---
## Solution 2
```
class Solution {
    public List<Integer> findSubstring(String s, String[] words) {
        ArrayList<Integer> retval = new ArrayList<Integer>();
    	int totalWord = words.length;
    	int vocCount = words[0].length();
    	
    	HashMap<String, Integer> map = new HashMap<String, Integer>();
    	
    	for(String sa : words) {
    		map.put(sa, map.getOrDefault(sa, 0) + 1);
    	}
    	System.out.println(map);
    	for(int i = 0; i < s.length() - totalWord * vocCount + 1; i++) {
    		String temp = s.substring(i, i + totalWord * vocCount);
    		if(CheckMatch(temp, map, totalWord, vocCount)) {
    			retval.add(i);
    		}
    	}
    	
		return retval;
    }
    private static boolean CheckMatch(String temp, HashMap<String, Integer> map, int totalWord, int VocCount) {
		HashMap<String, Integer> check = new HashMap<String, Integer>();
		for(int i = 0; i < temp.length(); i += VocCount) {
			check.put(temp.substring(i, i + VocCount), check.getOrDefault(temp.substring(i, i + VocCount), 0) + 1);
		}
		return check.equals(map);
	}
}
```
### Time complexity: O(n * wl)
#### Where n is length of s
#### Where wl is word length
### Space complexity: O(n * wl)
#### Where n is length of words array
#### Where wl is word length