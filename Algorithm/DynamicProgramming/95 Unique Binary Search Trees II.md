# 95. Unique Binary Search Trees II
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
    public static TreeNode copy(TreeNode tree) {
		if(tree == null) {
			return null;
		}
		TreeNode newNode = new TreeNode(tree.val);
		newNode.left = copy(tree.left);
		newNode.right = copy(tree.right);
		return newNode;
	}
    
    public List<TreeNode> generateTrees(int n) {
        ArrayList<ArrayList<TreeNode>> dp = new ArrayList<ArrayList<TreeNode>>();
    	
    	TreeNode firstNode = new TreeNode(1);
    	ArrayList<TreeNode>firstList = new ArrayList<TreeNode>();
    	firstList.add(firstNode);
    	dp.add(firstList);
    	for(int i = 1; i < n; i++) {
    		CreateTree(i, new ArrayList<TreeNode>(), dp);
    	}
    	
        return dp.get(n - 1);
    }
    
    private static void CreateTree(int index, ArrayList<TreeNode> newTreeList, ArrayList<ArrayList<TreeNode>> dp) {
		for(TreeNode tree : dp.get(index - 1)) {
			//Index is Head
			newTreeList.add(new TreeNode(index + 1, copy(tree), null));
			//Index at right subTree
			TreeNode pointer = tree;
			while(pointer.right != null) {
				TreeNode newTree = new TreeNode(index + 1, pointer.right, null);
				pointer.right = newTree;
				newTreeList.add(copy(tree));
				//recover
				pointer.right = pointer.right.left;
				pointer = pointer.right;
			}
			TreeNode newTree = new TreeNode(index + 1, pointer.right, null);
			pointer.right = newTree;
			newTreeList.add(copy(tree));
		}
		
		dp.add(newTreeList);
	}
}
```
