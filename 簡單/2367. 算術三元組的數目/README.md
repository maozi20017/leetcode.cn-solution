[題目敘述](https://leetcode.cn/problems/number-of-arithmetic-triplets/)

```go
func arithmeticTriplets(nums []int, diff int) int {
    cnt:=0    //三指針的方式
    i, j := 0, 1
	for _, x := range nums[2:] {
		for nums[j]+diff < x {    //先判斷nums[j]+diff是否存在
			j++
		}
		if nums[j]+diff > x {     //沒有就直接下一個循環
			continue
		}
		for nums[i]+diff*2 < x {     //後判斷nums[j]+2*diff是否存在
			i++
		}
		if nums[i]+diff*2 == x {
			cnt++
		}
	}
	return cnt
  
  //下面這個是用map尋找,但題目已經排序好了用上面的方法就好
    /*
    mp:=map[int]bool{}
    for _,value:= range nums{
        if mp[value-diff]&&mp[value-2*diff]{
            cnt++
        }
        mp[value]=true
    }
    return cnt
    */
}
