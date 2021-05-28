# 107. Binary Tree Level Order Traversal II
## Solution
```
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public List<List<Integer>> levelOrderBottom(TreeNode root) {
        HashMap<Integer, ArrayList<Integer>> HighMap = new HashMap<Integer, ArrayList<Integer>>();
    	
    	InOrder(HighMap, root, 0);
    	List<List<Integer>> retval = new ArrayList<List<Integer>>();
    	
    	for(int i = HighMap.size() - 1; i >= 0; i--) {
    		retval.add(HighMap.get(i));
    	}
    	
		return retval;
    }

	private static void InOrder(HashMap<Integer, ArrayList<Integer>> highMap, TreeNode root, int high) {
		if(root == null) {
			return;
		}
		
		InOrder(highMap, root.left, high + 1);
		
		if(!highMap.containsKey(high)) {
			ArrayList<Integer> cur = new ArrayList<Integer>();
			cur.add(root.val);
			highMap.put(high, cur);
		}else {
			ArrayList<Integer> cur = highMap.get(high);
			cur.add(root.val);
		}
		
		InOrder(highMap, root.right, high + 1);
	}
}
```
### Time complexity: O(n)
#### Where n is node of tree
### Space complexity: O(n)
#### Where n is node of tree