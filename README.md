## Doc
- [Docker + ASP.NET Core 远程调试](http://blog.wuwenxiang.net/Docker-AspNetCore-VS-Debug)

## Lab
1. [VisualStudio + 本地 + Docker + ASP.NET](https://github.com/wu-wenxiang/Training-AspDotNetCore-Docker-Public/tree/master/Docker-AspDotNet)
1. [VisualStudio + 本地 + Docker + ASP.NET Core](https://github.com/wu-wenxiang/Training-AspDotNetCore-Docker-Public/tree/master/Docker-AspDotNetCore)
1. [VisualStudio + RemoteDebug + CentOS + Docker + ASP.NET Core](https://github.com/wu-wenxiang/Training-AspDotNetCore-Docker-Public/tree/master/Docker-AspDotNetCore/AspDotNetCore-WebApi-Docker-Linux-RemoteDebug)
1. VScode + Debug + Docker + ASP.NET Core

## 容器技术栈入门
- Golang Debugging
	- 用户态调试时，Debugger能做些什么？
		- 以启动模式**Open**，或者**Attach**住进程：运行/暂停执行
		- 捕捉调试事件：单步执行/设置断点/捕获异常事件
		- 查看和修改寄存器、内存数据
	- 有哪些典型的调试事件？
		- 断点触发
		- 非法内存操作（Access Violation / Segment Fault）
		- 由被调试程序抛出的异常
		- 其它：进程/线程创建和消亡，动态链接库的运行时导入
	- 可以设置几种断点？
		- 软件断点
		- 硬件断点
		- 内存断点
	- Debug为什么难？因为缺失了信息。
		- 符号表
		- 源码
	- Go是一种什么样的语言？
		- 是：静态语言、静态类型语言、强类型语言、非托管、函数式编程、面向对象、内置GC
		- 没有：隐式类型转化、构造和析构、运算符重载、默认形参、继承、范型、异常、函数注释、线程局部变量
		- 设计哲学：
			- 不牺牲“简单性”来换取“方便性”
			- 兼顾表达力（易用性）、性能、和安全性（稳定性）
		- 数据类型：
			- 基本数据：整数、浮点数、复数、布尔值、字符串、常量
			- 复合数据：数组、slice、map、结构体
			- 函数/方法
			- 接口
			- goroutine与chan
				- goroutine是m个协程活在n个线程池中：epoll
				- 可以在代码层再次select
			- 低级编程：unsafe
			- 有指针但不能做算术运算
		- 从长期看：落地与生态
			- 适合写后端服务
			- 代表作：Docker、Kubernetes以及一干工具
			- 有规范强大的标准库
	- Debug with go
		- 基于源码的调试
- Docker usage, configuration & inside
	- 容器是什么？
	- 容器和虚拟机相比，有哪些优势和不足？
	- 容器适用于什么场景？
	- Docker和容器有什么关系？
	- EE和CE应该怎么选？
	- Quick Start
- Kubernetes quick start & usage
	- Kubernetes和Docker swarm应该怎么选？
	- Quick Start
- AKS
	- Quick Start

