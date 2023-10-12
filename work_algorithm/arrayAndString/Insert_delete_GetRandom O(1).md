# Insert Delete GetRandom O(1)

tip:
    array int and map
    map search cost time is O(1)
    
    delete method can store last index in map 
    

```go
type RandomizedSet struct {
    RandomArr []int
    ArrMap    map[int]int

}


func Constructor() RandomizedSet {
  return RandomizedSet{[]int{},map[int]int{}}
}


func (this *RandomizedSet) Insert(val int) bool {
   if _, ok := this.ArrMap[val]; ok {
        return false
    }
    this.ArrMap[val] = len(this.RandomArr)
    this.RandomArr = append(this.RandomArr, val)
    return true
 
}


func (this *RandomizedSet) Remove(val int) bool {
 if _, ok := this.ArrMap[val]; !ok {
        return false
    }
    //don't move all index,just move last

    lastIndex:=len(this.RandomArr)-1
    this.RandomArr[this.ArrMap[val]]= this.RandomArr[lastIndex]
       this.ArrMap[this.RandomArr[lastIndex]]=lastIndex
    this.RandomArr= this.RandomArr[:lastIndex]
    delete(this.ArrMap,val)
   
    return true
}


func (this *RandomizedSet) GetRandom() int {
  return this.RandomArr[rand.Intn(len(this.RandomArr))]
}


/**
 * Your RandomizedSet object will be instantiated and called as such:
 * obj := Constructor();
 * param_1 := obj.Insert(val);
 * param_2 := obj.Remove(val);
 * param_3 := obj.GetRandom();
 */
```