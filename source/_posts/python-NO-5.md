---
title: python-NO-5
categories:
  - Learn
comments: ture
date: 2020-10-15 23:10:55
tags:
  - python
---

# 函数式编程
函数式编程的一个特点就是，允许把函数本身作为参数传入另一个函数，还允许返回一个函数！
## 高阶函数
- 变量可以指向函数
- 函数名也是变量    

一个函数就可以接收另一个函数作为参数，这种函数就称之为高阶函数
### map()函数
根据提供的函数对指定序列做映射
`map(function, iterable, ...)`
-  function -- 函数
-  iterable -- 一个或多个序列   

### reduce()函数
对参数序列中元素进行累积
`reduce(function, iterable[, initializer])`
- function -- 函数，有两个参数
- iterable -- 可迭代对象
- initializer -- 可选，初始参数

```
from functools import reduce

DIGITS = {'0': 0, '1': 1, '2': 2, '3': 3, '4': 4, '5': 5, '6': 6, '7': 7, '8': 8, '9': 9}

def str2int(s):
    def fn(x, y):
        return x * 10 + y
    def char2num(s):
        return DIGITS[s]
    return reduce(fn, map(char2num, s))
```