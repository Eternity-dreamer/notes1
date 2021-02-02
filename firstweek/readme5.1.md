# 第五天

# 1.9 字典

## 判断可变类型与不可变类型

- 用 `id(X)` 函数，对 `X` 进行某种操作，比较操作前后的 `id`，如果不一样，则 `X` 不可变，如果一样，则 `X` 可变。
- 用 `hash(X)`，只要不报错，证明 `X` 可被哈希，即不可变，反过来不可被哈希，即可变。

- **数值、字符和元组 都能被哈希，因此它们是不可变类型。**
- **列表、集合、字典不能被哈希，因此它是可变类型。**

## 字典定义

* 字典是一种可变容器模型，且可存储任意类型对象

* 字典的每个键值 **key=>value** 对用冒号 **:** 分割，每个对之间用逗号(**,**)分割，整个字典包括在花括号 **{}** 中 ,格式如下所示：

  ```python
  d = {key1 : value1, key2 : value2, key3 : value3 }
  ```

* `dict` 内部存放的顺序和 `key` 放入的顺序没有关系

## 创建字典

### 通过字符串或数值作为`key`来创建字典

> ```python
> dic1 = {1: 'one', 2: 'two', 3: 'three'}
> print(dic1)  # {1: 'one', 2: 'two', 3: 'three'}
> print(dic1[1])  # one
> print(dic1[4])  # KeyError: 4
> 
> dic2 = {'rice': 35, 'wheat': 101, 'corn': 67}
> print(dic2)  # {'wheat': 101, 'corn': 67, 'rice': 35}
> print(dic2['rice'])  # 35
> ```

### 通过元组作为`key`来创建字典

> ```python
> dic = {(1, 2, 3): "Tom", "Age": 12, 3: [3, 5, 7]}
> print(dic)  # {(1, 2, 3): 'Tom', 'Age': 12, 3: [3, 5, 7]}
> print(type(dic))  # <class 'dict'>
> ```

* 一般不这样使用

### 通过构造函数`dict`来创建字典

* 用`dict()` 创建一个空的字典

  * 通过`key`直接把数据放入字典中，但一个`key`只能对应一个`value`，多次对一个`key`放入 `value`，后面的值会把前面的值冲掉

  > ```python
  > dic = dict()
  > dic['a'] = 1
  > dic['b'] = 2
  > dic['c'] = 3
  > 
  > print(dic)
  > # {'a': 1, 'b': 2, 'c': 3}
  > 
  > dic['a'] = 11
  > print(dic)
  > # {'a': 11, 'b': 2, 'c': 3}
  > ```

* `dict(mapping)`

  * 通过键值对表或元组建立字典

  > ```python
  > dic1 = dict([('apple', 4139), ('peach', 4127), ('cherry', 4098)])
  > print(dic1)  # {'cherry': 4098, 'apple': 4139, 'peach': 4127}
  > 
  > dic2 = dict((('apple', 4139), ('peach', 4127), ('cherry', 4098)))
  > print(dic2)  # {'peach': 4127, 'cherry': 4098, 'apple': 4139}
  > ```

* `dict(**kwargs)`

  * 这种情况下，键只能为字符串类型，并且创建的时候字符串不能加引号，加上就会直接报语法错误。

  > ```python
  > dic = dict(name='Tom', age=10)
  > print(dic)  # {'name': 'Tom', 'age': 10}
  > print(type(dic))  # <class 'dict'>
  > ```



## 访问字典

* 把**相应的键放入到方括号**中，如下实例:

  > ```python
  > dict = {'Name': 'Runoob', 'Age': 7, 'Class': 'First'}
  >  
  > print ("dict['Name']: ", dict['Name'])
  > print ("dict['Age']: ", dict['Age'])
  > 
  > # dict['Name']:  Runoob
  > # dict['Age']:  7
  > ```

## 字典中的内置方法

### `dict.fromkeys(seq[, value])` 

* 用于创建一个新字典，以序列 `seq` 中元素做字典的键，`value` 为字典所有键对应的初始值

  > ```python
  > seq = ('name', 'age', 'sex')
  > dic1 = dict.fromkeys(seq)
  > print(dic1)
  > # {'name': None, 'age': None, 'sex': None}
  > 
  > dic2 = dict.fromkeys(seq, 10)
  > print(dic2)
  > # {'name': 10, 'age': 10, 'sex': 10}
  > 
  > dic3 = dict.fromkeys(seq, ('小马', '8', '男'))
  > print(dic3)
  > # {'name': ('小马', '8', '男'), 'age': ('小马', '8', '男'), 'sex': ('小马', '8', '男')}
  > ```

### `dict.keys()`

* 返回一个可迭代对象，可以使用 `list()` 来转换为列表，列表为字典中的所有键。

  > ```python
  > dic = {'Name': 'lsgogroup', 'Age': 7}
  > print(dic.keys())  # dict_keys(['Name', 'Age'])
  > lst = list(dic.keys())  # 转换为列表
  > print(lst)  # ['Name', 'Age']
  > ```

### `dict.values()`

* 回一个迭代器，可以使用 `list()` 来转换为列表，列表为字典中的所有值

  > ```python
  > dic = {'Sex': 'female', 'Age': 7, 'Name': 'Zara'}
  > print(dic.values())
  > # dict_values(['female', 7, 'Zara'])
  > 
  > print(list(dic.values()))
  > # [7, 'female', 'Zara']
  > ```

### `dict.items()`

* 以列表返回可遍历的 (键, 值) 数组

  > ```python
  > dic = {'Name': 'Lsgogroup', 'Age': 7}
  > print(dic.items())
  > # dict_items([('Name', 'Lsgogroup'), ('Age', 7)])
  > 
  > print(tuple(dic.items()))
  > # (('Name', 'Lsgogroup'), ('Age', 7))
  > 
  > print(list(dic.items()))
  > # [('Name', 'Lsgogroup'), ('Age', 7)]
  > ```

### `dict.get(key, default=None)` 

* 返回指定键的值，如果值不在字典中返回默认值

  > ```python
  > dic = {'Name': 'Lsgogroup', 'Age': 27}
  > print("Age 值为 : %s" % dic.get('Age'))  # Age 值为 : 27
  > print("Sex 值为 : %s" % dic.get('Sex', "NA"))  # Sex 值为 : NA
  > print(dic)  # {'Name': 'Lsgogroup', 'Age': 27}
  > ```

### `dict.setdefault(key, default=None)`

* 和`get()`方法 类似, 如果键不存在于字典中，将会添加键并将值设为默认值

  > ```python
  > dic = {'Name': 'Lsgogroup', 'Age': 7}
  > print("Age 键的值为 : %s" % dic.setdefault('Age', None))  # Age 键的值为 : 7
  > print("Sex 键的值为 : %s" % dic.setdefault('Sex', None))  # Sex 键的值为 : None
  > print(dic)  
  > # {'Age': 7, 'Name': 'Lsgogroup', 'Sex': None}
  > ```

### `dict.copy()`

* 返回一个字典的浅复制

  > ```python
  > dic1 = {'Name': 'Lsgogroup', 'Age': 7, 'Class': 'First'}
  > dic2 = dic1.copy()
  > print(dic2)  
  > # {'Age': 7, 'Name': 'Lsgogroup', 'Class': 'First'}
  > ```

### `key in dict` 

* `in` 操作符用于判断键是否存在于字典中，如果键在字典 dict 里返回`true`，否则返回`false`。而`not in`操作符刚好相反，如果键在字典 dict 里返回`false`，否则返回`true`

### `dict.update(dict2)`

* 把字典参数 `dict2` 的 `key:value`对 更新到字典 `dict` 里

  > ```python
  > dic = {'Name': 'Lsgogroup', 'Age': 7}
  > dic2 = {'Sex': 'female', 'Age': 8}
  > dic.update(dic2)
  > print(dic)  
  > # {'Sex': 'female', 'Age': 8, 'Name': 'Lsgogroup'}
  > ```

## 删除字典中的值

* `dict.pop(key[,default])`**删除字典给定键 `key` 所对应的值**，返回值为被删除的值。`key` 值必须给出。若`key`不存在，则返回 `default` 值

- `del dict[key]` 删除字典给定键 `key` 所对应的值

  > ```python
  > dic1 = {1: "a", 2: [1, 2]}
  > print(dic1.pop(1), dic1)  # a {2: [1, 2]}
  > 
  > # 设置默认值，必须添加，否则报错
  > print(dic1.pop(3, "nokey"), dic1)  # nokey {2: [1, 2]}
  > 
  > del dic1[2]
  > print(dic1)  # {}
  > ```

* `dict.popitem()`随机返回并删除字典中的一对键和值，如果字典已经为空，却调用了此方法，就报出`KeyError`异常

* `dict.clear()`用于删除字典内所有元素

  > ```python
  > dic = {'Name': 'Zara', 'Age': 7}
  > print("字典长度 : %d" % len(dic))  # 字典长度 : 2
  > dic.clear()
  > print("字典删除后长度 : %d" % len(dic))  
  > # 字典删除后长度 : 0
  > ```

****

# 练习题

**1、字典基本操作**

字典内容如下:

```python
dic = {'python': 95, 'java': 99, 'c': 100}
```

用程序解答下面的题目

- 字典的长度是多少
- 请修改'java' 这个key对应的value值为98
- 删除 c 这个key
- 增加一个key-value对，key值为 php, value是90
- 获取所有的key值，存储在列表里
- 获取所有的value值，存储在列表里
- 判断 javascript 是否在字典中
- 获得字典里所有value 的和
- 获取字典里最大的value
- 获取字典里最小的value
- 字典 dic1 = {'php': 97}， 将dic1的数据更新到dic中

解答如下：

> ```python
> dic = {'python': 95, 'java': 99, 'c': 100}
> print(len(dic))
> dic['java'] = 98
> print(dic)
> dic.pop('c')
> print(dic)
> dic['pop'] = 90
> print(dic)
> lst1 = list(dic.keys())
> print(lst1, type(lst1))
> lst2 = list(dic.values())
> print(lst2)
> if 'javascript' in dic:
>     print(True)
> else:
>     print(False)
> value1 = sum(dic.values())
> print(value1)
> value2 = max(dic.values())
> print(value2)
> value3 = min(dic.values())
> print(value3)
> dic.update({'php': 97})
> print(dic)
> 
> ```

**2、字典中的value**

有一个字典，保存的是学生各个编程语言的成绩，内容如下

```
data = {
        'python': {'上学期': '90', '下学期': '95'},
        'c++': ['95', '96', '97'],
        'java': [{'月考':'90', '期中考试': '94', '期末考试': '98'}]
        }
```

各门课程的考试成绩存储方式并不相同，有的用字典，有的用列表，但是分数都是字符串类型，请实现函数`transfer_score(score_dict)`，将分数修改成int类型

答案如下：

```python
data = {'python': {'上学期': '90', '下学期': '95'},
        'c++': ['95', '96', '97'],
        'java': [{'月考': '90', '期中考试': '94', '期末考试': '98'}]}


def transfer_score(data0):
    if isinstance(data0, list):
        for i in range(len(data0)):
            if isinstance(data0[i], str):
                data0[i] = int(data0[i])
            else:
                data0[i] = transfer_score(data0[i])
        return data0
    elif isinstance(data0, dict):
        for item in data0.keys():
            if isinstance(data0[item], str):
                data0[item] = int(data0[item])
            else:
                data0[item] = transfer_score(data0[item])
        return data0


transfer_score(data)
print(data)

```













