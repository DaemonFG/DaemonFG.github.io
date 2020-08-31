---
title: 剑指 Offer 39. 数组中出现次数超过一半的数字
top: false
cover: false
toc: true
mathjax: true
date: 2020-08-31 13:30:51
password:
summary:
tags: Boyer–Moore majority vote algorithm
categories: 剑指Offer
---

### [剑指 Offer 39. 数组中出现次数超过一半的数字](https://leetcode-cn.com/problems/shu-zu-zhong-chu-xian-ci-shu-chao-guo-yi-ban-de-shu-zi-lcof/)

数组中有一个数字出现的次数超过数组长度的一半，请找出这个数字。

 你可以假设数组是非空的，并且给定的数组总是存在多数元素。

- 示例

  ~~~
  输入: [1, 2, 3, 2, 2, 2, 5, 4, 2]
  输出: 2
  ~~~

- 限制

  ~~~
  1 <= 数组长度 <= 50000
  ~~~

#### 思路

- 方法一
  - 排序以后取中间的值
- 方法二
  - 哈希表
- 方法三
  - [摩尔投票法](https://mp.weixin.qq.com/s?__biz=MjM5NjIyMjQ4Nw==&mid=2247483952&idx=1&sn=7099f8d70221c6854298f2c9ffdcc6eb&chksm=a6edc148919a485e700e85af33b83202fec8fa63bb7a2a932dc8e1375efc788c1954e2f66eb1&mpshare=1&scene=1&srcid=0831OmJKjFI4YyjOB0la7Hln&sharer_sharetime=1598850806960&sharer_shareid=5ab53476a7cb89b2d672acc6f12336c2&exportkey=AxLjiFaYkfiwL7MBCIbVXb0%3D&pass_ticket=aDyoYaRZ4qOEcaTU%2Bm0iEWOFMo1gSehqyi9Wl22ykuLufVdquAp%2FucVDc9dhevm5&wx_header=0#rd)求众数
    1. 对抗阶段：分属两个候选人的票数进行两两对抗抵消
    2. 计数阶段：计算对抗结果中最后留下的候选人票数是否有效

### Answer

#### Time Complexity $(Big O Notation)$

- $O(n)$

#### Space Complexity $(Big O Notation)$

- $O(1)$

#### Code `Boyer–Moore majority vote algorithm`

~~~C++
class Solution {
public:
    int majorityElement(vector<int>& nums) {
        int target = 0, count = 0;
        for (auto num: nums) {	//类似于python的for num in nums:
            if (count == 0) target = num;	//重新指定候选人
            if (target == num) count++;
            else count--;
        }
    return target;
    }
};
~~~

