# 第八天

# 1.15 模块

## 模块定义

- 模块（Module）是一个包含所有你定义的函数和变量的文件，其后缀名是`.py`。模块可以被别的程序引入，以使用该模块中的函数等功能。这也是使用 Python 标准库的方法。

- 容器 -> 数据的封装
- 函数 -> 语句的封装
- 类 -> 方法和属性的封装
- 模块 -> 程序文件

## 命名空间

命名空间因为对象的不同，也有所区别，可以分为如下几种：

- `内置命名空间（Built-in Namespaces）`：Python 运行起来，它们就存在了。内置函数的命名空间都属于内置命名空间，所以，我们可以在任何程序中直接运行它们，比如`id()`,不需要做什么操作，拿过来就直接使用了。
- `全局命名空间（Module：Global Namespaces）`：每个模块创建它自己所拥有的全局命名空间，不同模块的全局命名空间彼此独立，不同模块中相同名称的命名空间，也会因为模块的不同而不相互干扰。
- `本地命名空间（Function & Class：Local Namespaces）`：模块中有函数或者类，每个函数或者类所定义的命名空间就是本地命名空间。如果函数返回了结果或者抛出异常，则本地命名空间也结束了。

- 程序在查询上述三种命名空间的时候，就按照从里到外的顺序，即：Local Namespaces --> Global Namesspaces --> Built-in Namesspaces。

## 导入模块

### import 语句

> ```python
> import TemperatureConversion
> 
> print('32摄氏度 = %.2f华氏度' % TemperatureConversion.c2f(32))
> print('99华氏度 = %.2f摄氏度' % TemperatureConversion.f2c(99))
> 
> # 32摄氏度 = 89.60华氏度
> # 99华氏度 = 37.22摄氏度
> ```

### from ... import 语句

```python
from TemperatureConversion import c2f, f2c

print('32摄氏度 = %.2f华氏度' % c2f(32))
print('99华氏度 = %.2f摄氏度' % f2c(99))

# 32摄氏度 = 89.60华氏度
# 99华氏度 = 37.22摄氏度
```

### import 模块名 as 新名字

```python
import TemperatureConversion as tc

print('32摄氏度 = %.2f华氏度' % tc.c2f(32))
print('99华氏度 = %.2f摄氏度' % tc.f2c(99))

# 32摄氏度 = 89.60华氏度
# 99华氏度 = 37.22摄氏度
```

### from … import * 语句

**把一个模块的所有内容全都导入到当前的命名空间**也是可行的，只需使用如下声明：

```python
from modname import *
```

这提供了一个简单的方法来导入一个模块中的所有项目。然而**这种声明不该被过多地使用**。

## `if __name__ == '__main__'`

- `__name__`属性

  一个模块被另一个程序第一次引入时，其主程序将运行。如果我们想**在模块被引入时，模块中的某一程序块不执行**，我们可以**用`__name__`属性来使该程序块仅在该模块自身运行时执行**。

- 每个模块都有一个__name__属性，当其值是'__main__'时，表明该模块自身在运行，否则是被引入。
- 说明：`__name__ `与` __main__ `底下是双下划线。

- `if __name__ == '__main__'`的意思是：当` .py 文件`被直接运行时，`if __name__ == '__main__'`之下的代码块将被运行；**当` .py 文件`以模块形式被导入时，`if __name__ == '__main__'`之下的代码块不被运行**。

## dir()函数和help()函数

- **dir() 函数用来列出某个类或者某个模块中的全部内容，包括变量、方法、函数和类等**，它的用法为：`dir(obj)`
  - obj 表示要查看的对象。obj 可以不写，此时 dir() 会列出当前范围内的变量、方法和定义的类型。
  - **在 Python 标准库中，以`__`开头和结尾的方法都是私有的，不能在类的外部调用。**
- **help() 函数用来查看某个函数或者模块的帮助文档**，它的用法为：`help(obj)`
  - obj 表示要查看的对象。obj 可以不写，此时 help() 会进入帮助子程序。
  - 使用 help() 查看某个函数的用法时，函数名后边不能带括号

暂不理解，参考资料：

[Python dir()函数和help()函数](http://c.biancheng.net/view/4273.html)

## 包

- 包是一种管理 Python 模块命名空间的形式，采用"点模块名称"。
- 创建包分为三个步骤：
  - 创建一个文件夹，用于存放相关的模块，文件夹的名字即包的名字。
  - 在文件夹中创建一个 `__init__.py` 的模块文件，内容可以为空。
  - 将相关的模块放入文件夹中。

**目前~~非常~~不理解（头秃）**

----

# 练习题

**1、怎么查出通过 from xx import xx导入的可以直接调用的方法？**

参考解答：

> - 使用 help( ) 查看，例如查看datetime模块datetime类中可导入并可直接调用的方法： help( datetime.datetime )
>
> - 如果包内的`__init__.py`文件里有\_\_all\_\_=[]时，可以直接调用的方法为[]列表内定义的所有子模块。没有`__all__`列表时，就看`__init__.py`文件里的代码做具体判断。**\_\_all\_\_=[]** ，控制允许导入的模块列表。
> - （1）在test_package文件夹中创建_init_.py文件，里边什么都不需要编辑。
>   （2）在代码中把test_package的文件的路径加入到python解释器可以搜索到的路径列表中，这里就用到了python的包sys模块

**2、了解Collection模块，编写程序以查询给定列表中最常见的元素。**

题目说明：

输入：language = ['PHP', 'PHP', 'Python', 'PHP', 'Python', 'JS', 'Python', 'Python','PHP', 'Python']

输出：Python

```python
"""
Input file
language = ['PHP', 'PHP', 'Python', 'PHP', 'Python', 'JS', 'Python', 'Python','PHP', 'Python']
   
Output file
Python
"""
def most_element(language):
    """ Return a list of lines after inserting a word in a specific line. """
   
    # your code here
```

参考解答：

- **collection模块**

  是对Python的通用内置容器：`字典`、列表、元组和集合的扩展，它包含一些专业的容器数据类型：

  - **`Counter（计数器）`**：dict子类，用于计算可哈希性对象的个数。
  - **`OrderedDict（有序字典）`**：dict 子类，记录着数据成员添加的顺序。
  - **`defaultdict(默认字典）`**：dict 子类，调用一个工厂函数来为dict的values值缺失提供一个默认值。
  - **`namedtuple(可命名元组）`**：工厂函数生成有命名字段的tuple子类。
  - **`deque(双向队列`）**：能在“队列”两端快速出队、入队的函数，类似于队列的（list-like）的容器。
  - **`ChainMap`**:为多个映射创建单一视图的类字典类型。
  - **`UserDict`**：将字典包裹起来使得创建字典的子类更容易。
  - **`UserList`**：将列表对象包裹起来使得创建列表的子类更容易。
  - **`UserString`**：将字符串对象包裹起来使得创建字符串的子类更容易。

```python
from collections import Counter


def most_element():
    """ Return a list of lines after inserting a word in a specific line. """


language = ['PHP', 'PHP', 'Python', 'PHP', 'Python', 'JS', 'Python', 'Python', 'PHP', 'Python']
a = Counter(language)
print(a)  # Counter({'Python': 5, 'PHP': 4, 'JS': 1})
max_value = max(dict.values(a))
print(max_value)  # 5
for keys, values in dict.items(a):
    if values == max_value:
        print('出现次数最多的是：', keys, '出现次数为', values, '次')
most_element()

```



# 1.16datetime模块

- datetime 是 Python 中处理日期的标准模块，它提供了 4 种对日期和时间进行处理的类：**datetime**、**date**、**time** 和 **timedelta**。

## `datetime`类

## `date`类

## `time`类

## `timedelta`类

-----

# 练习题

**1、假设你获取了用户输入的日期和时间如`2020-1-21 9:01:30`，以及一个时区信息如`UTC+5:00`，均是`str`，请编写一个函数将其转换为timestamp：**

题目说明:

```python
"""
   
Input file
example1: dt_str='2020-6-1 08:10:30', tz_str='UTC+7:00'
example2: dt_str='2020-5-31 16:10:30', tz_str='UTC-09:00'
   
Output file
result1: 1590973830.0
result2: 1590973830.0
"""
   
   
def to_timestamp(dt_str, tz_str):
    # your code here
        pass
```

参考解答：

```python
import re
from datetime import timezone, timedelta
from dateutil import parser


def to_timestamp(dt_str, tz_str):
    dt = parser.parse(dt_str)
    utcRegex = re.compile(r'UTC(.*):')
    mo = utcRegex.search(tz_str)
    signed_hour = int(mo.group(1))
    tz = timezone(timedelta(hours=signed_hour))
    return dt.replace(tzinfo=tz).timestamp()


t1 = to_timestamp(dt_str='2020-6-1 08:10:30', tz_str='UTC+7:00')
t2 = to_timestamp(dt_str='2020-5-31 16:10:30', tz_str='UTC-09:00')
print(t1)
print(t2)

```



**2、编写Python程序以选择指定年份的所有星期日。**

题目说明:

```python
"""
   
Input file
   2020
   
Output file
   2020-01-05                         
   2020-01-12              
   2020-01-19                
   2020-01-26               
   2020-02-02     
   -----
   2020-12-06               
   2020-12-13                
   2020-12-20                
   2020-12-27 
"""
   
def all_sundays(year):
    # your code here
```

参考解答：

```python
import datetime


def all_sundays(year):
    d1 = datetime.date(year, 1, 1)
    d2 = datetime.date(year + 1, 1, 1)
    week = datetime.timedelta(7)
    day = d1 + datetime.timedelta(7 - d1.isoweekday())
    while day < d2:
        print(day.strftime("%Y-%m-%d"))
        day = day + week


all_sundays(2020)   
```











