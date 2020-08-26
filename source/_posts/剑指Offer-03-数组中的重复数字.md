---
title: 剑指Offer 03.数组中的重复数字
top: false
cover: false
toc: true
mathjax: true
date: 2020-08-21 16:06:53
password:
summary:
tags: Search Algorithm
categories: 剑指Offer
---

### [剑指 Offer 03. 数组中重复的数字](https://leetcode-cn.com/problems/shu-zu-zhong-zhong-fu-de-shu-zi-lcof/)

- 找出数组中重复的数字。

  - 在一个长度为 n 的数组 nums 里的所有数字都在 0～n-1 的范围内。数组中某些数字是重复的，但不知道有几个数字重复了，也不知道每个数字重复了几次。请找出数组中任意一个重复的数字。
  - **示例 1：**

  ```
  输入：
  [2, 3, 1, 0, 2, 5, 3]
  输出：2 或 3 
  ```

  - **限制：**

  ```
  2 <= n <= 100000
  ```


#### 思路

- 如果nums[i] != i，位置i处放得不是数字i，则利用swap()交换的方法将i换到nums[i]。
- 但如果位置nums[i]上已经等于nums[i]，则nums[i]就是重复数字。
- 如果nums[i]位置上第一次等于i，跳过。

#### 解答

- 时间复杂度
  - O\(n\)
- 空间复杂度
  
  - O\(1\)

~~~c++
class Solution {
public:
    int findRepeatNumber(vector<int>& nums) {
        for(int i=0; i < nums.size(); i++) {
            if (nums[i]==i) continue;
            if (nums[nums[i]] == nums[i]) return nums[i];
            swap(nums[i],nums[nums[i]]);
        }
        return 0;
    }
};
~~~