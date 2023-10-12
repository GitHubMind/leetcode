# Minimum Size Subarray Sum

```go 
func minSubArrayLen(target int, nums []int) int {

   l,r:= 0, 0
   //mark ansnwer ，can't use r-l. r will equal with len(nums) at last .
   ans :=math.MaxInt32
   sum :=0 
   for r  < len(nums){
     sum += nums[r]
     // > will more one  any, should  >=
     for  sum >= target{
         ans  = min (ans,r-l +1 )
         sum -= nums[l]
         l++
     }

     r++
   }
   if ans == math.MaxInt32 {
        return 0
    }
    return ans

}
func min(x, y int) int {
    if x < y {
        return x
    }
    return y
}
```