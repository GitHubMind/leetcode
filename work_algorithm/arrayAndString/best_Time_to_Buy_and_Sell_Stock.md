#  Best Time to Buy and Sell Stock 

```

DPprices = [7,1,5,3,6,4]

Day     Price   dp[i][0] dp[i][1]
----------------------------------
0       7       0        -7       // 刚开始，要么不买（利润为0），要么买入（利润为-price[i]，即-7）
1       1       0        -1       // 第一天不买，利润为0；或者买入，利润为-1
2       5       4        -1       // 第二天要么之前买入今天卖出，利润为4；要么之前买入继续持有
3       3       4         1       // 第三天要么不买卖，利润为4；要么买入，利润为1（因为可以利用前一天卖出的4减去今天的价格3得到1）
4       6       7         1       // 第四天要么卖出，利润为7；要么继续持有
5       4       7         3       // 第五天要么不买卖，利润为7；要么买入，利润为3


``` go
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
        // prices[i][0] sell out in yesterday
        dp[i][1]=MaxSelf(dp[i-1][1],prices[i][0]-prices[i])
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