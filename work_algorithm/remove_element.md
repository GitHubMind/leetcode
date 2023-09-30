# Remove Element

tip:
    n(0)

#### base code

```go
    func removeElement(nums []int, val int) int {
  left:=0
   for i :=0;i<len(nums);i++{
     if nums[i]!=val{
      
       nums[left]=nums[i]
       left++
     }
   }
   return  left
}
```

###  tow point code

 tip: I should  consider the possibility of utilizing  'for' next step .
 It seem quickly sort methods~
``` go
func removeElement(nums []int, val int) int {
  left:=0
  right:=len(nums)-1
   for left<=right{
      if nums[left]==val{
        nums[left]=nums[right]
           right--
      } else {
        left++
      }
   }
   return  left
}
```
