[題目敘述](https://leetcode.cn/problems/add-two-numbers/)

```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func addTwoNumbers(l1 *ListNode, l2 *ListNode) *ListNode {
    dummyHead := &ListNode{0, nil}
    current := dummyHead
    carry := 0

    for l1 != nil || l2 != nil {        //兩個鏈表中有一個還有內容就繼續
        x := 0
        y := 0
        if l1 != nil {
            x = l1.Val
            l1 = l1.Next
        }
        if l2 != nil {
            y = l2.Val
            l2 = l2.Next
        }
        sum := x + y + carry
        carry = sum / 10
        current.Next = &ListNode{sum % 10, nil}
        current = current.Next
    }

    if carry > 0 {      //計算完後多出來的位數
        current.Next = &ListNode{carry, nil}
    }

    return dummyHead.Next
}
