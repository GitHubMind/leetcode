# Gas Station

greekly: 

The cost to  `reach` the next station will be higher than then cureent statsion if the car `donestn'` reach statsion B from A, Therefore,i set tow values:'totalTank',which accumluates all 'gas[i]-cost[i]' values,and if it becomes negative,it indicates an inablilty to readch the destination, The other value is 'currentTank', which represents  whether it can reach the next station ,if 'cureentTank' becomes negative,it must be rest 0. 



```go
    func canCompleteCircuit(gas []int, cost []int) int {
    totalTank,CurrentTank:=0,0
    startStatsion:=0
    for i:=0;i<len(gas);i++{
        totalTank+= gas[i]-cost[i]
        CurrentTank+= gas[i]-cost[i]

        if CurrentTank<0{
            CurrentTank=0
            startStatsion=i+1
        }

    }
    if totalTank <0{
        return  -1
    }else{
        return startStatsion
    }
}

```