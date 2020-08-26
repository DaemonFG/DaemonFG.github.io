---
title: 剑指 Offer 53 - II. 0～n-1中缺失的数字
top: false
cover: false
toc: true
mathjax: true
date: 2020-08-24 11:17:38
password:
summary:
tags: Search Algorithm
categories: 剑指Offer
---

#### [剑指 Offer 53 - II. 0～n-1中缺失的数字](https://leetcode-cn.com/problems/que-shi-de-shu-zi-lcof/)

一个长度为n-1的递增排序数组中的所有数字都是唯一的，并且每个数字都在范围0～n-1之内。在范围0～n-1内的n个数字中有且只有一个数字不在该数组中，请找出这个数字。

- 示例1

  ~~~
  输入: [0,1,3]
  输出: 2
  ~~~

- 示例2

  ~~~
  输入: [0,1,2,3,4,5,6,7,9]
  输出: 8
  ~~~

- 限制

  ~~~
  1 <= 数组长度 <= 10000
  ~~~

#### 思路

- 有序考虑二分查找
- 观察得到缺失数字左侧nums[mid]==mid，令left=mid+1
- 否则缺失数字在mid左侧，令right=mid
- return值应该是在最终值的左侧，即left

#### 解答

- 时间复杂度

  - O(logn)

- 空间复杂度

  - O(1)

  ~~~C++
  class Solution {
  public:
      int missingNumber(vector<int>& nums) {
          int left = 0;
          int right = nums.size();
          while (left < right) {
              int mid = left + (right -left) / 2;
              if (nums[mid] == mid) left = mid + 1;
              else right = mid;
          }
          return left;
      }
  };
  ~~~

  