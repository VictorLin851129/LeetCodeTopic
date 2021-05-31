# 103. Binary Tree Zigzag Level Order Traversal
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
    public List<List<Integer>> zigzagLevelOrder(TreeNode root) {
        Deque<TreeNode> treeStack = new LinkedList<TreeNode>();
    	LinkedList<List<Integer>> retval = new LinkedList<List<Integer>>();
    	boolean front = true;
    	
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
    		if(!front) {
    			Collections.reverse(subAns);
    		}
    		front = !front;
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