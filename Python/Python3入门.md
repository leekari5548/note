## 数据类型

Python有六个标准的数据类型：

- Numbers（数字）
- String（字符串）
- List（列表）
- Tuple（元组）
- Set(集合)
- Dictionary（字典）

> 分类

- **不可变数据（3 个）：**Number（数字）、String（字符串）、Tuple（元组）
- **可变数据（3 个）：**List（列表）、Dictionary（字典）、Set（集合）

Numbers包含`int`,`double`,`complex`。

- Python可以同时为多个变量赋值，如a, b = 1, 2。
- 一个变量可以通过赋值指向不同类型的对象。
- 数值的除法包含两个运算符：/返回一个浮点数，// 返回一个整数(向下取整)。
- 在混合计算时，Python会把整型转换成为浮点数。
- **为乘方。

List为最常用的数据结构，有序的对象集合，用`[]`标识：

```python
list = ['1', '2', '3', '4', '5']
list1 = ['6', '7']

print(list)      # ['1', '2', '3', '4', '5']
print(list[0])   # 1
print(list[0:3]) # ['1', '2', '3']
print(list[3:])  # ['4', '5']
print(list * 2)  # ['1', '2', '3', '4', '5', '1', '2', '3', '4', '5']
print(list + list1)  # ['1', '2', '3', '4', '5', '6', '7']
```

Tuple为python元组，类似于`list`，但是用`()`标识，内部用逗号分隔，不能二次赋值，只读，相当于只读列表。

```python
tuple = ('1', '2', '3')
list = ['1', '2', '3']

tuple[1] = '0' # error
list[1] = '0'  
```

Set为python集合，无重复元素。用`{}`标识。可以使用大括号 `{ }`或者 `set()` 函数创建集合，注意：创建一个空集合必须用 `set()` 而不是 `{ }`，因为` { }` 是用来创建一个空字典。

```python
set0 = {1, 3}
set1 = set()
set2 = {}

print(set0)  ## {1, 3}
print(set1)  ## set()
print(set2)  ## {}
print(type(set1))  ## <class 'set'>
print(type(set2))  ## <class 'dict'>
```

Dictionary为python字典，无序的对象集合。key-value模式，通过key值来存取，用`{}`标识。

```python
dict = {'1': '一', '2': '二'}
dict['3'] = '三'

print(dict.get('1'))   # 一
print(dict)   # {'1': '一', '2': '二', '3': '三'}
print(dict.keys()) # dict_keys(['1', '2', '3'])
print(list(dict.keys()))  # ['1', '2', '3']
print(dict.values())  #  dict_values(['一', '二', '三'])
print(list(dict.values()))  # ['一', '二', '三']
```

`dict.keys()`返回了一个字典的所有key值，但这个结构并不是`list`，需要用`list(dict.keys())`转换，才可以获取到`list`类型。

python数据类型转换：

```python
print(int('1'))  ## int转换类型
print(float('1.1')) ## float类型转换
print(str(123))  ## str类型强制转换

class User:
    def __init__(self, index, name):
        self.index = index
        self.name = name
    def __str__(self):
        return str(self.index) + " - " + self.name
      
user = User(110, "leekari")   ## 创建user对象
print(user)    ## 110 - leekari
## repr(obj) repr() 函数将obj转化为供解释器读取的形式
print(repr(user))  ## <__main__.User object at 0x10ca67358>

num = 1
string = 'num == 1'
## 用来执行一个字符串表达式，并返回表达式的值
print(eval(string))  ## 返回True

list0 = [1, 2, 3]
set0 = {1, 2, 3}
dict0 = {1: 'a', 2: 'b', 3: 'c'}
tuple0 = (1, 2, 3)

tuplex = tuple(list0)  ## (1, 2, 3)
tuplex = tuple(set0)	 ## (1, 2, 3)
## 字典转换为元组时，将dict.keys()的list转换为元组
tuplex = tuple(dict0)  ## (1, 2, 3)

listx = list(set0)  ## [1, 2, 3]
## 只保留dict.keys()的list
listx = list(dict0)  ## [1, 2, 3]
listx = list(tuple0)  ## [1, 2, 3]

list1 = [1, 1, 1, 2]
## set去重
set(list1) ## {1, 2}

chr(97)  ## a
ord('a') ## 97

hex(15) ## 0xf
oct(9) ## 0o11

tupleList = [('1', '2')]  
dict(tupleList)			## 	类型转换为字典时，需要的参数为元组数组，即tuple list,并且tuple中包含的参数数量为2

##error 
tuple = [('1', '2', '3')]
print(dict(tuple))  ## ValueError: dictionary update sequence element #0 has length 3; 2 is required
```

支持给多个变量赋值

```python
a = b = c = 1
a, b, c = 1, "b", 'c'
```

## 注释类型

单行注释：` # ...`			 #开头

多行注释：`'''...'''` 或者`"""..."""`		三个单引号或者三个双引号

## 运算符

`:=` 海象运算符，可在表达式内部为变量赋值。**Python3.8 版本新增运算符**。

**位运算符：** 

- `&`按位与运算，`1&1 => 1`,` 1&0 => 0`,` 0&1 => 0`, `0&0 => 0`
- `|`按位或运算，`1|1 = >1 `,`1|0 => 1`,`0|1 => 1`,`0|0 => 0`
- `^`按位异或运算，`1^1 => 0`,`0^1 = >1`,`1^0 => 1`,`0^0 => 0`
- `~` 按位取反运算，`~1 => 0`,`~0 => 1`
- `<<`左移动运算，向左移动，高位丢弃，低位补0
- `>>`右移动运算，向右移动

```python
## 0 => 00000 , 15 => 01111
x, y = 0, 15

## 00000 & 01111 => 0000
print(x & y)  ## 0
## 00000 | 01111 => 01111
print(x | y)  ## 15
## 00000 ^ 01111 => 01111
print(x ^ y)  ## 15
## ~ 01111 => 10000 ???
print(~ y)  ## -16
## 01111 << 1 => 11110
print(y << 1) ##30
## 01111 >> 1 => 00111
print(y >> 1) ## 7
```

**逻辑运算符：**

- `and`  A and B, A = true, 则返回B, A = false, 则返回A
-  `or`  A or B, A = true,则返回A,A=false,则返回B
-  `not` not A, A=true,则返回false,A=false，则返回true

```python
a, b, c = 1, 2, 0

print(a and b) ## 2
print(c and b) ## 0
print(a or b)  ## 1
print(c or b) ## 2
print(not a) ## False
print(not c) ## True
```

**成员运算符：**

> 可以用于str、list、tuple、set、dict(只计算`dict.keys()`)

- `in`  在指定序列中包含，返回True，否则False
- `not in`  在指定序列中不包含，返回True，否则返回False

```python
list1 = [1, 2, 3, 4, 5]
a, b = 1, 10
str1 = "asdfghj"

print(a in list1)  ## True
print(b in list1)  ## False
print(a not in list1)  ## False
print("a" in str1)  ## True

tuple1 = (1, 3, 5)
set1 = {1, 3, 5}
dict1 = {1: 'a', 2: 'b'}

print(1 in tuple1) ## True
print(1 in set1)  ## True
print(1 in dict1)  ## True
print('a' in dict1)  ##False
```

**身份运算符：**

- `is`  A is B，引用相同的对象但会True，否则返回False
- `is not`

```python
class User:
    def __init__(self, index, name):
        self.index = index
        self.name = name
    def __str__(self):
        return str(self.index) + " - " + self.name

user1 = User(1, "lee")
user2 = User(2, "kari")
user3 = user1

print(user1 is user2)  ## False
print(user1 is user3)  ## True
print(user1 is not user2)  ##True

a, b = 1, 1

print(a is b)  ##True
## id(obj) 获得对象obj的内存地址
print(id(a) is id(b)) ##False
```

> Tips: 
>
> s 与 == 区别：is 用于判断两个变量引用对象是否为同一个， == 用于判断引用变量的值是否相等。

运算符优先级：指数运算符优先级最高，其他普通运算符及位运算符与其余语言相同，身份运算符(is,is not)，成员运算符(in, not in)，逻辑运算符(not,and,or)

### Number 类型

常用数学函数

| 函数                  | 描述                                                         | 所属包 |
| --------------------- | ------------------------------------------------------------ | ------ |
| abs(i)                | 返回数字i的绝对值                                            |        |
| ceil(i)               | 向上取整                                                     | math   |
| exp(i)                | e的i次方                                                     | math   |
| fabs(i)               | 返回数字i的绝对值，浮点类型                                  | math   |
| floor(i)              | 向下取整                                                     | math   |
| log(x, y)\log(x)      | log以y为底x的对数，没有y时，默认以e为底                      | math   |
| max(a,,b, c)\max(seq) | max获取序列的最大值                                          | math   |
| min(a,b,c)\min(seq)   | min获取序列的最小值                                          | math   |
| modf(f)               | 返回一个元组，第一个元素为浮点数位，第二个元素为整数位的浮点数表示，正负与f相同 | math   |
| pow(x,y)              | 等价于x**y                                                   |        |
| round(f, x)\round(f)  | 四舍五入，保留x位小数，没有x时，默认不保留小数位             |        |
| sqrt(x)               | x的平方根                                                    | math   |

```python
from math import ceil, exp, fabs, floor, log, sqrt, e, modf  ##math包需要单独引入

f = -1.1312321
i = 1

print(abs(f))  ## 1.1312321
print(ceil(f))  ## -1
print(exp(1))  # 2.718281828459045 => python中定义的e
print(fabs(i)) # 1.0
print(floor(f)) # -2
print(log(e))  # 1.0
print(log(1))  # 0.0
print(log(100, 10)) #2.0
print(type(modf(f))) # <class 'tuple'>
print(modf(f)) ## (-0.13123210000000007, -1.0)  浮点位这样表示的原因是计算机的通病，主要是因为计算机是使用二进制保存浮点数
		## 而导致了浮点数精度丢失
print(pow(2, 3)) # 8
print(round(f, 3)) # -1.131
print(sqrt(4)) # 2
```

随机数函数

| 函数                             | 描述                                                         | 所属包 |
| -------------------------------- | ------------------------------------------------------------ | ------ |
| choice(seq)                      | 从序列中随机选择一个,<font color='red'>字典偶尔会出错</font>,只适用于list，tuple对象 | random |
| randrange([start], stop, [step]) | 在start-stop之间选择一个随机数，step为区间内随机数的间隔，start、step可选，默认start = 0（？？？），step = 1 | random |
| random()                         | [0,1)的随机数                                                | random |
| shuffle(seq)                     | 把list随机排序,只可用于list                                  | random |
| uniform(x, y)                    | 随机生成一个实数x-y之间的随机浮点数                          | random |



```python
from random import choice, randrange, random, shuffle, uniform

tuple1 = (1, 2, 3, 4, 5, 6, 7, 8, 9, 0)
list1 = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0]
set1 = {1, 2, 3, 4}
dict1 = {1: '1', 2: '2', 3: '3'}

print(choice(tuple1))
print(randrange(1, 10, 2))
print(randrange(10))
print(random())
print(shuffle(list1))   # None
print(list1)
uniform(1000, 9999)
```

还有三角函数等...

### 字符串类型

- 字符串支持 `*`操作，输出相同的字符串n次。

- 字符串转义、字符串元素访问、字符串格式化基本与其他语言类似

- 支持`""" ... """`，按照原样输出文本，不进行转义、格式化等操作
- 在python3.6版本后加入f-string,python3.8之后支持`=`拼接
- python3中，所有的字符串都是用Unicode字符串存放的

```python
string = '1234'

pirnt(string * 2) # 12341234
print(f'Hello {string}')  # Hello 1234
print(f'{100 + 321 = }') # 100 + 32 = 132
```

**字符串内建函数：**

string = "asdfgh"

string1 = 'asd\tfgh'

| 函数                                | 描述                                                         |
| ----------------------------------- | ------------------------------------------------------------ |
| string.capitalize()                 | 将string的首字母变为大写                                     |
| string.center(length[, fillchar])   | string的长度大于length时，直接返回原字符串；如果小于length，则默认使用空格填充，将string居中，也可以指定filechar，使用指定的字符填充<font color='red'>填充两侧</font> |
| string.ljust(width[,fillchar])      | string的长度大于length时，直接返回原字符串；如果小于length，则默认使用空格填充，将string左对齐，也可以指定filechar，使用指定的字符填充 <font color='red'>填充右侧</font> |
| string.rjust(width[,fillchar])      | string的长度大于length时，直接返回原字符串；如果小于length，则默认使用空格填充，将string右对齐，也可以指定filechar，使用指定的字符填充 <font color='red'>填充左侧</font> |
| string.zfill(width)                 | 用0填充的rjust()                                             |
| string.count(str[, start, end])     | string中包含str的次数，start默认为0，end默认为len(string)。  |
| encode/decode                       | 字符串内建了encode函数，`encode = string.encode(encoding='ISO-8859-1', errors='strict')`,返回的encode类型为bytes，此时可以使用`bytes.decode(encoding='GBK', errors='strict')`，注意decode的返回值也是bytes类型 |
| string.endswith(str[, start, end])  | 判断字符串是否以str结尾，增加start，end参数时，在start-end间的字符串是否以str结尾 |
| string1.expandtabs([tabsize])       | 把字符串中的tab符号转换为空格，tabsize默认为8，可以自定义    |
| string.find(str[,start,end])        | 判断字符串中是否包含str，增加参数start，end时判断范围修改为start-end之间,如果包含str，则返回首次str出现的下标，否则返回-1 |
| string.index(str[,start,end])       | 与find类似，唯一区别的是，当不包含str时,抛出一个异常`ValueError: substring not found` |
| string.isalnum()                    | 当字符串是一个非空且由数字-字母-汉字组成的字符串时，返回True，否则返回False【alnum => alpha + numeric】 |
| string.isalpha()                    | 当字符串非空且只包含字母-汉字时，返回True，否则返回False     |
| string.isdigit()                    | 非空字符串只包含数字时，发挥True                             |
| string.islower()                    | 非空字符串只包含小写字母时，返回True，否则返回False          |
| string.isnumeric()                  | 非空字符串 只包含数字字符时，返回True                        |
| string.isspace()                    | 非空字符串只包含空格返回True                                 |
| string.istitle()                    | 非空字符串首字母都为大写，则返回True                         |
| string.isupper()                    | 非空字符串只包含大写字母时返回True                           |
| string.join(seq)                    | 使用字符串连接序列的每一个元素组成一个新的字符串             |
| len(string)                         | 返回字符串长度                                               |
| string.lower()                      | 将字符串中的大写字母转换为小写字母                           |
| string.lstrip([str])                | 截去字符串左侧的空格（默认），或者指定的字符串str            |
| string.maketrains(args)             | 创建一个字符串映射表，args可以为一个字典，也可以为两个长度相同的字符串，string.maketrains(intab, outtab)，intab为要替换的字符串，outtab为要被替换的字符串 |
| string.translate(trains)            | trains为string.maketrains()创建的映射表，将对应的映射表中对应的字母替换 |
| max(string)                         | 返回字符串string中最大的字母                                 |
| min(string)                         | 返回字符串string中最小的字母                                 |
| string.replace(oldstr,newstr[,max]) | 将字符串中的oldstr替换为newstr，如果指定max，则最多替换max次 |
| string.rfind(str[,start,end])       | 类似于find()，从右侧开始                                     |
| string.rindex(str[,start,end])      | 类似于index()，从右侧开始                                    |
| string.rtrip([str])                 | 类似于ltrip()，从右侧开始                                    |
| string.split(str[,num])             | 以str为分隔符分隔，如果指定num，则最多分隔num+1个子字符串    |
| string.splitlines([keepends])       | 按换行(`\r,\r\n,\n`)分隔字符串，保存为list，keepends为True保留换行符 |
| string.startwith(str[,start,end])   | 判断字符串是否以str开头，添加参数start、end表示在start-end范围内判断 |
| string.strip([str])                 | 从两端同时截去空格或者str                                    |
| string.sawpcase()                   | 将字符串中的大写字母转换为小写字母，将小写字母转换为大写字母 |
| string.title()                      | 将字符串的中所有的首字母大写，title格式                      |
| string.upper()                      | 将字符串中的小写字母转换为大写字母                           |
| string.isdecimal()                  | 非空字符串只包含十进制字符，返回True                         |

```python
string = 'asdaaaa\tfgh'
string1 = '中文'
string2 = '---'
print(string.capitalize())
print(string.center(20))
print(string.count('a'))
encode = string.encode(encoding='latin-1', errors='strict')
print(type(encode))
print(encode.decode(encoding='GBK', errors='strict'))
print(string.endswith("h", 0, 1))
print(string.expandtabs(20))
print(string.find('a'))
# print(string.index('x'))
print(string1.isalnum())
print(string2.isalpha())
print(string.isdigit())
print(string.isnumeric())
print(string.isspace())
string3 = "title"
print(string3.istitle())

tuple1 = ('1', '2', '3', '4')
list1 = ['1', '2', '3', '4']
set1 = {'1', '2', '3', '4'}
dict1 = {'1': 'yi', '2': 'er', '3': 'san'}
print(string2.join(dict1))
print(string2.ljust(10, "@"))
print(string2.lstrip("-"))
print(111)

intab = "aeiou"
outtab = "12345"
dict1 = {'a': '1', 'e': '2', 'i': '3', 'o': '4', 'u': '5'}
# trantab = str.maketrans(intab, outtab)

trantab = str.maketrans(dict1)

str = "this is string example....wow!!!"
print(str.translate(trantab))
```

### 列表类型

访问list的值：

```python
list1 = [1, 2, 3, 4, 5]

print(list1[0])  # 1
print(list1[0: 1]) #[1]
print(list1[0: 2]) #[1, 2]
print(list1[1:]) # [2, 3, 4, 5]
print(list1[: 2]) # [1, 2]
print(list1[::-1]) # [5, 4, 3, 2, 1]

print(list1[-2]) #4
```

更新list：

```python
list1[2] = 1000

print(list1) #[1, 2, 1000, 4, 5]
```

删除list中元素：

```python
del list[1]

print(list1) #[1, 1000, 4, 5]
```

其他：

```python
list1 = [1, 2, 3, 4, 5]

print(list1 + [6, 7]) # [1, 2, 3, 4, 5, 6, 7]
print(list1 * 2) #[1, 2, 3, 4, 5, 1, 2, 3, 4, 5]
len(list)  # 5
print(7 in list1) # False

## 遍历list
for item in list1:
  print(item)
for i in range(0, len(list1)):
  print(list1[i])
```

嵌套列表，类似于多维数组：

```python
list1 = [1, 2, 3]
list2 = ['a', 'b', 'c', 'd']
list3 = [list1, list2]

print(list3) # [[1, 2, 3], ['a', 'b', 'c', 'd']]
print(list3[0]) #[1, 2, 3]
print(list3[1][2]) # c
```

列表函数&方法：

| 名称                      | 含义                                                         |
| ------------------------- | ------------------------------------------------------------ |
| min(list)                 | 返回list中最小值                                             |
| max(list)                 | 返回list中最大值                                             |
| len(list)                 | 返回list的长度                                               |
| list(seq)                 | 将序列seq转换为list，支持list,tuple,set,dict,dict只获取dict.keys() |
| list.append(obj)          | list末尾新增obj，直接作用于list，返回值为None                |
| list.count(obj)           | 统计obj在list中出现的次数                                    |
| list.extend(seq)          | 在list末尾增加序列seq，支持list,tuple,set,dict,dict只获取dict.keys() |
| list.index(obj)           | 找出obj在list中第一个匹配的下标，没有则抛出异常`ValueError: obj is not in list` |
| list.insert(index, obj)   | 将obj插入list，指定索引为index                               |
| list.pop([index])         | 移除列表中一个元素，默认为-1（最后一个），也可以指定index    |
| list.remove(obj)          | 查找到第一个obj元素，并从列表中移除obj                       |
| list.reverse()            | 反转list                                                     |
| list.sort([key, reverse]) | reverse为True时，降序排列，为False时（默认），升序排列       |
| list.clear()              | 清空列表                                                     |
| list.copy()               | 复制列表                                                     |

```python
tuple1 = (1, 2, 3, 4)
set1 = {1, 3, 5, 6}
dict1 = {1: 'a', 2: 'b'}

print(list(tuple1)) #[1, 2, 3, 4]
print(list(set1)) #[1, 3, 5, 6]
print(list(dict1)) #[1, 2]
```

### 元组

与list相似，只是不能修改

> tips:重新赋值的元组 tup，绑定到新的对象了，不是修改了原来的对象

### 字典

```python
dict1 = {"1": "yi", "2":"er","3":"san"}

## 取值
print(dict1["1"])  # yi
## 修改字典
dict1["1"] = "一"
print(dict1["1"])  # 一
del dict1["1"] #删除字典元素
dict1.clear() #清空字典
del dict1 #删除字典
```

> 字典键的特性:
>
> 1. 不允许同一个键出现两次。创建时如果同一个键被赋值两次，后一个值会被记住
> 2. 键必须不可变，所以可以用数字，字符串或元组充当，而用列表就不行

字典内置函数&方法：

`dict = {"1": "yi", "2":"er","3":"san"}`

| 名称                          | 含义                                                         |
| ----------------------------- | ------------------------------------------------------------ |
| len(dict)                     | dict的长度                                                   |
| dict.copy()                   | 浅拷贝dict                                                   |
| dict.fromkeys(seq)            | 从seq序列中的元素作为字典的key，值为None                     |
| dict.get(key[,default])       | 从dict中获取key对应的value，不存在默认为None，可以指定default |
| key in dict                   | dict中包含key则返回True，否则False                           |
| dict.items()                  | 返回一个序列，每一个元素为key-value，可以转换为set、tuple、list |
| dict.keys()                   | 返回一个序列，每一个元素为key，可以转换为set、tuple、list    |
| dict.setdeault(key[,default]) | 与get类似，但是如果key不存在与dict中，添加key进入字典dict，default默认为None，可以自定义 |
| dict.update(dict1)            | 把dict1对应的key-value添加到dict，并更新原有的值             |
| dict.values()                 | 返回一个序列，每一个元素为value，可以转换为set、tuple、list  |
| dcit.pop(key[,default])       | 删除key对应的值，返回值为value，如果不存在，返回default，默认为None |
| dict.popitem()                | 返回一个键值对(key,value)形式，按照 LIFO（Last In First Out 后进先出法） 顺序规则，即最末尾的键值对 |

```python
list1 = [1,2,3,4]

print(dict2.fromkeys(list1)) # {1: None, 2: None, 3: None, 4: None}
print(dict1.items())  #dict_items([('1', '一'), ('2', 'er'), ('3', 'san')])
print(dict1.keys())  #dict_keys(['1', '2', '3'])
```

### 集合

> tips：初始化集合不能用`{}`，只能通过set()

```python
a = set('asdfghjkl')
b = set('abcdefghi')
print(a)  #{'a', 'g', 'h', 'j', 'f', 'l', 's', 'k', 'd'}
print(b)  #{'c', 'a', 'g', 'h', 'b', 'e', 'f', 'i', 'd'}

print(a - b)  # a和b的差集  {'s', 'k', 'l', 'j'}
print(a | b)  # a和b的合集  {'k', 'l', 'd', 'e', 'h', 'f', 'i', 'c', 's', 'b', 'j', 'a', 'g'}
print(a & b)  # a和b的交集  {'d', 'h', 'f', 'a', 'g'}
print(a ^ b)  # a和b的全集和交集的差集  {'k', 'l', 'e', 'j', 'i', 's', 'b', 'c'}

## 集合推导式(Set comprehension)
set1 = {x for x in 'aadasfdsf' if x not in 'abc'}
print(set1)  #{'d', 's', 'f'}


## 集合添加元素
set.add(obj)  #如果元素已存在，不进行任何操作
set.update(obj) #参数可以是列表，元组，字典等

## 移除元素
set.remove(obj) # set中不存在元素，报错
set.discard(obj) #set中不存在元素，不报错
set.pop() #随机删除一个set元素

## 元素个数
len(set)

## 清空
set.clear()

##判断元素是否存在
value in set # value在set中返回True，否则False
```


### python不定长参数函数

> 其他函数定义及循环方式与其他语言基本相似，不再赘述。

python中不定长参数函数的定义：

```python
def test(*test):
    print(test)   # (1, 2, 3, 4)
    print(type(test))  # <class 'tuple'>
    
def test2(**test):
    print(test)   # {'a': 2, 'b': 3}
    print(type(test))    # <class 'dict'>

def test3(a, b, *, c):
    print(a)
    print(b)
    print(c)
    print(type(a))
    print(type(b))
    print(type(c))

if __name__ == '__main__':
    test(1, 2, 3, 4)
		test2(a=2, b=3)
    test3(1, 2, c=3)
```

不定长参数的参数名前为`*`时，类型为`tuple`；参数名前为`**`时，参数类型为`dict`;`*`也可以单独出现，当`*`单独出现时，`*`后面必须有参数，并且`*`后面的参数必须要用关键字传入，否则报错(`TypeError: test3() takes 2 positional arguments but 3 were given`)。

### python的匿名函数

python使用`lambda`来定义匿名函数，此时不再使用`def`来定义函数。

匿名函数的特点：

- lambda 只是一个表达式，函数体比 def 简单很多。
- lambda的主体是一个表达式，而不是一个代码块。仅仅能在lambda表达式中封装有限的逻辑进去。
- lambda 函数拥有自己的命名空间，且不能访问自己参数列表之外或全局命名空间里的参数。
- 虽然lambda函数看起来只能写一行，却不等同于C或C++的内联函数，后者的目的是调用小函数时不占用栈内存从而增加运行效率。

匿名函数示例：

```python
sum = lambda x, y: x + y

if __name__ == '__main__':
    print(sum(x=1, y=2))   # 3
    print(sum(3, 5))    # 8
```

**强制位置参数：**

<font color='red'>python3.8新增</font>，函数形参语法 / 用来指明函数形参必须使用指定位置参数，不能使用关键字参数的形式。

```python
def f(a, b, /, c, d, *, e, f):
    print(a, b, c, d, e, f)
    
if __name__ == '__main__':
		f(10, 20, 30, d=40, e=50, f=60)       # 正确
		f(10, b=20, c=30, d=40, e=50, f=60)   # b 不能使用关键字参数的形式
		f(10, 20, 30, 40, 50, f=60)           # e 必须使用关键字参数的形式
```

### python迭代器和生成器

迭代器有两个基本的方法：**iter()** 和 **next()**。字符串，列表，元组，集合，字典(只遍历key)对象都可用于创建迭代器。

```python
string = '12345678'
set1 = {1, 2, 3, 4}
tuple1 = (1, 2, 3, 4)
list1 = [1, 2, 3, 4]
dict1 = {1: 'yi', 2: 'er'}
it_str = iter(string)
it_set = iter(set1)
it_tuple = iter(tuple1)
it_list = iter(list1)
it_dict = iter(dict1)
print(next(it_str))
print(next(it_set))
print(next(it_tuple))
print(next(it_list))
print(next(it_dict))

#也可以对迭代器对象for循环
for x in it_str:
  print(x)
```

#### 创建一个迭代器

把一个类作为一个迭代器使用需要在类中实现两个方法 __iter__() 与 __next__() 。

for example:

```python
class TestIter:
    def __iter__(self):
        self.a = 1
        return self

    def __next__(self):
        x = self.a
        self.a += 1
        return x

if __name__ == '__main__':
    t = TestIter()
    it = iter(t)
    print(next(it))
    print(next(it))
    print(next(it))
    print(next(it))
    print(next(it))
```

> tips: 上述迭代会出现无限循环，可以利用<font color='red'>StopIteration</font>来终止迭代。

改进版example：

```python
class TestIter:
    def __init__(self, stop):
        self.stop = stop

    def __iter__(self):
        self.a = 1
        return self

    def __next__(self):
        if self.a <= self.stop:
            x = self.a
            self.a += 1
            return x
        else:
            raise StopIteration

if __name__ == '__main__':
    t = TestIter(10)
    it = iter(t)
    for i in it:
        print(i)
```

##### 生成器

在 Python 中，使用了 yield 的函数被称为生成器（generator）。跟普通函数不同的是，生成器是一个返回迭代器的函数，只能用于迭代操作，更简单点理解生成器就是一个迭代器。在调用生成器运行的过程中，每次遇到 yield 时函数会暂停并保存当前所有的运行信息，返回 yield 的值, 并在下一次执行 next() 方法时从当前位置继续运行。调用一个生成器函数，返回的是一个迭代器对象。

```python
#!/usr/bin/python3
 
import sys
 
def fibonacci(n): # 生成器函数 - 斐波那契
    a, b, counter = 0, 1, 0
    while True:
        if (counter > n): 
            return
        yield a
        a, b = b, a + b
        counter += 1
f = fibonacci(10) # f 是一个迭代器，由生成器返回生成
 
while True:
    try:
        print (next(f), end=" ")
    except StopIteration:
        sys.exit()

From: https://www.runoob.com/python3/python3-iterator-generator.html
```


