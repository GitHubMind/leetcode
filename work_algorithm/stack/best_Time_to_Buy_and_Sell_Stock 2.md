#  Best Time to Buy and Sell Stock 


    dp[i][1]=MaxSelf(dp[i-1][1],dp[i-1][0]-prices[i])
              max   ( sell out ,last transaction )

```go

     func maxProfit(prices []int) int {
    n := len(prices)
    dp := make([][2]int, n)
    for i:=0;i< n;i++{
        if i==0{
        dp[0][0]=0
        dp[0][1]=-prices[i]
        continue
        }
        dp[i][0]=MaxSelf(dp[i-1][0],prices[i]+dp[i-1][1])
        dp[i][1]=MaxSelf(dp[i-1][1],-prices[i])
    }
    return dp[n-1][0]
}

func MaxSelf(a,b int) int{
    if a>b {
        return a 
    }
    return b
}
```