# Jump Game

    violent  way?  lt's must will time out !

    Greedy ? 

    lt's have ring ?  but can't find in question text.


```go
    func canJump(nums []int) bool {
    numLen:= len(nums) -1 
    sum:=0 
     for i:=0;i<numLen;i++{
        sum = max(sum,i + nums[i])
        if sum >= numLen{
            return true
        }
     }
    return false
    }
    func max(x int, y int) int {
        if x < y {
            return y
        }
        return x
    }
```