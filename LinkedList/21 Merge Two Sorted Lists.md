# 21. Merge Two Sorted Lists
```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        ListNode start = new ListNode();
    	ListNode retval = start;
    	
    	while(l1 != null || l2 != null) {
    		int l1val = l1 == null ? Integer.MAX_VALUE : l1.val;
    		int l2val = l2 == null ? Integer.MAX_VALUE : l2.val;
    		
    		if(l1val < l2val) {
				ListNode newNode = new ListNode(l1val);
				start.next = newNode;
    			l1 = l1 == null ? null : l1.next;
    		}else {
    			ListNode newNode = new ListNode(l2val);
    			start.next = newNode;
    			l2 = l2 == null ? null : l2.next;
    		}
    		start = start.next;
    	}
    	
        return retval.next;
    }
}
```
### Time complexity: O(n)
#### Where n is length of Max(l1, l2)
### Space complexity: O(n)
#### Where n is length of Max(l1, l2)