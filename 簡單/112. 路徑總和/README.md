[題目敘述](https://leetcode.cn/problems/path-sum/description/)
```go
/**
 * 定義二叉樹節點的結構。
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */

func hasPathSum(root *TreeNode, targetSum int) bool {
    // 如果樹根為空，直接返回 false。
    if root == nil {
        return false
    }

    // 使用堆棧儲存節點以及相應的目標和。
    stack := []*TreeNode{root}
    sums := []int{targetSum}

    // 深度優先搜索。
    for len(stack) > 0 {
        // 取出堆棧中最後一個節點。
        node := stack[len(stack)-1]
        stack = stack[:len(stack)-1]
        // 取出對應的目標和。
        currentSum := sums[len(sums)-1]
        sums = sums[:len(sums)-1]

        // 減去當前節點的值。
        currentSum -= node.Val

        // 如果當前節點是葉子節點且目標和為 0，則返回 true。
        if node.Left == nil && node.Right == nil && currentSum == 0 {
            return true
        }

        // 如果當前節點的左子節點不為空，將其壓入堆棧，並將相應的目標和壓入 sums。
        if node.Left != nil {
            stack = append(stack, node.Left)
            sums = append(sums, currentSum)
        }

        // 如果當前節點的右子節點不為空，將其壓入堆棧，並將相應的目標和壓入 sums。
        if node.Right != nil {
            stack = append(stack, node.Right)
            sums = append(sums, currentSum)
        }
    }

    // 如果遍歷完所有節點都沒有找到符合條件的路徑，返回 false。
    return false
}
