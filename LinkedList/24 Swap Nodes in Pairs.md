# 24. Swap Nodes in Pairs
## Solution 1: Iterative
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
    public ListNode swapPairs(ListNode head) {
        ListNode header = new ListNode(0);
    	header.next = head;
    	head = header;
    	
    	while(head.next != null && head.next.next != null) {
    		ListNode front = head.next;
    		head.next = front.next;
    		front.next = front.next.next;
    		head.next.next = front;
    		head = front;
    	}
    	
        return header.next;
    }
}
```
### Time complexity: O(n)
#### Where n is length of listNode
### Space complexity: O(n)
#### Where n is length of listNode
---
## Solution2: Recursive
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
    public ListNode swapPairs(ListNode head) {
        if(head == null || head.next == null) {
    		return head;
    	}
    	
    	ListNode retval = head.next;
    	head.next = swapPairs(head.next.next);
    	retval.next = head;

    	return retval;
    }
}
```
### Time complexity: O(n)
#### Where n is length of listNode
### Space complexity: O(n)
#### Where n is length of listNode