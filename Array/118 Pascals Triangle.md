# 118. Pascal's Triangle
```
class Solution {
    public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> ans = new LinkedList<List<Integer>>();
        
        for(int i = 1; i <= numRows; i++) {
        	List<Integer> ansChild = new ArrayList<Integer>();
        	if(i == 1) {
        		ansChild.add(1);
        		ans.add(ansChild);
        		continue;
        	}
        	ansChild = ans.get(ans.size() - 1);
        	List<Integer> temp = new ArrayList<Integer>();
        	temp.add(1);
        	for(int j = 1; j < ansChild.size(); j++) {
        		temp.add(ansChild.get(j) + ansChild.get(j - 1));
        	}
        	temp.add(1);
        	ans.add(temp);
        }
        
        return ans;
    }
}
```
### Time complexity: O(n ^ 2)
#### Where n is length of numRows
### Space complexity: O(n ^ 2)
#### Where n is length of numRows