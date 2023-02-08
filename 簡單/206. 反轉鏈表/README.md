[題目敘述](https://leetcode.cn/problems/reverse-linked-list/)

```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func reverseList(head *ListNode) *ListNode {
    if head==nil{
        return nil
    }
    var prev, next *ListNode        //雙指針
    current := head     //當前
    for current != nil {        //簡單來講就是把箭頭顛倒
        next = current.Next     //next為current的下個節點
        current.Next = prev     //將current的下個節點指到prev
        //更新節點
        prev = current          //prev為current
        current = next          //current為next
    }
    return prev
}
