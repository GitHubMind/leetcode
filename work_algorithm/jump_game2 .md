#jump_game2

it need return the minimum number of step 


greedy methds: local optimum,

        
             2 3 1 1 4
step1        x x
maxdistance    x
step2        x x x x x
maxdistance      x x x

ans= 2 ( local optimun)


```go
    func jump(nums []int) int {
    if len(nums) <= 1 {
        return 0 
    }
    curDistance, nextDistance, ans := 0, 0, 0
    for i := 0; i < len(nums); i++ {
        // local optimum
        nextDistance = max(nextDistance, i+nums[i])
        if i == curDistance {
            ans++
            curDistance = nextDistance
            if curDistance >= len(nums) - 1 {
                break
            }
        }
    }
    return ans
}

func max(x, y int) int {
    if x < y {
        return y
    }
    return x
}

    
```

