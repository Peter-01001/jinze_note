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
    