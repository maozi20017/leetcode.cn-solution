[題目敘述](https://leetcode.cn/problems/binary-tree-level-order-traversal/description/)
```go
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */

func levelOrder(root *TreeNode) [][]int {
    // 初始化結果數組
    ans := [][]int{}

    // 如果二叉樹為空，直接返回空數組
    if root == nil {
        return ans
    }

    // 建立隊列，初始時將根節點入隊
    queue := []*TreeNode{root}

    // 標準BFS遍歷
    for len(queue) > 0 {
        // 當前層的節點數
        size := len(queue)

        // 用於存儲當前層的節點值
        values := []int{}

        // 遍歷當前層的所有節點
        for i := 0; i < size; i++ {
            // 取出隊列的第一個節點
            node := queue[0]

            // 將第一個節點移出隊列
            queue = queue[1:]

            // 將節點值加到當前層的數組中
            values = append(values, node.Val)

            // 將左右子節點入隊，用於處理下一層
            if node.Left != nil {
                queue = append(queue, node.Left)
            }
            if node.Right != nil {
                queue = append(queue, node.Right)
            }
        }

        // 將當前層的節點值數組添加到結果中
        ans = append(ans, values)
    }

    // 返回最終的層序遍歷結果
    return ans
}
