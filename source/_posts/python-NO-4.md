---
title: python-NO-4
categories:
  - Learn
comments: ture
date: 2020-10-05 22:06:58
tags:
 - python
---
# 高级特性
## 切片
**取一个list或tuple的部分元素**  

   
```
L = ['Michael', 'Sarah', 'Tracy', 'Bob', 'Jack']
L[0:3]  #从索引0开始取，直到索引3为止，但不包括索引3
L[:3]   #索引是0，可以省略
L[-2:-1]  #索引倒数第2个，到倒数第1个，倒数第一个元素的索引是-1
L[::5]   #所有数，每5个取一个
L[:]   #原样复制一个
```
***

## 迭代
**遍历我们称为迭代**  
**可迭代对象:** 通过collections模块的Iterable类型判断      

```
from collections import Iterable
isinstance('abc', Iterable) # str是否可迭代
isinstance([1,2,3], Iterable) # list是否可迭代
```
    
Python内置的`enumerate`函数可以把一个list变成索引-元素对，这样就可以在for循环中同时迭代索引和元素本身

```
>>> for i, value in enumerate(['A', 'B', 'C']):
...     print(i, value)
...
0 A
1 B
2 C
```
   
 ***  
## 列表生成式
创建list的生成式
```
#[1x1, 2x2, 3x3, ..., 10x10]
>>> [x * x for x in range(1, 11)]
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```

for循环后面还可以加上if判断，if是一个筛选条件，不能带else
```
>>> [x * x for x in range(1, 11) if x % 2 == 0]
[4, 16, 36, 64, 100]
```
for前面的if ... else是表达式
```
>>> [x if x % 2 == 0 else -x for x in range(1, 11)]
[-1, 2, -3, 4, -5, 6, -7, 8, -9, 10]
```
使用两层循环
```
>>> [m + n for m in 'ABC' for n in 'XYZ']
['AX', 'AY', 'AZ', 'BX', 'BY', 'BZ', 'CX', 'CY', 'CZ']
```
***
## 生成器
一边循环一边计算的机制，称为生成器，保存的是算法。  
函数：
```
#斐波拉契数列 1, 1, 2, 3, 5, 8, 13, 21, 34, ...
def fib(max):
    n, a, b = 0, 0, 1
    while n < max:
        print(b)
        a, b = b, a + b
        n = n + 1
    return 'done'
```
生成器函数：
```
#如果一个函数定义中包含yield关键字，那么这个函数就不再是一个普通函数，而是一个生成器
def fib(max):    
    n, a, b = 0, 0, 1
    while n < max:
        yield b
        a, b = b, a + b
        n = n + 1
    return 'done'
#在每次调用next()的时候执行，遇到yield语句返回，再次执行时从上次返回的yield语句处继续执行
```
***   
## 迭代器
访问集合元素的一种方式，是一个可以记住遍历的位置的对象。迭代器对象从集合的第一个元素开始访问，直到所有的元素被访问完结束。迭代器只能往前不会后退。
---
方法|功能
---|---
iter()|创建迭代器对象
next()|输出迭代器的下一个元素
---
凡是可作用于for循环的对象都是可迭代对象;
凡是可作用于next()函数的对象都是迭代器;
