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
函数可以同时返回多个值，但其实就是一个tuple。  
函数的相关知识可参考：https://www.runoob.com/python3/python3-function.html
### 5.file
#### 打开文件方式（读写两种方式）
#### 读文件
要以读文件的模式打开一个文件对象，使用Python 内置的open()函数，传入文件名和标示符：
```python
>>> f = open('/Users/michael/test.txt', 'r')
```
如果文件不存在，open()函数就会抛出一个IOError的错误。  

#### 写文件
写文件和读文件是一样的，唯一区别是调用open()函数时，传入标识符'w'或者'wb'表示写文本文件或写二进制文件：
```python
>>> f = open('/Users/michael/test.txt', 'w')
>>> f.write('Hello, world!')
>>> f.close()
```

#### 文件对象的操作方法
如果文件打开成功，接下来，调用read()方法可以一次读取文件的全部内容，Python 把内容读到内存，用一个str对象表示：
```python
>>> f = read()
'Hello, world!'
```
要保险起见，可以反复调用read(size)方法，每次最多读取size 个字节的内容。另外，调用readline()可以每次读取一行内容，调用readlines()一次读取所有内容并按行返回list。  
调用close()方法关闭文件。文件使用完毕后必须关闭，因为文件对象会占用操作系统的资源，并且操作系统同一时间能打开的文件数量也是有限的：  
```python
>>> f.close()
```
Python 引入了with语句来自动帮我们调用close()方法：
```python
with open('/path/to/file', 'r') as f:
    print(f.read())
```
要读取二进制文件，比如图片、视频等等，用'rb'模式打开文件即可：
```python
>>> f = open('/Users/michael/test.jpg', 'rb')
```
#### 学习对excel及csv文件进行操作
1.读写csv文件
```python
import csv

#读取csv文件内容方法1
csv_file = csv.reader(open('testdata.csv','r'))
next(csv_file, None)    #skip the headers
for user in csv_file:
    print(user)

#读取csv文件内容方法2
with open('testdata.csv', 'r') as csv_file:
    reader = csv.reader(csv_file)
    next(csv_file, None)
    for user in reader:
        print(user)

#从字典写入csv文件
dic = {'fengju':25, 'wuxia':26}
csv_file = open('testdata1.csv', 'w', newline='')
writer = csv.writer(csv_file)
for key in dic:
    writer.writerow([key, dic[key]])
csv_file.close()   #close CSV file

csv_file1 = csv.reader(open('testdata1.csv','r'))
for user in csv_file1:
    print(user)
```
2.读写excel文件
import xlrd, xlwt   #xlwt只能写入xls文件

#读取xlsx文件内容
rows = []   #create an empty list to store rows
book = xlrd.open_workbook('testdata.xlsx')  #open the Excel spreadsheet as workbook
sheet = book.sheet_by_index(0)    #get the first sheet
for user in range(1, sheet.nrows):  #iterate 1 to maxrows
    rows.append(list(sheet.row_values(user, 0, sheet.ncols)))  #iterate through the sheet and get data from rows in list
print(rows)

#写入xls文件
```python
rows1 = [['Name', 'Age'],['fengju', '26'],['wuxia', '25']]
book1 = xlwt.Workbook()   #create new book1 excle
sheet1 = book1.add_sheet('user')   #create new sheet
for i in range(0, 3):    
    for j in range(0, len(rows1[i])):
        sheet1.write(i, j, rows1[i][j])
book1.save('testdata1.xls')   #sava as testdata1.xls
```
### 6.os模块
要在Python 程序中执行目录和文件的操作只是简单地调用了操作系统提供的接口函数，Python 内置的os模块可以直接调用操作系统提供的接口函数。  
```python
>>> import os
>>> os.name # 操作系统类型
nt
```
查看当前目录的绝对路径:
```python
>>> os.path.abspath('.')
'C:\\Users\\SongQ'
```
在某个目录下创建一个新目录，首先把新目录的完整路径表示出来:
```python
>>> os.path.join('/Users/SongQ','testdir')
'/Users/SongQ\\testdir'
```
然后创建一个目录:
```python
>>> os.mkdir('/Users/SongQ/testdir')
```
删掉一个目录:  
```python
>>> os.rmdir('/Users/SongQ/testdir')
```
os.path.split()函数，这样可以把一个路径拆分为两部分，后一部分总是最后级别的目录或文件名：
```python
>>> os.path.split('/Users/SongQ/testdir/file.txt')
('/Users/SongQ/testdir', 'file.txt')
```
os.path.splitext()可以直接让你得到文件扩展名，很多时候非常方便：
```python
>>> os.path.splitext('/Users/SongQ/testdir/file.txt')
('/Users/SongQ/testdir/file', '.txt')
```
各类os模块的方法请见：https://www.runoob.com/python3/python3-os-file-methods.html
### 7.datetime模块
datetime模块重新封装了time模块，提供更多接口，提供的类有：date,time,datetime,timedelta,tzinfo。
