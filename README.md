pylimit
========================================
**给python的动态特性加上约束**

介绍
----

python作为动态语言，他的方便和灵活是无需置疑的。但也是因为其动态的特性，有时会带给我们一些麻烦，
比如说函数传进错误的参数类型，当然你可以告诉我作为程序员，调用函数的时候理应知道该传进什么类型参数，
但总有一些情况你希望函数的参数类型能做一些约束（比如你一时粗心大意，或者项目很赶，心急容易犯错）。
虽然说，一些操作如果参数类型出现错误将无法进行，导致触发异常。但假如本来想做**数字相加**，
但结果传进**字符作为参数**，这类操作显然**不会触发异常(意味着很难找到)**，但得到结果却是错误的。


在python中检测函数参数类型的时候你可以用```isinstance```来处理，如果是参数数量太多，你也想约束,那么
用```isinstance```判断会显得很烦，如果能像```java```,```C++```这类静态语言那样在声明函数时就指定参数类型那该多好。

花费了半小时，写了这个装饰器，约束了函数的参数类型和返回类型以及减少其他python动态特性带来的一些负面效果。

简单示例
--------

    from pylimit import type_limit
    
    @type_limit(int,int)
    def test(x,y):
        return x + y


    print(test(1,'2'))
    >>> pylimit.LimitError: The param 2 should be <class 'int'>,but it's <class 'str'> now!

	print(test(1,2))
    >>> 3

文档
----------

[Document](doc.md)
    
**这个repository初衷只是给自己省去写insatance的目的，
如果你觉得有帮助，可以拿去使用，但切记不要乱用，不要因此使你的python代码失去了动态语言的灵活**

如何安装
--------

下载本代码，切换到对应的目录下
```python setup.py install```

在python交互式编程的环境下，```import pylimit```,无错误提示则安装成功。欢迎使用可以限制python的装饰器 ^ v ^ 

    
开源协议
--------

Apache License 2.0


To Do List
---------

- [x] 函数参数类型，返回值进行约束
- [x] 一维列表的作参数时，对最少长度进行约束,避免运行时才触发越界异常
- [x] 二维列表or 元组每一维的长度进行约束(长度必须相等)，某些算法可能需要，例如决策树的训练
- [x] 列表的长度，每一个位置固定一个指定类型，如规定一个list或tuple的类型为[int,float,str]等有序,同样是出于某些算法的需求。
- [x] 常量,即Const

等哪天我发现python某个方面让我不爽的时候再添加到To Do 




PS
--------

学了大概两年的python，深感动态语言的自由灵活，但这些特性有时却需要付出一些代价，突然觉得有句话说得很正确。**只有在一定约束下的自由才是真自由**

谢谢支持。