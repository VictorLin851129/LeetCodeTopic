# 102. Binary Tree Level Order Traversal
## Solution 1: Recursive
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
    public List<List<Integer>> levelOrder(TreeNode root) {
        LinkedList<List<Integer>> retval = new LinkedList<List<Integer>>();
    	GetLevelList(root, retval, 0);
    	return retval; 
    }

	private static void GetLevelList(TreeNode root, LinkedList<List<Integer>> retval, int level) {
		if(root == null) {
			return;
		}
		
		if(retval.size() <= level) {
			List<Integer> subAns = new LinkedList<Integer>();
			subAns.add(root.val);
			retval.add(subAns);
		}else {
			List<Integer> temp = retval.get(level);
			temp.add(root.val);
		}
		
		GetLevelList(root.left, retval, level + 1);
		GetLevelList(root.right, retval, level + 1);
	}
}
```
### Time complexity: O(n)
#### Where n is node of tree
### Space complexity: O(n)
#### Where n is node of tree
---
## Solution 2 Iterative
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
    public List<List<Integer>> levelOrder(TreeNode root) {
        Queue<TreeNode> treeStack = new LinkedList<TreeNode>();
    	LinkedList<List<Integer>> retval = new LinkedList<List<Integer>>();
    	
    	treeStack.add(root);
    	while(root != null && !treeStack.isEmpty()) {
    		List<Integer> subAns = new LinkedList<Integer>();
    		int size = treeStack.size();
    		for(int i = 0; i < size; i++) {
    			root = treeStack.poll();
    			subAns.add(root.val);
    			if(root.left != null) {
    				treeStack.add(root.left);
    			}
    			if(root.right != null) {
    				treeStack.add(root.right);
    			}
    		}
    		retval.add(subAns);
    	}
    	
		return retval;
    }
}
```
### Time complexity: O(n)
#### Where n is node of tree
### Space complexity: O(n)
#### Where n is node of tree