[題目敘述](https://leetcode.cn/problems/middle-of-the-linked-list/)

```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func middleNode(head *ListNode) *ListNode {
    fast, slow := head, head    //快慢指針 快的2格 慢的1格
    for fast != nil && fast.Next != nil {   //當前的跟後面一個不為null
        fast = fast.Next.Next
        slow = slow.Next
    }
    return slow
}
