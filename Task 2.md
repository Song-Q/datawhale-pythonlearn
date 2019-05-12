### 1.list
list 是一种有序的集合，可以随时添加和删除其中的元素。
#### 标志
列表的标志符号是[]
#### 基本操作(创建，append( )，pop( ) ,del( ), 拷贝）
创建  
用索引来访问list 中每一个位置的元素,list的索引从0开始,并且可以倒着获得索引。
```python
classmates = ['Michael', 'Bob', 'Tracy']
>>>classmates[-1]  
Michael
>>>classmates[-1]  
Tracy
```
append()  
向list中追加元素到末尾
```python
classmates.append('Adam')
```
insert()  
将元素插入到指定索引位置
```python
classmates.insert(1, 'Jack')
```
pop()  
.pop()从末尾依次删除一个元素
```python
classmates.pop(1)    #删除指定索引的元素
```
list.copy()  
```python
>>>list1 = ['Google', 'Runoob', 'Taobao', 'Baidu']
>>>list2 = list1.copy()
>>>print ("list2 列表: ", list2)
list2 列表:  ['Google', 'Runoob', 'Taobao', 'Baidu']
```
#### 列表相关方法
用len()函数可以获得list 元素的个数：
```python
>>>L = []
>>>len(L)
0
```
ist 元素也可以是另一个list  
```python
>>> s = ['python', 'java', ['asp', 'php'], 'scheme']
>>>s[2][1]
php
```

### 2.tuple
tuple一旦初始化就不可修改（即元素的指向不可改变），没有append(),insert(),其它获取元素的方法与list相同
#### 标志
列表的标志符号是()
#### 基本操作（创建及不可变性）
创建
```python
classmates = ('Michael', 'Bob', 'Tracy')
```
因为tuple 不可变，所以代码更安全。当你定义一个tuple 时，在定义的时候，tuple 的元素就必须被确定下来。  
只有1 个元素的tuple 定义时必须加一个逗号,，来消除歧义：
```pyhton
>>> t = (1,)
>>>t
(1,)
```

### 3.string字符串
#### 定义及基本操作（+，*，读取方式）
字符串是以单引号'或双引号"括起来的任意文本，比如'abc'，"xyz"等等。
+ 字符串连接  
```python
>>> a = 'Hello'
>>> b = 'Python'
>>> a + b
'HelloPython'
```
* 重复输出字符串  
```python
>>> a * 2
'HelloHello'
```
[] 通过索引获取字符串中字符
```python
>>> a[1]
'e'
>>> a[1:4]
'ell'
```
#### 字符串相关方法
转义字符\可以转义很多字符，比如\n表示换行，\t表示制表符，字符\本身也要转义，所以\\表示的字符就是\  
```python
>>>'I\'m \"OK\"!'
I'm "OK"!
```
in 成员运算符 如果字符串中包含给定的字符返回 True  
```python 
>>> 'H' in a
True
```
not in 成员运算符 如果字符串中不包含给定的字符返回 True
```python 
>>> 'M' not in a
True
```
r/R 原始字符串 - 原始字符串：所有的字符串都是直接按照字面的意思来使用，没有转义特殊或不能打印的字符。 原始字符串除在字符串的第一个引号前加上字母"r"（可以大小写）以外，与普通字符串有着几乎完全相同的语法。
```python
>>> print(r'\n')
\n
>>> print(R'\n')
\n
```

### 4.字符串格式化问题
在Python 中，采用的格式化方式和C 语言是一致的，用%实现.
```python
>>> 'Hello, %s' % 'world'
'Hello, world'
```
常见的占位符有:  
%d 整数  
%f 浮点数  
%s 字符串  
%x 十六进制整数  
有些时候，字符串里面的%是一个普通字符怎么办？这个时候就需要转义，用%%来表示一个%：
```pyhton
>>> 'growth rate: %d %%' % 7
'growth rate: 7 %'
```
  
### 参考文献
https://www.runoob.com/python/python-strings.html
