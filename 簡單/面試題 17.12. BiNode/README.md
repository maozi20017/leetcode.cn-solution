[題目敘述](https://leetcode.cn/problems/binode-lcci/)
老實說這題我還是不太會

```go
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func convertBiNode(root *TreeNode) *TreeNode {
    dummyHead := &TreeNode{}
    lastNode := dummyHead
    inOrder(root, &lastNode)
    return dummyHead.Right  //dummyHead的原節點的root為空
}

func inOrder(root *TreeNode, lastNode **TreeNode) {
    if root == nil {    //如果節點為空則返回上個
        return
    }

    inOrder(root.Left, lastNode)    //遞迴遍歷左節點

    root.Left = nil     //左節點更改成null
    (*lastNode).Right = root    //跟上個節點連接
    *lastNode = root    //更新為目前節點

    inOrder(root.Right, lastNode)   //遍歷右節點
}
