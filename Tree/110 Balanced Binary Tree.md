# 110. Balanced Binary Tree
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
    public boolean isBalanced(TreeNode root) {
        boolean[] retval = {true};
    	checkDepth(retval, root);
    	
    	return retval[0];
    }
    
    private static int checkDepth(boolean[] retval, TreeNode root) {
		if(root == null) {
			return 0;
		}
    	
		int leftMax  = 1 + checkDepth(retval, root.left);
    	int rightMax = 1 + checkDepth(retval, root.right);
    	
    	if(Math.abs(leftMax - rightMax) > 1) {
    		retval[0] = false;
    	}
    	
		return Math.max(leftMax, rightMax);
	}
}
```
### Time complexity: O(n)
#### Where n is node of tree
### Space complexity: O(n)
#### Where n is node of tree