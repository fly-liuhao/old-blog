---
title: LeetCode01-两数之和
top_img: true
comments: true
toc: true
toc_number: true
copyright: true
hide: false
date: 2020-02-22 17:55:20
tags:
	- LeetCode
	- 算法
categories: LeetCode
keywords: "LeetCode, 算法"
description: LeetCoded算法题
cover: https://sheey-blog-resources.oss-cn-hangzhou.aliyuncs.com/images/background.png
mathjax:
katex:
---

#### 题目描述
给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。

你可以假设每种输入只会对应一个答案。但是，你不能重复利用这个数组中同样的元素。

示例:
```java
给定 nums = [2, 7, 11, 15], target = 9

因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]
```
来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/two-sum



#### 代码

- 方法一
    > 暴力法，两层for循环，第一层控制第一个加数，第二层控制第二个加数，当 i,j 不相等的时候进行判断
    ```java（暴力法）
    class Solution {
        public int[] twoSum(int[] nums, int target) {
            for(int i = 0; i < nums.length; i++) {
                for(int j = 0; j < nums.length; j++) {
                    if(i != j) {
                        if((nums[i] + nums[j]) == target) {
                           return new int[] {i, j};
                        }
                    }
                }
            }
            throw new IllegalArgumentException("No two sum solution");
        }
    }
    ```
- 方法二（Hash表）
    > 首先构造一个哈希表，将数组中的数存放到map中去（key是数组元素的值，value是数组下标）
    > 然后从左到右遍历，判断target -num[i]是否在map中（并且要添加条件 map.get(temp) != i 防止使用同一个数），存在则返回 i 以及 temp对应的数组下标也就是map中对应temp的value值。
    ```java
    class Solution {
        public int[] twoSum(int[] nums, int target) {
            Map<Integer, Integer> map = new HashMap<Integer, Integer>();
            for(int i=0; i<nums.length; i++) {
                map.put(nums[i], i);
            }
            for(int i=0; i<nums.length; i++) {
                int temp = target - nums[i];
                if(map.containsKey(temp) && map.get(temp)!=i) {
                    return new int[] {i, map.get(temp)};
                }
            }
            throw new IllegalArgumentException("No two sum solution");
        }
    }
    ```
- 方法三（Hash表）
    > 与上面方法类似，只不过没有一开始就初始化map，随着程序的进行逐步加入到map中去，拿未加入的与已加入的做比较（可以省去判断是否为同一个数的那个条件）
    ```java
    class Solution {
        public int[] twoSum(int[] nums, int target) {
            Map<Integer, Integer> map = new HashMap<Integer, Integer>();
            for(int i=0; i<nums.length; i++) {
                int temp = target - nums[i];
                if(map.containsKey(temp)) {
                    return new int[] {i, map.get(temp)};
                }
                map.put(nums[i], i);
            }
            throw new IllegalArgumentException("No two sum solution");
        }
    }
    ```