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
如果没有return语句，函数执行完毕后也会返回结果，只是结果为None。return None可以简写为return。
### 3.函数参数与作用域

### 4.函数返回值
### 5.file
#### 打开文件方式（读写两种方式）
#### 文件对象的操作方法
#### 学习对excel及csv文件进行操作
### 6.os模块
### 7.datetime模块
