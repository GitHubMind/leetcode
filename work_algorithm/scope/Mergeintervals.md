# merge Intervals


##
   +  sort array [0] -> [[2,6],[1,3],[8,10],[15,18] -> [[1,3],[2,6],[8,10],[15,18]] ->sort.Slice(intervals, func(i, j int) bool { return intervals[i][0] < intervals[j][0] })
   +  get result by  one  for pool
### code 

```go
   func merge(intervals [][]int) (result [][]int) { 
    sort.Slice(intervals, func(i, j int) bool { return intervals[i][0] < intervals[j][0] })
 
    result=append(result,intervals[0])
    for i:=1;i<len(intervals);i++{
        if intervals [i][0] > result[len(result)-1][1]{
       //  [1,2] [3,4]
       //     ^   ^ 



             result=append(result , intervals[i])
        }else{
            result[len(result)-1][1] = max(result[len(result)-1][1] ,intervals [i][1])
        }   
    } 
    return  
}


func max(a,b int ) int {
    if a>b{
        return a
    }
    return b
}

```