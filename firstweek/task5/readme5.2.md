# 第五天

# 1.10 集合

## 集合定义

**集合（set）是一个无序的不重复元素序列**

* `set`与`dict`类似，也是一组`key`的集合，但**不存储`value`**，由于`key`不能重复，所以在`set`中，没有重复的`key`
* 集合为可变数据类型
* 集合的两个特点：无序 (unordered) 和唯一 (unique)
* 由于 `set` 存储的是无序集合，所以我们不可以为集合创建索引或执行切片(slice)操作，也没有键(keys)可用来获取集合中元素的值，但是可以判断一个元素是否在集合中

## 创建集合

 ### 先创建空集合

- 先创建对象再加入元素。
- 在创建空集合的时候**只能使用`s = set()`**，因为`s = {}`创建的是空字典。

> ```python
> basket = set()
> basket.add('apple')
> basket.add('banana')
> print(basket)  # {'banana', 'apple'}
> ```

### 直接创建

- 直接把一堆元素用花括号括起来`{元素1, 元素2, ..., 元素n}`。

- 重复元素在`set`中会被自动被过滤。

  > ```python
  > basket = {'apple', 'orange', 'apple', 'pear', 'orange', 'banana'}
  > print(basket)  # {'banana', 'apple', 'pear', 'orange'}
  > ```

  > ```python
  > lst = [0, 1, 2, 3, 4, 5, 5, 3, 1]
  > 
  > temp = []
  > for item in lst:
  >     if item not in temp:
  >         temp.append(item)
  > 
  > print(temp)  # [0, 1, 2, 3, 4, 5]
  > 
  > a = set(lst)
  > print(list(a))  # [0, 1, 2, 3, 4, 5]
  > ```

### 使用`set(value)`

* 使用`set(value)`工厂函数，把列表或元组转换成集合

  > ```python
  > a = set('abracadabra')
  > print(a)  
  > # {'r', 'b', 'd', 'c', 'a'}
  > 
  > b = set(("Google", "Lsgogroup", "Taobao", "Taobao"))
  > print(b)  
  > # {'Taobao', 'Lsgogroup', 'Google'}
  > 
  > c = set(["Google", "Lsgogroup", "Taobao", "Google"])
  > print(c)  
  > # {'Taobao', 'Lsgogroup', 'Google'}
  > ```

## 访问集合中的值

- 可以使用`len()`內建函数得到集合的大小

  > ```python
  > s = set(['Google', 'Baidu', 'Taobao'])
  > print(len(s))  # 3
  > ```

- 可以使用`for`把集合中的数据一个个读取出来

  > ```python
  > s = set(['Google', 'Baidu', 'Taobao'])
  > for item in s:
  >     print(item)
  > 
  > # Baidu
  > # Google
  > # Taobao
  > ```

- 可以通过`in`或`not in`判断一个元素是否在集合中已经存在

  > ```python
  > s = set(['Google', 'Baidu', 'Taobao'])
  > print('Taobao' in s)  # True
  > print('Facebook' not in s)  # True
  > ```

## 集合的内置方法

### `set.add(elmnt)`

* **用于给集合添加元素**，如果添加的元素在集合中已存在，则不执行任何操作

  > ```python
  > fruits = {"apple", "banana", "cherry"}
  > fruits.add("orange")
  > print(fruits)  
  > # {'orange', 'cherry', 'banana', 'apple'}
  > 
  > fruits.add("apple")
  > print(fruits)  
  > # {'orange', 'cherry', 'banana', 'apple'}
  > ```

### `set.update(set)`

* **用于修改当前集合**，可以添加新的元素或集合到当前集合中，如果添加的元素在集合中已存在，则该元素只会出现一次，重复的会忽略

  > ```python
  > x = {"apple", "banana", "cherry"}
  > y = {"google", "baidu", "apple"}
  > x.update(y)
  > print(x)
  > # {'cherry', 'banana', 'apple', 'google', 'baidu'}
  > 
  > y.update(["lsgo", "dreamtech"])
  > print(y)
  > # {'lsgo', 'baidu', 'dreamtech', 'apple', 'google'}
  > ```

### `set.remove(item)` 

* 用于移除集合中的指定元素。如果元素不存在，则会发生错误

  > ```python
  > fruits = {"apple", "banana", "cherry"}
  > fruits.remove("banana")
  > print(fruits)  # {'apple', 'cherry'}
  > ```

### `set.discard(value)` 

* 用于移除指定的集合元素。`remove()` 方法在移除一个不存在的元素时会发生错误，而 `discard()` 方法不会

  > ```python
  > fruits = {"apple", "banana", "cherry"}
  > fruits.discard("banana")
  > print(fruits)  # {'apple', 'cherry'}
  > ```

### `set.pop()` 

* 用于**随机移除**一个元素

  > ```python
  > fruits = {"apple", "banana", "cherry"}
  > x = fruits.pop()
  > print(fruits)  # {'cherry', 'apple'}
  > print(x)  # banana
  > ```

### 交集

- `set.intersection(set1, set2)` 返回两个集合的交集。

- `set1 & set2` 返回两个集合的交集。

- `set.intersection_update(set1, set2)` 交集，在原始的集合上移除不重叠的元素。

  > ```python
  > a = set('abracadabra')
  > b = set('alacazam')
  > print(a)  # {'r', 'a', 'c', 'b', 'd'}
  > print(b)  # {'c', 'a', 'l', 'm', 'z'}
  > 
  > c = a.intersection(b)
  > print(c)  # {'a', 'c'}
  > print(a & b)  # {'c', 'a'}
  > print(a)  # {'a', 'r', 'c', 'b', 'd'}
  > 
  > a.intersection_update(b)
  > print(a)  # {'a', 'c'}
  > ```

### 并集

- `set.union(set1, set2)` 返回两个集合的并集。

- `set1 | set2` 返回两个集合的并集

  > ```python
  > a = set('abracadabra')
  > b = set('alacazam')
  > print(a)  # {'r', 'a', 'c', 'b', 'd'}
  > print(b)  # {'c', 'a', 'l', 'm', 'z'}
  > 
  > print(a | b)  
  > # {'l', 'd', 'm', 'b', 'a', 'r', 'z', 'c'}
  > 
  > c = a.union(b)
  > print(c)  
  > # {'c', 'a', 'd', 'm', 'r', 'b', 'z', 'l'}
  > ```

### 差集

- `set.difference(set)` 返回集合的差集。

- `set1 - set2` 返回集合的差集。

- `set.difference_update(set)` 集合的差集，在原来的集合中移除元素，没有返回值

  > ```python
  > a = set('abracadabra')
  > b = set('alacazam')
  > print(a)  # {'r', 'a', 'c', 'b', 'd'}
  > print(b)  # {'c', 'a', 'l', 'm', 'z'}
  > 
  > c = a.difference(b)
  > print(c)  # {'b', 'd', 'r'}
  > print(a - b)  # {'d', 'b', 'r'}
  > 
  > print(a)  # {'r', 'd', 'c', 'a', 'b'}
  > a.difference_update(b)
  > print(a)  # {'d', 'r', 'b'}
  > ```

### 集合的异或

- `set.symmetric_difference(set)`返回集合的异或。

- `set1 ^ set2` 返回集合的异或。

- `set.symmetric_difference_update(set)`移除当前集合中在另外一个指定集合相同的元素，并将另外一个指定集合中不同的元素插入到当前集合中。

  > ```python
  > a = set('abracadabra')
  > b = set('alacazam')
  > print(a)  # {'r', 'a', 'c', 'b', 'd'}
  > print(b)  # {'c', 'a', 'l', 'm', 'z'}
  > 
  > c = a.symmetric_difference(b)
  > print(c)  # {'m', 'r', 'l', 'b', 'z', 'd'}
  > print(a ^ b)  # {'m', 'r', 'l', 'b', 'z', 'd'}
  > 
  > print(a)  # {'r', 'd', 'c', 'a', 'b'}
  > a.symmetric_difference_update(b)
  > print(a)  # {'r', 'b', 'm', 'l', 'z', 'd'}
  > ```

## 集合的转换

* 集合，列表，元组的转换

> ```python
> se = set(range(4))
> li = list(se)
> tu = tuple(se)
> 
> print(se, type(se))  # {0, 1, 2, 3} <class 'set'>
> print(li, type(li))  # [0, 1, 2, 3] <class 'list'>
> print(tu, type(tu))  # (0, 1, 2, 3) <class 'tuple'>
> ```

## 不可变集合

* Python 提供了**不能改变元素的集合**的实现版本，即**不能增加或删除元素**，类型名叫`frozenset`。需要注意的是`frozenset`仍然可以进行集合操作，只是**不能用带有`update`的方法**

- `frozenset([iterable])` 返回一个冻结的集合，冻结后集合不能再添加或删除任何元素。

  > ```python
  > a = frozenset(range(10))  # 生成一个新的不可变集合
  > print(a)  
  > # frozenset({0, 1, 2, 3, 4, 5, 6, 7, 8, 9})
  > 
  > b = frozenset('lsgogroup')
  > print(b)  
  > # frozenset({'g', 's', 'p', 'r', 'u', 'o', 'l'})
  > ```

****

# 练习题

1. **怎么表示只包含⼀个数字1的元组。**
2. **创建一个空集合，增加 {‘x’,‘y’,‘z’} 三个元素。**
3. **列表['A', 'B', 'A', 'B']去重。**
4. **求两个集合{6, 7, 8}，{7, 8, 9}中不重复的元素（差集指的是两个集合交集外的部分）。**
5. **求{'A', 'B', 'C'}中元素在 {'B', 'C', 'D'}中出现的次数。**

```python
tup1 = (1,)
print(tup1, type(tup1))

set1 = set()
set1.update(['x', 'y', 'z'])
print(set1)

list1 = ['A', 'B', 'A', 'B']
set2 = set(list1)
print(list(set2))

set3 = {6, 7, 8}
set4 = {7, 8, 9}
print(set3 ^ set4)

set5 = {'A', 'B', 'C'}
set6 = {'B', 'C', 'C'}
print(len(set5 & set6))

```

















