
tip:Given an m x n integer matrix matrix, if an element is 0, set its entire row and column to 0's.
```go
func setZeroes(matrix [][]int)  {
        col:= make([]bool ,len(matrix[0]))
        row := make([]bool ,len(matrix))

        for i:=0;i<len(row);i++{
            for j:=0;j<len(col);j++{
                if matrix[i][j]==0{
                  row[i]=true
                 col[j]=true
                }
            }
        }

        for i:=0;i<len(row);i++{
            for j:=0;j<len(col);j++{
            if row[i]==true|| col[j]==true{
                matrix[i][j]=0
            }
        } 
    }
}
```