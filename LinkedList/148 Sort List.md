# 148. Sort List(Merge sort)
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
    public ListNode sortList(ListNode head) {
        return DivideAndConquer(head);
    }
    private static ListNode Merge(ListNode front, ListNode rear) {
		ListNode start = new ListNode(0);
		ListNode retval = start;
		while(front != null || rear != null) {
			int frontVal = front == null ? Integer.MAX_VALUE : front.val;
			int rearVal = rear == null ? Integer.MAX_VALUE : rear.val;
			
			if(frontVal < rearVal) {
				start.next = new ListNode(frontVal);
				front = front.next;
			}else {
				start.next = new ListNode(rearVal);
				rear = rear.next;
			}
			start = start.next;
		}
		return retval.next;
	}

	private static ListNode FindMiddle(ListNode head) {
		ListNode front = head;
		ListNode rear = head;
		
		while(rear.next != null && rear.next.next != null) {
			front = front.next;
			rear = rear.next.next;
		}
		
		rear = front.next;
		front.next = null;
		return rear;
	}

	private static ListNode DivideAndConquer(ListNode head) {
		if (head == null || head.next == null)
            return head;
		ListNode mid = FindMiddle(head);
    	ListNode front = DivideAndConquer(head);
    	ListNode rear = DivideAndConquer(mid);
		return  Merge(front, rear);
	}
}
```
### Time complexity: O(n * log(n))
#### Where n is length of listNode
### Space complexity: O(n)