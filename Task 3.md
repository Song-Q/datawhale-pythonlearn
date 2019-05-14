### 1.dict字典
#### 定义
dict 全称dictionary，在其他语言中也称为map，使用键-值（key-value）存储，具有极快的查找速度。这种key-value 存储方式，在放进去的时候，必须根据key算出value 的存放位置，这样，取的时候才能根据key 直接拿到value。dict 内部存放的顺序和key 放入的顺序是没有关系的。正确使用dict 非常重要，需要牢记的第一条就是dict 的key 必须是不可变对象。

#### 创建
```python
>>>d = {'Michael': 95, 'Bob': 75, 'Tracy': 85}
>>> d['Michael']
95

```
#### 字典的方法
把数据放入dict 的方法，除了初始化时指定外，还可以通过key 放入：
```python
>>> d['Adam'] = 67
>>> d['Adam']
67
```
要避免key 不存在的错误，有两种办法，一是通过in判断key 是否存在：
```python
>>> 'Thomas' in d
False
```
二是通过dict 提供的get 方法，如果key 不存在，可以返回None，或者自己指定的value：
```python
>>> d.get('Thomas')    #返回None的时候Python 的交互式命令行不显示结果
>>> d.get('Thomas', -1)
-1
```
要删除一个key，用pop(key)方法，对应的value 也会从dict 中删除：
```python
>>> d.pop('Bob')
75
>>> d
{'Michael': 95, 'Tracy': 85}
```

### 2.集合
#### 特性
set 和dict 类似，也是一组key 的集合，但不存储value。由于key 不能重复，所以，在set 中，没有重复的key。
#### 创建
要创建一个set，需要提供一个list 作为输入集合(重复元素在set 中自动被过滤)：
```python
>>> s = set([1, 2, 3])
>>> s
{1, 2, 3}
```
#### 方法
通过add(key)方法可以添加元素到set 中:
```python
>>> s.add(4)
>>> s
{1, 2, 3, 4}
```
通过remove(key)方法可以删除元素：
```python
>>> s.remove(4)
>>> s
{1, 2, 3}
```
set 可以看成数学意义上的无序和无重复元素的集合，因此，两个set 可以做数学意义上的交集、并集等操作：
```python
>>> s1 = set([1, 2, 3])
>>> s2 = set([2, 3, 4])
>>> s1 & s2
{2, 3}
>>> s1 | s2
{1, 2, 3, 4}
```
### 3.判断语句（要求掌握多条件判断）
```pyhon
if <条件判断1>:
    <执行1>
elif <条件判断2>:
    <执行2>
elif <条件判断3>:
    <执行3>
else:
    <执行4>
```
### 三目表达式
条件为真时的结果 if 判段的条件 else 条件为假时的结果 
```python
x =1
y =2
r = x if x > y else y
```
### 循环语句
同其它语言一样有for和while两种。  
一种是for...in 循环，依次把list 或tuple 中的每个元素迭代出来。
```python
names = ['Michael', 'Bob', 'Tracy']
for name in names:
    print(name)
```
第二种循环是while 循环，只要条件满足，就不断循环，条件不满足时退出循环。
```python
sum = 0
n = 99
while n > 0:
    sum = sum + n
    n = n - 2
print(sum)
```
