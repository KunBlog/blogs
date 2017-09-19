# Python之路 - 字符串

<!-- TOC -->

- [Python之路 - 字符串](#python之路---字符串)
    - [字符串（str）🍀](#字符串str🍀)
    - [字符串方法 🍀](#字符串方法-🍀)
    - [字符串补充 🍀](#字符串补充-🍀)

<!-- /TOC -->

## 字符串（str）🍀

字符串类型是Python中的基础数据类型。字符串是序列类型（有序），字符串中每一个字符都是一个元素。**字符串是不可变的**，所以字符串操作都是重新创建了一个新的字符串。

创建字符串可以使用单引号、双引号、三引号来进行，如下：

```python
>>> name = 'Lyon'
>>> name = "Lyon"
>>> name = '''Lyon'''
>>> name = """Lyon"""
```

查看数据类型  👈

~~~ python
>>> name = 'Lyon'
# type用于查看变量的数据类型
>>> type(name)
<class 'str'>
~~~

在我们创建一个字符串时，python解释器为我们做了一件这样的事：

~~~ python
>>> name = 'Lyon'
# 解释器做的事：name = str('Lyon')
~~~

​所以其实创建字符串就是利用的`str()`方法     

## 字符串方法 🍀 

字符串中有很多的`内置方法`供我们使用，接下来就来讲讲各个方法

> ​`str.strip`([*chars*]) :   👈

去除特定字符，常用来去除空格 

*chars* : 默认去除空格，可规定字符

```python
>>> name = ' Ly on '
>>> name.strip()
# 去除了name左右两边的空格
'Ly on'
```

 *PS：strip()只能去除字符串两边的特定字符，并不能去除字符串中间的特定字符 。还有lstrip和rstrip ，分别用于去除字符串左边和右边的字符。* 

> `str.split`(*sep=None*, *maxsplit=-1*) :   👈

切割字符串，返回一个列表

sep* : 默认为空，规定切割格式

*maxsplit* : 默认按规则全部切割，可以自己规定切割次数

``` python
>>> name = 'Lyon'
>>> name.split('o')
['Ly', 'n']
>>> name.split('m')
['Lyon']
```

> `str.join`(*iterable*) : 👈

将可迭代对象用str进行拼接，返回一个字符串 

iterable* : 可迭代对象，如：字符串、元组、列表等

```python
>>> name = 'Lyon'
>>> ' '.join(name)
'L y o n'
# 迭代对象中的元素也必须为字符串
>>> nums = ['1','2','3','4']
# 以'+'进行拼接
>>> '+'.nums
'1+2+3+4'
```

> `str.isdigit`() :   👈

判断字符串中是否仅含数字，返回bool值

```python
>>> num = '123456789'
>>> num.isdigit()
True
>>> num = 'some4587'
>>> num.isdigit()
False
```

> `str.replace`(*old*, *new*[, *count*]) :  👈

替换字符串中的字符，返回新字符串

*old* : 替换前的字符

*new* : 替换后的字符

*count* : 替换次数，默认为替换整个字符串

```python
>>> name = 'Lyon'
>>> name.replace('L','l')
'lyon'
>>> name = 'Hello Word'
#替换1次，replace为从左往右开始替换
>>> name.replace('l','L',1)
'HeLlo Word'
```

> `str.format`(\*args, \*\*kwargs) :   👈

格式化输出，用' {} '占位

```python
# 按照位置传值
>>> '{}-{}-{}'.format('Lyon','Hubei','Wuhan')
'Lyon-Hubei-Wuhan'
# 按照关键字传值
>>> '{name}-{province}-{city}'.format(city='Wuhan',name='Lyon',province='Hubei')
'Lyon-Hubei-Wuhan'
# 按照索引传值
>>> '{1}-{0}-{1}'.format('Hubei','Lyon')
'Lyon-Hubei-Lyon'
```

*PS：格式化输出还有一个 % 的方式，不过 % 是从C语言里面借鉴过来的，而format才是python自己的东西。官方推荐用 format。*

> `str.capitalize`() :  👈

首字母大写

```python
>>> name = 'lyon'
>>> name.capitalize()
>>> 'Lyon'
```

> `str.count`(*sub*[, *start*[, *end*]]) :  👈

统计数量

*sub* :  要统计的子串

*start* : 设置统计范围的开始位置

*end* : 设置统计范围的结束位置

```python
>>> name = 'Alex'
>>> name.count('A')
1
# 统计范围下标1-3不包括3
>>> name.count('x',1,3)
0
>>> name.count('x',1,4)
1
```

`str.center`(*width*[, *fillchar*]) :  👈

中间对齐填充

*width* : 规定宽度，不够则补。往两边填充

*fillchar* : 填充字符

```python
>>> name = 'Lyon'
>>> name.center(20,'-')
'--------Lyon--------'
```

*PS* : `str.ljust(width,[fillchar]) `  左对齐，即向右填充；`str.rjust(width,[fillchar])`  右对齐，即向左填充；`str.zfill(width)`  右对齐，用0填充。

> `str.find`(*sub*[, *start*[, *end*]]) :  👈

查找子串，找到返回子串中第一个字符的下标，没找到返回-1

*sub* : 需要查找的子串

*start* : 设置查找范围的开始位置

*end* : 设置查找范围的结束位置

```python
>>> name = 'Lyon'
>>> name.find('L')
0
>>> name.find('s')
-1
>>> name.find('Ly')
0
>>> name.find('yn')
-1
```

*PS：find为从左往右查找，找到第一个就停止查找并返回下标；rfind 从右往左查找，找到第一个就停止查找并返回下标*

> `str.startswith`(*prefix*[, *start*[, *end*]])  :   👈

判断字符串是否以*prefix* 开头，返回bool值

*start* : 设置查找范围的开始位置

*end*  : 设置查找范围的结束位置

```python
>>> name = 'Lyon'
>>> name.startswith('L')
True
>>> name.startswith('y')
False
```

> `str.endswith`(*suffix*[, *start*[, *end*]])  : 👈

判断字符串是否以*suffix* 结尾，返回bool 值

*start*  : 设置查找范围的开始位置

*end*  : 设置查找范围的结束位置

```python
>>> name = 'Lyon'
>>> name.endswith('n')
True
>>> name.endswith('L')
False
```

> `str.index`(*sub*[, *start*[, *end*]])  :  👈

返回子串第一个元素的下标，没有就会报错

*sub*  : 子串内容

*start*  : 设置查找范围的开始位置

*end*  :  设置查找范围的结束位置

```python
>>> name = 'Lyon'
>>> name.index('L')
0
>>> name.index('yo')
1
# 没找到直接报错
>>> name.index('s')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: substring not found
```

*PS：rindex从右往左找*

> `str.lower`() :  👈

将字母转换成小写

```python
>>> name = 'LYON'
>>> name.lower()
'lyon'
```

> `str.upper`()  :   👈

将字母转换成大写

```python
>>> name = 'lyon'
>>> name.upper()
'LYON'
```

> `str.encode`(*encoding="utf-8"*, *errors="strict"*) :  👈

将字符串按照指定编码转换成bytes类型，默认编码utf-8

```python
>>> name = 'Lyon'
>>> name.encode()
# 字符串前面加b代表为bytes类型
b'Lyon'
```

> `str.splitlines`([*keepends*]) :   👈

官方的例子如下：

```python
>>> 'ab c\n\nde fg\rkl\r\n'.splitlines()
['ab c', '', 'de fg', 'kl']
>>> 'ab c\n\nde fg\rkl\r\n'.splitlines(keepends=True)
['ab c\n', '\n', 'de fg\r', 'kl\r\n']
```

编码与解码问题会放在字符编码一篇中进行详解

## 字符串补充 🍀 

字符串其他内置方法    

```python
str.isalnum()        #是否全是字母和数字，并至少有一个字符
str.isalpha()		 #是否全是字符，并且至少有一个字符　
#三者不能判断浮点数
str.isdigit()        #是否为纯数字，不可判断中文和罗马数字
str.isnumeric()      #可判断中文数字和罗马数字 
str.isdecimal()      #是否是十进制数字 
'''
总结:
    最常用的是isdigit,可以判断bytes和unicode类型,这也是最常见的数字应用场景
    如果要判断中文数字或罗马数字,则需要用到isnumeric
'''
str.islower()        #是否全为小写
str.isupper()        #是否全为大写 
str.isspace()        #是否全是空白字符，并至少有一个字符
str.istitle()        #首字母是否全为大写
str.isidentifier()   
'''
检测name是否可以被当作标标志符，即是否符合变量命名规则 
'''
str.swapcase()       #大小写互换
str.partition(sep)   
'''
以sep为分隔符，返回一个包含三个元素的元组，元素顺序为，分隔符前、分隔符、分隔符后；如果没有找到则前后个为空，第一个为原str
'''
str.rpartition(sep)  #同上，没找到则前两个为空，第三个为原str
str.expandtabs(tabsize=8)   
'''
把str中的tab字符替换没空格，每个tab替换为tabsize个空格，默认是8个
'''
str.format_map(mapping)  #不知道干嘛用的
'''
>>> class Default(dict):
...     def __missing__(self, key):
...         return key
...
>>> '{name} was born in {country}'.format_map(Default(name='Guido'))
'Guido was born in country'
'''
str.maketrans(from, to)    
'''
返回一个256个字符组成的翻译表，其中from中的字符被一一对应地转换成to，所以from和to必须是等长的。 
'''
str.translate(table[,deletechars])   
'''
使用上面的函数产后的翻译表，把S进行翻译，并把deletechars中有的字符删掉。需要注意的是，如果str为unicode字符串，那么就不支持 deletechars参数，可以使用把某个字符翻译为None的方式实现相同的功能。此外还可以使用codecs模块的功能来创建更加功能强大的翻译表。
'''
```

字符串拼接

可利用 ' + '，print时可用' , '连接

```python
>>> name = 'Lyon'
>>> res = name + 'Lyon'
>>> res
LyonLyon
>>> print("i am",name)
i am Lyon
```

字符串可进行切片操作

```python
>>> name = 'Lyon'
#不包括2
>>> name[0:2]
'Ly'
#隔一个取一个
>>> name[0:3:2]
'Lo'
```


