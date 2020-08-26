---
title: 剑指 Offer 11.旋转数组的最小数字
top: false
cover: false
toc: true
mathjax: true
date: 2020-08-21 16:32:01
password:
summary:
tags: Search Algorithm
categories: 剑指Offer
---

### [剑指 Offer 11.旋转数组的最小数字](https://leetcode-cn.com/problems/xuan-zhuan-shu-zu-de-zui-xiao-shu-zi-lcof/)

- 把一个数组最开始的若干个元素搬到数组的末尾，我们称之为数组的旋转。输入一个递增排序的数组的一个旋转，输出旋转数组的最小元素。例如，数组 [3,4,5,1,2] 为 [1,2,3,4,5] 的一个旋转，该数组的最小值为1。  

  - 示例 1：

  ~~~
  输入：[3,4,5,1,2]
  输出：1
  ~~~

  - 示例 2：

  ~~~
  输入：[2,2,2,0,1]
  输出：0
  ~~~

#### 思路


- 每个数组由两段有序数组组成，且第二段数组的最大值<第一段数组的最大值，所以最小值一定在最右边的数组上。
- 对于有序数组，采用二分查找的思想，numbers[mid]与右侧值numbers[end]作比较

  - 如果numbers[mid] > numbers[end]，说明mid取到了偏左的位置，此时让numbers[start]取numbers[mid]右边一个值，即start=mid+1
  - 如果numbers[mid] < numbers[end]，则将end移到mid，即end=mid
  - 为了防止出现好几个相同的数，例如示例2，如果numbers[mid]==numbers[end]，将end左移，即end--
- 一直循环到start和end相邻或相等

#### 解答

- 时间复杂度
  - O(logn)
- 空间复杂度

  - O(1)

~~~C++
class Solution {
public:
    int minArray(vector<int>& numbers) {
        int start = 0;
        int end = numbers.size() - 1;
        while (start < end) {
            int mid = start + (end - start) / 2;
            if (numbers[mid] > numbers[end]) start=mid+1;
            else if (numbers[mid] < numbers[end]) end=mid;
            else end--;
        }
       return numbers[start];
    }
};
~~~