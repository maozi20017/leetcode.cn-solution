[題目敘述](https://leetcode.cn/problems/find-the-difference-of-two-arrays/)

```go
func findDifference(nums1 []int, nums2 []int) [][]int {
    sm1,sm2:=make(map[int]int),make(map[int]int)
    //建map
    mp(sm1,nums1)
    mp(sm2,nums2)
    ans:=[][]int{make([]int, 0), make([]int, 0)} 
    //比較
    compareMap(sm1,sm2,&ans[0])
    compareMap(sm2,sm1,&ans[1])
    return ans
}

func mp(sm map[int]int,num []int){
    for _,value :=range num{
        sm[value]++
    }
}

func compareMap(mp1, mp2 map[int]int, ans *[]int){
    for key,_ := range mp1 {
        if mp2[key] == 0 {
            *ans = append(*ans, key)
        }
    }
    return 
}
