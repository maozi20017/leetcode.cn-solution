[題目敘述](https://leetcode.cn/problems/construct-binary-tree-from-preorder-and-inorder-traversal/description/)
```go
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func buildTree(preorder []int, inorder []int) *TreeNode {
    size:=len(preorder)

    if size==1{
        return &TreeNode{Val: preorder[0]}
    }

    // 根節點會是前序遍歷的第一個
    root:=&TreeNode{Val: preorder[0]}
    stack:=[]*TreeNode{root}

    //中序遍歷的起點
    inorderIndex:=0

    for i:=1;i<len(preorder);i++{
        currnode:=&TreeNode{Val: preorder[i]}
        var parent *TreeNode

        //中序遍歷的根結點會進入到這個迴圈 stack的最頂層元素是currnode的父節點
        for len(stack)>0&&stack[len(stack)-1].Val==inorder[inorderIndex]{
            parent=stack[len(stack)-1]
            stack=stack[:len(stack)-1]
            inorderIndex++
        }

        if parent!=nil{
            parent.Right=currnode
        }else{
            stack[len(stack)-1].Left=currnode
        }

        stack=append(stack,currnode)
    }

    return root
}
