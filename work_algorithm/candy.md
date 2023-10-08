# Candy Hard

line:
https://leetcode.cn/problems/candy/description/?envType=study-plan-v2&envId=top-interview-150

 lt's rate to deal with the problem, but it have 2 requirement

+  Each child must have at least one candy.
+  Children with a higher rating get more candies than their neighbors.


i think [0,0,0,0,0] output maybe is [1,2,3,4,5] result is 5!

##  two array

<!-- left arrau start left to right ,if find rate[i] more than rate[i+1] left[i]=i++
right array is same way.  seem greekly right? -->

If you start from the left in the array and find the rate[i] is greater than rate[i+1] ,then  set left[i] ++,。Similarly, for the right array. you can follow the same approach .

result = sum(right)

```go
func candy(ratings []int) int {
    leftArr:=make([]int,len(ratings))
  
    Result:=0

    // base requestment
    for i:=  range ratings{
        leftArr[i]=1
    }
    
    for i:=1;i<len(leftArr);i++{
        if ratings[i] > ratings[i-1]{
            leftArr[i]=leftArr[i-1]+1
        }
    }

      for i:=len(leftArr)-2;i>=0;i--{
        if ratings[i] > ratings[i+1]{
          leftArr[i]=func(a,b int )int{
              if a>b {return a}
              return b
          }(leftArr[i],leftArr[i+1]+1)
        }
    }

    for v:= range leftArr{
         Result +=leftArr[v]
    }
    return Result


}
```


