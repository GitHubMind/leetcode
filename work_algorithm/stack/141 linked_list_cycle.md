141. Linked List Cycle


#There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the next pointer. Internally, pos is used to denote the index of the node that tail's next pointer is connected to. Note that pos is not passed as a parameter.

# test case
# Example 1:case

list:：[3,2,0,-4]
```golang

head := &ListNode{Val: 3}
head.Next = &ListNode{Val: 2}
head.Next.Next = &ListNode{Val: 0}
head.Next.Next.Next = &ListNode{Val: -4, Next: head.Next}
```