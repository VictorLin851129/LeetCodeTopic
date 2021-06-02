# 113. Path Sum II
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
    public List<TreeNode> generateTrees(int n) {
       return GenerateSubTree(1, n);
	}

	private static List<TreeNode> GenerateSubTree(int start, int end) {
		LinkedList<TreeNode> ret = new LinkedList<TreeNode>();
		if(start > end) {
			ret.add(null);
			return ret;
		}
		
		if(start == end) {
			ret.add(new TreeNode(start));
			return ret;
		}
		
		List<TreeNode> LeftSubList = new LinkedList<TreeNode>();
		List<TreeNode> RightSubList = new LinkedList<TreeNode>();
		
		for(int i = start; i <= end; i++) {
			LeftSubList = GenerateSubTree(start, i - 1);
			RightSubList = GenerateSubTree(i + 1, end);
			
			for(TreeNode Lroot : LeftSubList) {
				for(TreeNode Rroot : RightSubList) {
					TreeNode cur = new TreeNode(i);
					cur.left = Lroot;
					cur.right = Rroot;
					ret.add(cur);
				}
			}
		}
		
		return ret;
	}
}
```
### Time complexity: O(n)
#### Where n is node of tree
### Space complexity: O(n)
#### Where n is node of tree