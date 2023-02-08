[題目敘述](https://leetcode.cn/problems/remove-nth-node-from-end-of-list/)

```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func removeNthFromEnd(head *ListNode, n int) *ListNode {
    dummy := &ListNode{Next: head}
    slow,fast:=dummy,head       //快慢指針
    for i:=0;i<n;i++{
        fast=fast.Next
    }
    for fast!=nil{
        slow=slow.Next
        fast=fast.Next
    }
    slow.Next=slow.Next.Next
    return dummy.Next
}
