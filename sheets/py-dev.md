# Python Development

## Exception Handlement

- 用**异常对象**表示异常状态

- 关键词: `try, except, finally, else`

`finally`是发生异常时执行清理工作,`else`在没有出现异常时执行一个代码块

```python
try:
    print('Occupation', person['occupation'])
except KeyError as e:
    print('Invalid Key: ', e)
```

## 生成器、迭代器、魔法方法

1. `yield`语句

e.g. 八皇后问题用生成器解决(TBD)

2. next, iter

```python
class Fibs:
    def __init__(self):
        self.a = 0
        self.b = 1
    def __next__(self):
        self.a, self.b = self.b, self.a + self.b
        return self.a
    def __iter__(self):
        return self
```

## 标准库

`batteries included`

- sys: 跟python解释器有关
- os: 操作系统


