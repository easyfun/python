###[笔记]Python解释器

Python语言从规范到解释器都是开源的，任何人都可以写Python解释器来执行Python代码。存在多种Python解释器。

###CPython
官方版本，用C语言开发，使用最广的Python解释器。

###IPython
基于CPython，增强了交互式

###PyPy
目标是提高执行速度，采用JIT技术，对Python代码进行动态编译（注意不是解释）。与CPython不是完全兼容的。

###Jython
运行在Java平台上的Python解释器，可以把Python代码编译成Java字节码执行。

###IronPython
运行在.Net平台上的Python解释器，可以把Python代码编译成.Net字节码。

使用最广泛的是CPython。如果与Java，.Net交互，最好用网络交互。