# Python

 # 第一天

## 1.1变量、运算符与数据类型

### 1.注释 

* `#`用于整行的注释

* 三个单引号：`'''`+内容+`'''`或

  三个双引号：`"""`+内容+`"""` 用于多行注释

### 2.运算符

* **算术运算符**  

  熟悉：加`+` 	减`-`	乘`*`	除`/`	取余`%`

  陌生：整除`//`	幂`**`

* __比较运算符__

  同C语言：大于 `>`	小于`<`	等于`=`

  ​				大于等于`>=`	小于等于`<=`	不等于`!=`

  > ```python
  > print(2!=5) #True
  > ```

* **逻辑运算符**

  与`and`	或`or`	非`not`

  > ```python
  > print((1>3) or (9>2))	#True
  > ```

  > ```python
  > print(not (2>1))	#False
  > ```

* ***位运算符***

  | 名称 |操作符|
  | :--- | :-----|
  | 按位取反 | `~` |
  | 按位与 | `&` |
  | 按位或 | `|` |
  | 按位异或 | `^` |
  | 左移 | `<<` |
  | 右移 | `>>` |

* ***成员运算符***

  存在`in`	不存在`not in`

* ***身份运算符***：用于比较两个对象的存储单元

  `is`	`is not`

  **注意：**

  is, is not 对比的是两个变量的内存地址；==, != 对比的是两个变量的值

* ***三目运算符***

  Python 是一种极简主义的编程语言，它没有引入`? :`，而是使用已有的 if else 关键字来实现相同的功能。

  `exp1 if contion else exp2`

* **运算符优先级**

​	[菜鸟教程python运算符](https://www.runoob.com/python/python-operators.html#ysf5)

### 3.变量和赋值

​	Python 中的变量不需要声明，变量没有类型。

- 在使用变量之前，需要对其先赋值
- 变量名可以包括字母、数字、下划线、但变量名不能以数字开头
- 大小写字母不相同

### 4.数据类型和转换

 #### 数据类型   

Python3 中有六个标准的数据类型：

- Number（数字）
- String（字符串）
- List（列表）
- Tuple（元组）
- Set（集合）
- Dictionary（字典）

​    Python3 的六个标准数据类型中：

- **不可变数据（3 个）：**Number（数字）、String（字符串）、Tuple（元组）；
- **可变数据（3 个）：**List（列表）、Dictionary（字典）、Set（集合）。

- 基本类型：整型、浮点型、布尔型
- 容器类型：字符串、元组、列表、字典和集合

##### Number（数字）:

Python3支持 `int`	`float`	`bool`	`complex(复数)`

* 只有一种整数类型` int`，表示为长整型
* 布尔 (`bool`) 型变量只能取两个值，`True` 和 `False`。当把布尔型变量用在数字运算中，用 `1` 和 `0` 代表 `True` 和 `False`。
* 复数由实数部分和虚数部分构成，可以用a + bj,或者complex(a,b)表示， 复数的实部a和虚部b都是浮点型
* 在混合计算时，Python会把整型转换成为浮点数。



内置的 `type() 函数`可以用来查询变量所指的对象类型。

```python
>>> a, b, c, d = 20, 5.5, True, 4+3j
>>> print(type(a), type(b), type(c), type(d))
<class 'int'> <class 'float'> <class 'bool'> <class 'complex'>
```

此外还可以用 `isinstance` 来判断：

> ```python
> >>> a = 111
> >>> isinstance(a, int)
> True
> >>>
> ```

注：

- `type()` 不会认为子类是一种父类类型，不考虑继承关系。
- `isinstance()` 会认为子类是一种父类类型，考虑继承关系。

如果要判断两个类型是否相同推荐使用 `isinstance()`。

#### 数据类型转换

| 函数                        | 描述                                |
| --------------------------- | ----------------------------------- |
| `int(x)`  或`int('x',base)` | 将x转换为一个整数，默认base为10进制 |
| `float(x)`                  | 转换为浮点数                        |
| `str(x)`                    | 转换为字符串                        |

参考网站：[菜鸟Python3基本数据类型](https://www.runoob.com/python3/python3-data-type.html)

### 5.print()函数

##### 暂时不太懂

*****

- **Python 是一种解释型语言：** 这意味着开发过程中没有了编译这个环节。类似于PHP和Perl语言。
- **Python 是交互式语言：** 这意味着，您可以在一个 Python 提示符 `>>>`后直接执行代码。
- **Python 是面向对象语言:** 这意味着Python支持面向对象的风格或代码封装在对象的编程技术。
- **Python 是初学者的语言：**Python 对初级程序员而言，是一种伟大的语言，它支持广泛的应用程序开发，从简单的文字处理到 WWW 浏览器再到游戏。

*****

## task1思考题

​	**1.Python是怎么诞生的？Python之父是谁？**

​	Python由荷兰数学和计算机科学研究学会的Guido van Rossum 于1990 年代初设计，	作为一门叫做[ABC语言](https://baike.baidu.com/item/ABC语言/334996)的替代品。

​	**2.Python和C++（或者C）的区别在哪？**

​	求助网络	[python脚本之家](https://www.jb51.net/article/164748.htm)

​	**3.相较于Python2，Python3做了哪些大的改进？**

​	[区别](https://www.runoob.com/python/python-2x-3x.html)			[为什么选Python3](https://blog.csdn.net/qq_39521554/article/details/80855086?utm_medium=distribute.pc_relevant.none-task-blog-baidujs_baidulandingword-2&spm=1001.2101.3001.4242)				

## 练习题：

​	**1.怎样对python中的代码进行注释？**

​	`#`进行单行注释；两组`'''`或`"""`进行多行注释

​	**2.python有哪些运算符，这些运算符的优先级是怎样的？**

​	主要有有算术运算符、比较运算符、逻辑运算符、位运算符、赋值运算符

​	优先级：

| 运算符                   | 描述                                                   |
| :----------------------- | :----------------------------------------------------- |
| **                       | 指数 (最高优先级)                                      |
| ~ + -                    | 按位翻转, 一元加号和减号 (最后两个的方法名为 +@ 和 -@) |
| * / % //                 | 乘，除，取模和取整除                                   |
| + -                      | 加法减法                                               |
| >> <<                    | 右移，左移运算符                                       |
| &                        | 位 'AND'                                               |
| ^ \|                     | 位运算符                                               |
| <= < > >=                | 比较运算符                                             |
| <> == !=                 | 等于运算符                                             |
| = %= /= //= -= += *= **= | 赋值运算符                                             |
| is is not                | 身份运算符                                             |
| in not in                | 成员运算符                                             |
| not and or               | 逻辑运算符                                             |

**3.python 中 `is`, `is not` 与 `==`, `!=` 的区别是什么？**

​	is, is not 对比的是两个变量的内存地址；==, != 对比的是两个变量的值

**4.python 中包含哪些数据类型？这些数据类型之间如何转换？**

​	Python中有六个标准的数据类型：Number （数字），String（字符串），

​	List（列表)，Tuple（元组），Set（集合），Dictionary（字典）

​	简单转换：

| 函数                        | 描述                                |
| --------------------------- | ----------------------------------- |
| `int(x)`  或`int('x',base)` | 将x转换为一个整数，默认base为10进制 |
| `float(x)`                  | 转换为浮点数                        |
| `str(x)`                    | 转换为字符串                        |

*****

## 1.2 位运算

*****

## 练习题：只出现一次的数字

给定一个**非空**整数数组，除了某个元素只出现一次以外，其余每个元素均出现两次。找出那个只出现了一次的元素。

尝试使用位运算解决此题。

题目说明:

```python
"""
Input file
example1: [2,2,1]
example2: [4,1,2,1,2]

Output file
result1: 1
result2: 4
"""



class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        
     # your code here
```



解答：

```python
class Solution:
    def singleNumber(self, nums):
        a = 0
        for i in nums:
            a ^= i
        return a

solution = Solution()
nums = [4,1,2,1,2]
print(solution.singleNumber(nums))
#	4
```



















