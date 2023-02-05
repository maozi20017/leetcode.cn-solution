[題目敘述](https://leetcode.cn/problems/linked-list-cycle-ii/)  
建議搭配[題解](https://leetcode.cn/problems/linked-list-cycle-ii/solution/linked-list-cycle-ii-kuai-man-zhi-zhen-shuang-zhi-/)服用

```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func detectCycle(head *ListNode) *ListNode {
    slow, fast := head, head
    for fast != nil && fast.Next != nil {
        slow = slow.Next
        fast = fast.Next.Next
        if slow == fast {       //相遇
            fast = head
            for slow != fast {
                slow = slow.Next
                fast = fast.Next
            }
            return slow
        }
    }
    return nil
    /*
    mp:=make(map[*ListNode]bool)    //建表
    cur:=head
    mp[cur]=true    //不寫這個最一開始的會還是false
    for cur!=nil&&cur.Next!=nil{
        cur = cur.Next
        if mp[cur] {
            return cur
        }
        mp[cur]=true
    }
    return nil
    */
}
