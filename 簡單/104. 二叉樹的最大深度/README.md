[題目敘述](https://leetcode.cn/problems/maximum-depth-of-binary-tree/description/)
```go
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func maxDepth(root *TreeNode) int {
    if root == nil {
        return 0
    }

    // 使用切片模擬隊列，初始化時將根節點和深度1入隊
    queue := []*TreeNode{root}
    depth := 1

    for len(queue) > 0 {
        size := len(queue)

        for i := 0; i < size; i++ {
            node := queue[i]

            // 將左右子節點入隊，用於處理下一層
            if node.Left != nil {
                queue = append(queue, node.Left)
            }
            if node.Right != nil {
                queue = append(queue, node.Right)
            }
        }
        // 更新隊列為下一層的節點
        queue = queue[size:]

        // 到達下一層，深度加一
        if len(queue) > 0 {
            depth++
        }
    }

    return depth
}
