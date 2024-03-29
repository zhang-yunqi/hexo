---
title: 右值引用与move语意
categories: [Morden C++]
---

# 左值（lvalue）和右值（rvalue）

左值与右值这两个概念是从C中传承而来的，左值指既能够出现在等号左边，也能出现在等号右边的变量；右值则是只能出现在等号右边的变量。
```c++
int 3;//a为左值
a = 3;//3为右值
```

## 他们具有这样的特点：
* 左值是可寻址的变量，有持久性；
* 右值一般是不可寻址的常量，或在表达式求值过程中创建的无名临时对象，短暂性的。

## 常见的右值
* 字面量
* 函数调用返回的值或对象（返回左值引用除外） 
* 构造的无名对象

# 右值引用
引用是在C++中非常常见的一种语法，当函数需要直接修改参数的值时十分常用。如下面是一个简单的双指针删除大写字母的案例：
```c++
string remove_capital(string &str, int size) {
  string res(size, ' ');
  int j = 0;
  for (int i = 0; i < size; i++) {
    if (str[i] > 90 || str[i] < 41) {
      res[j++] = str[i];
    }
  }
  return res;
}
```
当我们这样调用：
```c++
string str = "Hello world";
remove_capital(str, str.size());
cout<<str<<endl;
```
可以看到正常输出了“ello world”
但是假如我们要通过一个函数从服务器，数据库之类的地方去数据呢？
