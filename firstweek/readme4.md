# 第四天

# 1.6 列表

## 定义

* 列表是最常用的 Python 数据类型

* 创建一个列表，只要把逗号分隔的不同的数据项使用方括号括起来即可

  > [元素1，元素2，...]

### 访问列表中的值

* 与字符串的索引一样，列表索引从 **0** 开始，第二个索引是 **1**，依此类推。

* 索引也可以从尾部开始，最后一个元素的索引为 **-1**，往前一位为 **-2**，以此类推。

## 列表的创建

* 普通列表

  > ```
  > x = [2, 3, 4, 5, 6, 7]
  > print(x, type(x))
  > # [2, 3, 4, 5, 6, 7] <class 'list'>
  > ```

* 用推导式创建列表

  > ```
  > x = [i for i in range(10)]
  > print(x, type(x))
  > # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9] <class 'list'>
  > ```

  > ```
  > x = [0] * 5
  > print(x, type(x))
  > # [0, 0, 0, 0, 0] <class 'list'>
  > ```

  > ```
  > x = [0 for i in range(5)]
  > print(x, type(x))
  > # [0, 0, 0, 0, 0] <class 'list'>
  > ```

* 创建二维数组/列表

  > ```
  > x = [[1, 2, 3], [4, 5, 6], [7, 8, 9], [0, 0, 0]]
  > print(x, type(x))
  > # [[1, 2, 3], [4, 5, 6], [7, 8, 9], [0, 0, 0]] <class 'list'>
  > ```

  > ```
  > x = [[0 for col in range(3)] for row in range(4)]
  > print(x, type(x))
  > # [[0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0]] <class 'list'>
  > ```

## 添加列表元素

### 使用`list.append(obj)`

* 向列表的**尾部**添加**一个**新的元素
* 此元素如果是一个 list，那么这个 list 将作为一个整体进行追加

* 注意`append()`和`extend()`的区别

  > ```python
  > x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
  > x.append(['Thursday', 'Sunday'])
  > print(x)  
  > # ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', ['Thursday', 'Sunday']]
  > 
  > print(len(x))  # 6
  > ```

### 使用`list.extend(seq)`

* 在列表末尾一次性追加另一个序列中的多个值（用新列表扩展原来的列表）

* 严格来说 `append` 是追加，把一个东西整体添加在列表后，而 `extend` 是扩展，把一个东西里的所有元素添加在列表后

  > ```python
  > x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
  > x.extend(['Thursday', 'Sunday'])
  > print(x)  
  > # ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Thursday', 'Sunday']
  > 
  > print(len(x))  # 7
  > ```

### 使用`list.insert(index, obj)`

* 用于将**指定对象(obj)**插入列表的**指定位置(index)**

  > ```python
  > list1 = ['Google', 'Runoob', 'Taobao']
  > list1.insert(1, 'Baidu')
  > print ('列表插入元素后为 : ', list1)
  > # 列表插入元素后为 :  ['Google', 'Baidu', 'Runoob', 'Taobao']
  > ```

## 删除列表元素

### `list.remove(obj)`

*  移除列表中某个值的第一个匹配项

  > ```python
  > x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
  > x.remove('Monday')
  > print(x)  # ['Tuesday', 'Wednesday', 'Thursday', 'Friday']
  > ```

### `list.pop([index=-1])`

* 移除列表中的一个元素（默认最后一个元素），并且返回该元素的值

  > ```python
  > x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
  > y = x.pop()
  > print(y)  # Friday
  > 
  > y = x.pop(0)
  > print(y)  # Monday
  > 
  > y = x.pop(-2)
  > print(y)  # Wednesday
  > print(x)  # ['Tuesday', 'Thursday']
  > ```

### `del var1[, var2 ……]`

* 删除单个或多个对象

  ```python
  x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
  del x[0:2]
  print(x)  # ['Wednesday', 'Thursday', 'Friday']
  ```

* 如果你要从列表中删除一个元素，且不再以任何方式使用它，就使用`del`语句；如果你要在删除元素后还能继续使用它，就使用方法`pop()`

## 获取列表元素

### **`list[start : stop : step]`**

* 以具体的 `step` 从编号 `start` 往编号 `stop`**切片**

* `step`默认为**1**

  #### 从编号 `start` 往列表尾部切片

  > ```python
  > x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
  > print(x[3:])  # ['Thursday', 'Friday']
  > print(x[-3:])  # ['Wednesday', 'Thursday', 'Friday']
  > ```

  #### 从列表头部往编号 `stop` 切片

  > ```python
  > week = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
  > print(week[:3])  # ['Monday', 'Tuesday', 'Wednesday']
  > print(week[:-3])  # ['Monday', 'Tuesday']
  > ```

  #### 从编号 `start` 往编号 `stop` 切片

  > ```python
  > week = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
  > print(week[1:3])  # ['Tuesday', 'Wednesday']
  > print(week[-3:-1])  # ['Wednesday', 'Thursday']
  > ```

* **把 `step` 设为 -1，相当于将列表反向排列。**

  > ```python
  > week = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
  > print(week[1:4:2])  # ['Tuesday', 'Thursday']
  > print(week[:4:2])  # ['Monday', 'Wednesday']
  > print(week[1::2])  # ['Tuesday', 'Thursday']
  > print(week[::-1])  
  > # ['Friday', 'Thursday', 'Wednesday', 'Tuesday', 'Monday']
  > ```



* `list[:]`,复制列表中的所有元素**（浅拷贝）**

  > ```python
  > week = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
  > print(week[:])  
  > # ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
  > ```

## 列表常用操作符

- 等号操作符：`==`

  只有成员、成员位置都相同时才返回True

- 连接操作符 `+`

  **列表拼接有两种方式，用「加号 +」和「乘号 *」，前者首尾拼接，后者复制拼接**

- 重复操作符 `*`

- 成员关系操作符 `in`、`not `    

  > ```python
  > list1 = [123, 456]
  > list2 = [456, 123]
  > list4 = list1 + list2  # extend()
  > print(list4)  # [123, 456, 456, 123]
  > list5 = list1 * 3
  > print(list5)  # [123, 456, 123, 456, 123, 456]
  > ```

## 列表里的其他常用方法

* `list.sort(key=None, reverse=False)` 对原列表进行排序

  + `reverse` -- 排序规则，`reverse = True` 降序， `reverse = False` 升序（默认）

  + > ```python
    > aList = ['Google', 'Runoob', 'Taobao', 'Facebook']
    >  
    > aList.sort()
    > print ( "List : ", aList)
    > # List :  ['Facebook', 'Google', 'Runoob', 'Taobao']
    > ```

* 参考网址：[菜鸟教程—列表—底部](https://www.runoob.com/python3/python3-list.html)

****

# 练习题

**1、列表操作练习**

列表lst 内容如下

lst = [2, 5, 6, 7, 8, 9, 2, 9, 9]

请写程序完成下列操作：

1. 在列表的末尾增加元素15
2. 在列表的中间位置插入元素20
3. 将列表[2, 5, 6]合并到lst中
4. 移除列表中索引为3的元素
5. 翻转列表里的所有元素
6. 对列表里的元素进行排序，从小到大一次，从大到小一次

```python
lst = [2, 5, 6, 7, 8, 9, 2, 9, 9]
lst.append(15)
print('lst1=', lst)
lst.insert(5, 20)
print('lst2=', lst)
lst.extend([2, 5, 6])
print('lst3=', lst)
lst.pop(3)
print('lst4=', lst)
lst.reverse()
print('lst5=', lst)
lst.sort()
print('lst6=', lst)
lst.sort(reverse=True)
print('lst7=', lst)

```

**2、修改列表**

问题描述：

lst = [1, [4, 6], True]

请将列表里所有数字修改成原来的两倍

```python
def double_list(lst):
    for index, value in enumerate(lst):
        if isinstance(value, bool):
            continue
        if isinstance(value, (int, float)):
            lst[index] *= 2
        if isinstance(value, list):
            # 递归
            double_list(value)


if __name__ == '__main__':
    lst = [1, [4, 6], True]
    double_list(lst)
    print(lst)
```



**3、leetcode 852题 山脉数组的峰顶索引**

```python
class Solution:
    def peakIndexInMountainArray(self, A):
        """
        : type A: List[int]
        : rtype: int
        """
        return A.index(max(A))


solution = Solution()
A = [1, 2, 4, 6, 4, 5]
print(solution.peakIndexInMountainArray(A))


```

*****

# 1.7 元组

## 定义

「元组」定义语法为：`(元素1, 元素2, ..., 元素n)`

- 小括号把所有元素绑在一起

- 逗号将每个元素一一分开

- Python 的元组与列表类似，不同之处在于**元组的元素不能修改**。

  元组使用**小括号 **( )****，列表使用方括号 **[ ]**。

  

## 创建元组

* 元组创建很简单，只需要在括号中添加元素，并使用逗号隔开即可。

  > tuple = ("Google", 'Runoob', "Taobao")

* 元组中**只包含一个元素时,需要在元素后面添加逗号**，否则括号会被当作运算符使用。

* 创建元组可以用小括号 ()，也可以什么都不用，为了可读性，建议还是用 ()

  > ```python
  > x = (1)
  > print(type(x))  # <class 'int'>
  > x = 2, 3, 4, 5
  > print(type(x))  # <class 'tuple'>
  > x = []
  > print(type(x))  # <class 'list'>
  > x = ()
  > print(type(x))  # <class 'tuple'>
  > x = (1,)
  > print(type(x))  # <class 'tuple'>
  > ```

## 访问元组

* 元组可以使用下标索引来访问元组中的值

* 元组与字符串类似，下标索引从 0 开始，可以进行截取，组合等

  > ```python
  > tup1 = ('Google', 'Runoob', 1997, 2000)
  > tup2 = (1, 2, 3, 4, 5, 6, 7 )
  >  
  > print ("tup1[0]: ", tup1[0])
  > print ("tup2[1:5]: ", tup2[1:5])
  > '''
  > 输出结果：
  > tup1[0]:  Google
  > tup2[1:5]:  (2, 3, 4, 5)
  > '''
  > ```

* 与字符串一样，**元组之间也可以使用 + 号和 * 号进行运算**。这就意味着他们可以组合和复制，运算后会生成一个新的元组。

| Python 表达式                  | 结果                         | 描述         |
| :----------------------------- | :--------------------------- | :----------- |
| len((1, 2, 3))                 | 3                            | 计算元素个数 |
| (1, 2, 3) + (4, 5, 6)          | (1, 2, 3, 4, 5, 6)           | 连接         |
| ('Hi!',) * 4                   | ('Hi!', 'Hi!', 'Hi!', 'Hi!') | 复制         |
| 3 in (1, 2, 3)                 | True                         | 元素是否存在 |
| for x in (1, 2, 3): print (x,) | 1 2 3                        | 迭代         |

## 更新元组

* 元组中的元素值是不允许修改的，因此不能直接给元组的元素赋值，但我们可以对元组进行连接组合

* 所谓元组的不可变指的是元组所指向的内存中的内容不可变，**当元素是可变对象时。对象内部属性是可以修改的**

  > ```python
  > t1 = (1, 2, 3, [4, 5, 6])
  > print(t1)  # (1, 2, 3, [4, 5, 6])
  > 
  > t1[3][0] = 9
  > print(t1)  # (1, 2, 3, [9, 5, 6])
  > ```

* 元组中的元素值是不允许删除的，但我们**可以使用del语句来删除整个元组**

  > ```python
  > tup = ('Google', 'Runoob', 1997, 2000)
  > print (tup)
  > del tup
  > print ("删除后的元组 tup : ")
  > print (tup)
  > '''
  > 删除后的元组 tup : 
  > Traceback (most recent call last):
  >   File "test.py", line 8, in <module>
  >     print (tup)
  > NameError: name 'tup' is not defined
  > '''
  > ```

 ##   内置方法

元组大小和内容都不可更改，因此只有 `count` 和 `index` 两种方法。

```python
t = (1, 10.31, 'python')
print(t.count('python'))  # 1
print(t.index(10.31))  # 1
```

- `count('python')` 是记录在元组 `t` 中该元素出现几次，显然是 1 次
- `index(10.31)` 是找到该元素在元组 `t` 的索引，显然是 1

*****

# 练习题

**1、元组概念**

写出下面代码的执行结果和最终结果的类型

```
(1, 2)*2
(1, )*2
(1)*2
```

分析为什么会出现这样的结果.

答：

> **结果：**
>
> (1, 2, 1, 2) <class 'tuple'>
> (1, 1) <class 'tuple'>
> 2 <class 'int'>
>
> **分析：**
>
> 前两个按元组进行复制两次
>
> 第三个按照整型数据进行了乘法运算

**2、**

拆包过程是什么？

```
a, b = 1, 2
```

上述过程属于拆包吗？

可迭代对象拆包时，怎么赋值给占位符？

答：

> 对于函数中的多个返回数据, 去掉元组, 列表 或者字典 直接获取里面数据的过程.
>
> 对于可迭代对象，如元组、列表、字符串、集合、字典这些可迭代对象都可以被拆包，拆包是指将一个结构中的数据拆分为多个单独变量中。

> 该过程属于对元组拆包，用拆包的形式定义变量

> 拆包时使用占位符_可以丢弃对应的元素

****

# 1.8字符串

****

# 练习题

**1、字符串函数回顾**

- 怎么批量替换字符串中的元素？
- 怎么把字符串按照空格进⾏拆分？
- 怎么去除字符串⾸位的空格？

答：

> * 用`str.replace(old,new) `把字符串中的元素替换为新元素，批量替换时可使用链式的`str.replace().replace()`
> * 用`string.split("str",num)`对字符串进行分割，不带参数默认是以空格为分隔符进行拆分，`sting.split()`
> * 用`string.lstrip()`删除字符串首位的空格

**2、实现isdigit函数**

题目要求

实现函数isdigit， 判断字符串里是否只包含数字0~9

```python
def isdigit(string):
    """
    判断字符串只包含数字
    :param string:
    :return:
    """
    test_number0 = "0123456789"
    for char in string:
        if char not in test_number0:
            return False
            break
        else:
            continue
    return True



```

**3、leetcode 5题 最长回文子串**

给定一个字符串 `s`，找到 `s` 中最长的回文子串。你可以假设 `s` 的最大长度为 1000。

示例:

输入: "babad"

输出: "bab"

输入: "cbbd"

输出: "bb"

```python
class Solution:
    def longestPalindrome(self, s):
        """
        :type s: str
        :rtype: str
        """
        if s is None or len(s) == 0:
            return ""
        start = 0
        end = 0
        for i in range(len(s)):
            len1 = self.expandAroundCenter(s, i, i)  # 中心为1个字符的回文子串
            len2 = self.expandAroundCenter(s, i, i + 1)  # 中心为2个字符的回文子串
            maxLen = max(len1, len2)
            if maxLen > (end - start + 1):
                start = i - (maxLen - 1) // 2
                end = i + maxLen // 2
        return s[start: end + 1]

    def expandAroundCenter(self, s, left, right):
        """
        :type s: str
        :type left: int
        :type right: int
        :rtype: int
        """
        L = left
        r = right
        while L >= 0 and r < len(s) and s[L] == s[r]:
            L = L - 1
            r = r + 1
        return r - L - 1


solution = Solution()
str1 = input("请输入待检测字符串：")
result = solution.longestPalindrome(str1)
print(result)
    
```

