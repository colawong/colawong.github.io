---
title: python-NO-3
categories:
  - Learn
comments: ture
date: 2020-10-04 20:27:04
tags:
  - python
---

# 函数
## 调用函数 
所有函数见[官方网站文档](https://docs.python.org/3/library/functions.html#abs)

## 定义函数
定义一个函数要使用`def`语句，依次写出函数名、括号、括号中的参数和冒号:，然后，在缩进块中编写函数体，函数的返回值用`return`语句返回
```
def 函数名():
    函数体
    return
```
### 空函数
一个什么事也不做的空函数，可以用`pass`语句
```
def 函数名():
    pass
```
#### 返回值

1. 函数执行完毕也没有return语句时，自动return None。

2. 函数可以同时返回多个值，但其实就是一个tuple

#### 参数
1. 位置参数：调用函数时根据函数定义的参数位置来传递参数
   ```
   def power(x, n):   #用来计算xn ;x,n都为位置参数
    s = 1
    while n > 0:
        n = n - 1
        s = s * x
    return s
   ```
2. 默认参数：为参数提供默认值，调用函数时可传可不传该默认参数的值（注意：所有位置参数必须出现在默认参数前，包括函数定义和调用）
   ```
    def power(x, n=2):  #默认计算x2
      s = 1
      while n > 0:
        n = n - 1
        s = s * x
      return s
   ```
    *默认参数必须指向不变对象*
3. 可变参数：可变参数就是传入的参数个数是可变的。可变参数允许你传入0个或任意个参数，这些可变参数在函数调用时自动组装为一个tuple。
    ```
    def calc(*numbers): #*号代表可变参数
      sum = 0
      for n in numbers:
        sum = sum + n * n
      return sum
    ```
   `*tuple`号可将list或tuple转为可变参数
4. 关键参数：关键字参数允许你传入0个或任意个含参数名的参数，这些关键字参数在函数内部自动组装为一个dict。**作用：***可以扩展函数的功能*
   ```
   def person(name, age, **kw):  #**号表示关键字参数
    print('name:', name, 'age:', age, 'other:', kw)
   ```
   `**dict`可将dict的所有key-value用关键字参数传入
5. 命名关键字参数:限制关键字参数的名字
   ```
    def person(name, age, *, city, job):   #命名关键字参数需要一个特殊分隔符*，*后面的参数被视为命名关键字参数
        print(name, age, city, job)
    ```

   *缺少`*`，city和job被视为位置参数*
6. 参数组合：参数定义的顺序必须是：必选参数、默认参数、可变参数、命名关键字参数和关键字参数
    ```
    def f1(a, b, c=0, *args, **kw):
      print('a =', a, 'b =', b, 'c =', c, 'args =', args, 'kw =', kw)

    def f2(a, b, c=0, *, d, **kw):
      print('a =', a, 'b =', b, 'c =', c, 'd =', d, 'kw =', kw)
    ```

## 递归函数
一个函数在内部调用自身本身，这个函数就是递归函数。    

              
```
#  阶乘
def fact(n):
    if n==1:
        return 1
    return n * fact(n - 1)
```    
**栈：** 函数调用是通过栈（stack）这种数据结构实现的，每当进入一个函数调用，栈就会加一层栈帧，每当函数返回，栈就会减一层栈帧   
**尾递归优化：** *解决递归调用栈溢出*   
```
def fact(n):
    return fact_iter(n, 1)

def fact_iter(num, product):
    if num == 1:
        return product
    return fact_iter(num - 1, num * product)   #返回递归函数本身
```
    

  

## 说明
```
from 文件名 import 函数名
```
