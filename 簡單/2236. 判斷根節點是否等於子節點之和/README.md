[題目敘述](https://leetcode.cn/problems/root-equals-sum-of-children/)

```go
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func checkTree(root *TreeNode) bool {   //應該不用註解
    return root.Left.Val+root.Right.Val==root.Val
}
