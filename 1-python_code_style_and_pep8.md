Python代码风格和PEP8

PEP8描述了Python的代码风格。Python开发成员共同遵守这个文档风格，可以最大程度保持Python代码风格的一致，易于阅读，易于交流。

###1 变量

__普通变量：小写加下划线，使用完整单词，避免使用缩写，避免使用幻数变量。__

__常量__：大写加下划线

    USER_CONSTANT

__私有变量__：小写和一个前导下划线

    _private_value

Python中不存在私有变量。当需要封装变量，对外隐藏时，使用小写和一个前导下划线。这是一种约定，实际上外部任然可以访问。

__内置变量__：小写，两个前导下划线和两个后置下划线
      
    __class__

两个前导下划线会导致变量在解释期间被更名。这样做是为了避免内置变量和其他变量产生冲突。

用户定义的变量禁止使用这种风格。


###2 函数和方法

总体上使用小写和下划线。有些比较老的库使用的混合大小写，首单词小写，之后每个单词首字母大写，其余小写。现在，小写和下划线是规范。

__私有方法__：小写和一个前导下划线

    def _secrete(self):
        print "don't test me."

与私有变量一样，不是真正的私有访问权限。

_注意：_一般函数不要使用两个前导下划线。当遇到两个前导下划线时，Python的名称改编特性将发挥作用。

__特殊方法：__小写，两个前导下划线和两个后置下划线

    def __add__(self,other):
        return int.__add__(other)

这种风格只适用于特殊函数，比如操作符重载。

__函数参数：__小写和下划线，缺省值等号两边无空格

    def connect(self, user=None):
        self._user = user

###3 类

类总是使用驼峰格式命名，即所有单词首字母大写，其余字母小写。类名应该简明，精确，并足以从中理解类的功能。常见的一个方法是使用表示其类型或者特性的后缀，例如：<br/>
SQLEngin<br/>
MimeTypes

对于基类而言，可以使用一个Base或者Abstract前缀<br/>
BaseCookie<br/>
AbstractGroup

    class UserProfile(object):
        def __init__(self,profile):
            return self._profile = profile

        def profile(self):
            return self._profile


###4 模块和包

除特殊模块__init__之外，模块名称都使用不带下划线的小写字母。<br/>
若模块或者包实现一个协议，通常使用lib为后缀，例如：<br/>
import smtplib

    import os
    import sys

###5 关于参数

5.1 不要用断言实现静态类型检测<br/>
>断言可以用于检查参数，不要用断言做静态类型检查。<br/>
Python是动态语言，静态类型检查违背了动态语言的设计思想。<br/>
断言应该用于避免函数不被毫无意义的调用。

5.2 不要滥用\*args 和 \*\*kwargs<br/>
\*args 和 \**kwargs参数可能破坏函数的健壮性。

###6 其他

6.1 使用has或is前缀命名布尔元素

    is_connect= True
    has_member = False

6.2 用复数形式命名序列

    members = ['user_1','user_2']

6.3 用显示名称命名字典

    person_address = {'user_1':'10 road WD','user_2':'20 street huafu'}

6.4 避免通用名称

诸如list，dict，sequence或者element这样的名称应该避免。

6.5 避免现有名称

诸如os，sys这样系统已经存在的名称应该避免。

###7 一些数字

一行列数：PEP8规定为79列。做到不动水平游标，即可看到全部代码。<br/>
一个函数：不要超过30行代码，即可显示在一个屏幕上。<br/>
一个类：不要超过200行代码，不要有超过10个方法。<br/>
一个模块：不要超过500行。 
	
###8 验证脚本

可以安装一个pep8脚本用于验证代码风格是否符合PEP8。

     http://pypi.python.org/pypi/pep8/#downloads
     >>easy_install pep8
     >>pep8 -r --ignore E501 Test.py

这个命令行的意思是，重复打出错误，并且忽略 501 错误(代码超过 79 行)。

Ubuntu上的安装可以用命令

     sudo apt-get install pep8



参考文章：

1. http://www.blogjava.net/lincode/archive/2011/02/02/343859.html
