[題目敘述](https://leetcode.cn/problems/binary-tree-inorder-traversal/description/)
```go
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func inorderTraversal(root *TreeNode) []int {
    if root==nil{
        return []int{} // 處理空樹的情況
    }
    
    ans:=[]int{}
    stack:=[]*TreeNode{} // 使用指向 TreeNode 的指針作為堆疊的元素類型
    currentNode:=root
    
    for currentNode!=nil||len(stack)!=0{
        if currentNode!=nil{
            stack=append(stack,currentNode)
            currentNode=currentNode.Left
        } else{
            // 從堆疊中彈出頂部元素
            top:=stack[len(stack)-1]
            stack=stack[:len(stack)-1]
            ans=append(ans, top.Val)
            currentNode=top.Right
        }
    }
    
    return ans
}
