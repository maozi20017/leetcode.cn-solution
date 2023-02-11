[題目敘述](https://leetcode.cn/problems/palindrome-linked-list/)

```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func isPalindrome(head *ListNode) bool {
    dummy:=&ListNode{Next:head}     //快慢指針
    slow,fast:=dummy,dummy
    for fast!=nil&&fast.Next!= nil{
        slow=slow.Next
        fast=fast.Next.Next
    }

    p,q:=head,reverseList(slow.Next)    //反轉後半部
    for q!=nil{
        if p.Val!=q.Val{
            return false
        }
        p=p.Next
        q=q.Next
    }
    return true
}

//206. 反轉鏈表修改的
func reverseList(head *ListNode) *ListNode {
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
