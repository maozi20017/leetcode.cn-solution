[題目敘述](https://leetcode.cn/problems/average-salary-excluding-the-minimum-and-maximum-salary/)   
```go
func average(salary []int) float64 {
    sum, max, min := 0, salary[0], salary[0] // 初始化總和、最高和最低薪資為第一個薪資
    for _, s := range salary { // 迴圈遍歷所有薪資
        sum += s // 加總所有薪資
        if s > max { // 如果這個薪資比目前最高薪資還高
            max = s // 將最高薪資更新為這個薪資
        }
        if s < min { // 如果這個薪資比目前最低薪資還低
            min = s // 將最低薪資更新為這個薪資
        }
    }
    return float64(sum-max-min) / float64(len(salary)-2) // 返回其他薪資的平均值
}
