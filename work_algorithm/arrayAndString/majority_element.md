# majority element

tip : esay right?
+ map [too more spend]
+ vote methods

The topNum should be the largest to accommodate a great number.

```
func majorityElement(nums []int) int {
    if len(nums)==0{
        return 0
    }
    topNums:=1
    topName:=nums[0]
 
    // 111112 =>1
    // 
    // 22 11 i think it is unvalid
    // 22 1 22 44
    
    for i:=1;i<len(nums);i++{
         if nums[i]==topName{
             topNums++

         }else if topNums ==1 {
             topName=nums[i]
         }else{
             topNums--
         }
    }
    return topName

}
```