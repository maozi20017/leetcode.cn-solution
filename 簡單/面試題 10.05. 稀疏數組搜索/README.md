[題目敘述](https://leetcode.cn/problems/sparse-array-search-lcci/)

```go
func findString(words []string, s string) int {
    start,end:=0,len(words)-1
    for start<=end{
        mid:=(end+start)/2
        for ; mid < end; mid++ {
			if words[mid] != "" {   //指向不為空的字串
				break
			}
		}   //下面就基本的二分
        if words[mid]==s{
            return mid
        }
        if mid == end {
			end = (end+start)/2 - 1
			continue
		}
		if words[mid] < s {
			start = mid + 1
		} else {
			end = mid - 1
		}
	}
	return -1   
    /*    //這題應該是要考二分搜索法但這樣硬幹也能過
    for key,value:=range words{
        if value==s{
            return key
        }
    }
    return -1
    */
}
