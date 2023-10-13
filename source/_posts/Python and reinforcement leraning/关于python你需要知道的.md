---
title:关于python你需要知道的
tags: Python
categories:
  - Python
date: 2023-10-13 00:21:03
---
# python的特点

我们简单对比下python和c++完成输出字符Hello world的源代码就可以发现一些事

## python

```python
print("Hello world")
```

## c++



```cpp
#include<iortream>
using namespace std;
int main{
    cout<<"Hello world"<<endl;
    return 0;
}
```

python 的代码要简洁很多，这还只是一个十分简单的功能。一旦功能复杂起来，那python为你节省的代码行数将以100行为单位。正是因此python常被用于一些更加注重与逻辑而不是细节的颗粒度的事情，如人工智能，大数据等。

那么在下面的部分我会详细的列出python的一些值得注意特性。

# python是Auto GC的编程语言

## 什么是Auto GC

auto GC是自动垃圾回收。在无GC的编程语言中当你申请的一个变量不再被使用那它就是一个垃圾变量，但它会一直占用你的内存空间，除非你手动释放内存。如果程序员的水平不行，那他写的程序就可能会非常卡顿。那Auto GC机制就可以帮我们自动清理不用的垃圾变量

## python的Auto GC机制

Python在垃圾回收时使用如下步骤来寻找需要释放的对象:

1.对于每一个容器对象, 设置一个gc_refs值, 并将其初始化为该对象的引用计数值.

2.对于每一个容器对象, 找到所有其引用的对象, 将被引用对象的gc_refs值减1.

3.执行完步骤2以后所有gc_refs值还大于0的对象都被非容器对象引用着, 至少存在一个非循环引用. 因此不能释放这些对象, 将他们放入另一个集合.

*注：这一步能很好地解决循环引用的问题。*

4.在步骤3中不能被释放的对象, 如果他们引用着某个对象, 被引用的对象也是不能被释放的, 因此将这些对象也放入另一个集合中.

5.此时还剩下的对象都是无法到达的对象. 现在可以释放这些对象了.

> 这一部分的内容了解python可以帮我们自动删除垃圾对象就好，其实现过程不必深究。

# python是动态语言

python有良好的类型推导，在申明python变量时你无需指定变量的类型。在申明函数时也不需要变量类型相关的设置。

```python
num = 20
string = "Hello"
li = [1, 2, 3, 4]

a = 1
b = 1
def add(a, b):
    return a+b
```

而不像c语言等

``` c
int num = 20;
std::string str = "Hello";
int li[4]={1, 2, 3, 4};

int a = 1;
int b = 1;
int add(int a, int b){
    return a+b;
}
```

## 类型注释

当然在编写代码时注明变量的类型是个好习惯。类型注释和注释并不相同，注释不会影响程序的运行，但是如果你不遵循类型注释去做一些操作那解释器是会报错的！

```python
num:int = 20
string:str = "Hello"
li:list = [1, 2, 3, 4]

a:int = 1
b:int = 1
def add(a:int, b:int) -> int:
    return a+b
```

# python的第三方库和Pypi

python有很多优秀的第三方库，借助于第三方库为我们的便利，我们可以很轻松的实现一些十分复杂的功能。实现程序员们不重复造轮子的愿景。

## Pypi

pypi是python官方的第三方库仓库，我们可以从中在线获取第三方库。python安装时自带的cli（命令行）工具pip，是Pypi为我们提供的客户端。

以安装pygame举例，我们可以这么安装一个库。在命令行（cmd）中执行

```cmd
pip install pygame
```



# Pythonic：优雅的python

pytonic是python的编程哲学。python是一种代表简单主义简单主义思想的语言。阅读一个良好的Python程序就感觉像是在读英语一样。它使你能够专注于解决问题而不是去搞明白语言本身。

pythonic主要体现在python没有其他语言中常见的“；”，“{}”等格式字符，还有它提供的一些语法糖。

> 语法糖：
>
> 语法糖（Syntactic sugar），也译为糖衣语法，是由英国计算机科学家彼得·约翰·兰达（Peter J. Landin）发明的一个术语，指计算机语言中添加的某种语法，这种语法对语言的功能并没有影响，但是更方便程序员使用。通常来说使用语法糖能够增加程序的可读性，从而减少程序代码出错的机会。
>
> 在python中以"\*"\*4代替"\****"就是一种语法糖

