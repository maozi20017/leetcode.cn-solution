[題目敘述](https://leetcode.cn/problems/symmetric-tree/description/)
```go
/**
 * 檢查二叉樹是否對稱
 * 
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func isSymmetric(root *TreeNode) bool {
    
    // 使用堆疊來追蹤節點
    stack := []*TreeNode{root.Left, root.Right}
    
    // 當堆疊不為空時執行循環
    for len(stack) > 0 {
        // 從堆疊中取出左子樹節點和右子樹節點
        left := stack[len(stack)-2]
        right := stack[len(stack)-1]
        stack = stack[:len(stack)-2]
        
        // 如果左右子樹節點皆為空，則繼續迴圈
        if left == nil && right == nil {
            continue
        }
        // 如果左右子樹節點其中一個為空，或者值不相等，則返回 false
        if left == nil || right == nil || left.Val != right.Val {
            return false
        }
        
        // 將左子樹的左節點、右子樹的右節點、左子樹的右節點、右子樹的左節點依序壓入堆疊中
        stack = append(stack, left.Left)
        stack = append(stack, right.Right)
        stack = append(stack, left.Right)
        stack = append(stack, right.Left)
    }
    
    // 如果循環結束都沒有返回 false，則表示二叉樹對稱，返回 true
    return true
}
