#  第六天

# 1.12 函数与Lambda表达式

-----

# 练习题

**1 .怎么给函数编写文档？** 

解答：

> * 函数的说明文档，本质就是**一段字符串**
> * 函数的说明文档通常位于函数内部、所有代码的最前面
> * python 中三种注释方式。在定义函数后，在下方一行**用三引号的注释方式**进行函数说明，此注释就是函数的说明文档。
> * 可以用**`my_function.__doc__`或`help(my_function)`**获取自定义函数`my_function`的说明文档。

> ```python
> def str_max(str1,str2):
>     '''
>     比较 2 个字符串的大小
>     '''
>     str = str1 if str1 > str2 else str2
>     return str
> help(str_max)
> print(str_max.__doc__)
> """ 
> Help on function str_max in module __main__:
> 
> str_max(str1, str2)
>     比较 2 个字符串的大小
> """
> # 比较 2 个字符串的大小
> ```

**2. 怎么给函数参数和返回值注解？**

解答：

> * python是一门强类型、动态语言，既同类型的变量才能一起运算、定义变量前不用事先声明变量类型。这样虽然带来了便利，但是也会带来弊端。可以用函数注解和参数注解来解决。
> * 参数注解就是，在定义函数的时候，参数列表内部的参数后面，**加上冒号和要传入的类型**。
> * 返回值注解是在参数列表后面，冒号前面，**增加一个 -> 后面接返回值的类型**。
> * 写了参数注解也无法强制限定变量的类型，**只能作为提示**，来告知使用者应该传入什么类型的参数。
> * 这些注解都会以字典的形式存在函数的.__annotations__属性中。

> ```python
> def accumlate(x:int, y:int) -> int:
>  return x*y
> 
> def func(x: int, y: int) -> int:
> 	return x+y
> 
> accumlate.__annotations__
> {'x': int, 'y': int, 'return': int}
> 
> print(accumlate.__annotations__)
> {'x': <class 'int'>, 'y': <class 'int'>, 'return': <class 'int'>}
> 
> 
> ```

**3. 闭包中，怎么对数字、字符串、元组等不可变元素更新。**

解答：

> * 如果要修改闭包作用域中的变量则需要 `nonlocal` 关键字。
>
>   ```python
>   def outer():
>       num = 10
>
>       def inner():
>           nonlocal num  # nonlocal关键字声明
>           num = 100
>           print(num)
>
>       inner()
>       print(num)
>       
>       
>   outer()
>   
>   # 100
>   # 100 
>   
>   ```
>

**4. 分别根据每一行的首元素和尾元素大小对二维列表 a = [[6, 5], [3, 7], [2, 8]] 排序。(利用lambda表达式)**

解答：

> * 用`sorted()`函数对二维列表a进行排序
>
> * [Python闭包](http://c.biancheng.net/view/5335.html)
>
>   ```python
>   a = [[6, 5], [3, 7], [2, 8]]
>   print(sorted(a, key=lambda a: a[0]))
>   print(sorted(a, key=lambda a: a[1]))
>   ```

**5. 利用python解决汉诺塔问题？**

有a、b、c三根柱子，在a柱子上从下往上按照大小顺序摞着64片圆盘，把圆盘从下面开始按大小顺序重新摆放在c柱子上，尝试用函数来模拟解决的过程。（提示：将问题简化为已经成功地将a柱上面的63个盘子移到了b柱）

解答：

> ```python
> def hannuota(num, a, b, c):
>     if num == 1:  # 如果只有一片
>         print(a, '-->', c)  # 那就直接把它从a柱移动c柱
>     else:  # 两片以上的话
>         hannuota(num-1, a, c, b)  # 先把 num-1 片移到b柱
>         print(a, '-->', c)  # 在把最底层的那片移到c柱
>         hannuota(num-1, b, a, c)  # 接下来就是想办法把b柱上面的移到c柱了
> 
> 
> num = int(input('请输入片数：'))  # 片数由我们来自己手动输入
> hannuota(num, 'a', 'b', 'c')  # 在此调用函数，柱子a，b，c就默认使用形参吧
> ```









