---
title: 剑指 Offer 21. 调整数组顺序使奇数位于偶数前面
top: false
cover: false
toc: true
mathjax: true
date: 2020-08-27 14:14:48
password:
summary:
tags: 对撞指针
categories: 剑指Offer
---

### [剑指 Offer 21. 调整数组顺序使奇数位于偶数前面](https://leetcode-cn.com/problems/diao-zheng-shu-zu-shun-xu-shi-qi-shu-wei-yu-ou-shu-qian-mian-lcof/)

输入一个整数数组，实现一个函数来调整该数组中数字的顺序，使得所有奇数位于数组的前半部分，所有偶数位于数组的后半部分。

- 示例：

  ~~~
  输入：nums = [1,2,3,4]
  输出：[1,3,2,4] 
  注：[3,1,2,4] 也是正确的答案之一。
  ~~~

- 提示：

  ~~~
  1 <= nums.length <= 50000
  1 <= nums[i] <= 10000
  ~~~

#### 思路

1. 对撞指针left控制奇数，right控制偶数
2. 如果nums[left]是奇数，left右移
3. 同理right左移
4. 否则交换nums[left]和nums[right]

#### Answer

##### Time Complexity

- $O(N)$

##### Space Complexity

- $O(1)$

##### Code

~~~C++
class Solution {
public:
    vector<int> exchange(vector<int>& nums) {
        int left = 0, right = nums.size() - 1;
        while (left < right) {
            if ((nums[left] & 1) != 0) {	//奇数的二进制数的最后一位永远是 1，与 1 按位且只会得到 1，偶数相反
                left+=1; 
                continue;
                }
            if ((nums[right] & 1) != 1) {
                right-=1; 
                continue;
                }
            swap(nums[left++], nums[right--]);	//先使用再++
        }
        return nums;
    }
};
~~~

