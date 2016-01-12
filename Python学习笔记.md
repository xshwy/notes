
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
1. for...in
```python
names = ['Nicolas','Jay','Jack']
for name in names:
    print(name)
```

2. while
```python
sum = 0
n = 99
while n > 100:
    n = n + 1
    print()
```

# 函数

定义函数
```python
def diy_sum(a,b):
    return a+b

# 如果要定义一个空的函数，则函数体使用 `pass` 代替即可
# 函数可返回多个值
# 返回多个值只需要写  return a,b,c 即可
# 接收返回值时可以使用 a,b,c = my_fun()
# 如果没有设置retun返回值，则自动返回None
```

函数的参数
0. 所有参数都可以使用`func(*args,**kw)`的方式调用，args是list或者tuple，kw是dict
1. 位置参数:为必须传入的参数，定义方式为`def diy_sum(a,b) # a,b都是位置参数`
2. 默认参数:若不传入，则使用默认的值，定义方式为
```python
def diy_sum(a,b=2,c=3):
    print('a:%s,b:%s,c:%s' % (a,b,c))

diy_sum(1) # 结果为a:1,b:2,c:3
diy_sum(1,c=4) # 结果为 a:1,b:2,c:4
# b就是默认参数，默认值为2`
```
3. 可变参数:允许传入任意个参数，内部会将传入的参数组合位tuple，定义方式为在参数前面增加`*`
```python
# names可以是直接传入list或者tuple
def diy(*names):
    for name in names:
        print(name)

diy(1,2,3,4) # 输出结果为 1 2 3 4
```
4. 关键词参数:允许传入任意个`参数名`与`值`，内部将会组合成dict，定义方式为在参数前面增加`**`
```python
# kw参数可以是直接传入dict
def diy(a,b,**kw):
    print(a,b,kw)

diy(1,2,c=3,d=4) # 输出结果为 1,2,{'a':3,'b':4}
```
5. 命名关键字参数:设置`关键字参数`可接受的参数，定义方式位：
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

# 其他

直接运行.py文件
1. 再.py文件开头加入 `#!/usr/bin/env python3`
2. 给文件执行权限`chmod a+x ./file.py`
3. 执行.py文件 `./file.py`

设置文件编码 `# _*_ coding: utf-8 _*_`

学习地址 [Python基础教程][0]


[0]: http://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000
