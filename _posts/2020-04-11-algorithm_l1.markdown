---
layout:     post
title:      "九章算法笔记"
subtitle:   " 第一课 "
date:       2020-04-14 12:00:00
author:     "Yida"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - 九章
    - Algorithm
---

> “Yeah It's on. ”

### 面试常见问题
#### 常见错误 1： 简单问题
简单题基本上是一个热门问题， 不应该很难。 

比如从一个字符串中找另一个字符串，往往不需要考虑KMP算法（source n , target m, KMP O(n + m)）。 对于该题，
基本上两个for循环就可以了（遍历长字符每一个字符，对比短字符的每一个字符， O(n * m)）。

面试心得：
* **面试时，一定要从最简单的算法做起， 不要从最难的方法开始。**
    * 万一做不出来怎么办？ 
    * 告诉面试官你刷题，装也要装一装。 
* **不要刷特别难得题**

#### 常见错误 2： 代码风格
代码是工程师的一张脸, 命名风格， 很重要
* Java if 只有一句也要加 {} 空格
* 空格问题：
    * 二元运算符左右两边都要加空格， 
    * 分号前面不叫空格，后面要要加空格
    * 单元运算符不要加空格。

#### 常见错误 3： Bug free 
* 要判空，不想要bug.
* (i + j) 访问任何数字的下表，要考虑是否越界的问题

### 常见误区

* 算法想出来，代码没写完肯定没戏。 必须实现才能算完成，所以不要一直都说，程序写不完。 
* 代码写出来后，不一定能过。 coding style, bug, and logic
* 题目不会的时候直接说不会？可以google

### 面试官眼中的求职者

你可能是面试官后未来的同事。因此会着重考虑
* 你写的代码舒服么？ 需要多长时间来Review你的代码
* 你的Coding习惯好么？ 你会不会动不动就搞挂网站，造成损失
* 和你交流要舒服。是不是很难和你合作。 是人的打分， 不是机器打分。 因此要表现的Nice 
* Follow up question 是很正常的， 不要觉得他问难你。

### 刷题技巧及主要经验

* 编程完了之后要认真的检查一下， 最后一步才是LintCode编译。每道题的平均提交次数是一个很重要的指标，体现出bug free的能力，基本上小于3会比较好
* 每道题要吃透， 不能以量取胜。 重新写一遍，可以加一个收藏。 
* 可能的一个资料（Cracking the Coding Interview: 189 Programming Questions and Solutions）
* 找出相似的合适同一类型的题目的模板程序，比如宽度优先搜索，深度优先搜索，二分法， 排序。 这种基础的程序应该直接写出来而不是思考，这样会浪费时间。

### 为什么考算法
可以完成一段代码， 来看你的编程能力。 

### 排列和组合
Subsets 给出所有子集， 换句话说就是给出所有组合。 例如 给【1， 2， 3】 给出所有的子集。

* 数据范围不会很大，因为是2的n次方。因此数据量不会很大，不用担心递归的空间复杂度问题。 

* 搜索问题的时间复杂度 O(答案的个数 * 构造每个答案的时间) 
    * 组合问题 O(2^n * n)
        * 有 2^n 个答案
        * 每个答案至少得看一遍 n
    * permutation 所有去全排列 O(n * n!)

#### 深度优先搜索。

* 整体思想是：不撞南墙不回头，撞了南墙就回头
* 怎么避免重复状态的搜索。 
    * 错误的想法，用Hash表技术某一个东西是否存在， 这样的做法往往是效率不好的。
    * 制定规则， 选代表， 选一个好看的（有序的）
        * 集合的加的数字，小的数字不能再大的数字后面加。 
* 回溯 backtracking = DFS 
    * 加进去的东西，要吐出来。 
* 递归的算法其实就是由大到小的解决问题。 把大问题分解成小问题（Recursion）
整个问题是四个部分。 

#### 经验总结
* 
 
 ```java

class Solution{

    // 对外结构 interface 
    public Arraylist<ArrayList<Integer>> subset(int[] nums){
        ArrayList<ArrayList<Integer>> results = new ArrayList<>();
        if (nums == null || nums.length = 0)
        { 
            return results
         }
        // 找到所有 [] 开头的子集，放到results里
        helper(results, new ArrayList<Integer>(), nums, 0);
        return results;        

    }
    
    // 1. 递归的定义， 接收什么样的参数，返回什么值， 做了什么事。 
    
    // 找到所有以subset开始的子集， 然后丢到results里面去。
    // 不要超过这个字符， 写在一行并且对其。 
    private void helper(ArrayList<Integer> subset, 
                        ArrayList<ArrayList<Integer>> results, 
                        int[] nums,
                        int statrIndex) {
        
        // 2. 递归的拆解
        // soft copy (reference)
        results.add(subsets);  //这样写是不对的。 因为subset一直在变化。
        resutls.add(subset) []
        resutls.add(subset) [[]]
        results.add(subset)
        subset = [1]
        results.add(new ArrayList<Integer>(subset));
        for (int i = startIndex, i < nums.length; i ++){
            subset.add(nums[i]) //[]->[1] or [1] -> [1, 2]
            // 比如开始为1， 找到所有以1，2 开始的
            helper(results, subset, nums, i + 1)
            subset.remove(subset.size() - 1); //把1， 2， 变成 1， 3
            //做了什么全部撤销。
        }
        // 自然而然退出。 
    
        // 3. 递归的出口， 自然而且的出口。 什么时候不往下递归，可以直接找到答案退出。 
    }

}


```
不要轻易的点击提交按钮。 搜索问题是考的是基本功。 怎么看是深度优先搜索， 题目中的关键字是 all possible solution 所有的
可能性那么就是搜索。 
https://www.cnblogs.com/zcy-backend/p/6675158.html
https://www.zybuluo.com/nalan90/note/1170566