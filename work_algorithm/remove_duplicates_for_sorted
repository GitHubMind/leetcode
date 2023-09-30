# Remove Dumplicates from Sorted Array

seem easy


```go
func removeDuplicates(nums []int) int {
    if len(nums)==0{
        return 0
    }
    pre:=nums[0]
    left:=0
    for i:=1; i < len(nums);i++{
        if pre ^ nums[i] !=0{
        
            left++
            nums[left]=nums[i]
            pre=nums[i]
            
        }
    }
    return left+1
}
```