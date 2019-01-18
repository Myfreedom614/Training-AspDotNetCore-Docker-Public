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
- [Demo](https://github.com/adonovan/gopl.io)
- U1804
	- `sudo apt-get update -y && sudo apt-get upgrade -y`
	- `sudo apt install golang-go`
	- go lang
	
			pear@testU1804:~$ cat test.go 
			package main
			
			import (
				"fmt"
			)
			
			func main() {
				fmt.Println("Hello")
			}
			pear@testU1804:~$ go build test.go 
			pear@testU1804:~$ ls
			test  test.go
			pear@testU1804:~$ ./test 
			Hello
	- `sudo apt-get install gdb`
	- GDB
	
		| 命令 | windbg | gdb | 
		| :-- | :---------- | :--------- |
		| 附加 | attach | attach | 
		| 脱离附加 | detach | detach | 
		| 运行 | g/F5 | run/r | 
		| 继续 | g/F5 | continue/c | 
		| 步过 | p/F10 | n/ni | 
		| 步进 | F11 | s/si | 
		| 执行到返回 | gu | finish | 
		| 下断点 | bp ba | break/br | 
		| 查看断点 | bl | info break | 
		| 禁止断点 | bd | disable breakpoint | 
		| 开启断点 | be | enable breakpoint | 
		| 删除断点 | bc | delete breakpoints | 
		| 查看寄存器 | r | info register/i r | 
		| 修改寄存器 | r | set | 
		| 查看内存 | db dw dd | x | 
		| 修改内存 | eb ew ed | set {type}address | 
		| 查看调用栈 | k kb kb kPL | bt | 
		| 查看全部线程 | ~* | info threads | 
		| 线程切换 | ~ threadid s | thread threadid | 
		| 查看进程 | | * | info inferior | 
		| 进程切换 | | pid s | inferior | 
		| 查看符号 | x module!symbol | info symbol | 
		| 反汇编 | u uf | x /i            disassemble | 
		| 寄存器表示 | eax.... | $eax  ... | 
	- [Debugging Go Code with GDB](https://golang.org/doc/gdb)
	
			$ cat test.go 
			package main
			
			import (
				"fmt"
			)
			
			func fun1(c string) {
				fmt.Println("Begin fun1... =>", c)
				fun2(5)
				fmt.Println("End fun1...")
			}
			
			func fun2(a int) {
				b := a+1
				fmt.Println("=>", b)
			}
			
			func main() {
				fmt.Println("Hello")
				fun1("Play")
				fun2(4)
			}
			pear@testU1804:~$ go build -gcflags=all="-N -l" test.go
			pear@testU1804:~$ curl https://golang.org/src/runtime/runtime-gdb.py?m=text -o runtime-gdb.py
			
			source /home/pear/runtime-gdb.py
	- Demo1: [使用 gdb 工具调试 Go](https://www.oschina.net/translate/using-gdb-debugger-with-go)
	- Demo2: [using gdb debugger with go](https://blog.codeship.com/using-gdb-debugger-with-go/)