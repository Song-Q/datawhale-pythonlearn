### 1.类和对象
面向过程的程序设计把计算机程序视为一系列的命令集合，即一组函数的顺序执行。为了简化程序设计，面向过程把函数继续切分为子函数，即把大块函数通过切割成小块函数来降低系统的复杂度。  
面向对象的程序设计把计算机程序视为一组对象的集合，而每个对象都可以接收其他对象发过来的消息，并处理这些消息，计算机程序的执行就是一系列消息在各个对象之间传递。  
在Python 中，所有数据类型都可以视为对象，当然也可以自定义对象。自定义的对象数据类型就是面向对象中的类（Class）的概念。对象是类的实例。    
如果采用面向对象的程序设计思想，我们首选思考的不是程序的执行流程，而是Student这种数据类型应该被视为一个对象，这个对象拥有name和score这两个属性（Property）。如果要打印一个学生的成绩，首先必须创建出这个学生对应的对象，然后，给对象发一个print_score消息，让对象自己把自己的数据打印出来。  
```python
class Student(object):
    def __init__(self, name, score):
        self.name = name
        self.score = score
    def print_score(self):
        print('%s: %s' % (self.name, self.score))
```
给对象发消息实际上就是调用对象对应的关联函数，我们称之为对象的方法（Method）。面向对象的程序写出来就像这样：
```python
bart = Student('Bart Simpson', 59)
lisa = Student('Lisa Simpson', 87)
bart.print_score()
lisa.print_score()
```
面向对象最重要的概念就是类（Class）和实例（Instance），必须牢记类是抽象的模板，比如Student 类，而实例是根据类创建出来的一个个具体的“对象”，每个对象都拥有相同的方法，但各自的数据可能不同。  
class后面紧接着是类名，即Student，类名通常是大写开头的单词，紧接着是(object)，表示该类是从哪个类继承下来的。通常，如果没有合适的继承类，就使用object类，这是所有类最终都会继承的类。
```python
class Studetn(object):
    pass
```
定义好了Student类，就可以根据Student类创建出Student的实例，创建实例是通过类名+()实现的：
```python
>>> bart = Student()
>>> bart
<__main__.Student object at 0x00000211BC704320>
>>> Student
<class '__main__.Student'>
```
可以自由地给一个实例变量绑定属性，比如，给实例bart绑定一个name属性：
```python
>>> bart.name = 'Bart Simpson'
>>> bart.name
'Bart Simpson'
```
由于类可以起到模板的作用，因此，可以在创建实例的时候，把一些我们认为必须绑定的属性强制填写进去。通过定义一个特殊的__init__方法，在创建实例的时候，就把name，score等属性绑上去：
```python
class Student(object):
    def __init__(self, name, score):
        self.name = name
        self.score = score
```
注意到__init__方法的第一个参数永远是self，表示创建的实例本身，因此，在__init__方法内部，就可以把各种属性绑定到self，因为self就指向创建的实例本身。
```python
>>> bart = Student('Bart Simpson', 59)
>>> bart.name
'Bart Simpson'
```
有了__init__方法，在创建实例的时候，就不能传入空的参数了，必须传入与__init__方法匹配的参数，但self不需要传。除此之外，类的方法和普通函数没有什么区别
#### 数据封装
在上面的Student类中，每个实例就拥有各自的name和score这些数据。既然Student实例本身就拥有这些数据，要访问这些数据，就没有必要从外面的函数去访问，可以直接在Student类的内部定义访问数据的函数，这样，就把“数据”给封装起来了。这些封装数据的函数是和Student类本身是关联起来的，我们称之为类的方法：
```python
class Student(object):
    def __init__(self, name, score):
        self.name = name
        self.score = score
    def print_score(self):
        print('%s: %s' % (self.name, self.score))
```
要调用一个方法，只需要在实例变量上直接调用，除了self不用传递，其他参数正常传入：
```python
>>> bart.print_score()
Bart Simpson: 59
```
如果要让内部属性不被外部访问，可以把属性的名称前加上两个下划线__，在Python 中，实例的变量名如果以__开头，就变成了一个私有变量（private），只有内部可以访问，外部不能访问。  
若外部代码要获取name 和score，则可以给Student 类增加get_name和get_score这样的方法。  
若要允许外部代码修改score，则可以再给Student 类增加set_score方法，所以，我们把Student类改一改：
```python
class Student(object):
    def __init__(self, name, score):
        self.__name = name
        self.__score = score
    def print_score(self):
        print('%s: %s' %(self.__name, self.__score))
    def get_name(self):
        return self.__name
    def get_score(self):
        return self.__score
    def set_score(self, score):
        self.__score = score        
```
```python
>>> bart = Student('Bart Simpson', 60)
>>> bart.__name
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'Student' object has no attribute '__name'
>>> bart.get_score()
60
>>> bart.set_score(80)
>>> bart.get_score()
80
```
#### 继承和多态
当我们定义一个class 的时候，可以从某个现有的class 继承，新的class 称为子类（Subclass），而被继承的class 称为基类、父类或超类（Base class、Super class）。继承最大的好处是子类获得了父类的全部功能。  
继承的第二个好处需要我们对代码做一点改进。当run()的时候，显示的是Animal is running...，符合逻辑的做法是显示Dog is running...
```python
class Animal(object):
    def run(self):
        print('Animal is running...')

class Dog(Animal):
    def run(self):
        print('Dog is running...')
    def eat(self):
        print('Eating meat...')
```
```python
>>>dog = Dog()
>>>dog.run()
Dog is running...
```

当子类和父类都存在相同的run()方法时，我们说，子类的run()覆盖了父类的run()，在代码运行的时候，总是会调用子类的run()。这样，我们就获得了继承的另一个好处：多态。
```python
>>>a = list() # a是list类型
>>>b = Animal() # b是Animal类型
>>>c = Dog() # c是Dog类型
>>> isinstance(c, Dog)
True
>>> isinstance(c, Animal)
True
```

对于一个变量，我们只需要知道它是Animal类型，无需确切地知道它的子类型，就可以放心地调用run()方法，而具体调用的run()方法是作用在Animal、Dog、Cat还是Tortoise对象上，由运行时该对象的确切类型决定，这就是多态真正的威力：调用方只管调用，不管细节，而当我们新增一种Animal的子类时，只要确保run()方法编写正确，不用管原来的代码是如何调用的。这就是著名的“开闭”原则：  
对扩展开放：允许新增Animal子类；  
对修改封闭：不需要修改依赖Animal类型的run_twice()等函数。
```python
def run_twice(animal):
    animal.run()
    animal.run()
class Tortoise(Animal):
    def run(self):
        print('Tortoise is running slowly...')
```
```python
>>> run_twice(Tortoise())
Tortoise is running slowly...
Tortoise is running slowly...
```
### 2.正则表达式
正则表达式是一种用来匹配字符串的强有力的武器。它的设计思想是用一种描述性的语言来给字符串定义一个规则，凡是符合规则的字符串，我们就认为它“匹配”了，否则，该字符串就是不合法的。  
在正则表达式中，如果直接给出字符，用\d可以匹配一个数字,\s匹配任意空白字符等价于[\t\n\r\f],\w可以匹配一个字母或数字,例如：'\w\w\d'可以匹配'py3'；.可以匹配任意字符，所以：'py.'可以匹配'pyc'、'pyo'、'py!'等等。  
要匹配变长的字符，在正则表达式中，用\*表示任意个字符（包括0 个），用+表示至少一个字符，用?表示0 个或1 个字符，用{n}表示n 个字符，用{n,m}表示n-m 个字符：\d{3}\s+\d{3,8}。其中，\d{3}表示匹配3 个数字；\s可以匹配一个空格（也包括Tab 等空白符），所以\s+表示至少有一个空格；\d{3,8}表示3-8 个数字。  
[0-9a-zA-Z\_]+可以匹配至少由一个数字、字母或者下划线组成的字符串，比如'a100'，'0_Z'，'Py3000'等等；  
[a-zA-Z\_][0-9a-zA-Z\_]\*可以匹配由字母或下划线开头，后接任意个由一个数字、字母或者下划线组成的字符串，也就是Python合法的变量；  
[a-zA-Z\_][0-9a-zA-Z\_]{0, 19}更精确地限制了变量的长度是1-20个字符（前面1 个字符+后面最多19 个字符）。  
A|B可以匹配A 或B，所以[P|p]ython可以匹配'Python'或者'python'。^表示行的开头，^\d表示必须以数字开头。$表示行的结束，\d$表示必须以数字结束。  
正则表达式的其它相关知识见：https://www.runoob.com/regexp/regexp-tutorial.html
### 3.re模块
Python 提供re模块，包含所有正则表达式的功能。由于Python 的字符串本身也用\转义，强烈建议使用Python 的r前缀，就不用考虑转义的问题了：
```python
s = r'ABC\-001' # Python的字符串
```
match()方法判断是否匹配，如果匹配成功，返回一个Match对象，否则返回None
```python
>>> import re
>>> re.match(r'^\d{3}\-\d{3,8}$', '010-12345')
<_sre.SRE_Match object; span=(0, 9), match='010-12345'>
>>> re.match(r'^\d{3}\-\d{3,8}$', '010 12345')
>>>
```
用正则表达式切分字符串比用固定的字符更灵活，无法识别连续的空格，用正则表达式试试：
```python
>>> 'a b   c'.split(' ')
['a', 'b', '', '', 'c']
>>> re.split(r'\s+', 'a b c')
['a', 'b', 'c']
>>> re.split(r'[\s\\,]+', 'a,b, c  \ d')
['a', 'b', 'c', 'd']
```
除了简单地判断是否匹配之外，正则表达式还有提取子串的强大功能。用()表示的就是要提取的分组（Group）。比如：
```python
>>> m = re.match(r'^(\d{3})-(\d{3,8})$', '010-12345')
>>> m.group(0)
'010-12345'
>>> m.group(1)
'010'
>>> m.group(2)
'12345'

>>> t = '19:05:30'
>>> m = re.match(r'^(0[0-9]|1[0-9]|2[0-3]|[0-9])\:(0[0-9]|1[0-9]|2[0-9]|3[0-9]|4[0-9]|5[0-9]|[0-9])\:(0[0-9]|1[0-9]|2[0-9]|3[0-9]|4[0-9]|5[0-9]|[0-9])$', t)
>>> m.groups()
('19', '05', '30')
```
正则匹配默认是贪婪匹配，也就是匹配尽可能多的字符。举例如下，匹配出数字后面的0：
```python
>>> re.match(r'^(\d+)(0*)$', '102300').groups()
('102300', '')
```
必须让\d+采用非贪婪匹配（也就是尽可能少匹配），才能把后面的0匹配出来，加个?就可以让\d+采用非贪婪匹配：
```python
>>> re.match(r'^(\d+?)(0*)$', '102300').groups()
('1023', '00')
```
### 4.http请求

