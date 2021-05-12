# 2. Add Two Numbers
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
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode start = new ListNode();
    	ListNode first = new ListNode();
    	start = first;
    	int carry = 0;
    	while(l1 != null || l2 != null || carry != 0) {
    		int l1val = l1 == null ? 0 : l1.val;
    		int l2val = l2 == null ? 0 : l2.val;
    		
			ListNode newNode = new ListNode();
			newNode.val = (l1val + l2val + carry) % 10;
			carry = (l1val + l2val + carry) / 10;
			first.next = newNode;
    		
    		l1 = l1 == null ? null : l1.next;
    		l2 = l2 == null ? null : l2.next;
    		first = first.next;
    	}
    	
		return start.next;  
    }
}
```
### Time complexity: O(n)
#### Where n is length of Max(l1, l2)
### Space complexity: O(n)
#### Where n is length of Max(l1, l2)