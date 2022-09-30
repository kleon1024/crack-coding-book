# Fint the Maximum

## LC363 Max Sum of Rectangle No Larger Than K
🔴[lc363](https://leetcode.com/problems/max-sum-of-rectangle-no-larger-than-k/)

* brute force

{% tabs %}
{% tab title="Go" %}
```go
func maxSumSubmatrix(matrix [][]int, k int) int {
    n, m := len(matrix), len(matrix[0])
    maxSum := math.MinInt
    for row := 0; row < n; row++ {
        col := make([]int, m)
        for i := row; i < n; i++ {
            for j := 0; j < m; j++ {
                col[j] += matrix[i][j]
            }
            maxSum = max(maxSum, maxSumSubarray(col, k))
        }
    }
    
    return maxSum
}

func maxSumSubarray(arr []int, k int) int {
    n := len(arr)
    curSum, maxSum := 0, math.MinInt
    
    for i := 0; i < n; i++ {
        curSum = 0
        for j := i; j < n; j++ {
            curSum += arr[j]
            if curSum <= k {
                maxSum = max(maxSum, curSum)
            }
        }
    }
    
    return maxSum
}

func max(a, b int) int {
    if a > b {
        return a
    }
    return b
}
```
{% endtab %}
{% tab title="Rust" %}
```rust
impl Solution {
    pub fn max_sum_submatrix(matrix: Vec<Vec<i32>>, k: i32) -> i32 {
        let n = matrix.len();
        let m = matrix[0].len();
        let mut maxSum = i32::MIN;
        
        for row in 0..n {
            let mut col = vec![0; m];
            for i in row..n {
                for j in 0..m {
                    col[j] += matrix[i][j];
                }
                maxSum = std::cmp::max(maxSum, Self::max_sum_subarray(&col, k));
            }
        }
        maxSum
    }
    
    pub fn max_sum_subarray(arr: &Vec<i32>, k: i32) -> i32 {
        let n = arr.len();
        let mut curSum = 0;
        let mut maxSum = i32::MIN;
        
        for i in 0..n {
            curSum = 0;
            for j in i..n {
                curSum += arr[j];
                if curSum <= k {
                    maxSum = std::cmp::max(maxSum, curSum);
                }
            }
        }
        maxSum
    }
}
```
{% endtab %}
{% endtabs %}