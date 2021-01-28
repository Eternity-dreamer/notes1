

# 第三天

# 1.5 异常处理

## 1.Python 标准异常

## 2.Python标准警告

## 3.==try-except 语句==

### **捕捉异常可以使用`try/except`语句**

* > try:
  >
  > ​	<检测的语句>
  >
  > except <异常的名字1>[as error]:
  >
  > ​	<发生异常时执行的语句>
  >
  > except<异常的名字2>[as error]:
  >
  > ​	<发生异常时执行的语句>
  >
  > …

  - 首先，执行`try`子句（在关键字`try`和关键字`except`之间的语句）
  - **如果没有异常发生，忽略`except`子句，`try`子句执行后结束。**
  - **如果发生了异常，那么`try`子句余下的部分将被忽略。如果异常的类型和`except`之后的名称相符，那么对应的`except`子句将被执行。最后执行`try`语句之后的代码。**
  - 如果异常没有与任何的`except`匹配，那么这个异常将会传递给上层的`try`中。
  - 一个 try 语句可能包含多个except子句，分别来处理不同的特定的异常。最多**只有一个分支**会被执行。
  - 使用多个`except`代码块时，必须坚持对其规范排序，**要从最具针对性的异常到最通用的异常**。

* **一个except子句可以同时处理多个异常**，这些异常将被放在一个括号里成为一个==元组==，例如:

  > **except** (RuntimeError,  TypeError,  NameError):
  >
  > ​	<发生异常时执行的语句>

* **使用except 可以不带任何异常类型**

  > try:
  >
  > ​	<语句>
  >
  > except:
  >
  > ​	<发生异常时执行的语句>

  该种 `try-except `语句**捕获所有发生的异常**。但这不是一个很好的方式，**不能通过该程序识别出具体的异常信息**。

### try-except-else 语句

* ```
  try:
      检测范围
  except:
      出现异常后的处理代码
  else:
      如果没有异常执行这块代码
  ```

  如果在`try`子句执行时没有发生异常，Python将执行`else`语句后的语句。

### try-finally 语句

* ```
  try:
      检测范围
  except Exception[as reason]:
      出现异常后的处理代码
  finally:
      无论如何都会被执行的代码
  ```

  + 不管`try`子句里面有没有发生异常，**`finally`子句都会执行**。

  + 如果一个异常在`try`子句里被抛出，而又没有任何的`except`把它截住，那么这个异常会在`finally`子句执行后被抛出。

### ` raise `语句

* Python 使用 raise 语句抛出一个**指定的**异常。

* raise语法格式如下：

  ```
  raise [Exception [, args [, traceback]]]
  ```

  + 语句中 Exception 是异常的类型（例如，`NameError`）参数标准异常中任一种，`args` 是自已提供的异常参数。

  + 最后一个参数是可选的（在实践中很少使用），如果存在，是跟踪异常对象。

* ```python
  try:
      raise NameError('HiThere')
  except NameError:
      print('An exception flew by!')
      raise
  '''
  Traceback (most recent call last):
    File "<stdin>", line 2, in ?
  NameError: HiThere
  An exception flew by!
  '''
  ```

****

## 练习题：猜数字游戏

题目描述:

电脑产生一个零到100之间的随机数字，然后让用户来猜，如果用户猜的数字比这个数字大，提示太大，否则提示太小，当用户正好猜中电脑会提示，"恭喜你猜到了这个数是......"。在用户每次猜测之前程序会输出用户是第几次猜测，如果用户输入的根本不是一个数字，程序会告诉用户"输入无效"。

(尝试使用try catch异常处理结构对输入情况进行处理)

获取随机数采用random模块。

```python
import random
number0 = random .randint(0, 100)
# 产生[0,100]之间的随机数
m = 1
while True:
    print("这是第 %d 次猜测" % m)
    try:
        number1 = int(input("请猜一个数字（整数）："))
        if number1 > number0:
            print("太大啦！请再猜一次：")
        elif number1 < number0:
            print("太小啦！请再猜一次：")
    except ValueError:
        print("输入无效，请重新输入：")
        continue
    else:
        if number1 == number0:
            print("恭喜你猜到了这个数是 {}".format(number0))
            break
        m += 1

```

















