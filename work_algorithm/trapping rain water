# Trapping Rain Water

Given n non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it can trap after raining.

[ LINKE] ( https://leetcode.cn/problems/trapping-rain-water/description/?envType=study-plan-v2&envId=top-interview-150 )


### double point

 trap([]int{0, 0, 3, 1, 0})
 left ,right ,L max , R max , ans
 0    , 4    , 0    ,0      ,0
 0    , 3    , 0    ,0      ,0
 1    , 3    , 0    ,1      ,0    //offset it
 2    , 3    , 3    ,1      ,0    //offset it

 ans = 0

```GO
func trap(height []int) int {
    left ,right :=0, len(height)-1
    leftmax,rightMax :=0,0
    ans:=0
    for left < right{
    
        leftmax = max(leftmax,height[left])
        rightMax = max(rightMax, height[right])

        if height[left] < height[right]{
            ans+= leftmax - height[left]
            left++
        }else{
            ans += rightMax -height[right]
            right--
        }
    }
    return ans
}
func max(a, b int) int {
    if a > b {
        return a
    }
    return b
}
```

