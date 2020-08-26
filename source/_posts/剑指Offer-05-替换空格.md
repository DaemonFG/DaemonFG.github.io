---
title: 剑指 Offer 05. 替换空格
top: false
cover: false
toc: true
mathjax: true
date: 2020-08-26 09:53:13
password:
summary:
tags: String
categories: 剑指Offer
---

### [剑指 Offer 05. 替换空格](https://leetcode-cn.com/problems/ti-huan-kong-ge-lcof/)

请实现一个函数，把字符串 s 中的每个空格替换成"%20"。

- 示例

  ~~~
  输入：s = "We are happy."
  输出："We%20are%20happy."
  ~~~

- 限制：

  ~~~
  0 <= s 的长度 <= 10000
  ~~~

#### 思路

- 统计空格数count
- 用resize对字符串进行扩容
- c从后往前，双指针查找位置，并替换

#### Answer

##### Time Complexity $(Big O Notation)$

- $O(n)$

##### Space Complexity $(Big O Notation)$

- $O(1)$

##### Code

~~~C++
class Solution {
public:
    string replaceSpace(string s) {
        int count = 0;	
        int oldSize = s.size();
        for (int i = 0; i < oldSize; i++) {
            if (s[i] == ' ') count++;	//统计空格数量
        }
        s.resize(s.size() + count * 2);		//字符串扩容
        int newSize = s.size();
        for (int i = oldSize - 1, j = newSize - 1;i < j;i--,j--) {
            if (s[i] != ' ') s[j] = s[i];	//旧位置移到新位置
            else {
                s[j] = '0';
                s[j-1] =  '2';
                s[j-2] = '%';
                j -= 2;		//*
            }
        }
        return s;
    }
};
~~~

