---
title: Numpy基础
date: 2019-08-04 22:30:00
img: https://gitee.com/wenguang0816/blogPic/raw/master/20190804-1.jpg
summary: Numpy基础
categories: 分享
tags:
  - Numpy
---
## 安装Numpy
```bash
pip install numpy
pip install pandas
```

## 导入Numpy
```python
# 导入numpy
import numpy as np
```
## Numpy属性
+ ndim：纬度
+ shape：行数和列数
+ size：元素个数

## Numpy创建array

### 关键字
+ array：创建数组
+ dtype：指定数据类型
+ zeros：创建数据全为0
+ ones：创建数据全为1
+ empty：创建数据接近于0
+ arange：按指定范围创建数据
+ linspace：创建线段

### 创建数组
1. 指定数组
```python
# 2维矩阵，2行3列
a = np.array([[1, 2, 3],[2, 3, 4]])
```
2. 全零数组
```python
# 2维矩阵，2行3列
a = np.zeros((3,4)) # 数据全为0，3行4列
'''
[[0. 0. 0. 0.]
 [0. 0. 0. 0.]
 [0. 0. 0. 0.]]
'''
```
3. 全一数组
```python
# 2维矩阵，2行3列
a = np.ones((3,4), dtype = np.int) # 数据全为1，3行4列，数据类型为int
'''
[[0. 0. 0. 0.]
 [0. 0. 0. 0.]
 [0. 0. 0. 0.]]
'''
```
4. 全空数组
```python
# 2维矩阵，2行3列
a = np.empty((3,4)) # 数据为empty，接近于0，3行4列
'''
[[ 1.72723371e-077 -4.32976793e-311  2.96439388e-323  0.00000000e+000]
 [ 0.00000000e+000  0.00000000e+000  0.00000000e+000  0.00000000e+000]
 [ 0.00000000e+000  0.00000000e+000  0.00000000e+000  8.34402697e-309]]
'''
```
5. 创建连续数组
```python
# 2维矩阵，2行3列
a = np.arange(10, 20, 2) # 10-19的数据，2步长
'''
[10 12 14 16 18]
'''
```
6. 用`reshape`改变数组形状
```python
# 2维矩阵，2行3列
a = np.arange(12).reshape((3, 4)) # 10-19的数据，2步长
'''
[[ 0  1  2  3]
 [ 4  5  6  7]
 [ 8  9 10 11]]
'''
```
7. 创建线段型数组
```python
# 2维矩阵，2行3列
a = np.linspace(1, 10, 20).reshape(5, 4) # 10-19的数据，2步长
'''
[[ 1.          1.47368421  1.94736842  2.42105263]
 [ 2.89473684  3.36842105  3.84210526  4.31578947]
 [ 4.78947368  5.26315789  5.73684211  6.21052632]
 [ 6.68421053  7.15789474  7.63157895  8.10526316]
 [ 8.57894737  9.05263158  9.52631579 10.        ]]
'''
```

## Numpy基础运算
```python
a = np.array([10, 20, 30, 40])
b = np.arange(4)
```

### 加减乘除
```python
c = a + b # array([10, 21, 32, 43])
c = a - b # array([10, 19, 28, 37])
c = a * b # array([0, 20, 60, 120])
c = a / b # array([inf, 20, 15, 13.33333333])
```

### 函数运算
```python
c = b ** 2 # 乘方运算 array([0, 1, 4, 9])
c = 10 * np.sin(a) # sin函数 array([-5.44021111, 9.12945251, -9.88031624, 7.4511316 ])
print(b < 3) # 逻辑运算 array([ True, True, True, False])

```

### 矩阵运算
```python
# 符合数学矩阵运算
a = np.array([[1, 1], [0, 1]])
b = np.array([[0, 1], [2, 3]])
c_dot = np.dot(a, b)
# 另一种写法
c_dot_2 = a.dot(b)
print(c_dot)
'''
[[2 4]
 [2 3]]
'''
```

### sum、min、max
`sum()`对数组所有元素求和，`min()`寻找数组最小值，`max()`寻找数组最大值
```python
a = np.arange(12).reshape((3, 4))
'''
[[ 0  1  2  3]
 [ 4  5  6  7]
 [ 8  9 10 11]]
'''
print(np.sum(a)) # 数组所有元素求和
print(np.min(a)) # 数组中的最小元素
print(np.max(a)) # 数组中的最大元素
'''
66
0
11
'''
```
如果要对行或列单独操作，则可以为`axis`参数赋值，当`axis = 1`时，将会以行作为查找单元，`axis = 0`时，将会以列作为查找单元
```python
print(np.sum(a, axis = 1))
print(np.min(a, axis = 1))
print(np.max(a, axis = 1))
'''
[ 6 22 38]
[0 4 8]
[ 3  7 11]
'''
print(np.sum(a, axis = 0))
print(np.min(a, axis = 0))
print(np.max(a, axis = 0))
'''
[12 15 18 21]
[0 1 2 3]
[ 8  9 10 11]
'''
```

### 其他运算
1. `argmin()`返回矩阵中最小元素的索引，`argmax()`返回矩阵中最大元素的索引
    ```python
    a = np.arange(12).reshape((3, 4))
    print(a)
    print(np.argmin(a)) # 最小元素的索引
    print(np.argmax(a)) # 最大元素的索引
    '''
    [[ 0  1  2  3]
    [ 4  5  6  7]
    [ 8  9 10 11]]
    0
    11
    '''
    ```
2. `mean()`和`average()`返回矩阵的平均值
    ```python
    print(np.mean(a)) # 5.5
    print(a.mean()) # 另一种写法
    print(np.average(a)) # 5.5
    ```
3. `cumsum()`累加函数
   ```python
   # cumsum()函数生成的每一项矩阵元素均是从原矩阵首项累加到对应项的元素之和
   print(np.cumsum(a)) # [ 0  1  3  6 10 15 21 28 36 45 55 66]
   ```
4. `diff()`累差函数
   ```python
   # 该函数计算的是每一行中后一项与前一项之差，所以3x4的矩阵通过函数计算后得到3x3的矩阵
   print(np.diff(a))
   '''
   [[1 1 1]
    [1 1 1]
    [1 1 1]]
   '''
   ```
5. 矩阵转置
   ```python
   print(np.transpose(a))
   print(a.T)
   '''
   [[ 0  4  8]
    [ 1  5  9]
    [ 2  6 10]
    [ 3  7 11]]
   '''
   ```

## Numpy索引

### 一维索引
```python
# 和数组索引类似
a = np.arange(12)
print(a)
print(a[3])
'''
[ 0  1  2  3  4  5  6  7  8  9 10 11]
3
'''

b = np.arange(12).reshape(3,4)
print(b)
'''
[[ 0  1  2  3]
 [ 4  5  6  7]
 [ 8  9 10 11]]
'''
print(b[1]) # 打印矩阵第1行（从0起算）
'''
[4 5 6 7]
'''
```
### 二维索引
```python
# 和python二维list相似
b = np.arange(12).reshape(3,4)
print(b[1][1])
print(b[1, 1]) # 另一种写法
print(b[1, 1:3]) # 同时支持切片处理
'''
5
5
[5 6]
'''
```
### 行列遍历以及迭代
```python
a = np.arange(12).reshape(3, 4)
# 按行遍历
for row in a:
    print(a)
'''
[0 1 2 3]
[4 5 6 7]
[8 9 10 11]
'''
# 按列遍历：将矩阵转置后遍历行
for column in a.T:
    print(column)
'''
[0 4 8]
[1 5 9]
[2 6 10]
[3 7 11]
'''
# 迭代
# flatten()是一个展开性质的函数，将多维矩阵展开为1行数列
print(a.flatten())
'''
[ 0  1  2  3  4  5  6  7  8  9 10 11]
'''
# flat迭代器
for item in a.flat:
    print(item)
'''
1
2
...
11
'''
```
## array合并
```python
a = np.array([1, 2, 3])
b = np.array([4, 5, 6])
# vstack()将两个array上下合并，列数必须相同
c = np.vstack((a, b))
print(c)
'''
[[1 2 3]
 [4 5 6]]
'''
# hstack()将两个array左右合并，行数必须相同
d = np.hstack((a, b))
print(d)
'''
[1 2 3 4 5 6]
'''
# 对于a序列来说，其并不是矩阵，需要通过新的方式进行转置
print(a[np.newaxis, :])
'''
[[1 2 3]]
'''
print(a[:, np.newaxis])
'''
[[1]
 [2]
 [3]]
'''
# 合并多个矩阵或序列时，使用concatenate()更方便
a = np.array([1, 2, 3])[:, np.newaxis]
b = np.array([4, 5, 6])[:, np.newaxis]
# axis = 0纵向合并
c = np.concatenate((a, b, b, a), axis = 0)
print(c)
'''
[[1]
 [2]
 [3]
 [4]
 [5]
 [6]
 [4]
 [5]
 [6]
 [1]
 [2]
 [3]]
'''
# axis = 1横向合并
d = np.concatenate((a, b, b, a), axis = 1)
print(d)
'''
[[1 4 4 1]
 [2 5 5 2]
 [3 6 6 3]]
'''
```
## array分割
### 纵向分割
```python
# 纵向分割，即按列分割，分割数量必须是列数的公约数（列数能整除分割数）
a = np.arange(12).reshape(3, 4)
# 第二个参数为分割数量，第三个参数表示纵向分割(按列分割)
print(np.split(a, 2, axis=1))
'''
[array([[0, 1],
       [4, 5],
       [8, 9]]), array([[ 2,  3],
       [ 6,  7],
       [10, 11]])]
'''
```
### 横向分割
```python
# 横向分割，即按行分割，分割数量必须是行数的公约数（行数能整除分割数）
# 第二个参数为分割数量，第三个参数表示横向分割(按行分割)
print(np.split(a, 3, axis=0))
'''
[array([[0, 1, 2, 3]]), array([[4, 5, 6, 7]]), array([[ 8,  9, 10, 11]])]
'''
```
### 不等量分割
```python
# 将4列矩阵不等量分割为3个矩阵
print(np.array_split(a, 3, axis=1))
'''
[array([[0, 1],
       [4, 5],
       [8, 9]]), array([[ 2],
       [ 6],
       [10]]), array([[ 3],
       [ 7],
       [11]])]
'''
```
### 其他分割方式
```python
# 横向分割
print(np.vsplit(a, 3)) # 等同于print(np.split(a, 3, axis=0))
'''
[array([[0, 1, 2, 3]]), array([[4, 5, 6, 7]]), array([[ 8,  9, 10, 11]])]
'''
# 纵向分割
print(np.hsplit(a, 2)) # 等同于print(np.split(a, 2, axis=1))
'''
[array([[0, 1],
       [4, 5],
       [8, 9]]), array([[ 2,  3],
       [ 6,  7],
       [10, 11]])]
'''
```
## 浅拷贝和深拷贝
### 浅拷贝
> 拷贝了最外围的对象本身，内部的元素都只是拷贝了一个引用而已。也就是，把对象复制一遍，但是该对象中引用的其他对象不复制

`=`的赋值方式带有关联性
```python
a = np.arange(4)
b = a
c = b
# a的值改变，b，c的值会同时改变
a[0] = 11
print(a, b, c)
'''
[11  1  2  3] [11  1  2  3] [11  1  2  3]
'''
```
### 深拷贝
> 外围和内部元素都进行了拷贝对象本身，而不是引用。也就是，把对象复制一遍，并且该对象中引用的其他对象也复制。
`copy()`的方式没有关联性
```python
d = a.copy()
print(d)
# a的值改变，d的值不会改变
a[3] = 44
print(a)
print(d)
'''
[11  1  2  3]
[11  1  2 44]
[11  1  2  3]
'''
```