# python编程 从入门到实践

## 安装python

没什么好说的

## 程序出现错误

解释器提供一个trackback（回溯），traceback是一条记录

## 变量和简单的数据类型

### 变量的命名

+ 经典字母数字下划线构成变量名，数字不能做开头
+ 不能包含空格，可用_分割不同单词
+ 见名知意

### 变量是标签

变量是标签或指向特定的值

### 字符串

用单引号或双引号引起的是字符串，三个单引号或双引号可引起多行字符串

#### 字符串的一些方法

> .title()  使单词首字母大写
> .upper()  使单词全大写
> .lower()  使单词全小写
> .rstrip() 删除字符串左侧空白
> .lstrip() 删除字符串右侧空白
> .strip()  删除字符串左右侧空白
> .removeprefix()   删除字符串前缀，括号内为前缀内容（用引号引起）

#### f字符串和format函数

字符串前加上f，可将f后的字符串内{}内的变量替换为值

    name="lingyi"
    print(f"my name is {name}")

### 数

+ 任意两数相除结果为浮点数
+ 整数和浮点数运算结果为浮点数
+ 数中出现下划线分组，print出来没有下划线。1_000_000，print后为1000000

### 同时给多个变量赋值

     x,y,z=1,2,3

### 常量

py没有内置常量类型，一般用全大写来表示

## python之禅

    >>> import this
    The Zen of Python, by Tim Peters

    Beautiful is better than ugly.
    Explicit is better than implicit.
    Simple is better than complex.
    Complex is better than complicated.
    Flat is better than nested.
    Sparse is better than dense.
    Readability counts.
    Special cases aren't special enough to break the rules.
    Although practicality beats purity.
    Errors should never pass silently.
    Unless explicitly silenced.
    In the face of ambiguity, refuse the temptation to guess.
    There should be one-- and preferably only one --obvious way to do it.
    Although that way may not be obvious at first unless you're Dutch.
    Now is better than never.
    Although never is often better than *right* now.
    If the implementation is hard to explain, it's a bad idea.
    If the implementation is easy to explain, it may be a good idea.
    Namespaces are one honking great idea -- let's do more of those!
    
### 列表

[]表示列表,`,`分割其中的元素，列表是有序集合

#### 访问列表中的值

列表名[-2],访问的是倒数第二个元素

列表索引从0开始

#### 修改列表元素

通过索引用赋值语句直接修改元素的值

#### 在列表中添加元素

##### 利用.append()方法在列表末尾增加元素

    列表名.append(元素)

##### 利用.insert()方法在列表中插入新元素

    列表名.insert(索引,元素) //即在索引处插入新元素，后面的依次向后移

#### 从列表中删除元素

##### 使用del语句删除元素

    del 列表名[索引]

##### 使用.pop()方法删除元素

    列表名.pop() //弹出栈顶即最后一个元素的同时返回该元素
    列表名.pop(索引) //弹出索引位置元素并返回

##### 根据值删除元素

    列表名.remove(元素) //删除第一个出现该值的元素

#### 管理列表

##### 使用sort()方法对列表永久排序

    列表名.sort() //将列表中元素按升序排序
    列表名.sort(reverse=Ture) //将列表中的元素按降序排列

##### 使用sorted()方法对列表进行临时排序

    sorted(列表名)  //对列表进行临时排序
    sorted(列表名，reverse=True) //对列表进行反向排序

##### 反转列表

    列表名.reverse() //永久反转列表中的元素

##### 确定列表长度

    len(列表名) //获取列表长度

### 操作列表

#### 循环

注意写`:`

#### 创建数值列表

##### 使用range()函数

    for value in range(1,5) :
        print(value)
    输出结果为1~4

range函数第三个参数表示步长

    for value in range (2,11,2)
        print(value)
    输出结果为从1~10的偶数

##### 使用list函数创建数值列表

    number_list=list(range(2,11,2))
    print(number_list)
    输出结果为[2,4,6,8,10]

#### 数值列表的一些函数

    list=[0,1,2,3]
    min(list)==0
    max(list)==3
    sum(list)==6

#### 使用列表的一部分

##### 切片

利用索引和`：`对列表部分进行操作

    num_list=[0,1,2,3]
    print(num_list[1:3])
    输出[1,2]

`:`前省略从列表头开始，`:`后省略索引到列表，索引为复数代表倒数第几个，最后一个从-1开始

切片可被遍历

#### 复制列表

通过变量名赋值会导致改变一个列表时另一个也被改变

应该使用列表名[:]进行赋值

### 元组

不可变的列表

#### 定义元组

圆括号来标识，有趣的是其实是用逗号来标识的，圆括号只是看起来整洁

## if语句

### 检查多个条件

+ and
+ or

### 检查特定的值在列表中

    my_list=[1,2,3]
    print(1 in my_list)
    输出为True
    print('1'in my_list)
    输出为False

    不在为not in

### 布尔表达式

结果为True或False

### 确定列表非空

在if后跟上列表名，如果列表为空则返回False，如果列表不空则返回True

## 字典

字典用{}和键值对表示，键和值用`:`分开，键必须是不可变的数据类型，值可以是任意数据类型

### 添加键值对

    字典名[键]=值

### 修改键值对

    字典名[键]=值

### 删除键值对

    del 字典名[键]

键值对被永久删除

### get方法

列表名.get(键，如果见不存在返回的值)

如果键不存在且第二个参数省略则为None

### 遍历字典

items()方法

for 键，值 in 属性名.items() //items()返回的是一个包含字典所有键值对的 dict_items 对象

### 遍历字典里的键

    for name in 字典名.keys():
    for name in 字典名:

以上两种写法等价

### 遍历字典里的值

    for name in 字典名.values():

## 集合 set

集合内无重复元素

    set(字典名.values())  //去重复的值

可由{ }直接创建集合
