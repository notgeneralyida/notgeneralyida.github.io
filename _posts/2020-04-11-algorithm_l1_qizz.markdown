---
layout:     post
title:      "九章算法笔记-刷题"
subtitle:   " 第一课 "
date:       2020-04-15 12:00:00
author:     "Yida"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - 九章
    - Algorithm
    - Coding
---

> “Yeah It's on. ”

### 13. Implement strStr()

#### 题目

For a given source string and a target string, you should output the first index(from 0) of target string in source string.

If target does not exist in source, just return -1.

#### 解法

暴力算法，一个 for 循环，加一个while 循环。 
* 注意数组边界的问题，因此是range(source_len - target_len + 1)。 访问数组的时候一定要注意越界的问题。
* 注意特殊情况，None. 因此要有 if target is None or source is None 语句。
* 三不要用source[i, i + target_len] == target 来代替while 循环
    * 可能会引入边界问题
    * 算法复杂度会高一些 （总考虑最坏情况）

```python
class Solution:
    """
    @param source: 
    @param target: 
    @return: return the index
    """
    def strStr(self, source, target):
        # Write your code here
        if source is None or target is None:
            return -1

        source_len = len(source)
        target_len = len(target)
        
        for i in range(source_len - target_len + 1):
            j = 0
            while (j < target_len):
                if source[i + j] != target[j]:
                    break 
                j += 1 
                
            if j == target_len:
                return i 
        return -1 
        

```
