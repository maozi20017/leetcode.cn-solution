[題目敘述](https://leetcode.cn/problems/remove-linked-list-elements/)

```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func removeElements(head *ListNode, val int) *ListNode {
    if head == nil {
        return nil
    }
    dummy := &ListNode{Next: head}
    cur := dummy
    for cur.Next != nil {       //cur的下個節點不為null
        if cur.Next.Val == val {        //如果cur的下個節點存在跟val相同的值
            cur.Next = cur.Next.Next
        } else {
            cur = cur.Next
        }
    }
    return dummy.Next
    /*遞迴寫法
    if head == nil {
        return nil
    }
    head.Next = removeElements(head.Next, val)
    if head.Val == val {
        return head.Next
    }
    return head
    */
}
