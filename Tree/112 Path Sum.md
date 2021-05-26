# 112. Path Sum
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
    public boolean hasPathSum(TreeNode root, int targetSum) {
       if(root == null) {
    		return false;
    	}else if(root.val == targetSum && root.left == null && root.right == null) {
    		return true;
    	}
    	
		return hasPathSum(root.left, targetSum - root.val) || hasPathSum(root.right, targetSum - root.val);
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
    public boolean hasPathSum(TreeNode root, int targetSum) {
        Stack<TreeNode> TreeStack = new Stack<TreeNode>();
    	TreeStack.push(root);
    	
    	while(root != null && !TreeStack.isEmpty()) {
    		root = TreeStack.pop();
    		if(root.left == null && root.right == null && root.val == targetSum) {
    			return true;
    		}
			if(root.left != null) {
				root.left.val += root.val;
				TreeStack.push(root.left);
			}
			if(root.right != null) {
				root.right.val += root.val;
				TreeStack.push(root.right);
			}
    	}
    	
    	return false;
    }
}
```
### Time complexity: O(n)
#### Where n is node of tree
### Space complexity: O(n)
#### Where n is node of tree