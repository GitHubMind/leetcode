# Remove duplicates from sorted_array

## different  for 1 is

```shell
Input: nums = [1,1,1,2,2,3]
Output: 5, nums = [1,1,2,2,3,_]
```

tip:
    read tip should be more careful!


 [slow-2] = origin postion
 fast     = check  postion
 1. if the nums is orrectl that nums[slow]==nums[slow+1]

 2. and then nums[slow] must not be euqal to nums[slow+2](nums[fast])


```go
func removeDuplicates(nums []int) int {
  if len(nums)<2{
    return 0
  }
  // becase  at most twice and keep the same
  fast :=2
  slow :=2
  for fast <  len(nums) {
      //  nums[slow-2] = right postion
      if nums[slow-2] != nums[fast]{
          nums[slow]= nums[fast]
          slow++
      }
          fast++
      
  }
  return slow
}```
