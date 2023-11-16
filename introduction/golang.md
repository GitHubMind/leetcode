#  Base work_algorithm
 
## tip:

+ Do not surpass the array limit when it comes to array length
+ Notice about nums2.length when its length is0.
+ you should do more quickly becase it's easy

```
func merge(nums1 []int, m int, nums2 []int, n int)  {
 
    index := m+n -1
    m--
    n--
    for  n>=0{  
            if m >=0 && nums1[m]> nums2[n]{
                    nums1[index]= nums1[m]
                    m--
            }else{
                    nums1[index]= nums2[n]
                    n--
            }
             index--
       
    } 
}
```
