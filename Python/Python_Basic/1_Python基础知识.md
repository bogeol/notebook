# 1_Python基础知识

[toc]

- [x] 发布cnblogs

## 简介

Python is a programming language that lets you work quickly and integrate systems more effectively.

## 内置数据类型

> `标量、序列、映射`的理解 【参考[阮一峰的博客：数据类型和JSON格式](http://www.ruanyifeng.com/blog/2009/05/data_types_and_json.html)】

- 标量
  - Number
    - int / float / complex
  - String
    - str【官网上str归类为text sequence type，暂且将String理解为标量】
  - Boolean
    - bool
- 序列
  - list
  - set
  - tuple
- 映射
  - dict
- ...

[详情参考官网](https://docs.python.org/3/library/stdtypes.html)

## 集合

### 常见集合

- `list = []`
- `set = set() ~ {} `【定义的时候必须要用set()，因为{}是定义一个dict，所以为了防止冲突】
- `tuple = ()`
- `dict = {}`

### 集合操作

- list
  - list[index] / list[x:y] / list[x:] / list[-1] / ...
  - list.append(x)
  - list.pop(x)
  - ...
- set【set中无重复元素】【set ~ 类似于只有key没有value的dict或者是有key但是value为None的dict】【set数学定义：确定性（元素是确认的）、互异性（无重复元素）、无序性（排列顺序不一样，但是是相同的set）（{1, 2, 3} == {2, 1, 3}）】
  - set.add(x)
  - set.pop(x)
  - ...
- tuple
  - 初始化后就不能改变元素了【TypeError: 'tuple' object does not support item assignment】
  - ...
- dict【dict中无重复key】
  - dict[key]
  - dict[key] = value
  - del dict[key]
  - ...

## 遍历

- range
  - for i in range(x) # [0,x)
  - for i in range(x, y) # [x, y)
  - list(range(x)) / list(range(x, y)) # [x, y) - generate range list
- list / set / tuple
  - for item in list # same to list / set / tuple
  - for index, item in enumerate(list)
- dict
  - for key in dict # default loop key
  - for key in dict.keys()
  - for value in dict.values()
  - for item in dict.items() / for key, value in dict.items() # item -> tuple -> (key, value)

## 常用方法

- type(x)
- len(x)
- str(x) / int(x) /  bool(x) / ...【强制类型转换（Python是动态强类型语言）（动态：不需要声明变量类型）（强类型：不允许隐式类型转换，必须手动显示类型转换）】
- ...

## Python中特殊

### 算术运算

```python
print(1 + 1)
print(2 - 1)
print(3 * 2)
print(11 / 3) # / - 结果为float类型
print(11 % 3)  # % - 除余
# --------------------------------------
print(11 // 3) # // - 除整
print(2 ** 5) # ** - 次方

output:
2
1
6
3.6666666666666665
2
3
32
```

### Boolean操作

- `True - False` <<< `true - false`

- `and - or - not` <<< `&& - || - !`【`与 - 或 - 非`】

```python
if 1 and 0:
    print("x")
else:
    print("y")

if not 1:
    print('x')
else:
    print('y')

print(not False)
print(True or False)
print(True and not True)
```


### 判断语句

**if**

```python
# 常见的
if (...){
} else if (...) {
} else {
}

# Python中
if ...:
	print("")
elif ...:
	print("")
else ...:
	print("")
```

**while**

```python
while ...:
    print("")

# Python中没有do...while【实际上可以使用while...if...break去实现】
# PS：Python中没有[i++ / ++i]操作
while True:
    statement
    if condition:
        break
```
**PS：Python中特殊的判断方法**

Here are most of the built-in objects considered false:

- constants defined to be false: `None` and `False`.
- zero of any numeric type: `0`, `0.0`, `0j`, `Decimal(0)`, `Fraction(0, 1)`
- empty sequences and collections: `''`, `()`, `[]`, `{}`, `set()`, `range(0)`

```python
list_ = []

# 判断list为空，传统方法使用length判断
if len(list_) == 0:
    print("list is empty")

# Python中特殊：'' [] set() () {} ...如果为空元素，则默认用False去判断
if not list_:
    print("list is empty")

set_ = set()
set_.add(1)
set_.add(2)
set_.add(3)
if set_: # 也就是说Python帮你自动判断(len==0就为False，len>0就为True【表示有元素在里面】)
    print(set_)
else:
    print("set is empty")
```
