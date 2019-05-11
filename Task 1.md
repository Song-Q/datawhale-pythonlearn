### 1.环境搭建
#### Anaconda环境配置
通过官网下载并安装Anaconda，在系统设置的PATH中检查Python已被添加到系统路径，打开Anaconda Prompt,输入python，返回python版本信息，并进入python编译环境。
#### 解释器
当我们编写Python代码时，我们得到的是一个包含Python代码的以.py为扩展名的文本文件。要运行代码，就需要Python解释器去执行.py文件。
CPython
这个解释器是用C语言开发的，所以叫CPython。在命令行下运行python就是启动CPython解释器。
其他类型的解释器，见：https://www.liaoxuefeng.com/wiki/897692888725344/966138843228672

### 2.python初体验
#### print and input
```python
name = input('Please enter your name:')
print('hello,', name)
```

### 3.基础讲解
#### python变量特性+命名规则
变量的概念基本上和初中代数的方程变量是一致的，只是在计算机程序中，变量不仅可以是数字，还可以是任意数据类型。
变量在程序中就是用一个变量名表示了，变量名必须是大小写英文、数字和_的组合，且不能用数字开头。
理解变量在计算机内存中的表示也非常重要。当我们写：
a = 'ABC'
时，Python 解释器干了两件事情：
1. 在内存中创建了一个'ABC'的字符串；
2. 在内存中创建了一个名为a的变量，并把它指向'ABC'。
#### 注释方法
python的单行注释只需要在需要被注释的语句或者代码前加#
```python
#这是一个注释行
```
#### python中:的作用是提示符
#### 学会使用dir( )及和help( )
如果要获得一个对象的所有属性和方法，可以使用dir()函数，它返回一个包含字符串的list
比如，获得一个str 对象的所有属性和方法：
```python
>>> dir('ABC')
['__add__', '__class__', '__contains__', '__delattr__', '__dir__', '__doc__', '__eq__', '__format__', '__ge__', '__getattribute__', '__getitem__', '__getnewargs__', '__gt__', '__hash__', '__init__', '__iter__', '__le__', '__len__', '__lt__', '__mod__', '__mul__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__rmod__', '__rmul__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', 'capitalize', 'casefold', 'center', 'count', 'encode', 'endswith', 'expandtabs', 'find', 'format', 'format_map', 'index', 'isalnum', 'isalpha', 'isdecimal', 'isdigit', 'isidentifier', 'islower', 'isnumeric', 'isprintable', 'isspace', 'istitle', 'isupper', 'join', 'ljust', 'lower', 'lstrip', 'maketrans', 'partition', 'replace', 'rfind', 'rindex', 'rjust', 'rpartition', 'rsplit', 'rstrip', 'split', 'splitlines', 'startswith', 'strip', 'swapcase', 'title', 'translate', 'upper', 'zfill']
```
help函数帮助我们了解模块、类型、对象、方法、属性的详细信息
#### import使用
1.module
通常模块为一个文件，直接使用import来导入就好了。可以作为module的文件类型有".py"、".pyo"、".pyc"、".pyd"、".so"、".dll"。
2.package
通常包总是一个目录，可以使用import导入包，或者from + import来导入包中的部分模块。包目录下为首的一个文件便是 __init__.py。然后是一些模块文件和子目录，假如子目录中也有 __init__.py 那么它就是这个包的子包了。
相关详细内容：https://www.cnblogs.com/kungfupanda/p/5257174.html
#### pep8介绍
pep8是python编程风格的代码规范，其详细要求可以从python官网中学到。
https://www.python.org/dev/peps/pep-0008/

### 4.python数值基本知识
#### python中数值类型，int，float，bool，e记法等
计算机能处理的远不止数值，还可以处理文本、图形、音频、视频、网页等各种各样的数据，不同的数据，需要定义不同的数据类型。
##### int 
Python 可以处理任意大小的整数，当然包括负整数，在程序中的表示方法和数学上的写法一模一样
##### float
浮点数也就是小数，之所以称为浮点数，是因为按照科学记数法表示时，一个浮点数的小数点位置是可变的。整数和浮点数在计算机内部存储的方式是不同的，整数运算永远是精确的（除法难道也是精确的？是的！），而浮点数运算则可能会有四舍五入的误差。
##### bool
布尔值和布尔代数的表示完全一致，一个布尔值只有True、False两种值，要么是True，要么是False，在Python 中，可以直接用True、False表示布尔值（请注意大小写），也可以通过布尔运算计算出来
##### e记法
对于很大或很小的浮点数，就必须用科学计数法表示，把10 用e 替代，1.23x10^9 就是1.23e9，或者12.3e8，0.000012 可以写成1.2e-5，等等。

#### 算数运算符
python算数运算符包括：
+（加法）
```python
>>> 1 + 2
3
```
-（减法）
```python
>>> 5 - 2
3
```
*（乘法）
```python
>>> 5 * 2
10
```

**（幂运算）
```python
>>> 5 ** 3
125
```
/（除法）
```python
>>> 7 / 3
2.3333333333333335
```
//（整除）
```python
10 // 4
2
```
%（取余）。
```python
10 % 3
1
```
#### 逻辑运算符
and运算是与运算，只有所有都为True，and运算结果才是True
or运算是或运算，只要其中有一个为True，or运算结果就是True：
not运算是非运算，它是一个单目运算符，把True变成False，False变成True：
#### 成员运算符

#### 身份运算符
in  
如果在指定的序列中找到值返回 True，否则返回 False。  
not in  
如果在指定的序列中没有找到值返回 True，否则返回 False。
```python
>>> list = [1, 3, 5, 7, 8, 9]
>>> a = 2
>>> b = 7
>>> a in list
False
>>> b in list
True
```
#### 运算符优先级

运算符 |描述 |  
---- |----- |  
** |指数 (最高优先级) |  
~ + -、 |按位翻转, 一元加号和减号 (最后两个的方法名为 +@ 和 -@) |    
/ * % // |乘，除，取模和取整除 |  
+- |加法减法 |  
\>><< |右移，左移运算符 |  
& |位 'AND' |  
^\| |位运算符 |  
<= < > >= |比较运算符 |  
<> == != |等于运算符|  
= %= /= //= -= += *= **= |赋值运算符 |  
is is not |身份运算符 |  
in not in |成员运算符 |  
not and or |逻辑运算符 |  

### 参考文献
Python3基础教程 廖雪峰

