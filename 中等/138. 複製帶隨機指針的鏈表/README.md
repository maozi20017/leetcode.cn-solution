[題目敘述](https://leetcode.cn/problems/copy-list-with-random-pointer/)

```go
/**
 * Definition for a Node.
 * type Node struct {
 *     Val int
 *     Next *Node
 *     Random *Node
 * }
 */
func copyRandomList(head *Node) *Node {
    // 複製
    cur := head
    for cur != nil {
        copyNode := &Node{Val: cur.Val, Next: cur.Next}
        cur.Next = copyNode
        cur = copyNode.Next
    }

    // 處理random指针
    cur = head
    for cur != nil {
        if cur.Random != nil {
            cur.Next.Random = cur.Random.Next
        }
        cur = cur.Next.Next
    }

    // 拆分链表
    var newHead, newCur *Node
    cur = head      //cur指向head
    if cur != nil {     //如果原始鏈表非空
        newHead = cur.Next     //新鏈表的頭節點newHead指向原始鏈表的第二個節點cur.Next
        newCur = newHead       //變量newCur指向新鏈表的頭節點
        cur.Next = newCur.Next  //原始鏈表的頭節點cur的Next指向新鏈表的頭節點newCur.Next
        cur = cur.Next          //cur指向原始鏈表的下一個待拆分的節點cur.Next
    }
    for cur != nil {
        newCur.Next = cur.Next  //新鏈表的節點newCur的Next指向原始鏈表中對應節點的下一個節點
        newCur = newCur.Next    //變量newCur指向新鏈表的下一個待連接節點
        cur.Next = newCur.Next  //原始鏈表的節點cur的Next指向新鏈表中對應節點的下一個節點
        cur = cur.Next      //變量cur指向原始鏈表的下一個待拆分的節點cur.Next
    }
    return newHead
}
