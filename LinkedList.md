# Linked List

## Core Functionality

Linked List is a linear data structure comprising of nodes, where each node has a value and a pointer `next` pointing to the next node. 
The end node of a linked list will point to `null`. 

Most linked list problems are concerned with singly linked list, where there's only `next`.
A doubly linked list also has the attribute `previous`, which is a pointer to the previous node. The first node in a doubly linked list has `prev` pointing to `null`.

Most linked list problems are also not circular. Circular linked lists have the last node pointing to the first node.
A linked list can also be not circular, but there exists a loop in the linked list.

In Python, a linked list is defined as:

![image](https://user-images.githubusercontent.com/54465320/200944878-b72bd023-2a2f-4d60-ab74-97315011fd42.png)

Most linked list questions have complexity `O(n)`

## Important Functions

- Linked lists can be traversed with recursion or while loop. While loop is usually easier and more intuitive, but some niche questions require recursion.

- Probably most important algo: reverse linked list. Have 3 pointers: `cur`, `nxt` initialized to `head`, while `prev` initialized to `null`.
  
  Traverse until `nxt` is `null`. Move `nxt` to the next node (save the next node), point `cur` at `prev` (connect the current node to the already built reversed list), 
  assign `prev` to `cur` (update the new head of the reversed list), assign `cur` to `nxt` (at the end, `cur` and `next` need to be at the same spot). 
  Return `prev` after traversal (new `head`). 
  
  Sample code:
  
  ![image](https://user-images.githubusercontent.com/54465320/200955239-a729b4c1-b7ca-44e1-a9e9-804d3ef0332a.png)
  
 - `Odd` and `even` length lists handling is very important. There's usually no hidden intention of a problem to use a linked list like a heap or stack or hashmap.

## Tricks

- One pass: In questions that require the knowledge of how long the linked list is, for example 19. Remove Nth Node From End of List, first intuition is 
traverse thru the linked list once to determine the position from the beginning, but it could take long if the linked list is very long. We can set a `fast` pointer
to the n-th position from the `head`, and a `slow` pointer at the head, then traverse them at the same speed. When the fast pointer reaches the end, the slow pointer will
be where we desire, as the distance between the pointers doesn't change.

- Another two pointer: We can also have a `fast` and `slow` pointer, with the fast one travelling twice as fast and both start at head. When the fast pointer reaches the
end, the slow pointer will be right in the middle.

- Both `two pointer` methods require careful consideration of the length of the linked list being `even` or `odd`, since `fast` can end up at the last node, or at `null`.
A neat way to handle this is to put the condition in the while loop:

  `while fast and fast.next:`

  `fast.next` will not be considered if `fast` is already at `null` avoiding `None Type doesn't have attribute next` (because `fast == None`).

  This will require handling `if fast == None:` after the while loop is done. 
  In the case of `fast` traveling twice as fast as `slow`, if the linked list has `odd` length, `slow` will be right at the middle, while `fast` will be at the last node.
  If the linked list has `even` length, the `slow` pointer will be at the middle right node, while `fast` will be at `null`.
