[題目敘述](https://leetcode.cn/problems/clone-graph/description/)
```go
/**
 * 定義節點結構
 * type Node struct {
 *     Val int                // 節點的數值
 *     Neighbors []*Node      // 連接的鄰居節點列表
 * }
 */

func cloneGraph(node *Node) *Node {
    // 如果輸入節點為空，則返回空指針
    if node == nil {
        return nil
    }
    
    // 創建一個映射，用於保存已經複製的節點
    clonedNodes := make(map[*Node]*Node)

    // 創建一個隊列，將原始圖的根節點加入其中
    queue := []*Node{node}

    // 創建一個根節點的複製，並將其放入映射
    clonedNode := &Node{Val: node.Val}
    clonedNodes[node] = clonedNode

    // 使用BFS遍歷原始圖
    for len(queue) > 0 {
        // 取出隊列的第一個節點
        current := queue[0]
        queue = queue[1:]

        // 遍歷當前節點的鄰居節點
        for _, value := range current.Neighbors {
            // 如果鄰居節點還未被複製，則創建複製節點並放入映射
            if clonedNodes[value] == nil {
                clonedNeighbor := &Node{Val: value.Val}
                clonedNodes[value] = clonedNeighbor

                // 將複製的鄰居節點加入當前節點的複製的鄰居列表中
                clonedNodes[current].Neighbors = append(clonedNodes[current].Neighbors, clonedNeighbor)

                // 將複製的鄰居節點加入隊列，以便後續處理
                queue = append(queue, value)
            } else {
                // 如果鄰居節點已經被複製，則直接將複製節點加入當前節點的複製的鄰居列表中
                clonedNodes[current].Neighbors = append(clonedNodes[current].Neighbors, clonedNodes[value])
            }
        }
    }

    // 返回根節點的複製，即整個複製圖的根節點
    return clonedNodes[node]
}
