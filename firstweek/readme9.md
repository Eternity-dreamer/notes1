# 第九天

# 1.17 文件与文件系统

## 打开文件

```python
open(file, mode='r', buffering=None, encoding=None, errors=None, newline=None, closefd=True)
# Open file and return a stream. Raise OSError upon failure.
# 打开文件，得到文件流对象，如果该文件无法被打开，会抛出OSError。
```

- `file`: 必需，文件路径（相对或者绝对路径）。
- `mode`: 可选，文件打开模式
- `buffering`: 设置缓冲
- `encoding`: 一般使用utf8
- `errors`: 报错级别
- `newline`: 区分换行符

常见的`mode`如下表所示：

| 打开模式 | 执行操作                                                     |
| -------- | ------------------------------------------------------------ |
| 'r'      | 以只读方式打开文件。文件的指针将会放在文件的开头。这是默认模式。 |
| 'w'      | 打开一个文件只用于写入。 如果该文件已存在则打开文件，并从开头开始编辑。 即原有内容会被删除。 如果该文件不存在，创建新文件。 |
| 'x'      | 写模式，新建一个文件，如果该文件已存在则会报错。             |
| 'a'      | 追加模式，打开一个文件用于追加。 如果该文件已存在，文件指针将会放在文件的结尾。 也就是说，新的内容将会被写入到已有内容之后。 如果该文件不存在，创建新文件进行写入。 |
| 'b'      | 以二进制模式打开文件。一般用于非文本文件，如：图片。         |
| 't'      | 以文本模式打开（默认）。一般用于文本文件，如：txt。          |
| '+'      | 可读写模式（可添加到其它模式中使用）                         |

## 文件对象方法

### `fileObject.close()` 

- 用于**关闭一个已打开的文件**。关闭后的文件不能再进行读写操作， 否则会触发`ValueError`错误

  > ```python
  > f = open("将进酒.txt")
  > print('FileName:', f.name)  # FileName: 将进酒.txt
  > f.close()
  > ```



### `fileObject.read([size])` 

- 用于**从文件读取指定的字符数**，如果**未给定或为负则读取所有**。

  > ```python
  > f = open('将进酒.txt', 'r')
  > line = f.read(20)
  > print("读取的字符串: %s" % line)
  > # 读取的字符串: 君不见，黄河之水天上来，奔流到海不复回。
  > 
  > f.close()
  > ```



### `fileObject.readline()`

- **读取整行**，包括 "\n" 字符。

  > ```python
  > f = open('将进酒.txt', 'r')
  > line = f.readline()
  > print("读取的字符串: %s" % line)
  > # 读取的字符串: 君不见，黄河之水天上来，奔流到海不复回。
  > f.close()
  > ```



### `fileObject.readlines()`

- 用于**读取所有行**(直到结束符 EOF)并返回列表，该列表可以由 Python 的 `for... in ...` 结构进行处理。

  > ```python
  > f = open('将进酒.txt', 'r')
  > lines = f.readlines()
  > print(lines)
  > 
  > for each in lines:
  >     each.strip()
  >     print(each)
  > 
  > # 君不见，黄河之水天上来，奔流到海不复回。
  > # 君不见，高堂明镜悲白发，朝如青丝暮成雪。
  > # 人生得意须尽欢，莫使金樽空对月。
  > # 天生我材必有用，千金散尽还复来。
  > # 烹羊宰牛且为乐，会须一饮三百杯。
  > # 岑夫子，丹丘生，将进酒，杯莫停。
  > # 与君歌一曲，请君为我倾耳听。
  > # 钟鼓馔玉不足贵，但愿长醉不复醒。
  > # 古来圣贤皆寂寞，惟有饮者留其名。
  > # 陈王昔时宴平乐，斗酒十千恣欢谑。
  > # 主人何为言少钱，径须沽取对君酌。
  > # 五花马，千金裘，呼儿将出换美酒，与尔同销万古愁。
  > 
  > f.close()
  > ```

  

### `fileObject.tell()`

- 返回文件的当前位置，即文件指针当前位置。



### `fileObject.seek(offset[, whence])`

- 用于移动文件读取指针到指定位置。

  - `offset`：开始的偏移量，也就是代表需要移动偏移的字节数，如果是负数表示从倒数第几位开始。
  - `whence`：可选，默认值为 0。给 `offset` 定义一个参数，表示要从哪个位置开始偏移；**0 代表从文件开头开始算起，1 代表从当前位置开始算起，2 代表从文件末尾算起。**

  > ```python
  > f = open('将进酒.txt', 'r')
  > line = f.readline()
  > print(line)
  > # 君不见，黄河之水天上来，奔流到海不复回。
  > line = f.readline()
  > print(line)
  > # 君不见，高堂明镜悲白发，朝如青丝暮成雪。
  > f.seek(0, 0)
  > line = f.readline()
  > print(line)
  > # 君不见，黄河之水天上来，奔流到海不复回。
  > f.close()
  > ```



### `fileObject.write(str)`

- 用于**向文件中写入指定字符串**，**返回的是写入的字符长度**。

  > ```python
  > f = open('workfile.txt', 'wb+')
  > print(f.write(b'0123456789abcdef'))  # 16
  > print(f.seek(5))  # 5
  > print(f.read(1))  # b'5'
  > print(f.seek(-3, 2))  # 13
  > print(f.read(1))  # b'd'
  > ```

- 在文件关闭前或缓冲区刷新前，字符串内容存储在缓冲区中，这时你在文件中是看不到写入的内容的。

- 如果文件打开模式带`b`，那写入文件内容时，`str`（参数）要用`encode`方法转为`bytes`形式，否则报错：`TypeError: a bytes-like object is required, not 'str'`。

  > ```python
  > f = open('将进酒.txt', 'r+')
  > str = '\n作者：李白'
  > f.seek(0, 2)
  > line = f.write(str)
  > f.seek(0, 0)
  > for each in f:
  >     print(each)
  > 
  > # 君不见，黄河之水天上来，奔流到海不复回。
  > # 君不见，高堂明镜悲白发，朝如青丝暮成雪。
  > # 人生得意须尽欢，莫使金樽空对月。
  > # 天生我材必有用，千金散尽还复来。
  > # 烹羊宰牛且为乐，会须一饮三百杯。
  > # 岑夫子，丹丘生，将进酒，杯莫停。
  > # 与君歌一曲，请君为我倾耳听。
  > # 钟鼓馔玉不足贵，但愿长醉不复醒。
  > # 古来圣贤皆寂寞，惟有饮者留其名。
  > # 陈王昔时宴平乐，斗酒十千恣欢谑。
  > # 主人何为言少钱，径须沽取对君酌。
  > # 五花马，千金裘，呼儿将出换美酒，与尔同销万古愁。
  > # 作者：李白
  > 
  > f.close()
  > ```



### `fileObject.writelines(sequence)`

- 向文件**写入一个序列字符串列表**，如果需要换行则要**自己加入每行的换行符`\n`**。

  > ```python
  > f = open('test.txt', 'w+')
  > seq = ['小马的程序人生\n', '老马的程序人生']
  > f.writelines(seq)
  > f.seek(0, 0)
  > for each in f:
  >     print(each)
  >     
  > # 小马的程序人生
  > # 老马的程序人生
  > f.close()
  > ```

  

## 简洁的with语句

- Python提供了一个with语句，利用这个语句抽象出文件操作中频繁使用的try/except/finally相关的细节。 对文件使用with语句，将可以大大减少你的代码量，而且不用担心文件打开了忘记关闭了（**with会自动帮你关闭文件**）。

- 关键词 with 语句就可以保证诸如文件之类的对象在使用完之后一定会正确的执行它的清理方法。

  > ```python
  > try:
  >     f = open('myfile.txt', 'w')
  >     for line in f:
  >         print(line)
  > except OSError as error:
  >     print('出错啦!%s' % str(error))
  > finally:
  >     f.close()
  > 
  > # 出错啦!not readable
  > ```

  使用with语句：

  > ```python
  > try:
  >     with open('myfile.txt', 'w') as f:
  >         for line in f:
  >             print(line)
  > except OSError as error:
  >     print('出错啦!%s' % str(error))
  > 
  > # 出错啦!not readable    
  > ```

## OS 模块中关于文件/目录常用的函数

- OS（Operation System）模块

## 序列化与反序列化

- Python 的 pickle 模块实现了基本的数据序列和反序列化。
  - 通过 pickle 模块的序列化操作我们能够将程序中运行的对象信息保存到文件中去，永久存储。
  - 通过 pickle 模块的反序列化操作，我们能够从文件中创建上一次程序保存的对象。

pickle模块中最常用的函数为：

- `pickle.dump(obj, file, [,protocol])` 

  - **将`obj`对象序列化存入已经打开的`file`中**。

  - `obj`：想要序列化的`obj`对象。
  - `file`:文件名称。
  - `protocol`：序列化使用的协议。如果该项省略，则默认为0。如果为负值或`HIGHEST_PROTOCOL`，则使用最高的协议版本。

- `pickle.load(file)` 

  - **将`file`中的对象序列化读出**。

  - `file`：文件名称。





------

# 练习题

**1、打开中文字符的文档时，会出现乱码，Python自带的打开文件是否可以指定文字编码？还是只能用相关函数？**

解答：



> 可以指定
>
> ```python
> open(file, mode=‘r’, buffering=None, encoding=None, errors=None, newline=None, closefd=True)
> ```
>
>
> 在mode中设置文件打开的编码形式

**2、编写程序查找最长的单词**

输入文档: res/test.txt

题目说明:

```
"""
   
Input file
   test.txt
   
Output file
   ['general-purpose,', 'object-oriented,']
   
"""
def longest_word(filename):
    # your code here
        pass
```

参考解答：

> ```python
> def longest_word(filename):
>     try:
>         with open(filename, 'r', encoding='UTF-8') as f:
>             lis = []
>             string1 = f.read().split(' ')
>             s = [[x, len(x)] for x in string1]
>             s = sorted(s, key=lambda x: x[1], reverse=True)
>             for x in s:
>                 if x[1] < s[0][1]:
>                     break
>                 lis.append(x[0])
>             return lis
>     except OSError as error:
>         print('出错啦!%s' % str(error))
> 
> 
> word1 = longest_word('test.txt')
> print(word1)
> 
> ```















