---
title: 剑指offer笔记
date: 2017-06-05 14.42.00
tags: [algorithm,data structure]
keywords: 算法，剑指offer
---

## 剑指offer题目

> 记录是为了更好的回顾，没有回顾的记录，等于没有记录。
---
### 目录

- [面试题2：实现Singleton模式](https://github.com/fanjiangqi/AlgorithmOffer/blob/master/src/main/java/Singleton1.java)
- [面试题11：数值的整数次方](https://github.com/fanjiangqi/AlgorithmOffer/blob/master/src/main/java/Power.java)，需要分指数正负和0的情况讨论，以及主要浮点数相等的判断，不能直接使用 == 来判断
- [面试题12：打印1到最大的n位数](https://github.com/fanjiangqi/AlgorithmOffer/blob/master/src/main/java/Test12.java)
  + 大数问题，**用char[] 解决**，思路很指定借鉴
  + char 类型的 ascii码，和 两个方法int Character.digit(char ch, int radix), char Character.forDigit(int digit, int radix) 
- [面试题12：在O(1)时间内删除链表结点](https://github.com/fanjiangqi/AlgorithmOffer/blob/master/src/main/java/Test13.java)
  + 把要删除的下一个结点复制到删除节点上，删除下一个节点。从而实现O(1)复杂度
  + 此方法只能删除非尾节点，尾节点还需要通过遍历的方法，找到尾节点的前一个结点
- [面试题16：反转链表](https://github.com/fanjiangqi/AlgorithmOffer/blob/master/src/main/java/Test16.java)
  + **很基础，很基础，需要记住**
- [面试题17：合并两个排序的链表](https://github.com/fanjiangqi/AlgorithmOffer/blob/master/src/main/java/Test17.java)
  + **递归解决，不然会很复杂**
- [面试题18：树的子结构](https://github.com/fanjiangqi/AlgorithmOffer/blob/master/src/main/java/Test18.java)
  + 前序变量和递归的使用，*第一次没做出来*
---
### 第四章 解决面试题的思路
- [面试题19：二叉树的镜像](https://github.com/fanjiangqi/AlgorithmOffer/blob/master/src/main/java/Test18.java)
  + 递归解决，要细心
- [面试题24：二叉树的后序遍历序列](https://github.com/fanjiangqi/AlgorithmOffer/blob/master/src/main/java/Test24.java)
  + 递归，递归中止条件
- [面试题28：字符串的排列](https://github.com/fanjiangqi/AlgorithmOffer/blob/master/src/main/java/Test28.java),2017.6.22
  + permutation 问题， 回溯法
- [面试题30: 最小的K个数](https://github.com/fanjiangqi/AlgorithmOffer/blob/master/src/main/java/Test30.java),2017.6.23
  + **很经典的问题** 2中方法解决
- [面试题31：连续子数组的最大和](https://github.com/fanjiangqi/AlgorithmOffer/blob/master/src/main/java/Test30.java),2017.6.23
  + **dp[i]定义为，以第 i 个元素结尾的连续子数组的最大和**
- [面试题34：丑数](https://github.com/fanjiangqi/AlgorithmOffer/blob/master/src/main/java/Test34.java),2017.6.28
- [面试题35：第一个出现一次的字符](https://github.com/fanjiangqi/AlgorithmOffer/blob/master/src/main/java/Test35.java),2017.6.28
 
 ---
 ## 编程之美
- [题目3.1：字符串移位包含问题](https://github.com/fanjiangqi/AlgorithmOffer/blob/master/src/main/java/beautyOfProgramming/Chapter3_1.java)
  + 2中方法： 1. 暴力搜索，一次移位一个然后判断，其实暴力搜索有时也不是那么容易想到 2. s的位移后所有字符串都是 ss（组合）字符串的子字符串
  + 主要是java strStr方法的编写
- [题目3.8：求二叉树中节点的最大距离](https://github.com/fanjiangqi/AlgorithmOffer/blob/master/src/main/java/beautyOfProgramming/BinaryTreeMaxDistance.java)
  + 分治法，构建返回结果的数据结构
  + 很好的一题，多看看，思考，[参考资料](http://www.cnblogs.com/miloyip/archive/2010/02/25/binary_tree_distance.html)
