# 第五天

# 1.11 序列

## 序列定义

* 序列指的是一块可存放多个值的连续内存空间，这些值按一定顺序排列，可通过每个值所在位置的编号（称为索引）访问它们
* 在 [Python](http://c.biancheng.net/python/) 中，序列类型包括字符串、列表、元组、集合和字典，这些序列支持以下几种通用的操作，但比较特殊的是，集合和字典不支持索引、切片、相加和相乘操作

## 序列索引

* 序列中，每个元素都有属于自己的编号（索引），从起始元素开始，**索引值从 0 开始**递增。

* 还支持**索引值是负数**，此类索引是从右向左计数，换句话说，从最后一个元素开始计数，**从索引值 -1 开始**

  > ```python
  > str="C语言中文网"
  > print(str[0],"==",str[-6])
  > print(str[5],"==",str[-1])
  > #C == C
  > #网 == 网
  > 
  > ```

## 序列切片

* 切片操作是访问序列中元素的另一种方法，它可以访问一定范围内的元素，通过切片操作，可以生成一个新的序列

* 序列实现切片操作的语法格式如下：

  > ```python
  > sname[start : end : step]
  > ```

  - `sname`：表示序列的名称；
  - `start`：表示切片的开始索引位置（包括该位置），此参数也可以不指定，会**默认为 0**，也就是从序列的开头进行切片；
  - `end`：表示切片的结束索引位置（不包括该位置），如果不指定，则**默认为序列的长度**；
  - `step`：**表示在切片过程中，隔几个存储位置（包含当前位置）取一次元素**，也就是说，如果 step 的值大于 1，则在进行切片去序列元素时，会“跳跃式”的取元素。如果省略设置 step 的值，则最后一个冒号就可以省略。

  > ```python
  > str = "C语言中文网"
  > #取索引区间为[0,2]之间（不包括索引2处的字符）的字符串
  > print(str[:2])
  > #隔 1 个字符取一个字符，区间是整个字符串
  > print(str[::2])
  > #取整个字符串，此时 [] 中只需一个冒号即可
  > print(str[:])
  > 
  > # C语
  > # C言文
  > # C语言中文网
  > ```

## 序列相加

* Python 中，支持两种类型相同的序列使用“+”运算符做相加操作，它**会将两个序列进行连接，但不会去除重复的元素**

  > ```python
  > str="c.biancheng.net"
  > print("C语言"+"中文网:"+str)
  > 
  > # C语言中文网：c.biancheng.net
  > ```

## 数乘序列

* Python 中，使用数字 n 乘以一个序列会生成新的序列，其**内容为原来序列被重复 n 次**的结果

  > ```python
  > str="C语言中文网"
  > print(str*3)
  > 
  > # 'C语言中文网C语言中文网C语言中文网'
  > ```

- 比较特殊的是，列表类型在进行乘法运算时，还可以实现**初始化指定长度列表**的功能

  > ```python
  > list = [None]*5
  > print(list)
  > 
  > # [None, None, None, None, None]
  > ```

## 检查元素是否在序列中

- Python 中，可以使用` in `关键字检查某元素**是否为序列的成员**，其语法格式为：

  - `value in sequence`

  - value 表示要检查的元素，sequence 表示指定的序列

  > ```python
  > str="c.biancheng.net"
  > print('c'in str)
  > 
  > # True
  > ```

- 和 in 关键字用法相同，但功能恰好相反的，还有 `not in `关键字，它用来检查某个元素**是否不包含在指定的序列中**

  > ```python
  > str="c.biancheng.net"
  > print('c' not in str)
  > 
  > # False
  > ```

## 序列内置函数

### `list(sub)` 

- 把一个可迭代对象转换为列表

  ```python
  a = list()
  print(a)  # []
  
  b = 'I Love LsgoGroup'
  b = list(b)
  print(b)  
  # ['I', ' ', 'L', 'o', 'v', 'e', ' ', 'L', 's', 'g', 'o', 'G', 'r', 'o', 'u', 'p']
  
  c = (1, 1, 2, 3, 5, 8)
  c = list(c)
  print(c)  # [1, 1, 2, 3, 5, 8]
  ```

### `tuple(sub)` 

- 把一个可迭代对象转换为元组

  > ```python
  > a = tuple()
  > print(a)  # ()
  > 
  > b = 'I Love LsgoGroup'
  > b = tuple(b)
  > print(b)  
  > # ('I', ' ', 'L', 'o', 'v', 'e', ' ', 'L', 's', 'g', 'o', 'G', 'r', 'o', 'u', 'p')
  > 
  > c = [1, 1, 2, 3, 5, 8]
  > c = tuple(c)
  > print(c)  # (1, 1, 2, 3, 5, 8)
  > ```

### `str(obj)` 

- 把对象转换为字符串

  > ```python
  > a = 123
  > a = str(a)
  > print(a)  # 123
  > ```

### `len()`

- 返回对象（字符、列表、元组等）长度或元素个数

  > ```python
  > a = list()
  > print(len(a))  # 0
  > 
  > b = ('I', ' ', 'L', 'o', 'v', 'e', ' ', 'L', 's', 'g', 'o', 'G', 'r', 'o', 'u', 'p')
  > print(len(b))  # 16
  > 
  > c = 'I Love LsgoGroup'
  > print(len(c))  # 16
  > ```

### `max(sub)`

- 返回序列或者参数集合中的最大值

  > ```python
  > print(max(1, 2, 3, 4, 5))  # 5
  > print(max([-8, 99, 3, 7, 83]))  # 99
  > print(max('IloveLsgoGroup'))  # v
  > ```

### `min(sub)`

- 返回序列或参数集合中的最小值 

  > ```python
  > print(min(1, 2, 3, 4, 5))  # 1
  > print(min([-8, 99, 3, 7, 83]))  # -8
  > print(min('IloveLsgoGroup'))  # G
  > ```

### `sum(iterable[, start=0])` 

- 返回序列`iterable`与可选参数`start`的总和

  > ```python
  > print(sum([1, 3, 5, 7, 9]))  # 25
  > print(sum([1, 3, 5, 7, 9], 10))  # 35
  > print(sum((1, 3, 5, 7, 9)))  # 25
  > print(sum((1, 3, 5, 7, 9), 20))  # 45
  > ```

### `sorted(iterable, key=None, reverse=False) `

* 对所有可迭代的对象进行排序操作

  - `iterable` -- 可迭代对象。
  - `key` -- 主要是用来进行比较的元素，只有一个参数，具体的函数的参数就是取自于可迭代对象中，**指定可迭代对象中的一个元素**来进行排序。
  - `reverse` -- 排序规则，`reverse = True` 降序 ， **`reverse = False` 升序（默认）**。
  - 返回重新排序的列表

  > ```python
  > x = [-8, 99, 3, 7, 83]
  > print(sorted(x))  # [-8, 3, 7, 83, 99]
  > print(sorted(x, reverse=True))  # [99, 83, 7, 3, -8]
  > 
  > t = ({"age": 20, "name": "a"}, {"age": 25, "name": "b"}, {"age": 10, "name": "c"})
  > x = sorted(t, key=lambda a: a["age"])
  > print(x)
  > # [{'age': 10, 'name': 'c'}, {'age': 20, 'name': 'a'}, {'age': 25, 'name': 'b'}]
  > ```

### `reversed(seq)`

- 返回一个反转的迭代器，反向序列中的元素

  - - `seq` -- 要转换的序列，可以是 tuple, string, list 或 range

  > ```python
  > s = 'lsgogroup'
  > x = reversed(s)
  > print(type(x))  # <class 'reversed'>
  > print(x)  # <reversed object at 0x000002507E8EC2C8>
  > print(list(x))
  > # ['p', 'u', 'o', 'r', 'g', 'o', 'g', 's', 'l']
  > 
  > t = ('l', 's', 'g', 'o', 'g', 'r', 'o', 'u', 'p')
  > print(list(reversed(t)))
  > # ['p', 'u', 'o', 'r', 'g', 'o', 'g', 's', 'l']
  > 
  > r = range(5, 9)
  > print(list(reversed(r)))
  > # [8, 7, 6, 5]
  > 
  > x = [-8, 99, 3, 7, 83]
  > print(list(reversed(x)))
  > # [83, 7, 3, 99, -8]
  > ```

### `enumerate(sequence, [start=0])`

- 用于将一个可遍历的数据对象(如列表、元组或字符串)**组合为一个索引序列**，同时**列出数据和数据下标**，一般用在 for 循环当中

  > ```python
  > seasons = ['Spring', 'Summer', 'Fall', 'Winter']
  > a = list(enumerate(seasons))
  > print(a)  
  > # [(0, 'Spring'), (1, 'Summer'), (2, 'Fall'), (3, 'Winter')]
  > 
  > b = list(enumerate(seasons, 1))
  > print(b)  
  > # [(1, 'Spring'), (2, 'Summer'), (3, 'Fall'), (4, 'Winter')]
  > 
  > for i, element in a:
  >     print('{0},{1}'.format(i, element))
  > # 0,Spring
  > # 1,Summer
  > # 2,Fall
  > # 3,Winter
  > ```

### `zip(iter1 [,iter2 [...]])`

- 用于将可迭代的对象作为参数，将对象中对应的元素打包成一个个元组，然后返回由这些元组组成的对象，这样做的好处是节约了不少的内存。

- 我们可以使用 `list()` 转换来输出列表。

- 如果各个迭代器的元素个数不一致，则返回列表长度与最短的对象相同，利用 `*` 号操作符，可以将元组解压为列表。

  > ```python
  > a = [1, 2, 3]
  > b = [4, 5, 6]
  > c = [4, 5, 6, 7, 8]
  > 
  > zipped = zip(a, b)
  > print(zipped)  # <zip object at 0x000000C5D89EDD88>
  > print(list(zipped))  # [(1, 4), (2, 5), (3, 6)]
  > zipped = zip(a, c)
  > print(list(zipped))  # [(1, 4), (2, 5), (3, 6)]
  > 
  > a1, a2 = zip(*zip(a, b))
  > print(list(a1))  # [1, 2, 3]
  > print(list(a2))  # [4, 5, 6]
  > ```

-------

# 练习题

1. **怎么找出序列中的最大、小值？**

   > 使用内置函数max()和min()

2. **sort() 和 sorted() 区别**

   > 1.`sort()`方法仅被定义在列表（list）中，`sorted()`方法可对所有的可迭代对象进行排序操作。
   >
   > 2.`sort()`使用格式为`list.sort`，而`sorted()`使用格式为`sorted(obj)`
   >
   > 3.

3. **怎么快速求 1 到 100 所有整数相加之和？**

   > ```python
   > a = range(1, 101)
   > print(sum(a))
   > ```

4. **求列表 [2,3,4,5] 中每个元素的立方根。**

   > ```python
   > b = [2, 3, 4, 5]
   > for i in b:
   >     i = i**(1/3)
   >     print('%.6f' % i)
   > ```

5. **将[‘x’,‘y’,‘z’] 和 [1,2,3] 转成 [(‘x’,1),(‘y’,2),(‘z’,3)] 的形式**

   > ```python
   > c = ['x', 'y', 'z']
   > d = [1, 2, 3]
   > e = zip(c, d)
   > print(list(e))
   > 
   > ```



























