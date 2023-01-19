[題目敘述](https://leetcode.cn/problems/convert-sorted-array-to-binary-search-tree/)

```go
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func sortedArrayToBST(nums []int) *TreeNode {
    if len(nums)==0{
        return nil
    }
    mid:=len(nums)/2    //中序
    left:=nums[:mid]
    right:=nums[mid+1:]

    node:=&TreeNode{nums[mid], sortedArrayToBST(left), sortedArrayToBST(right)}
    return node
}
