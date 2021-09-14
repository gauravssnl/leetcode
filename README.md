# leetcode
LeetCode Solutions in Rust, Python, Java and other lanaguages.


## Easy Questions

1. Two Sum

Solution1 (Rust):

```rust

use std::collections::HashMap;

impl Solution {
    pub fn two_sum(nums: Vec<i32>, target: i32) -> Vec<i32> {
        let mut value_index_map = HashMap::new();
        for (index, value) in nums.iter().enumerate() {
            let diff = target - nums[index];
            if let Some(&prev_index) =  value_index_map.get(&diff) {
                return vec![prev_index as i32, index as i32];
            } else {
                value_index_map.insert(value, index);
            }
        }
        vec![-1, -1]
    }
}

```
