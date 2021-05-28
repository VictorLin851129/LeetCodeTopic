# 98. Validate Binary Search Tree
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
    TreeNode pre = null;
	boolean result = true;
    public boolean isValidBST(TreeNode root) {
        InorderCheck(root);
    	return result;
    }

	private void InorderCheck(TreeNode root) {
        if(root == null){
            return;
        }
		InorderCheck(root.left);
		
		if(pre != null && pre.val >= root.val) {
			result = false;
		}
		
		pre = root;
		InorderCheck(root.right);
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
    public boolean isValidBST(TreeNode root) {
        Stack<TreeNode> treeStack = new Stack<TreeNode>();
    	
    	TreeNode pre = null;
    	while(root != null || !treeStack.isEmpty()) {
    		while(root != null) {
    			treeStack.push(root);
    			root = root.left;
    		}
    		root = treeStack.pop();
    		
    		if(pre != null && root.val <= pre.val) {
    			return false;
    		}
    		
    		pre = root;
    		root = root.right;
    	}
    	
		return true;
    }
}
```
### Time complexity: O(n)
#### Where n is node of tree
### Space complexity: O(n)
#### Where n is node of tree