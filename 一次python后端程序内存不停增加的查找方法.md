由于后端代码不是自己写的，刚接手就遇到了棘手的OOM，发现程序运行一定时间，内存一直飙升。
发现Python真的很nice，竟然有这么好的工具。

# 使用 memory_profiler 监控函数级别的内存使用
memory_profiler 允许分析 Python 代码在每行的内存使用情况。

安装 memory_profiler
```bash
pip install memory_profiler
```
示例：监测函数内存使用

```python

from memory_profiler import profile

@profile
def memory_test():
    x = [i for i in range(1000000)]  # 创建大列表
    y = [j**2 for j in range(1000000)]  # 另一个大列表
    return x, y

memory_test()
```

# 使用工具后，很快定位到内存不断增加的地方。
![GitHub Logo](https://github.com/yangdanfeng115/pythonStudy/blob/main/images/previous_bug.jpg)

具体哪一行导致内存增加

![GitHub Logo](https://github.com/yangdanfeng115/pythonStudy/blob/main/images/bug.jpg)

问题解决后：

![GitHub Logo](https://github.com/yangdanfeng115/pythonStudy/blob/main/images/after_bug.jpg)

# 优点：

可以逐行分析 Python 代码的内存占用情况。

适用于优化函数内存使用。



