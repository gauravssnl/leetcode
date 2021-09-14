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

Solution2 (Rust):

```rust

use std::collections::HashMap;

impl Solution {
    pub fn two_sum(nums: Vec<i32>, target: i32) -> Vec<i32> {
        let mut diff_index_map:HashMap<i32, i32> = HashMap::new();
        for index in 0..nums.len() {
            match diff_index_map.get(&nums[index]) {
                Some(&other_index) => { return vec![other_index as i32, index as i32]; },
                None => { diff_index_map.insert(target - nums[index], index as i32); }
            }
        }
        vec![-1, -1]
    }
}

```

2. Contains Duplicate

Solution1 (Rust):

```rust

use std::collections::HashMap;

impl Solution {
    pub fn contains_duplicate(nums: Vec<i32>) -> bool {
        let mut element_count_map = HashMap::new();
        for index in 0..nums.len() {
            if let Some(&count) = element_count_map.get(&nums[index]) {
                return true;
            } else {
                element_count_map.insert(nums[index], 1);
            }
        }
        false
    }
}

```
