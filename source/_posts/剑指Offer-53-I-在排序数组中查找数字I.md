---
title: 剑指 Offer 53 - I. 在排序数组中查找数字 I
top: false
cover: false
toc: true
mathjax: true
date: 2020-08-24 10:33:02
password:
summary:
tags: Search Algorithm
categories: 剑指Offer
---

#### [剑指 Offer 53 - I. 在排序数组中查找数字 I](https://leetcode-cn.com/problems/zai-pai-xu-shu-zu-zhong-cha-zhao-shu-zi-lcof/)

统计一个数字在排序数组中出现的次数。

- 示例 1:

  ~~~
  - 输入: nums = [5,7,7,8,8,10], target = 8
    输出: 2
  ~~~

- 示例 2:

  ~~~
  输入: nums = [5,7,7,8,8,10], target = 6
  输出: 0
  ~~~

- 限制：

  ~~~
  0 <= 数组长度 <= 50000
  ~~~

#### 思路

- 有序数组首选二分查找
- 因为要统计次数，所以要考虑target重复
- 首先二分查找到target，再以target为中心，左右统计相同的个数

#### 解答

- 时间复杂度
  - O(logn)
- 空间复杂度

  - O(1)

~~~C++
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int start = 0;
        int end = nums.size() - 1;
        int p = -1;
        while (start <= end) {
            int mid = start + (end - start) / 2;	//不写(start+end)/ 2是为了防止数字过大带来加法益处
            if (nums[mid] == target) {
                p = mid;
                break;
            } else if (nums[mid] > target) end = mid - 1;
            else start = mid + 1;
        }
        if (p == -1) return 0;
        int low = p;
        int high = p;
        while ( low >= 0 && nums[low] == target) low-=1;	//此处如果写成(nums[low] == target &&  low >= 0) 会报越界，下一行同理
        while ( high < nums.size() && nums[high] == target) high+=1;
        return high - low -1;
    }
};
~~~

