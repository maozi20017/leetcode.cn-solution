[題目敘述](https://leetcode.cn/problems/remove-one-element-to-make-the-array-strictly-increasing/)

```go
func canBeIncreasing(nums []int) bool {
	for i := 1; i < len(nums); i++ {
		if nums[i-1] >= nums[i] {   //兩個必定要刪除其中一個 各個刪除檢查一遍就好
			return CombineAndCheckSort(nums,i-1) || CombineAndCheckSort(nums,i)
		}
	}
	return true
}

func CombineAndCheckSort(nums []int,i int)bool{
    s := make([]int, len(nums)-1)   //建立一個 s 且這樣不會影響到原nums
    copy(s, nums[:i])
    copy(s[i:], nums[i+1:])
    return sort.SliceIsSorted(s, func(i, j int) bool { return s[i] <= s[j] })   //檢查是否升序並傳回布林值
}
