# 3 sum

Given an integer array nums, return all the triplets [nums[i], nums[j], nums[k]] such that i != j, i != k, and j != k, and nums[i] + nums[j] + nums[k] == 0.

Notice that the solution set must not contain duplicate triplets.


 tip: 
 + sort the array
 + Three nested llops
  
  ```go
    func threeSum(nums []int) [][]int {
    n := len(nums)
    sort.Ints(nums)
    ans := make([][] int ,0)
    
    for first :=0; first<n ; first++{
        //相等的数字就过滤，因为已经排序了
        if first >0 && nums[first] == nums[first -1 ]{
            continue
        }
         third := n - 1
      target := -1 * nums[first]
         for second := first + 1; second < n; second++ {
           //老套路
            if second > first + 1 && nums[second] == nums[second - 1] {
                continue
            }
            //greedly? 并且找第三个c的数字 ,
            for second < third && nums[second] +nums[third] > target{
              third --
            }
            // can't find anything.
            if second==third{
                break
            }
            if nums[second] + nums[third] == target{
               ans = append(ans, []int{nums[first], nums[second], nums[third]})
            } 
         } 
    }
return ans
}

  ```