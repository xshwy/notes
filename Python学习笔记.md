
# 语法

输入 `name = input('请输入您的姓名')`
输出 `print('hello')`
不换行输出 `print('hello',end='')`
格式化输出 `print('Hi %s , you have %s.' % ('Jay',10000))`
常见占位符
1. `%d` 整数
2. `%f` 浮点数
3. `%s` 字符串
4. `%x` 十六进制数

类型转换 `int(age)` `float(age)`

获取字符的整数编码 `ord('哈')`
将整数转成字符`chr(123)`

生成整数序列 `list(range(5)) #[0, 1, 2, 3, 4]`

List:有序的集合，可以随时添加或删除元素
1. 定义`names = ['Nicolas','Jay']`
2. 使用索引访问元素值 `names[0]`
3. 追加新元素到末尾 `names.append('Jasmin')`
4. 插入新元素到指定位置 `names.insert(1,'Jack')`
5. 删除最后一个元素 `names.pop()`
6. 删除指定位置的元素 `names.pop(1)`
7. 修改/替换指定元素的值 `names[1]='Erika'`

Tuple:叫做`元祖`的有序列表，相当于不可修改的`List`
1. 定义`names = ('Nicolas','Jay','Jack')`
2. 访问如`List`

dict:使用键值对存储的值，相当于其他语言的map类型
1. 定义 `students = {'Jay':'male','Erika':'female','Jack':'die'}`
2. 增加/修改/重新赋值 `students[Jay] = 30 #如果key存在，这是修改key的值，如果key不存在，则是增加一个元素`
3. 访问
    1. `students['Erika'] # 如果key不存在，则会报错`
    2. `students.get('Erika','other value') # 如果key不存在，返回None；如果key不存在并且第二个参数不为空，则返回第二个参数的值`
4. 删除 `students.pop('Erika')`
5. 获取dict的所有key `students.keys()`
6. 获取dict的所有value `students.values()`

> dict与list相比，dict的访问速度更快，占用内存更大

set:没有重复元素的无序的key的合集
1. 定义 `gender = set(['male','female'])`
2. 增加 `gender.add(key)`
3. 删除 `gender.remove(key)`

条件判断
```python
if a>b:
    print('a>b')
    print('b<a')
elif a=b:
    print('a=b')
    print('b=a')
else:
    print('a<b')
    print('b>a')
```

循环
for...in
```python
names = ['Nicolas','Jay','Jack']
for name in names:
    print(name)
```

while
```python
sum = 0
n = 99
while n > 100:
    n = n + 1
    print(n)
```

# 函数

__定义函数__
```python
def diy_sum(a,b):
    return a+b

# 如果要定义一个空的函数，则函数体使用 `pass` 代替即可
# 函数可返回多个值
# 返回多个值只需要写  return a,b,c 即可
# 接收返回值时可以使用 a,b,c = my_fun()
# 如果没有设置retun返回值，则自动返回None
```

__函数的参数__
所有参数都可以使用`func(*args,**kw)`的方式调用，args是list或者tuple，kw是dict
位置参数:为必须传入的参数，定义方式为`def diy_sum(a,b) # a,b都是位置参数`
默认参数:若不传入，则使用默认的值，定义方式为

```python
def diy_sum(a,b=2,c=3):
    print('a:%s,b:%s,c:%s' % (a,b,c))

diy_sum(1) # 结果为a:1,b:2,c:3
diy_sum(1,c=4) # 结果为 a:1,b:2,c:4， b就是默认参数，默认值为2`
```

可变参数:允许传入任意个参数，内部会将传入的参数组合位tuple，定义方式为在参数前面增加`*`

```python
# names可以是直接传入list或者tuple
def diy(*names):
    for name in names:
        print(name)

diy(1,2,3,4) # 输出结果为 1 2 3 4
```

关键词参数:允许传入任意个`参数名`与`值`，内部将会组合成dict，定义方式为在参数前面增加`**`

```python
# kw参数可以是直接传入dict
def diy(a,b,**kw):
    print(a,b,kw)

diy(1,2,c=3,d=4) # 输出结果为 1,2,{'a':3,'b':4}
```
命名关键字参数:设置`关键字参数`可接受的参数，定义方式位：

```python
# * 不是一个参数，是命名关键字的分隔符，命名关键字为必须传入的参数，可以设置默认值
def diy(a,b,*,c,d=222):
    print(a,b,c,d)

diy(1,2) # 报错
diy(1,2,3) # 报错
diy(1,2,c=3) # 输出结果为 1,2,3
```

导入函数
```python
from file_name import diy_sum
```

# 高级特性

切片:对于`list`,`tuple`,`dict`,`set`,`str`等便捷的取值方式，使用方式`S[start:end]` 不包含end；
注：起始索引是0，倒数索引是-1
1. 取索引1 ~ 3的值 `S[1:3]`
2. 取前三个的值 `S[:3]`
3. 取最后三个的值 `S[-3:]`
4. 取倒数2~倒数4的值 `S[-2:-4]`
5. 取前十个值，每2个取一个 `S[:10:2]`
6. 取出所有值，每2个取一个 `S[::2]`

迭代:
0. 所有迭代都使用`for...in`
1. 判断是否可以迭代
```python
from collections import Iterable
isinstance('abc',Iterable) # 如果可以迭代，则返回true，反之返回false
```
2. 将list转成`索引-元素`的方法`enumerate(list)`
3. 所有数据集合是`Iterable`类型
4. 生成器的generator是`Iterator`类型，表示可以使用`next()`不断获取下一个值

列表生成式:
1. `[x * x for x in range(1,10)]` 表示循环1~10，每次x相乘
2. `[m + n for m in 'ABC' for n in 'XYZ']`
3. `[s.lower() for s in ['A','B','C']]` 将所有字符变成小写
4. `[s.lower() for s in ['A','B','C',1,2] if isinstance(s,str)]` 将所有str类型的字符变成小写

生成器:不用一次性生成完毕的`列表生成式`，它的类型是`generator`
1. 定义`g = (x * x for x in range(1,10))` 生成了一个`generator`
2. 访问
    1. `next(g)` 会一直获取下一个元素值，如果获取完毕，会抛出异常错误
    2. 通过for迭代，for会自动处理错误
3. generator函数，将输出的地方设置为 `yield`即可

```python
def odd():
    print('step 1')
    yield 1
    print('step 2')
    yield(3)
    print('step 3')
    yield(5)

o = odd()
next(o) # 输出 step 1 \n 1
next(o) # 输出 step 2 \n 2
next(o) # 输出 step 3 \n 3    
```

`定制类`:先略过，日后返回来在看 __TODO__

```python
# 使用枚举类型
from enum import Enum
Week = Enum('Week',('Mon','Tue','Wed','Thu','Fir','Sat','Sun'))
Week.Mon # 可以直接调用，也可以迭代 Week.__members__
```

# 高阶函数

map():`map`接收俩个参数，第一个是`函数`，第二个是`Iterable`，map将传入的函数一次作用到序列的每个元素，并把结果作为`Iterator`返回
```python
list(map(str,[1,2,3,4,5]))
# 结果将所有元素转成了字符串，输出结果为 ['1', '2', '3', '4', '5']
# 因为map的返回类型是`Iterator`，所以需要用转换成list才能直接显示输出

```

reduce():`reduce`接收俩个参数，第一个是`函数`这个函数必须接收俩个参数，第二个是`Iterable`，`reduce`把一个函数作用到序列上，将结果和序列的下一个元素累计计算
```python
from functools import reduce
def add(x,y):
    return x + y

reduce(add,[1,2,3,4])
# 输出的值是 10，相当于 add(add(add(1,2),3),4)
```

filter():`filter`同`map`一样，也是接收一个函数一个序列，与`map`不同的是，`filter`将传入的函数作用于每个元素，然后根据返回的`True`或`False`来决定是保留还是丢弃这个元素，返回值为`Iterator`
```python
def is_odd(n):
    return n % 2 == 1

list(filter(is_odd,[1,2,3,4,5])) # 输出的值为[1, 3, 5]
```

sorted():`sorted`是一个排序函数，接收三个参数，第一个参数是`序列`，第二个参数是`key=`自定义排序条件，第三个条件是`reverse=True/False`表示是否反向排序
```python
L = [('Bob',20),('Erika',10)]
def by_name(s):
    return s[0]

def by_score(s):
    return s[1]

print(sorted(L,key=by_name)) # 按照名字排序
print(sorted(L,key=by_score,reverse=True)) # 按照成绩倒序排序
```

返回函数:在一个函数内部再定义一个函数，并且将该函数作为返回值返回，返回的时候并没有执行，需要调用之后才会执行`返回函数中不要引用任何可能会变化的变量`
```python
def count(*args):
    def sum():
        ax = 0
        for x in args:
            ax = x + ax
        return ax
    return sum  # 注意，这里不可以写成 return sum()，否则会直接执行，这样返回的并不是函数本身

c = count(1,2,3) # 在这里的时候，并没有执行计算结果

print(c()) # 需要调用之后才会返回计算结果

```

匿名函数:使用`lambda`关键字表示，匿名函数只能有一个表达式，可以将匿名函数复制给一个变量，也可以作为返回值返回
```python
lambda x : x * x # 相当于f(x)，冒号前面的x表示函数参数

def f(x):
    return x * x

ff = lambda x : x * x # 将匿名函数赋值给ff

def fff(x,y):
    return lambda :x * y # 将匿名函数返回，相当于 返回函数
```

装饰器:可以在代码运行期间动态增加功能的方式叫做`装饰器(decorator)`
```python
import functools
def log(text):
    def decorator(func):
        @functools.warps(func) # 增加这个装饰器可以使函数名称不会改变
        def wrapper(*args,**kw):
            print('%s %s()' % (text,func.__name__))
            return func(*args,**kw)
        return wrapper
    return decorator

@log('开始执行:')
def now():
    print('2016-01-14')

now() # 输出结果第一行为：开始执行:now ，第二行为 2016-01-14
now.__name__ # 结果为 wrapper，如果希望函数名称不要改变，则可以在  def wrapper(*agrs,**kw)上面增加装饰器  @functools.warps(func)即可，需要先导入functools，import functools
```

偏函数:`偏函数(Partial function)`，当函数的参数个数太多，需要简化时，使用functools.partial可以创建一个新的函数，这个新函数可以固定住原函数的部分参数，从而在调用时更简单。可以简单理解为其他语言里的`重载`,简单总结functools.partial的作用就是，把一个函数的某些参数给固定住（也就是设置默认值），返回一个新的函数，调用这个新函数会更简单。

```python
def f(x,y):
    return x * y

f2 = functools.partial(f,y=3)

f2(2) # 返回结果是 2 * 3 = 6
```

# 模块(Module)
一个.py文件即是一个模块，模块通过`包`来组织，为了避免冲突，可以设置一个顶层的包(建一个文件夹)，包目录下必须有一个 `__init__.py`的文件，可以是空文件也可以有内容，这样python才不会将这个`包`识别为普通目录。
模块名称是 `包名.py文件名`，名为`包名`的py文件是 `包名/__init__.py`

文档注释：任何模块代码的第一个字符串都被视为模块的`文档注释`
作者名字：`__author__='xxx'`

# 类(class)

```python
# 默认参数是object，这里可以传入 其他类作为参数
# 若传入其他类，则表示继承这个类，若传入多个值，表示为多重继承
class Person(object):

    gender = 'male' # gender变量为Person的类属性

    # 绑定初始参数，init方法第一个参数永远是self变量，表示自身
    # 有了 __init__ 方法之后，创建实例的时候就不可以传入空的参数了
    def __init__(self,name,age):
        self.__name = name # 俩个下划线开头的变量为私有变量，无法在外部访问，但是可以使用 _Person__name 来访问
        self.age = age # 这个是正常的变量，可以在外部直接访问

    def sayHi(self):
        print("大家好，我叫%s，我今年%s岁了" % (self.__name,self.age))

wg = Person('王刚',18)
print(wg.__name) # 报错，无法在外部访问私有变量
print(wg.age) # 18
print(wg.gender) # male
wg.sayHi() # 调用sayHI方法，输出 大家好，我叫王刚，今年18岁了

```

```python
class Person(object):
    # 创建类的时候，不创建__init__方法也可以
    def sayHi(self):
        print(self.name)


xshwy = Person()
xshwy.name = '王刚'
xshwy.sayHi()
```

```python

wg = Person()

# 获取对象信息
type(wg) # <class 'classTest.Person'>

# 通过与types常量对比，来获取类型
import types
types.FunctionType
types.BuiltinFunctionType
types.LambdaType
types.GeneratorType

# 通过isinstance来判断
isinstance(wg,Person) # True

# 通过dir() 来获取对象信息
print(dir(wg))

# 通过hasattr() getattr() setattr()来操作对象
hasattr(wg,'age') # True
hasattr(wg,'address') # False

getattr(wg,'age') # 18
hi = getattr(wg,'sayHi') # 将wg的sayHi函数赋值给hi变量
hi() # 调用hi变量相当于调用 wg.sayHi
getattr(wg,'address',404) # 第三个参数为 无法获取参数 时报错的默认值，若不设置默认值，则会抛出错误

setattr(wg,'age',15) # 将年龄修改为15岁
```

# 面向对象高级编程

```python
__slots__ = ('__name','age','cry') # 限制当前类能添加的属性和方法，对继承的子类不起作用

def cry(self):
    pritn('嘤嘤嘤')

from types import MethodType
# 动态的给变量增加函数，只针对当前实例，并不能作用于所有实例
wg.cry = MethodType(cry,wg)

# 若要针对所有实例，则可以给class绑定方法
classTest.Person = MethodType(cry,classTest.Person)

wg.cry() # 输出 嘤嘤嘤

```

```python
#!/usr/bin/env python3
# _*_ coding:utf-8 _*_

__author__ = "CodeMart.io"

class Screen(object):

    # 使用 @property 装饰器来设置属性的 get 与 set 函数
    @property
    def width(self): # 获取width的值
        return self._width # 这里有下划线是，如果不使用下划线的话 self.width是调用的函数，而不是变量

    @width.setter # 设置width的值
    def width(self,value):
        self._width = value

    @property
    def height(self):
        return self._height

    @height.setter
    def height(self,value):
        self._height = value

    @property
    def resolution(self): # 对于resolution属性只设置了get方法，没设置set方法，这样只能访问，无法设置
        return self._height * self._width

s = Screen()
s.width = 1024
s.height = 768
s.resolution = 100 # 无法设置，抛出异常

print(s.width,'*',s.height,'=',s.resolution)
```

# 错误、调试和测试
```python
import logging

class ErrorTest(object):
    def tryTest(self):
        try:
            r = 10 / 0
            print('result:',r)
        except Exception as e: # 捕获错误
             logging.exception(e)  # 记录错误
        finally:
            print('finally')

if __name__=='__main__':
    err = ErrorTest()
    err.tryTest()
```

调试

```python
# 如果n=0，则抛出异常 'n is zero!'
# 启动Python解释器时可以用-O参数来关闭assert
assert n != 0, 'n is zero!' # 断言

# logging不会抛出异常，而是输出自定义的错误信息
import logging
# 若需要输出info级别的信息，需要在引入之后，添加下面这行配置
logging.basicConfig(level=logging.INFO)
logging.info('n = %d' % n)

```

测试

```python
# 单元测试
import unittest
from errorTest import MyCalc

class TestMyCalc(unittest.TestCase):

    def setUp(self):
        print('start...')

    def tearDown(self):
        print('end...')

    def test_mySum(self):
        m = MyCalc()
        result = m.mySum(1,2)
        self.assertEqual(result,3) # 如果结果不等于3，则会报错

    if __name__ == '__main__':
        unittest.main()

# 文档测试
def mySum(x,y):
    '''
    >>> mySum(1,2)
    3
    '''
    return x + y

if __name__ == '__main__':
    import doctest
    doctest.testmod()

```

# 其他

直接运行.py文件
1. 再.py文件开头加入 `#!/usr/bin/env python3`
2. 给文件执行权限`chmod a+x ./file.py`
3. 执行.py文件 `./file.py`

设置文件编码 `# _*_ coding: utf-8 _*_`

学习地址 [Python基础教程][0]


[0]: http://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000
