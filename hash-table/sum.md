# Sum

## 1. Two Sum

🟢[lc1](https://leetcode.com/problems/two-sum/)

The basic idea is using a hash map to store the {v, i}. If (target - v) is in the map, if means the we find the results with current index and the previous index.

{% tabs %}
{% tab title="Go" %}
```go
func twoSum(nums []int, target int) []int {
    m := map[int]int{}
    for i, n := range nums {
        if v, ok := m[target - n]; ok {
            return []int{v, i}
        }
        m[n] = i
    }
    return []int{}
}
```
{% endtab %}
{% tab title="Rust" %}
```rust
use std::collections::HashMap;

impl Solution {
    pub fn two_sum(nums: Vec<i32>, target: i32) -> Vec<i32> {
        let mut m: HashMap<i32, i32> = HashMap::new();
        for (i, v) in nums.iter().enumerate() {
            match m.get(&(target - v)) {
                Some(i2) => return vec![i as i32, *i2],
                None => m.insert(*v, i as i32),
            };
        }
        vec![]
    }
}
```
{% endtab %}
{% endtabs %}

## 167. Two Sum II - Input Array Is Sorted

🟡[lc167](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)

We can use the solution from Two Sum, or we can just use two pointers to get close to the target.

{% tabs %}
{% tab title="Go" %}
```go
func twoSum(numbers []int, target int) []int {
    l, r := 0, len(numbers) - 1
    
    for l < r {
        s := numbers[l] + numbers[r]
        if s == target {
            break;
        } else if s < target {
            l++
        } else {
            r--
        }
    }
    return []int{l+1, r+1}
}
```
{% endtab %}
{% tab title="Rust" %}
```rust
impl Solution {
    pub fn two_sum(numbers: Vec<i32>, target: i32) -> Vec<i32> {
        let mut left = 0;
        let mut right = numbers.len() - 1;
        
        while left < right {
            let sum = numbers[left] + numbers[right];
            
            if sum == target {
                break;
            } else if sum < target {
                left+=1;
            } else {
                right-=1;
            }
        }
        vec![left as i32 + 1, right as i32 + 1]
    }
}
```
{% endtab %}
{% endtabs %}

## LC1546 Maximum Number of Non-Overlapping Subarrays With Sum Equals Target

🟡[lc1546](https://leetcode.com/problems/maximum-number-of-non-overlapping-subarrays-with-sum-equals-target/)

The basic idea is using a map to store the prefix sum and the target = prefixSum[0...i] - prefixSum[0...j]

1. use a map to store prefixSum and it's rightMost index
2. initialize sum with O, available Index with -1, which means index bigger than -1 are unused
3. initialize map with {0:-1}, which means the initial sum is 0
4. for each nums[il in the array:
    1. update prefixSum with nums[il
    2. Let's say there's a subarray from index j to current index i whose sum is target, prefixSum[0...i] - prefixSum[0...j] = target, which means prefixSum - remain = target
    3. if remain = prefixSum-target exists, and it's starting index is bigger than availablelndex, it means a valid subarray exists:
        1. res++
        2. update availablelndex with i, because subarray from j to i is used
    4. always update map with prefixSum and i, so that it is guaranteed that the starting index j above is the rightMost index for prefixSum so that the subarray is as short as possible
5. return res in the end

{% tabs %}
{% tab title="Go" %}
```go
func maxNonOverlapping(nums []int, target int) int {
    m := map[int]int{}
    prefixSum, availableIdx, res := 0, -1, 0
    m[0] = -1
    for i := 0; i < len(nums); i++ {
        prefixSum += nums[i]
        remain := prefixSum - target
        if value, exists := m[remain]; exists {
            if value >= availableIdx {
                res++
                availableIdx = i
            }
        }
        m[prefixSum] = i
    }
    
    return res
}
```
{% endtab %}

{% tab title="Java" %}
```go
class Solution {
    public int maxNonOverlapping(int[] nums, int target) {
        Map<Integer, Integer> map= new HashMap<>();
        int prefixSum=0, availableIdx=-1, res=0;
        map.put(0,-1);
        for (int i=0; i<nums.length; i++){
            prefixSum+=nums[i];
            int remain = prefixSum - target;
            if (map.containsKey(remain) && map.get(remain)>=availableIdx){
                res++;
                availableIdx=i;
            }
            map.put(prefixSum, i);
        }
        return res;
    }
}
```
{% endtab %}

{% endtabs %}