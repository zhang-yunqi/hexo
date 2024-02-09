---
title: chrono现代C++的时间库
date: 2009-10-10
categories: [Morden C++]
---

# chrono现代C++中的时间库

## 时钟
chrono提供了3种时钟
* steady_clock 是单调的时钟，相当于教练手中的秒表；只会增长，适合用于记录程序耗时
* system_clock 是系统的时钟；因为系统的时钟可以修改；甚至可以网络对时； 所以用系统时间计算时间差可能不准
* high_resolution_clock 是当前系统能够提供的最高精度的时钟；它也是不可以修改的。相当于 steady_clock 的高精度版本 

### 函数
时钟所返回的值是time_point他们有相同的函数，下面列举一些:
1.time_sence_epoch()
返回一个duration对象，与1970年一月一日凌晨零点零分零秒的时间间隔
2.max()
返回最大持续时间对应的时间点
3.min()
返回最小持续时间对应的时间点

system_clock是系统时钟，具有一些特殊的属性，其中常用到的是可以转为time_t。究其原因是ctime中time_t也是系统时钟的时间点。
```c++
std::chrono::system_clock::to_time_t(& time_point<std::chrono::system_clock>)
```

## duration
duration 是chrono中表示时间间隔的类
### 常用函数
1.const()
返回这段时间的ticks数
2.min()
返回特殊持续时间值min
3.max()
返回特殊持续时间值max
4.zero()
返回特殊持续时间值零


