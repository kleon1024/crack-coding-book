# Rotate

## LC48. Rotate Image

🟡[lc48](https://leetcode.com/problems/rotate-image/)

A common method to solve the image rotation problem.

```go
/*
 * clockwise rotate
 * first reverse up to down, then swap the symmetry 
 * 1 2 3     7 8 9     7 4 1
 * 4 5 6  => 4 5 6  => 8 5 2
 * 7 8 9     1 2 3     9 6 3
*/

/*
 * anticlockwise rotate
 * first reverse left to right, then swap the symmetry
 * 1 2 3     3 2 1     3 6 9
 * 4 5 6  => 6 5 4  => 2 5 8
 * 7 8 9     9 8 7     1 4 7
*/
```

{% tabs %}
{% tab title="Go" %}
```go
func rotate(matrix [][]int) {
    for i, j := 0, len(matrix)-1; i < j; i, j = i+1, j-1 {
        matrix[i], matrix[j] = matrix[j], matrix[i]
    }
    for i := 0; i < len(matrix); i++ {
        for j := i + 1; j < len(matrix[i]); j++ {
            matrix[i][j], matrix[j][i] = matrix[j][i], matrix[i][j]
        }
    }
}
```
{% endtab %}
{% tab title="Java" %}
```java
void rotate(vector<vector<int> > &matrix) {
    reverse(matrix.begin(), matrix.end());
    for (int i = 0; i < matrix.size(); ++i) {
        for (int j = i + 1; j < matrix[i].size(); ++j)
            swap(matrix[i][j], matrix[j][i]);
    }
}
```
{% endtab %}
{% tab title="Rust"%}
```rust
impl Solution {
    pub fn rotate(matrix: &mut Vec<Vec<i32>>) {
        matrix.reverse();
        for i in 0..matrix.len() {
            for j in i+1 .. matrix[i].len() {
                let tmp = matrix[i][j];
                matrix[i][j] = matrix[j][i];
                matrix[j][i] = tmp;
            }
        }
    }
}
```
{% endtab %}
{% endtabs %}