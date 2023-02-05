[題目敘述](https://leetcode.cn/problems/linked-list-cycle/)

```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func hasCycle(head *ListNode) bool {
    fast,slow:=head,head        //快慢指針
    for (fast!=nil&&fast.Next!=nil){
        fast=fast.Next.Next
        slow=slow.Next
        if fast==slow{      
            return true
        }
    }
    return false
    /*
    cur:=head   //建表
    mp:=make(map[*ListNode]bool)
    for cur!=nil&&cur.Next!=nil{
        cur = cur.Next
        if mp[cur] {
            return true
        }
        mp[cur] = true
    }
    return false
    */
}
