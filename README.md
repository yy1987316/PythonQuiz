# PythonQuiz

## 1.python合并字典，相同key的value相加
> ```python
> x = { 'apple': 1, 'banana': 2 }
> y = { 'banana': 10, 'pear': 11 }
> 需要把两个字典合并，最后输出结果是：
> { 'apple': 1, 'banana': 12, 'pear': 11 }
> ```

```python
from collections import Counter
dict(Counter(x) + Counter(y))
```

## 2.python函数参数传递机制
```python
python参数传递采用的是“传对象引用”的方式。这种方式相当于“传值和传引用”的一种综合。
如果函数收到的是一个可变对象（比如字典或者列表）的引用，就能修改对象的原始值－－相当于通过“传引用”来传递对象。
如果函数收到的是一个不可变对象（比如数字、字符或者元组）的引用，就不能直接修改原始对象－－相当于通过“传值'来传递对象。
```

## 3.*args和**kwargs的用法
```python
*args 收集位置参数到元组
**kwargs 收集关键字参数到字典
```
> 扩展：分配参数。与其相反，定义函数是不带\*或**，调用时参数前加\*或**，分别将元组或字典中的值，分配给函数的位置或关键字参数。


## 4.python中实现单例模式的几种方式
> 单例模式：确保某一个类只有一个实例存在。
1. 模块导入
```python
# mysingleton.py
class Singleton():
  def foo(self):
    pass
singleton = Singleton()

# 使用时，导入文件中的对象即可
from a import singleton
```
2. 装饰器
```python
def Singleton(cls):
  _instance = {}
  
  def _singleton(*args, **kwargs):
    if cls not in _instance:
      _instance[cls] = cls(*args, **kwargs)
     return _instance[cls]
     
  return _singleton
  
@Singleton
class A():
  def __init__(self, x=0):
    self.x = x
    
# test
a1 = A(10)
a2 = A(20)
```
3. classmethod
```python
class Singleton():
  def __init__(self):
    pass
    
  @classmethod
  def instance(cls, *args, **kwargs):
    if not hasattr(Singleton, "_instance"):
      Singleton._instance = cls(*args, **kwargs)
    return Singleton._instance
```
4. 基于__new__方法
```python
class Singleton(object):
  def __new__(cls, *args, **kwargs):
    if not hasattr(Singleton, "_instance")
      Singleton._instance = object.__new__(cls)
    return Singleton._instance
```
5. 基于metaclass
```python
class SingletonType(type):
    def __call__(cls, *args, **kwargs):
        if not hasattr(cls, "_instance"):
            cls._instance = super(SingletonType,cls).__call__(*args, **kwargs)
        return cls._instance

class Foo(metaclass=SingletonType):
    def __init__(self,name):
        self.name = name

obj1 = Foo('name1')
obj2 = Foo('name2')
print(obj1,obj2)
```

## 5.read, readline, readlines的区别
```python

read([size])方法从文件当前位置起读取size个字节，若无参数size，则表示读取至文件结束为止，它返回为字符串对象
readline()方法每次读出一行内容，所以，读取时占用内存小，比较适合大文件，该方法返回一个字符串对象
readlines()方法读取整个文件所有行，保存在一个列表(list)变量中，每行作为一个元素，但读取大文件会比较占内存
```

## 6.Post和Get的区别
## 7.Cookie和Session的区别
cookie数据存放在客户的浏览器上，session数据放在服务器上  
cookie不是很安全，别人可以分析存放在本地的cookie并进行cookie欺骗，考虑到安全应当使用session  
session会在一定时间内保存在服务器上，当访问增多，会比较占用你服务器的性能，考虑到减轻服务器性能方面，应当使用cookie  
单个cookie保存的数据不能超过4K，很多浏览器都限制一个站点最多保存20个cookie  
建议将登录信息等重要信息存放为session，其他信息如果需要保留，可以放在cookie中  
session保存在服务器，客户端不知道其中的信息；cookie保存在客户端，服务器能够知道其中的信息  
session中保存的是对象，cookie中保存的是字符串  
session不能区分路径，同一个用户在访问一个网站期间，所有的session在任何一个地方都可以访问到，而cookie中如果设置了路径参数，那么同一个网站中不同路径下的cookie互相是访问不到的  
## 8.Python2.x与Python3.x的区别
print函数  
ASCII，Unicode  
除法运算  
异常  
xrange, raw_input, file  
八进制字面量表示，必须有o  
不等运算符，去掉了<>  
去掉了repr表达式\`\`  
多个模块被改名 ConfigParser -> configparser  
数据类型：去除了long，增加了bytes，有些方法返回改为可迭代对象map filter dict.keys()...  
## 9.Python的数据类型
整型、浮点型、布尔型、字符串、元组、列表、字典、集合
## 10.tuple和list的区别
tuple不可改变，逻辑上作为一个整体。list可以改变。
## 11.字符串列表转化为数字列表
> ```python
> num_string = ['1', '21', '53', '84', '50', '66', '7', '38', '9']
> ```
```python
lt = [int(s) for s in num_string]
```
## 12.建立一个用于下载文件的线程池，活动线程数为5
## 13.有多少种设计模式
* 创建模式，提供实例化的方法，为适合的状况提供相应的对象创建方法。
  * 工厂方法
  * 抽象工厂
  * 建造者
  * 原型
  * 单例
* 结构化模式，通常用来处理实体之间的关系，使得这些实体能够更好地协同工作。
  * 适配器
  * 桥接
  * 组合
  * 装饰
  * 外观
  * 享元
  * 代理
* 行为模式，用于在不同的实体建进行通信，为实体之间的通信提供更容易，更灵活的通信方法。
  * 解释器
  * 模板方法
  * 责任链
  * 命令
  * 迭代器
  * 中介者
  * 备忘录
  * 观察者
  * 状态
  * 策略
  * 访问者
## 14.匿名函数
```python
lambda x, y: x+y
```
## 15.利用filter过滤出列表中大于5的数字
> ```python
> a = [1,2,3,4,5,6,7]
> ```
```python
list(filter(lambda x: x>5, a))
```
## 16.利用map让列表每项都乘以2
```python
list(map(lambda x: x*2, a))
```
## 17.Python垃圾回收
引用计数机制为主，标记-清除和分代收集两种机制为辅的策略
引用计数机制导致循环引用占用的内存永远无法被回收，因此又引入新的回收机制，标记-清除和分代收集。

对象池：
  - 小整数[-5,257)共用对象，常驻内存
  - 单个字符共用对象，常驻内存
  - 大整数不共用内存，引用计数为0，销毁
  - 单个单词，不可修改，默认开启intern机制，共用对象，引用计数为0，则销毁
  - 字符串（含有空格），不可修改，没开启intern机制，不共用对象，引用计数为0，销毁

## 18.Python生成器和迭代器
迭代器是一个更抽象的概念，任何对象，如果它的类有 next() 方法和 iter() 方法返回自己本身，使用 for 循环遍历是很方便的。在后台 for 语句对容器对象调用 iter()函数，iter() 是 python 的内置函数。iter()会返回一个定义了 next() 方法的迭代器对象，它在容器中逐个访问容器内元素，next() 也是 python 的内置函数。在没有后续元素时，next()会抛出一个 StopIteration 异常。  

生成器（Generator）是创建迭代器的简单而强大的工具。它们写起来就像是正规的函数，只是在需要返回数据的时候使用 yield 语句。每次 next()被调用时，生成器会返回它脱离的位置（它记忆语句最后一次执行的位置和所有的数据值）

区别：生成器能做到迭代器能做的所有事,而且因为自动创建了 iter()和 next()方法,生成器显得特别简洁,而且生成器也是高效的，使用生成器表达式取代列表解析可以同时节省内存。除了创建和保存程序状态的自动方法,当发生器终结时,还会自动抛出 StopIteration 异常。

## 19.OSI7层网络模型
物数网传会表应
