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
> 扩展：分配参数。与其相反，定义函数是不带*或**，调用时参数前加*或**，分别将元组或字典中的值，分配给函数的位置或关键字参数。


## 4.python中实现单例模式的集中方式
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
