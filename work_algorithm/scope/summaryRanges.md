# Summary Ranges


```go

    func summaryRanges(nums []int) (result []string) {
	
	if len(nums)==0{
			return  
	}
	L:=0
	N :=len(nums)
	for L<N{
		pre := nums[L]
		L++
		for  L<N &&  nums[L]-nums[L-1]==1{
				L++
		}
		if pre != nums[L-1]{
			result =append(result, strconv.Itoa(pre)+"->"+ strconv.Itoa(nums[L-1]))
		}else{
			result= append(result,strconv.Itoa( nums[L-1]))
		} 
 
	}
	return  
}


```