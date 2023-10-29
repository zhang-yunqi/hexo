---
categories:
  - Python and reinforcement leraning
---
# python的for循环是range-based for loop

提到range-based for loop 就必须要提到与之对应的另一个概念regular for loop。顾名思义，regular for loop是一种更传统的for loop。很多有历史[^ 1]的编程语言都是regular for loop。比如c/c++

```cpp
for (int i=0; i<10; i++){
    std::cout<<i;
}
std::cout<<std::endl;
```

## regular for loop为什么regular（传统）：

这涉及到一个关于汇编语言的知识点。汇编只有一种循环——loop循环

```asm
mov cx, 100 //将cx寄存器的值设为100
s:
//doing some thing
loop s
```

这个循环的作用就是将s段的内容执行100次，可以发现高级编程语言中的regular for loop与汇编的loop有异曲同工之妙。

> cx寄存器是计数（count）寄存器

## range-based for loop的诞生

如果你善于总结那你就会发现，regular for loop是基于计数的一种for loop的实现，以上代码可以用这样的while loop来替代：

```cpp
int i=0;
while i<10{
    std::cout<<i;
    i++;
}
std::cout<<std::endl;
```

不难发现for循环和while循环在regular for loop中并不能减少特别多的思考，尤其是再for循环应用最多的场景，数组的遍历。优秀的程序员总是懒人，他们当然不满与regular for loop的现状，所以range-based for loop应运而生。

下面就是python中range-based for loop遍历一个列表的代码：

```python
li:list=[1,2,3,4]
for i in li:
    print(i)
```

就是如此简单，range-based for loop就是为遍历而生的。

## for loop 常用于知道循环次数的循环

遍历只是很小的一种功能，range-based for loop的能力当然不止于此。它和range关键字组合在一起将是一个王炸。

### range关键字

range关键字是用于生成列表的，它可以生成一个前闭后开的整型数组。它通常接受两个参数，起始数和结束数。如果只填写一个参数那默认填写的参数是结束数，而起始数为0。

这一段代码就可以实现前面c++代码的功能

```python
for i in range(10):
    print(i, end="")
print("")
```

## c++的range-based for loop

c++11中增加的对rande-based for loop的支持

```cpp
vector<int> li = {0, 1, 2, 3, 4};
for(int i: li){
    std::cout<<i;
}
```





[^ 1]: 相对而言