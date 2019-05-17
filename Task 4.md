### 1.函数关键字
关键字是python内置的，具有特殊意义的标识符，自定义标识符命名时不可与之重复。可通过以下代码查看python内置的关键字内容
```python
import keyword
print(keyword.kwlist)
```
['False', 'None', 'True', 'and', 'as', 'assert', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
### 2.函数的定义
在Python 中，定义一个函数要使用def语句，依次写出函数名、括号、括号中的参数和冒号:，然后，在缩进块中编写函数体，函数的返回值用return语句返回。
```python
def my_abs(x):
    if x >= 0:
        return x
    else:
        return -x
```
### 3.函数参数与作用域
#### 函数参数
对于函数的调用者来说，只需要知道如何传递正确的参数，以及函数将返回什么样的值就够了，函数内部的复杂逻辑被封装起来，调用者无需了解。除了正常定义的必选参数外，还可以使用默认参数、可变参数和关键字参数，使得函数定义出来的接口，不但能处理复杂的参数，还可以简化调用者的代码。

#### 作用域
Python 中，程序的变量并不是在哪个位置都可以访问的，访问权限决定于这个变量是在哪里赋值的。
变量的作用域决定了在哪一部分程序可以访问哪个特定的变量名称。Python的作用域一共有4种，分别是：  
L （Local） 局部作用域  
E （Enclosing） 闭包函数外的函数中  
G （Global） 全局作用域  
B （Built-in） 内置作用域（内置函数所在模块的范围）  
### 4.函数返回值
如果没有return语句，函数执行完毕后也会返回结果，只是结果为None。return None可以简写为return。  
如果有必要，可以先对参数的数据类型做检查；函数体内部可以用return随时返回函数结果；函数执行完毕也没有return语句时，自动return None。  
函数可以同时返回多个值，但其实就是一个tuple
### 5.file
#### 打开文件方式（读写两种方式）
#### 读文件
要以读文件的模式打开一个文件对象，使用Python 内置的open()函数，传入文件名和标示符：
```python
>>> f = open('/Users/michael/test.txt', 'r')
```
如果文件不存在，open()函数就会抛出一个IOError的错误。  
如果文件打开成功，接下来，调用read()方法可以一次读取文件的全部内容，Python 把内容读到内存，用一个str对象表示：
```python
>>> f = read()
'Hello, world!'
```
调用close()方法关闭文件。文件使用完毕后必须关闭，因为文件对象会占用操作系统的资源，并且操作系统同一时间能打开的文件数量也是有限的：
```python
>>> f.close()
```

#### 文件对象的操作方法
#### 学习对excel及csv文件进行操作
### 6.os模块
### 7.datetime模块
