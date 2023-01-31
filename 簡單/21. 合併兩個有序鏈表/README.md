[題目敘述](https://leetcode.cn/problems/merge-two-sorted-lists/)

```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func mergeTwoLists(list1 *ListNode, list2 *ListNode) *ListNode {
    ans := &ListNode{}
    head:= ans
    for list1!=nil&&list2!=nil{     //判斷
        if list1.Val<list2.Val{
            ans.Next = list1
            list1=list1.Next
        }else{
            ans.Next = list2
            list2=list2.Next
        }
        ans = ans.Next
    }
    //其中一個鏈表結束後會出來for迴圈
    if list1!=nil{      //把剩下的捕到ans後面
        ans.Next=list1
    }else if list2!=nil{
        ans.Next=list2
    }
    return head.Next
}
