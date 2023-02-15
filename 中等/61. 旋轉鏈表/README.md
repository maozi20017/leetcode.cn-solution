[題目敘述](https://leetcode.cn/problems/rotate-list/)

```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func rotateRight(head *ListNode, k int) *ListNode {
    if head==nil||k==0{     //這題我認為不用註解
        return head
    }
    cnt:=1
    cur:=head
    for cur.Next!=nil{
        cur=cur.Next
        cnt++
    }
    cur.Next=head

    slow,fast:=head,head
    for i:=0;i<(k%cnt);i++{
        fast=fast.Next
    }

    for fast!=cur{
        slow, fast = slow.Next, fast.Next
    }

    newHead := slow.Next
    slow.Next = nil
    return newHead  
}
