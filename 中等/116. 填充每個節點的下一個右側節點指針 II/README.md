[題目敘述](https://leetcode.cn/problems/populating-next-right-pointers-in-each-node-ii/description/)   
其實跟前一題一樣 BFS無視是否完美二元樹
```go
/**
 * Definition for a Node.
 * type Node struct {
 *     Val int
 *     Left *Node
 *     Right *Node
 *     Next *Node
 * }
 */

func connect(root *Node) *Node {
    // 如果根節點為空，則直接返回空
    if root == nil {
        return nil
    }

    // 創建一個隊列，將根節點加入
    queue := []*Node{root}
    // 遍歷隊列，直到隊列為空
    for len(queue) > 0 {
        // 當前層的節點數
        levelSize := len(queue)
        // 遍歷當前層的節點
        for i := 0; i < levelSize; i++ {
            // 取出隊列中的第一個節點
            curr := queue[0]
            // 將取出的節點從隊列中移除
            queue = queue[1:]
            // 如果是當前層的最後一個節點，則將其 Next 指針指向空
            if i == levelSize-1 {
                curr.Next = nil
            } else {
                // 否則將其 Next 指針指向下一個節點
                curr.Next = queue[0]
            }
            // 如果當前節點有左子節點，則將其左子節點加入隊列
            if curr.Left != nil {
                queue = append(queue, curr.Left)
            }
            // 如果當前節點有右子節點，則將其右子節點加入隊列
            if curr.Right != nil {
                queue = append(queue, curr.Right)
            }
        }
    }

    // 返回根節點
    return root
}
