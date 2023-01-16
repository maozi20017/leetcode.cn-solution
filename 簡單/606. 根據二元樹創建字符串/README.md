[題目敘述](https://leetcode.cn/problems/construct-string-from-binary-tree/)

```go
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func tree2str(root *TreeNode) string {
    if root.Left==nil&&root.Right==nil{     //如果 root 左右子節點都不存在，返回root
        return strconv.Itoa(root.Val)+"";
    }
    if root.Left==nil{      //如果 root 只有右節點存在，返回root()(tight)
        return strconv.Itoa(root.Val)+"()"+"("+tree2str(root.Right)+")";
    }
    if root.Right==nil{     //如果 root 只有左節點存在，返回root(left)
        return strconv.Itoa(root.Val)+"("+tree2str(root.Left)+")";
    }
    return strconv.Itoa(root.Val)+"("+tree2str(root.Left)+")"+"("+tree2str(root.Right)+")";     //如果 root 左右子節點都存在，返回root(left)(right)
}
