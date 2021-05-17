# 61. Rotate List
## Solution
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
    public ListNode rotateRight(ListNode head, int k) {
        if(head == null || head.next == null || k == 0) {
    		return head;
    	}
    	ListNode First = head;
    	int count = 1;
    	
    	while(head.next != null) {
    		head = head.next;
    		count++;
    	}
    	head.next = First;
    	int priorLen = ((count - k)  > 0 ? count - k : count - (k % count));
    	while(priorLen > 0) {
    		head = head.next;
    		priorLen--;
    	}
    	First = head.next;
    	head.next = null;
    	
		return First;
    }
}
```
### Time complexity: O(n)
#### Where n is length of listNode
### Space complexity: O(1)