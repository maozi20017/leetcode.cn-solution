[題目敘述](https://leetcode.cn/problems/odd-even-linked-list/)

```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func oddEvenList(head *ListNode) *ListNode {
    if head == nil || head.Next == nil {        //內容只有0或1個
        return head
    }
    odd := head     //奇數節點
    even := head.Next   //偶數節點
    evenHead := even    //偶數頭 連接用
    for even != nil && even.Next != nil {
        odd.Next = even.Next
        odd = odd.Next
        
        even.Next = odd.Next
        even = even.Next
    }
    odd.Next = evenHead //連接
    return head
}
