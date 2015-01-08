Python编码风格就用这个了


<h3 id="python-coding-specification">Python编码规范</h3>
> 很多书都把代码编写规范写在附录中， 其实大多数人都是不看的，  
但是在很多公司的团队协作中代码编写规范都放在第一位。  

> 很多人不理解， 为什么大家写的代码习惯需要规范？  
如果所有项目编码规范都是一致的， 大家会有更多的时间专注于核心逻辑的沟通上，  
而不是浪费时间在不同人书写的不同习惯。  
特别是 Python 这种对缩进非常敏感的语言对编码的规范就要求更高了，  
否则不同缩进的 Python 代码完全没有办法就行有效的互通。  

> 我希望把Python编码规范写在这里让大家明白好的代码规范对于团队协作的重要性。  
以下是具体的 Python 编码规范：

>> * **文件开头**:  
>>    在Python源代码的第一行添加  
>>> <pre lang="python"><code>
>>>		#! /usr/bin/env python
>>> </code></pre>

>>    这样可以让系统找到 python 的路径并执行, 而不会因为写死了 python 路径在其他系统上无法运行.  

>> * **编码**:  
>>    在Python源代码的第二行添加
>>> <pre lang="python"><code>
>>>		# -*- coding: utf-8 -*-
>>> </code></pre>

>>    设置默认编码为 utf-8 格式

>> * **版权申明**:  
下面是一个简单的版权申明模板, 从Python源代码第四行插入(第三行为空行),  
请在拷贝后修改 Copyright, Author, Maintainer 相关的信息:  

>>    \# Copyright (C) 2011 ~ 2013 Wang Yong  
\# 						  
\# Author:     Wang Yong <wangyong@linuxdeepin.com>  
\# Maintainer: Wang Yong <wangyong@linuxdeepin.com>  
\#   
\# This program is free software: you can redistribute it and/or modify  
\# it under the terms of the GNU General Public License as published by  
\# the Free Software Foundation, either version 3 of the License, or  
\# any later version.  
\#   
\# This program is distributed in the hope that it will be useful,  
\# but WITHOUT ANY WARRANTY; without even the implied warranty of  
\# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the  
\# GNU General Public License for more details.  
\#   
\# You should have received a copy of the GNU General Public License  
\# along with this program. If not, see <http://www.gnu.org/licenses/>.  

>> * **import 语句**:  
import 语句有以下几个原则需要遵守：  
>>> 1\. 一行语句 import 一个模块。  
>>>   
>>>    **Yes**:  
>>> <pre lang="python"><code>
>>>     import os
>>>     import sys
>>> </code></pre>
>>>    **No**:  
>>> <pre lang="python"><code>
>>>		import os, sys	
>>> </code></pre>
>>> 2\. import 从行首开始写, 不要在import前面添加空格.  
>>> 3\. 当从模块中 import 多个对象且超过一行时，使用如下断行法（此语法 py2.5 以上版本才支持）：  
>>> <pre lang="python"><code>
>>>     from module import (obj1, obj2,
>>>                         obj3, obj4)
>>> </code></pre>
>>> 4\. 不要使用  
>>> <pre lang="python"><code>
>>>		from module import *	
>>> </code></pre>
>>>    除非是 import 常量定义模块或其它你确保不会出现命名空间冲突的模块。    
>>> 5\. 如果从包导入模块, 你需要在包中的每一级目录中创建 \_\_init\_\_.py 文件,  
\_\_init\_\_.py 文件内容为空.  
比如 import dtk.ui.application ,  
dtk/ 和 dtk/ui/ 目录下都需要建立 \_\_init\_\_.py ,  
否则 python 不能发现包中的模块, 下面是对 import dkt.ui.application 的目录结构图:  
>>>     <pre>
>>> dtk/
>>> |
>>> |- __init__.py
>>> |
>>> +- ui/
>>>    |
>>>    |- __init__.py
>>>    |
>>>    +- application.py
>>> 
>>>    </pre>
>>> 6\. 导入模块的代码规范:  
>>> <pre lang="python"><code>
>>>		import foo
>>> </code></pre>
>>> 7\. 从模块中导入特定对象规范:  
>>> <pre lang="python"><code>
>>>		from foo import bar
>>> </code></pre>
>>> 8\. 从包中导入模块:  
>>> <pre lang="python"><code>
>>>		import dtk.ui.application
>>> </code></pre>
>>> 9\. 从包中导入特定对象规范:  
>>> <pre lang="python"><code>
>>>		from foo.bar import hello
>>> </code></pre>

>> * **缩进**:  
>> Python 依赖缩进来确定代码块的层次，行首空白符主要有两种：  
tab 和空格，但是严禁使用 tab, 在写代码之前请把编辑器中的 tab 强制转换为 4 个空格.  

>>     名字很长函数的参数缩进  
有时候一个函数的名字很长,它的参数应该另起一行再缩进,  
这样既美观又不印象函数层级的阅读, 下面是例子:  
>>>   
>>    **Yes**:  
>> <pre lang="python"><code>
>>     foo = long_function_name(
>>             var_one, var_two,
>>             var_three, var_four)
>>     def long_function_name(
>>             var_one, var_two,
>>             var_three, var_four):
>> </code></pre>
>>>   
>>    **No**:  
>> <pre lang="python"><code>
>>     foo = long_function_name(var_one, var_two,
>>             var_three, var_four)
>>     def long_function_name(var_one, var_two,
>>             var_three, var_four):
>> </code></pre>

>> * **空格**:   
>> 空格在 Python 代码中是有意义的，  
因为 Python 的语法依赖于缩进，在行首的空格称为前导空格。  
在这一节不讨论前导空格相关的内容，只讨论非前导空格。  
非前导空格在 Python 代码中没有意义，但适当地加入非前导空格可以增进代码的可读性。  

>>> 1\. 在二元算术、逻辑运算符前后加空格：  
>>>   
>>>    **Yes**:     
`a = b + c`
>>>   
>>>    **No**:  
`a=b+c`

>>> 2\. 在一元前缀运算符后不加空格:  
>>>    **Yes**:     
>>> <pre lang="python"><code>
>>>     if !flg:
>>>         pass
>>> </code></pre>

>>>    **No**:     
>>> <pre lang="python"><code>
>>>     if ! flg:
>>>         pass
>>> </code></pre>
	
>>> 3\. 函数名和括号之间不能有空格:  
>>>    **Yes**:     
>>> <pre lang="python"><code>
>>>     def foo():
>>>         pass
>>> </code></pre>

>>>    **No**:     
>>> <pre lang="python"><code>
>>>     def foo ():
>>>         pass
>>> </code></pre>
	
>>> 4\. : 用在行尾时前后皆不加空格，如分枝、循环、函数和类定义语言  
>>>    **Yes**:     
>>> <pre lang="python"><code>
>>>     if flag:
>>>         pass
>>> </code></pre>
>>>    **No**:     
>>> <pre lang="python"><code>
>>>     if flag:
>>>         pass
>>> </code></pre>

>>> 5\. : 用在非行尾时两端加空格，如 dict 对象的定义:  
>>>    **Yes**:     
>>> <pre lang="python"><code>
>>>		d = {‘key’ : ’value’}
>>> </code></pre>

>>>    **No**:     
>>> <pre lang="python"><code>
>>>		d = {'key':'value'}
>>> </code></pre>

>>> 6\. 括号（含圆括号、方括号和花括号）前后不加空格:  
>>>    **Yes**:     
>>> <pre lang="python"><code>
>>>		do_something(arg1, arg2)
>>> </code></pre>

>>>    **No**:     
>>> <pre lang="python"><code>
>>>		do_something( arg1, arg2 )
>>> </code></pre>

>>> 7\. 逗号后面加一个空格，前面不加空格  

>>> 8\. 函数参数的等号两边不添加空格, 比如:  
>>>    **Yes**:     
>>> <pre lang="python"><code>
>>>     def foo(arg1="hello",
>>>             arg2="world"):
>>>         ...
>>> </code></pre>
	
>>>    **No**:     
>>> <pre lang="python"><code>
>>>     def foo(arg1 = "hellow",
>>>             arg2 = "world"):
>>>         ...
>>> </code></pre>
	
>>> 9\. 不要为多行赋值语句添加过多的对齐空格, 快速的修改代码比局部的美观更重要:  
>>>    **Yes**:     
>>> <pre lang="python"><code>
>>>     var_a = 1
>>>     var_long_a = 2
>>>     var_long_long_a = 3
>>> </code></pre>

>>>    **No**:     
>>> <pre lang="python"><code>
>>>     var_a            = 1
>>>     var_long_a       = 2
>>>     var_long_long_a  = 3
>>> </code></pre>

>>> 上面的代码看似漂亮, 但你能保证以后没有更长的变量名?  
>>> 更长的变量名添加以后是否要对在一块的代码都要统一加空格呢? 为什么要浪费时间按空格呢?  

>> * **空行**:   
>> 适当的空行有利于增加代码的可读性，加空行可以参考如下几个准则：  
>>> 1\. 在类、函数的定义间加空行；  
>>> 2\. 在 import 不同种类的模块间加工行；  
>>> 3\. 在函数中的逻辑段落间加空行，即把相关的代码紧凑写在一起，作为一个逻辑段落，段落间以空行分隔；  

>> * **命名**:   
>>> 一致的命名可以给开发人员减少许多麻烦，  
而恰如其分的命名则可以大幅提高代码的可读性，降低维护成本。  
好的命名可以让代码有自解释性,  
代码中严禁写 var1, var2 这种结合幻数的名字, 一时的偷懒只会让代码更难维护.  

>>> * **常量**  
>>> 常量名所有字母大写，由下划线连接各个单词，如  
>>> <pre lang="python"><code>
>>>     WHITE = 0XFFFFFF
>>>     THIS_IS_A_CONSTANT = 1
>>> </code></pre>

>>> * **变量**  
>>> 变量名全部小写，由下划线连接各个单词，如  
>>> <pre lang="python"><code>
>>>     color = WHITE
>>>     this_is_a_variable = 1
>>> </code></pre>

>>>> 不论是类成员变量还是全局变量，均不使用 m 或 g 前缀。  
私有类成员使用单一下划线前缀标识，多定义公开成员，少定义私有成员。  
变量名不应带有类型信息，因为 Python 是动态类型语言。  
如 iValue、names_list、dict_obj 等都是不好的命名。  

>>> * **函数**  
>>> 函数名的命名规则与变量名相同。  

>>> * **函数参数**  
>>> 函数参数的命名规则与变量名相同.  

>>> * **类**  
>>> 类名单词首字母大写，不使用下划线连接单词，也不加入 C、T 等前缀。如：  
>>> <pre lang="python"><code>
>>>     class ThisIsAClass(object):
>>>           passs
>>> </code></pre>

>>> * **异常名**  
>>> 异常的命名规则和类名的规则相同．  
异常名最好在后面跟随 Error:  
>>>> **Yes**:
>>>> <pre lang="python"><code>
>>>>     try:
>>>>        ... bla bla ...
>>>>     except MyError:
>>>>        ... bla bla ...
>>>> </code></pre>
>>>> **No**:
>>>> <pre lang="python"><code>
>>>>     try:
>>>>        ... bla bla ...
>>>>     except my_error:
>>>>        ... bla bla ...
>>>> </code></pre>

>>> * **模块**  
>>> 模块名全部小写，对于包内使用的模块，可以加一个下划线前缀，如  
>>> `this_is_a_module.py`  
>>> `_this_is_an_internal_module.py`  

>>> * **包**  
>>> 包的命名规范与模块相同。  

>>> * **缩写**  
>> 命名应当尽量使用全拼写的单词, 不建议大范围使用缩写,  
除非某些一目了然的缩写, 比如 tmp.  
命名长一点没关系, 但是一个晦涩难懂的缩写会导致维护困难和更难于发现 bug.  

>> * **分枝和循环**:  
>>> 不要写成一行，如：  
>>> <pre lang="python"><code>
>>> 		if !flg: pass
>>> </code></pre>
>>>
>>>		或者
>>>
>>> <pre lang="python"><code>
>>>			for i in xrange(10): print i
>>> </code></pre>
>>> 都不是好代码，应写成  
>>> <pre lang="python"><code>
>>>     if !flg:
>>>         pass
>>> </code></pre>
>>>
>>>		或者
>>>
>>> <pre lang="python"><code>
>>>     for i in xrange(10):
>>>         print i
>>> </code></pre>

>> * **语句**:   
>> 不推荐在一行里写入多行语句  
>>> **Yes**:  
>>> <pre lang="python"><code>
>>>     if foo == 'blah':
>>>         do_blah_thing()
>>>         do_one()
>>>         do_two()
>>>         do_three()
>>> </code></pre>
>>> **No**:  
>>> <pre lang="python"><code>
>>> 	if foo == 'blah': do_blah_thing(); do_one(); do_two(); do_three()
>>> </code></pre>

>> * **注释**:  
>>> 注释必须用英文编写, 熟练的英文读写能力是一个合格程序员的基本能力,  
用英文写可以让更多的人阅读你的源代码, 帮你打补丁.  
注释必须是简洁, 清晰易懂的.  
每句注释的首字母要大写.  

>>>> **函数注释**  
>>>> 函数注释以 ”’ 开头, 以 ”’ 结尾, 函数注释另起一行, ”’  
包围的注释有更强的兼容性, 能在注释中写入引号 ( ” , ‘ ) 而不会有问题.  

>>>> **Yes**:
>>>> <pre lang="python"><code>
>>>>     def foo():
>>>>         '''
>>>>         This is comment line.
>>>>         This is another comment line.
>>>>         '''
>>>> </code></pre>

>>>> **No**:
>>>> <pre lang="python"><code>
>>>>     def foo():
>>>>         "This is comment line. This is another comment line."
>>>> </code></pre>

>>>> **代码块注释**  
>>>> 函数中经常存在很多相互独立的代码块,  
为了代码清晰易读, 不但要在代码块之间添加空行,  
最好在代码块起始位置添加一行注释用于说明代码块的作用:  
代码块注释用 #　开头，　在 # 紧跟一个空格开始写注释．  

>>>> **Yes**:
>>>> <pre lang="python"><code>
>>>>     # This is first block comment.
>>>>     var_first = 1
>>>>     ...
>>>>     # This is second block comment.
>>>>     var_second = 2
>>>>     ...
>>>>     # This is third block comment.
>>>>     var_third = 3
>>>>     ...
>>>> </code></pre>

>>>> **No**:
>>>> <pre lang="python"><code>
>>>>    # This is first block comment.
>>>>    var_first = 1
>>>>    ...
>>>>    # This is second block comment.
>>>>    var_second = 2
>>>>    ...
>>>>    # This is third block comment.
>>>>    var_third = 3
>>>>    ...
>>>> </code></pre>


>>>> **语句尾部注释**  
>>>> 语句尾部注释用 #　开头，　在 # 紧跟一个空格开始写注释．  

>>>> **Yes**:
>>>> <pre lang="python"><code>
>>>>     var_a = 1 # This is first comment
>>>> </code></pre>

>>>> **No**:
>>>> <pre lang="python"><code>
>>>>     var_a = 1 #this is first comment
>>>> </code></pre>

>> * **字符串**:   
>>> 善用　% 符号对字符串进行排版  
>>> % 可以有效的让动态字符串有更好的阅读性例子，　比如下面的例子：  

>>>>> **Yes**:
>>>>> <pre lang="python"><code>
>>>>> 		print "First: %s, Second: %s, Third: %s" % ("1", "2", "3")
>>>>> </code></pre>

>>>>> **No**:
>>>>> <pre lang="python"><code>
>>>>> 		print "First: " + "1, " + "Second: " + "2, " + "Thrid: " + "3"
>>>>> </code></pre>

>>> * **语言陷阱**:   
>>>> * **判断变量有可能为None时的编程规范**   
一个变量的值有可能为None的时候，　应该以下面的方式来判断：  
>>>> <pre lang="python"><code>
>>>>     if var != None:
>>>>        pass
>>>>     else:
>>>>        pass
>>>> </code></pre>
>>>> 而不能是：  
>>>> <pre lang="python"><code>
>>>>     if var:
>>>>         pass
>>>>     else:
>>>>         pass
>>>> </code></pre>
>>>> 试想一下当　var 为　0 的时候　if 语句永远不能执行，　  
>>>> 所以要写　`if var != None` 来避免这一类的陷阱  
>>>>   
>>>> * **不要比较布尔值**  
>>>> 很多时候布尔表达式是不需要比较的，　看一看下面的例子:   
>>>> **Yes**:
>>>> <pre lang="python"><code>
>>>>     if test:
>>>>        do_something()
>>>> </code></pre>
>>>> **No**:
>>>> <pre lang="python"><code>
>>>>     if test == True:
>>>>        do_something()
>>>> </code></pre>
>>>> **Yes**:
>>>> <pre lang="python"><code>
>>>>     def foo():
>>>>         return 1 == 2
>>>> </code></pre>
>>>> **No**:
>>>> <pre lang="python"><code>
>>>>     def foo():
>>>>         test = 1 == 2
>>>>         return test == True
>>>> </code></pre>
>>>>  
>>>> * **函数默认参数规则**  
>>>> Python 的函数参数是可以支持参数预置值的，　  
>>>> 但是有一点，　所有有默认值的函数参数变量必须放在没有预置值的后面．  
>>>> **Yes**:
>>>> <pre lang="python"><code>
>>>>     def foo(arg1, arg2, arg3=3, arg4=4):
>>>>         ...
>>>> </code></pre>
>>>> **No**:
>>>> <pre lang="python"><code>
>>>>     def foo(arg1, arg2=2, arg3, arg4):
>>>>         ...
>>>> </code></pre>
>>>> * **如果类型不继承与任何其他类型，　默认继承object**  
>>>> 如果类型不继承与任何其他类型，　  
>>>> 默认继承object, 这样做的好处是让你的代码和新版python有更好的兼容性．  
>>>> **Yes**:
>>>> <pre lang="python"><code>
>>>>     class Foo(object):
>>>>           ...
>>>> </code></pre>
>>>> **No**:
>>>> <pre lang="python"><code>
>>>>     class Foo():
>>>>          ...
>>>> </code></pre>
>>>> * **不要使用 . 和 .. 来连接文件路径**  
>>>> **Yes**:
>>>> <pre lang="python"><code>
>>>> 		os.path.join(os.path.dirname(os.path.realpath(__file__)), "foo.py")
>>>> </code></pre>
>>>> **No**:
>>>> <pre lang="python"><code>
>>>> 		"." + "/" + "foo.py"
>>>> </code></pre>
>>>> 我们要取得当前目录的文件, 一般我们会用 “.” 或 “..” 来进行文件路径连接.  
如果当前文件就是直接执行文件应该是没有问题的, 但是这行代码却充满陷阱,  
因为 “.” 并不代表你源代码定义时的目录, 而是相对于运行时的目录,  
比如有一个其他目录的软链接链接到当前文件, “.” 的意思是软链接的目录, 而不是定义 “.” 源代码所在的目录.  
>>>>   
>>>> 为了避免这个问题, 可以用 \_\_file\_\_ 来代替, \_\_file\_\_ 会在运行前就用当前定义文件的路径给替换掉,  
这样不论是否有软链接,
`os.path.dirname(os.path.realpath(__file__))` 都表示的是源文件所在的目录.  
另一个注意的地方是用 `os.path.join` 替代 `“dirname” + “/” + “file.py”` 的形式,  
因为非Linux平台(比如Widnows)文件链接符不是 “/”, 而是 “\”,  
用 `os.path.join` 可以自动使用平台所在的链接符, 代码更具通用性.