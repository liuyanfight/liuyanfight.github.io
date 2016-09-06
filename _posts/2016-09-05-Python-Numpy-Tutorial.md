---
layout: post
title: "Python Numpy Tutorial"
subtitle: "Computer Vision Software"
date: 2016-09-05
author: L
category: Computer Vision
tags: ML 学习 CV DL Python Sydney
finished: true
---
> These notes accompany the Stanford CS class CS231n: Convolutional Neural Networks for Visual Recognition.

- Numpy有Matlab版。

## Python
- Python is a high-level, dynamically typed multiparadigm programming language.

### [Basic data types](https://docs.python.org/2/library/stdtypes.html#numeric-types-int-float-long-complex)
- __Numbers__
  - `type()`显示字符类型
  - 没有  ++ 和 --
- __Booleans__
  - 使用 `and or not`而不是&& ! 等
- [__Strings__](https://docs.python.org/2/library/stdtypes.html#string-methods)
  - 可以使用单引号或双引号
  - `len()`显示字符串长度
  - 使用 `+` 用于字符串拼接
  - `hw12 = '%s %s %d' % (hello, world, 12)` 字符串格式化
  - String类型有很多方法

    ```
    s = "hello"
    print s.capitalize() # Capitalize a string; prints "Hello"
    print s.upper() # Convert a string to uppercase; prints "HELLO"
    print s.rjust(7) # Right-justify a string, padding with spaces; prints
    print s.center(7) # Center a string, padding with spaces; prints " hello
    print s.replace('l', '(ell)') # Replace all instances of one substring with
    # prints "he(ell)(ell)o"
    print ' world '.strip() # Strip leading and trailing whitespace; pr
    ```

### Containers
- 包含Lists，Dictionaries，settings，Tuples 几种类型

#### [Lists](https://docs.python.org/2/tutorial/datastructures.html#more-on-lists)
- `xs=[3,1,2]`创建list
- list可以包含不同类型的元素
- list可以出栈和进栈操作
- __Slicing__

  ```
  nums = range(5) # range is a built-in function that creates a list of int
  print nums # Prints "[0, 1, 2, 3, 4]"
  print nums[2:4] # Get a slice from index 2 to 4 (exclusive); prints "[2,3]" 不包括第4个
  print nums[2:] # Get a slice from index 2 to the end; prints "[2, 3, 4]
  print nums[:2] # Get a slice from the start to index 2 (exclusive); prints "[0, 1]"
  print nums[:] # Get a slice of the whole list; prints ["0, 1, 2, 3, 4]
  print nums[:-1] # Slice indices can be negative; prints ["0, 1, 2, 3]"
  nums[2:4] = [8, 9] # Assign a new sublist to a slice
  print nums # Prints "[0, 1, 8, 9, 4]"
  ```

- __Loops__
  - `for ... in ... ：`
  - 枚举遍历列表`for ... in enumerate(...)：`
- List comprehensions:变换类型

  ```
  nums = [0, 1, 2, 3, 4]
  squares = []
  for x in nums:
    squares.append(x ** 2)
  # or
  squares = [x ** 2 for x in nums]
  # 包含条件
  even_squares = [x ** 2 for x in nums if x % 2 == 0]
  print squares # Prints [0, 1, 4, 9, 16]
  ```

#### [Dictionaries](https://docs.python.org/2/library/stdtypes.html#dict)
- dictionary保存一对(key, value).
- __Loops:__

  ```
  d = {'person': 2, 'cat': 4, 'spider': 8}
  for animal in d:
    legs = d[animal]
    print 'A %s has %d legs' % (animal, legs)
  # Prints "A person has 2 legs", "A spider has 8 legs",
  # "A cat has 4 legs

  # or use `iteritems`
  d = {'person': 2, 'cat': 4, 'spider': 8}
  for animal, legs in d.iteritems():
    print 'A %s has %d legs' % (animal, legs)
  # Prints "A person has 2 legs", "A spider has 8 legs",
  # "A cat has 4 legs
  ```

#### [Sets](https://docs.python.org/2/library/sets.html#set-objects)
- a set is an unordered collection of distinct elements.无序的

#### [Tuples](https://docs.python.org/2/tutorial/datastructures.html#tuples-and-sequences)
- A tuple is an (immutable不变的) ordered list of values.

### [Functions]https://docs.python.org/2/tutorial/controlflow.html#defining-functions
- `def` 定义函数

### [Classes](https://docs.python.org/2/tutorial/classes.html)
- `class ...():`

## Numpy
- Numpy is the core library for scientiAc computing in Python.
- Numpy的安装时需要源文件编译，若使用**Anaconda**则可以直接使用~

### [Arrays](http://docs.scipy.org/doc/numpy/user/basics.creation.html#arrays-creation)
- A numpy array is a grid of values.相同类型
- The number of dimensions is the rank of the array;
- the shape of an array is a tuple of integers giving the size of the array along each dimension.
- `import numpy as `导入包

### [Array indexing](http://docs.scipy.org/doc/numpy/reference/arrays.indexing.html)
- __Slicing__
  - `b = a[:2, 1:3]` 前两行，第2，3列。
  - 索引从0开始
  - 序号不包含后一个
  - 矩阵处理有点像matlab
- __Integer array indexng__ 数组索引
- __Boolean array indexing__ 判断数组条件

### [Datatypes](http://docs.scipy.org/doc/numpy/reference/arrays.dtypes.html)
- Every numpy array is a grid of elements of the same type.
- 可以强制定义类型

### Array math
- 基本的数学操作是可以在array上使用的，也可以使用方法（函数）
  - `+` np.add()
  - `-` np.subtract()
  - `*` np.multiply() 元素乘
  - `/` np.divide()
- `dot`函数用来矩阵相乘，两种形式v.dot(w), np.dot(v,w)
- `np.sum` 函数计算和。`np.sum(x, axis=0)` 列相加，axis=1行相加。没有则是全部相加。
- 更多函数见 http://docs.scipy.org/doc/numpy/reference/routines.math.html
- `x.T`转置矩阵x。 rank=1的数组不做任何变化。
- 更多对array的操作见 http://docs.scipy.org/doc/numpy/reference/routines.array-manipulation.html

### Broadcasting
- `np.tile(v,(4,1))` stack 4 copies of v on top of each other
- Numpy broadcasting allows us to perform this computation without actually creating multiple copies of `v`.

  ```python
  import numpy as np
  # We will add the vector v to each row of the matrix x,
  # storing the result in the matrix y
  x = np.array([[1,2,3], [4,5,6], [7,8,9], [10, 11, 12]])
  v = np.array([1, 0, 1])
  y = x + v # Add v to each row of x using broadcasting
  print y # Prints "[[ 2 2 4]
  # [ 5 5 7]
  # [ 8 8 10]
  # [11 11 13]]"

  # y = x + v 此公式依然有效，当x是4*3矩阵而v是3*1矩阵
  ```
- 广播(broadcasting)两个array遵循以下规则
  1. 如果array没有相同的rank，可以用1填充地址array知道两个array有相同的长度
  2. 如果两个array在同一维度有相同的大小或者其中一个array在该维度为1，则可以直接进行操作
  3. 如果arrays在所有维度都兼容可以一起广播
  4. 广播后的每个array等于最大的那个array
  5. 在任意维度，当其中一个大小为1而其他array大于1，那么前一个array填充为相同大小
  - 详见 http://docs.scipy.org/doc/numpy/user/basics.broadcasting.html
  - 或 http://scipy.github.io/old-wiki/pages/EricsBroadcastingDoc

```python
import numpy as np
# Compute outer product of vectors
v = np.array([1,2,3]) # v has shape (3,)
w = np.array([4,5]) # w has shape (2,)
# To compute an outer product, we first reshape v to be a column
# vector of shape (3, 1); we can then broadcast it against w to yield
# an output of shape (3, 2), which is the outer product of v and w:
# [[ 4 5]
# [ 8 10]
# [12 15]]
print np.reshape(v, (3, 1)) * w
# Add a vector to each row of a matrix
x = np.array([[1,2,3], [4,5,6]])
# x has shape (2, 3) and v has shape (3,) so they broadcast to (2, 3),
# giving the following matrix:
# [[2 4 6]
# [5 7 9]]
print x + v
# Add a vector to each column of a matrix
# x has shape (2, 3) and w has shape (2,).
# If we transpose x then it has shape (3, 2) and can be broadcast
# against w to yield a result of shape (3, 2); transposing this result
# yields the final result of shape (2, 3) which is the matrix x with
# the vector w added to each column. Gives the following matrix:
# [[ 5 6 7]
# [ 9 10 11]]
print (x.T + w).T
# Another solution is to reshape w to be a row vector of shape (2, 1);
# we can then broadcast it directly against x to produce the same
# output.
print x + np.reshape(w, (2, 1))
# Multiply a matrix by a constant:
# x has shape (2, 3). Numpy treats scalars as arrays of shape ();
# these can be broadcast together to shape (2, 3), producing the
# following array:
# [[ 2 4 6]
# [ 8 10 12]]
print x * 2
```
- [More about Numpy](http://docs.scipy.org/doc/numpy/reference/)

## [SciPy](http://docs.scipy.org/doc/scipy/reference/index.html)
- SciPy builds on Numpy's function, and provides a large number of functions that operate on numpy arrays and are useful for different types of scientific and engineering applications.

### Image operations
- SciPy可以导入一个image到numpy arrays，并且可以write,resize等等。
- `from scipy.misc import imread, imsave, imresize`
- `imread`读入图片
- `imresize`resize图片
- `imsave`将图片保存到本地

### [MATLAB Ales](http://docs.scipy.org/doc/scipy/reference/io.html)
- `scipy.io.loadmat`和`scipy.io.savemat`可以读写Matlab文件

### Distance between points
- `scipy.spatial.distance.pdist`计算一个给定数据集中所有点的距离
- http://docs.scipy.org/doc/scipy/reference/generated/scipy.spatial.distance.pdist.html
- `scipy.spatial.distance.cdist`计算两个数据集之间的距离
- http://docs.scipy.org/doc/scipy/reference/generated/scipy.spatial.distance.cdist.html

## Matplotlib
- 画图的库，与Matlab相似

### [Plotting](http://matplotlib.org/api/pyplot_api.html#matplotlib.pyplot.plot)
- `import matplotlib.pyplot as plt`
- `plt.plot` 作图
- `plt.show` 显示图像

### Subplots
- [子图](http://matplotlib.org/api/pyplot_api.html#matplotlib.pyplot.subplot)

### Images
- `imshow`显示图像
- 有些图像不是uint8格式可能会导致图像效果不好，这时，可以强制给定uint8来显示。`plt.imshow(np.uint8(img_tinted))`

## Finished at 2016-09-06 18:18 Sydney
