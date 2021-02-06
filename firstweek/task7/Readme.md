# 第七天

# 1.13类与对象

## 太难了

* **类中的函数叫方法**

* **类中的变量叫属性**

****

# 练习题

**1、以下类定义中哪些是类属性，哪些是实例属性？**

```python
class C:
    num = 0
    def __init__(self):
        self.x = 4
        self.y = 5
        C.count = 6
```

解答：

> `num`,`C.count`是类属性
>
> `self.x`,`self.y`是实例属性



**2、怎么定义私有方法？**

解答：

> 在变量名或函数名前加上“__”两个下划线，那么这个函数或变量就会为私有的。
>
> 方法名前面加了2个下划线的话表示该方法是私有的。



**3、尝试执行以下代码，并解释错误原因：**

```python
class C:
    def myFun():
        print('Hello!')
    c = C()
    c.myFun()
```

解答：

> * `TypeError: myFun() takes 0 positional arguments but 1 was given`	缺少self参数
>
>   ```python
>   class c:
>       def myFun(self): 
>           print('Hello')
>   c = C() 
>   c.myFun()
>   ```
>
> * 类的所有的方法都必须带有一个self的形参，但是调用时不需要传值（静态方法和类方法除外）

**4、按照以下要求定义一个游乐园门票的类，并尝试计算2个成人+1个小孩平日票价。**

要求:

- 平日票价100元
- 周末票价为平日的120%
- 儿童票半价

借鉴别人答案：

> ```python
> class Ticket:
>     def __init__(self):
>         self.weekday_price = 100
>         self.weekend_price = self.weekday_price * 1.2
> 
>     def WeekdayPrice(self):
>         self.adult = int(input('请输入成人数量：'))
>         self.children = int(input('请输入儿童数量：'))
>         print('总票价为：', self.adult * self.weekday_price + self.children * self.weekday_price / 2)
> 
>     def WeekendPrice(self):
>         self.adult = int(input('请输入成人数量：'))
>         self.children = int(input('请输入儿童数量：'))
>         print('总票价为：', self.adult * self.weekend_price + self.children * self.weekend_price / 2)
> 
> 
> t = Ticket()
> t.WeekdayPrice()
> 
> '''请输入成人数量：2
> 请输入儿童数量：1
> 总票价为： 250.0'''
> ```

# 1.14魔法方法

* 魔法方法总是被双下划线包围，例如`__init__`。

- 魔法方法的“魔力”体现在它们总能够在适当的时候被自动调用。

- 魔法方法的第一个参数应为`cls`（类方法） 或者`self`（实例方法）。

  - `cls`：代表一个类的名称

  - `self`：代表一个实例对象的名称

-------

# 练习题

**1、上面提到了许多魔法方法，如`__new__`,`__init__`, `__str__`,`__rstr__`,`__getitem__`,`__setitem__`等等，请总结它们各自的使用方法。**

解答：

> \_\_new\_\_
>
> - ` __new__`决定是否要使用该` __init__`方法，因为`__new__`可以调用其他类的构造方法或者直接返回别的实例对象来作为本类的实例，**如果 `__new__`没有返回实例对象，则 `__init__` 不会被调用**。
> - `__new__ `是在一个对象实例化的时候所调用的第一个方法，在调用` __init__ `初始化前，先调用 `__new__` 。
> - `__new__ `至少要有一个参数 `cls `，代表要实例化的类，此参数在实例化时由 Python 解释器自动提供，后面的参数直接传递给` __init__ `。
> - `__new__` 对当前类进行实例化，并将实例返回，传给 `__init__ `的` self` 。但执行了 `_*new*_ `，并不一定会进入` __init__ `，只有 `__new__` 返回了当前类` cls` 的实例，当前类的 `__init__ `才会进入



> \_\_init\_\_
>
> - 构造器，一个实例被创建的时候调用的初始化方法。



> \_\_str\_\_
>
> * `__str__`在**打印对象，用%s格式化以及强制转换数据类型时**触发。
>
> * `__rstr__`在没有实现`__str__`以及使用%r格式化的时候 触发。



> \_\_getitem\_\_
>
> - `__getitem__`(self, key) 定义获取容器中元素的行为，相当于 self[key] 。



> \_\_setitem\_\_
>
> `__setitem__`(self, key, value) 定义设置容器中指定元素的行为，相当于 self[key] = value 。



**2、利用python做一个简单的定时器类**

要求:

- 定制一个计时器的类。
- `start`和`stop`方法代表启动计时和停止计时。
- 假设计时器对象`t1`，`print(t1)`和直接调用`t1`均显示结果。
- 当计时器未启动或已经停止计时时，调用`stop`方法会给予温馨的提示。
- 两个计时器对象可以进行相加：`t1+t2`。
- 只能使用提供的有限资源完成。

借鉴答案：

> ```python
> import time
> 
> 
> class Clock(object):
>     def __init__(self):
>         print('未开始计时')
>         self.info = '未开始计时'
>         self.start_time = None
>         self.sec = None
> 
>     def __str__(self):
>         return self.info
> 
>     def __add__(self, others):
>         return '共计时 %f s' % (self.sec + others.sec)
> 
>     def start(self):
>         print('开始计时')
>         self.start_time = time.time()
>         self.info = '正在计时'
> 
>     def stop(self):
>         try:
>             self.sec = time.time() - self.start_time
>         except:
>             print('未开始计时或计时已结束')
>         else:
>             print('停止计时')
>             self.info = '已计时：%f s' % self.sec
> 
> 
> t1 = Clock()    # 未开始计时
> t1.stop()   # 未开始计时或计时已结束
> t1.start()  # 开始计时
> time.sleep(1)   
> t1.stop()   # 停止计时
> print(t1)   # 已计时：1.010612 s
> t2 = Clock()    # 未开始计时
> t2.start()  # 开始计时
> time.sleep(2)   
> t2.stop()   # 停止计时
> print(t1+t2)    # 共计时 3.030239 s
> 
> ```



























