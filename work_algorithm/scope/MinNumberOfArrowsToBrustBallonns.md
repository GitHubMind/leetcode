#  Minimum Number of Arrows to Burst Balloons





```go
  func findMinArrowShots(points [][]int) (ans int) {
    if len(points)==0{
        return 0
    }
    sort.Slice(points, func( i,j int )bool { return points[i][1]< points[j][1]})
    ansPoint:=points[0][1]
    ans=1
    for i:=1;i<len(points);i++{
        if ansPoint< points[i][0]{
            ans++
            ansPoint=points[i][1]
        
        }
    }
    return 
}
```