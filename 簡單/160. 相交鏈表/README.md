[題目敘述](https://leetcode.cn/problems/intersection-of-two-linked-lists/)

```go
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func getIntersectionNode(headA, headB *ListNode) *ListNode {
    if headA == nil || headB == nil {
        return nil
    }
    a,b:=headA,headB        //鏈表A:a+c,鏈表B:b+c a+c+b+c = b+c+a+c 
    for a!=b{
        if a==nil{
            a=headB
        }else{
            a=a.Next
        }
        if b==nil{
            b=headA
        }else{
            b=b.Next
        }
    }
    return a        //就算不相交也會退出,如果長度相同,a跟b同時到達尾節點同時變null->兩者相同->退出迴圈
}                   //如果長度不同,a跟b都會遍歷完兩個鏈表(m+n),同時到達尾節點同時變null->兩者相同->退出迴圈
