#  Best Time to Buy and Sell Stock 

O(1) Simulated code

``` go  
func maxProfit(prices []int) int {
    sell:=0
    buy := math.MaxInt64
    for i:=0;i<len(prices);i++{
        buy =  MinSelf(prices[i],buy)
        sell= MaxSelf(sell,prices[i]-buy)
    }
return  sell
}

func MaxSelf(a,b int) int{
    if a>b {
        return a 
    }
    return b
}

func MinSelf(a,b int) int{
    if a>b {
        return b
    }
    return a
}
```