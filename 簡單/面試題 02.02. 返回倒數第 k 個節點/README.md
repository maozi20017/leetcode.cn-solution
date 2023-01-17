[題目敘述](https://leetcode.cn/problems/kth-node-from-end-of-list-lcci/)

```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func kthToLast(head *ListNode, k int) int {
    var fast,slow=head,head       //快慢指針問題
    for;k>0;k--{        //讓快的指針先走使慢的在第0個快的在第k-1個
        fast=fast.Next
    }
    for fast!=nil{      //同時走最後快的會比給的表多出一個
        fast=fast.Next
        slow=slow.Next
    }
    return slow.Val
}
