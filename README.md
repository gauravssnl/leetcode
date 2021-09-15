# leetcode
LeetCode Solutions in Rust, Python, Java and other lanaguages.


## Easy Questions

1. [Two Sum](https://leetcode.com/explore/featured/card/top-interview-questions-easy/92/array/546/)

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


2. [Contains Duplicate](https://leetcode.com/explore/featured/card/top-interview-questions-easy/92/array/578/)

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

3. [Rotate Array](https://leetcode.com/explore/featured/card/top-interview-questions-easy/92/array/646/)

Solution1 (Rust):

```rust

impl Solution {
    pub fn rotate(nums: &mut Vec<i32>, k: i32) {
        let mut result = vec![0; nums.len()];
        for index in 0..nums.len() {
            let result_index = (index as i32 + k) % nums.len() as i32;
            result[result_index as usize] = nums[index];
        }
        *nums = result;
    }
}

```

Solution2 (Rust) : Time Limit Exceeded - 36/37 Test Cases Passed

```rust

impl Solution {
    pub fn rotate(nums: &mut Vec<i32>, k: i32) {
        for _ in 1..=k {
            let last_element = nums[nums.len() - 1];
            for i in (1..nums.len()).rev() {
                nums[i] = nums[i - 1];
            }
            nums[0] = last_element;
        }
    }
}

```
