[題目敘述](https://leetcode.cn/problems/merge-sorted-array/)

```go
func merge(nums1 []int, m int, nums2 []int, n int)  {
    i, j, k := m-1, n-1, m+n-1  //i指向nums1最後一個不為0的 j指向nums2最後一個 k指向nums1最後一個
    for i >= 0 && j >= 0 {
        if nums1[i] > nums2[j] {    //較大的先到最後面
            nums1[k] = nums1[i]     //交換
            i--     //指針移動
        } else {
            nums1[k] = nums2[j]
            j--
        }
        k--
    }
    for j >= 0 {    //nums2剩餘的
        nums1[k] = nums2[j]
        j--
        k--
    }
    /* 沒有利用到數組已經被排序的性質
    nums1=append(nums1[:m],nums2...)
    sort.Ints(nums1)
    return 
    */
}
