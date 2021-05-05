# 49. Group Anagrams
```
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        List<List<String>> retval = new LinkedList<List<String>>();
    	
    	HashMap<String, List<String>> map = new HashMap<String, List<String>>();
    	for(String s : strs) {
    		char[] c = s.toCharArray();
    		Arrays.parallelSort(c);
    		String sSort = String.valueOf(c);
    		if(map.containsKey(sSort)) {
    			List<String> list = map.get(sSort);
    			list.add(s);
    		}else {
    			List<String> listChild = new LinkedList<String>();
    			listChild.add(s);
    			map.put(sSort, listChild);
    		}
    	}
    	
    	retval.addAll(map.values());
    	
		return retval;
    }
}
```
### Time complexity: O(n * klok)
#### Where n is length of str
#### Where k is max length of s in string array
### Space complexity: O(n * k)
#### Where n is length of str
#### Where k is max length of s in string array