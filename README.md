# DAY_9
Swap Nodes in a Linked List (Java)
This project provides a Java solution to the LeetCode problem "1721. Swapping Nodes in a Linked List", where the goal is to swap the values of the k-th node from the beginning and the k-th node from the end in a singly linked list.

Problem Statement
Given the head of a singly linked list and an integer k, swap the values of the k-th node from the beginning and the k-th node from the end, and return the modified list.

Example:
Input: head = [1,2,3,4,5], k = 2
Output: [1,4,3,2,5]

Approach
The solution uses a two-pointer technique:

Traverse k-1 nodes from the beginning to find the k-th node from the start.

Use a second pointer (slow) to find the k-th node from the end by moving it while a fast pointer (initially k-th node) goes to the end of the list.

Swap the values of these two nodes.

This method ensures O(n) time complexity and O(1) space complexity.

Code Overview
java
Copy
Edit
public ListNode swapNodes(ListNode head, int k)
Parameters:

head: The head of the singly linked list.

k: The position (1-based index) to identify nodes to swap.

Returns: The modified linked list after swapping the values of the two nodes.

Key Concepts
Two-pointer technique: Used to find the k-th node from the end in a single pass.

In-place swapping: Only the values of the nodes are swapped, not the actual nodes.

Notes
The implementation prioritizes readability by using explicit variables (first and second) even though reusing pointers is possible.

The code assumes that k is always a valid index (i.e., 1 <= k <= length of list).



class Solution {
    public ListNode swapNodes(ListNode head, int k) {		
        ListNode fast = head;
        ListNode slow = head;
        ListNode first = head, second = head;
        
		// Put fast (k-1) nodes after slow
        for(int i = 0; i < k - 1; ++i)
            fast = fast.next;
            
		// Save the node for swapping
        first = fast;

		// Move until the end of the list
        while(fast.next != null) {
			slow = slow.next;
            fast = fast.next;
        }
        
        // Save the second node for swapping
		// Note that the pointer second isn't necessary: we could use slow for swapping as well
		// However, having second improves readability
        second = slow;
		
		// Swap values
        int temp = first.val;
        first.val = second.val;
        second.val = temp;
        
        return head;
    }
}
