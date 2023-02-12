[題目敘述](https://leetcode.cn/problems/flatten-a-multilevel-doubly-linked-list/)

```go
/**
 * Definition for a Node.
 * type Node struct {
 *     Val int
 *     Prev *Node
 *     Next *Node
 *     Child *Node
 * }
 */

func flatten(root *Node) *Node {
    if root == nil {
        return nil
    }

    dummy := &Node{Next: root}
    stack := []*Node{root}

    var prev *Node
    for len(stack) > 0 {
        curr := stack[len(stack)-1]     //取出列表的最後面的節點 因為堆疊
        stack = stack[:len(stack)-1]    //刪除取出的節點

         //如果取出的節點有 prev 節點，則將 prev 節點的 Next 指向取出的節點，並將取出的節點的 Prev 指向 prev 節點。           
        if prev != nil {        
            prev.Next = curr
            curr.Prev = prev
        }

        //檢查 curr 節點是否有 Next 節點。如果有，則將 Next 節點添加到 stack 中，並將 curr 指向 Next 節點。
        if curr.Next != nil {
            stack = append(stack, curr.Next)
        }

        //檢查 curr 節點是否有 Child 節點。如果有，則將 Child 節點添加到 stack 中，並將 curr 的 Child 設為 nil，因為它已經被扁平化了。
        if curr.Child != nil {
            stack = append(stack, curr.Child)       
            curr.Child = nil
        }

        prev = curr
    }

    return dummy.Next
}
