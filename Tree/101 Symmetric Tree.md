# 101. Symmetric Tree
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
    public boolean isSymmetric(TreeNode root) {
        return checkSymmetric(root, root);
    }
    private static boolean checkSymmetric(TreeNode left, TreeNode right) {
    	if(left == null && right == null) {
    		return true;
    	}else if(left == null || right == null) {
    		return false;
    	}else if(left.val != right.val){
    		return false;
    	}
    	
    	return checkSymmetric(left.left, right.right) && checkSymmetric(left.right, right.left);
    }
}
```
### Time complexity: O(n)
#### Where n is node of tree
### Space complexity: O(n)
#### Where n is node of tree