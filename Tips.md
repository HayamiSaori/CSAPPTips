## 第1章：计算机系统漫游

* 计算机系统是由**硬件**和**系统软件**组成的

#### 1.1：信息就是位+上下文

* ASCII字符表

	![img](Tips.assets/ASCII.png)

* 只由ASCII字符构成的文件称为**文本文件**，所有其它文件称为**二进制文件**

#### 1.2：程序被其他程序翻译成不同的格式

###### 编译系统的构成

编译系统由预处理器（cpp）、编译器（ccl）、汇编器（as）、链接器（ld）组成

![编译系统](Tips.assets/编译系统.png)

* 预处理阶段，即预编译，根据代码中以`#`开头的命令，修改原始的C代码，生成`.i`文件
* 编译阶段，编译器将`.i`翻译成汇编语言程序`.s`
* 汇编阶段，汇编器将`.s`翻译成机器语言指令，将这些指令打包成可重定位目标程序的格式，保存为`.o`
* 链接阶段，链接器负责将涉及到的`.o`文件合并起来，生成可执行文件

#### 1.4：处理器读并解释储存在内存中的指令

###### 1.4.1：系统的硬件组成

* **总线**，通常被设计成传送定长的字节块，也就是字。字的字节数是基本的系统参数，通常为地址的长度
* **IO设备**
* **主存**，通常按字节寻址
* **处理器**，处理器的核心是大小为一个字的存储设备，称为程序计数器

#### 1.6：存储器形成层次结构

![存储层次结构](Tips.assets/存储层次结构.png)

#### 1.7：操作系统管理硬件

* 操作系统的两个基本功能：（1）防止硬件被失控的应用程序滥用；（2）向应用程序提供简单一致的机制来控制复杂而又通常大不相同的低级硬件设备

* 文件是对IO设备的抽象表示；
	虚拟内存是对主存和磁盘IO设备的抽象表示；
	进程是对处理器、主存和IO设备的抽象表示
	
	![抽象表示](Tips.assets/抽象表示.png)

###### 1.7.3：虚拟内存

![虚拟地址空间](Tips.assets/虚拟地址空间.png)

* **程序代码和数据**，对所有的进程来说，代码从同一固定地址开始，紧接着是和C全局变量相对应的数据位置。

* **堆**，调用`malloc`和`free`这样的函数时，堆可以动态地拓展和收缩。

* **共享库**

* **栈**

* **内核虚拟内存**，不允许应用程序读写这个区域的内容或者直接调用内核代码定义的函数

#### 1.9：重要主题

###### 1.9.2：并发和并行

* **并发**，指一个同时具有多个活动的系统
* **并行**，指用并发来使一个系统运行得更快

## 第2章：信息的表示和处理

#### 2.1：信息存储

###### 2.1.2：字数据大小

* 每台计算机都有一个字长，表明指针数据的标称大小。因为虚拟地址是以这样的一个字来编码的。

	![基本C数据大小](Tips.assets/基本C数据大小.png)

###### 2.1.3：寻址和字节顺序

大端法和小端法，对于变量`int x=0x01234567`。大多数Intel兼容机采用小端模式

![大小端法](Tips.assets/大小端法.png)

#### 2.2：整数表示

###### 2.2.1：整型数据类型

C语言整形数据保证的最小取值范围

![C语言整型数据保证范围](Tips.assets/C语言整型数据保证范围.png)

###### 2.2.2：无符号数的编码

$$
B2U_w(\vec{x})=\overset{w-1}{\underset{i=0}{\Sigma}}x_i2^i
$$

###### 2.2.3：补码编码

最高位为符号位，有负权重$2^{w-1}$
$$
B2T_w(\vec{x})=-x_{w-1}2^{w-1}+\overset{w-2}{\underset{i=0}{\Sigma}}x_i2^i
$$

* 反码和原码存在`+0`和`-0`现象

###### 2.2.4：有符号数和无符号数之间的转换

强制类型转换的结果保持位值不变，只是改变了解释这些位的方式

###### 2.2.5：C语言中的有符号数与无符号数

* 当执行一个运算时，如果它的一个运算数是有符号的而另一个是无符号的，那么C语言会隐式地将有符号参数类型转换为无符号数，并假设这两个数都是非负的，来执行这个运算
###### 2.2.6：扩展一个数字的位表示
* 对于`short sx`，`(unsigned)sx`实际上为`(unsigned)(int)sx`，即先进行补码拓展，再进行类型转换

#### 2.3：整数运算
###### 2.3.1：无符号加法

对于`w`位无符号数`x,y,s`，其中`s=x+y`当且仅当`s<x`（等价于`s<y`）时，产生了溢出

###### 2.3.2：补码加法

对于`w`位有符号数补码`x,y,s`，其中`s=x+y`

当且仅当`x>0,y>0,s<=0`，发生正溢出；

当且仅当`x<0,y<0,s>=0`，发生负溢出

###### 2.3.3：补码的非

对于`w`位补码数`x`

![补码的非](Tips.assets/补码的非.png)

计算方法，设`k`为`x`最右边的`1`的位置，即
$$
x=[x_{w-1},x_{w-2},\cdots,1,0,\cdots,0]
$$
有
$$
-x=[~x_{w-1},~x_{w-2},\cdots,1,0,\cdots,0]
$$
即`k`位之前的所有位取反，例如`x=1100,-x=0100`

#### 2.4：浮点数

###### 2.4.2：IEEE浮点表示

阶码用**移码**表示，即补码的符号位取反。这么做便于大小的比较

> 如果阶码（指数）也用补码来表示，就会使得一个浮点数中出现两个符号位：浮点数自身的和浮点数指数部分的。这样的结果是，在比较两个浮点数大小时，无法像比较整数时一样使用简单的无逻辑的二进制比较

![IEEE浮点数](Tips.assets/IEEE浮点数.png)

![IEEE浮点数精度](Tips.assets/IEEE浮点数精度.png)

![IEEE浮点数分类](Tips.assets/IEEE浮点数分类.png)

###### 2.4.4：舍入

* 向偶数舍入，当不取中间值时，就近舍入，如`1.4->1`，`1.6->2`；

	当取中间值时，舍入使得最低有效数字是偶数，如`1.5->2`，`2.5->2`

## 第3章：程序的机器级表示

#### 3.4：访问信息

**x86-64**包含一组16个存储64位的通用目的寄存器

* `%rdi,%rsi,%rdx,%rcx,%r8,%r9`依次为第1到第6个参数，多余参数保存在栈中
* `%rbx,%rbp,%r12,%r13,%r14,%r15`均为调用者（caller）保存
* `%rax`为默认的返回值

![x86-64通用目的寄存器](Tips.assets/x86-64通用目的寄存器.png)

8086中的段寄存器，指明段的起始地址

* **CS**代码段
* **DS**数据段
* **SS**堆栈段
* **ES**附加段

在8086体系中，汇编指令中操作数长度标识

整数

* **b**：字节
* **w**：字，占2个字节
* **l**：双字，占4个字节
* **q**：四字，占8个字节

浮点数

* **s**：单精度浮点数
* **l**：双精度浮点数

###### 3.4.2：数据传送指令

**无条件传送指令**

指令格式

* `mov* src,dst`，`*`可以是`b,w,l,q`中之一，也可以是空白，分别表示1/2/4/8字节。对于指令`movl src,dst`，当`dst`为寄存器时，该指令会将该寄存器的高4字节置零
* `movabsq imm,reg`，将任意64位立即数作为源操作数，`reg`只能为寄存器

操作数类型

* 立即数
* 寄存器，可以是16个整数寄存器之一，但不能用`%rsp`（系统保留），也不能用其他特殊指令专用寄存器
* 内存

单条`mov`指令不能进行从内存到内存的数据传送

**拓展传送指令：按零拓展**

指令格式

* `movz* src,reg`，`*`可以是`bw,bl,wl,bq,wq`中之一，前一个字母为源的大小，后一个字母为指定目的的大小，例如`bw`为将做了零拓展的字节传送到字

操作数类型

* `src`可以是寄存器或内存
* `reg`只能是寄存器

**拓展传送指令：按符号拓展**

指令格式

* `movs* src,reg`，`*`可以是`bw,wl,wl,bq,wq,lq`中之一，前一个字母为源的大小，后一个字母为指定目的的大小，例如`bw`为将做了符号拓展的字节传送到字
* `cltq`，将`%eax`符号拓展到`%rax`

操作数类型

* `src`可以是寄存器或内存
* `reg`只能是寄存器

**条件传送指令**

指令格式

* `cmov* reg,dst`，`*`为一个或两个字符，作为条件，后面还可以接`b,w,l,q`作为长度；条件字符为`g,l,e,n,o`分别表示大于、小于、等于、否、溢出；例如`cmovgel`为当大于或等于时传送一个双字

![条件传送指令](Tips.assets/条件传送指令.png)

###### 3.4.4：压入和弹出栈数据

指令格式

* `push src`，其行为是

```
%rsp	=	%rsp - 8
M[%rsp]	=	src
```

* `pop dst`，其行为是

```
dst		=	M[%rsp]
%rsp	=	%rsp + 8
```

#### 3.5：算术和逻辑操作

**常见整数算术操作**

![整数算术操作](Tips.assets/整数算术操作.png)

###### 3.5.1：加载有效地址

指令格式

* `leaq src,dst`

操作数格式

* `src`是源地址模式表达式，如`(%rax,%rdi,4)`，`6(%rax)`等

`lea`指令不涉及内存引用，也不会改变标志位，可以用来计算形如`x+k*y`的算术表达式

###### 3.5.3：移位操作

移位操作的移位量可以是一个立即数，或者放在单字节寄存器`%cl`中

###### 3.5.5：特殊的算术操作

利用`%rdx:%rax`组成一个八字（128位）数据

默认的被乘数和被除数分别为`%rax`，`%rdx:%rax`

`S`默认为乘数和除数

![特殊的算术操作](Tips.assets/特殊的算术操作.png)

对于64位全乘法，源操作数与`%rax`相乘，高64位存在`%rdx`，低64位存在`%rax`

对于64位除法，`%rdx`存放余数，`%rax`存放商

#### 3.6：控制

###### 3.6.1：条件码

常用条件码

* **CF**，进位标志。从无符号计算角度判断
* **ZF**，零标志。
* **SF**，符号标志。结果为负数
* **OF**，溢出标志。从有符号计算角度判断

特殊指令的行为

* `leaq`指令不改变任何条件码
* 对于逻辑操作，例如`xor`，进位标志和溢出标志置零
* 对于移位操作，进位标志设置为最后一个移出的位；溢出标志置零
* `inc`和`dec`指令会设置`OF`和`ZF`，但是不会改变`CF`

比较和测试指令

![比较和测试指令](Tips.assets/比较和测试指令.png)

不改变目的寄存器的值，仅设置条件码

###### 3.6.2：访问条件码

`set`指令，根据条件码，将一个字节置零或置一

![set指令](Tips.assets/set指令.png)

`greater/less`为有符号数的比较；`above/below`为无符号数的比较

###### 3.6.3：跳转指令

![跳转指令](Tips.assets/跳转指令.png)

在机器实现上，`j* x`满足`%PC = x+%PC`，在计算之前，`%PC`为跳转指令的下一条指令的地址

![跳转指令实现](Tips.assets/跳转指令实现.png)

###### 3.6.7：循环

**do-while循环**

通常汇编形式

```assembly
loop:
	body-statement
	t = test-expression;
	if(t)
		goto loop;
	...
```

**while循环**

通常汇编形式

* 跳转到中间（*jump to middle*）

```assembly
	goto test;
loop:
	body-statement
test:
	t = test-expression;
	if(t)
		goto loop;
```

* *guarded-do*

```assembly
	t = test-expression;
	if(!t)
		goto done;
loop:
	body-statement
	t = test-expression;
	if(t)
		goto loop;
done:
	...
```

**for循环**

通常汇编形式

* 跳转到中间（*jump to middle*）

```assembly
	init-expression;
	goto test;
loop:
	body-statement
	update-expression;
test:
	t = test-expression;
	if(t)
		goto-loop;
```

* *guarded-do*

```assembly
	init-expression;
	t = test-expression;
	if(!t)
		goto done;
loop:
	body-statement
	update-expression;
	t = test-expression;
	if(t)
		goto loop;
done:
	...
```

###### 3.6.8：switch语句

`switch`语句根据一个整数索引值进行多重分支，通过使用跳转表使得实现更加高效。

![switch跳转表](Tips.assets/switch跳转表.png)

`index`为生成的变量，通过对`n`进行计算得来（缩小原索引值的范围），从上到下递增，初值为0

#### 3.7：过程

假设过程`P`调用过程`Q`，`Q`执行后返回到`P`，动作包括下面一个或多个机制

* **传递控制**，在进入过程`Q`的时候，程序计数器必须被设置为`Q`的代码的起始地址，然后在返回时，要把程序计数器设置为`P`调用`Q`指令的下一条指令的地址
* **传递数据**，`P`必须能够向`Q`提供一个或多个参数，`Q`必须能够向`P`返回一个值
* **分配和释放内存**，在开始时，`Q`可能需要为局部变量分配空间，在返回前又必须释放这些空间

###### 3.7.1：运行时栈

通用的栈帧结构

![通用的栈帧结构](Tips.assets/通用的栈帧结构.png)

###### 3.7.2：转移控制

`call`指令和`ret`指令

![call和ret指令](Tips.assets/call和ret指令.png)

###### 3.7.3：数据传送

默认情况下，通过寄存器，可以传送6个参数，参数依次存放的顺序为`%rdi,%rsi,%rdx,%rcx,%r8,%r9`

如果一个函数有大于6个整型参数，超过6个的部分就要通过栈来传递

###### 3.7.4：栈上的局部存储

运行时栈提供了在需要时分配，函数完成时释放局部存储的机制（分配栈即`%rsp`值减小，释放即`%rsp`增加回原来分配的尺寸）

###### 3.7.5：寄存器中的局部存储空间

根据惯例，`%rbx,%rbp,%r12,%r13,%r14,%r15`被划分为**被调用者保存（callee）**寄存器。当过程`P`调用`Q`时，`Q`必须保护这些寄存器的值（不予更改或者压入栈中）

所有的其他寄存器，除了栈指针`%rsp`之外都划分为**调用者保存（caller）**寄存器，这意味着任何函数都可以修改他们，调用之前的保护是`P`的责任

#### 3.9：异质的数据结构

###### 3.9.3：数据对齐

通常的对齐原则是任何**K**字节的基本对象的地址必须是**K的倍数**

#### 3.10：在机器级程序中将控制与数据结合起来

###### 3.10.3：内存越界引用和缓冲区溢出

在栈中分配某个字符数组来保存一个字符串，但是字符串的长度超出了为数组分配的空间。

###### 3.10.4：对抗缓冲区溢出攻击

* **栈随机化**

使得栈的位置在程序每次运行时都有变化，程序开始时，在栈上分配`0~n`字节的随机大小的空间。程序不使用这段空间，但是它会导致程序每次执行时后续的栈位置发生了变化

* **栈破坏检测**

在栈帧中任何局部缓冲区与栈状态之间存储一个特殊的**金丝雀**值，在每次运行时随机产生。在恢复寄存器状态和从函数返回之前，检查该值是否改变（将栈中的金丝雀与段中的只读值进行比较）

![金丝雀栈](Tips.assets/金丝雀栈.png)

* **限制可执行代码区域**

#### 3.11：浮点代码

* 媒体寄存器

![浮点寄存器](Tips.assets/浮点寄存器.png)

###### 3.11.1：浮点传送和转换操作

**浮点传送指令**

![浮点传送指令](Tips.assets/浮点传送指令.png)

**双操作数浮点转换指令**

![双操作数浮点转换指令](Tips.assets/双操作数浮点转换指令.png)

**三操作数浮点转换指令**

![三操作数浮点转换指令](Tips.assets/三操作数浮点转换指令.png)

###### 3.11.2：过程中的浮点代码

* XMM寄存器`%xmm0~%xmm7`最多可以传递8个浮点参数，按照参数列出的顺序使用这些寄存器，可以通过栈传递额外的浮点参数
* 函数使用寄存器`%xmm0`来返回浮点值
* 所有的XMM寄存器都是**调用者保存**，被调用者可以不保存就覆盖其中任意一个

当函数包含指针、整数和浮点数混合的参数时，指针和整数就通过寄存器传递，而浮点值通过XMM寄存器传递。

###### 3.11.3：浮点运算操作

每条指令有一个或两个源操作数`(S1,S2)`和一个目的操作数`D`，其中，`S2,D`必须是XMM寄存器

![标量浮点算术运算](Tips.assets/标量浮点算术运算.png)

###### 3.11.4：定义和使用浮点常数

AVX浮点操作不能以立即数作为操作数，编译器必须为所有的常量值分配和初始化存储空间，然后代码再把这些值从内存读入

###### 3.11.5：在浮点代码中使用位级操作

![浮点位级操作](Tips.assets/浮点位级操作.png)

###### 3.11.6：浮点比较操作

当任一操作数为`NaN`时，就会出现无序的情况，此时`PF`置1

![浮点比较指令](Tips.assets/浮点比较指令.png)

## 第4章：处理器体系结构

#### 4.1：Y86-64指令集体系结构

###### 4.1.1：程序员可见的状态

在Y86-64体系结构中，有15个64位程序寄存器：`%rax,%rcx,%rdx,%rbx,%rsp,%rbp,%rsi,%rdi,%r8~%r14`；有一个程序计数器`PC`

有3个条件码：`ZF,SF,OF`；有状态码`Stat`

![Y86程序员可见状态](Tips.assets/Y86程序员可见状态.png)

###### 4.1.2：Y86-64指令

* x86-64的`movq`指令被分成4个不同的指令：`irmovq,rrmovq,mrmovq,rmmovq`。

	第一个字符代表源，可以是`i,r,m`分别代表立即数、寄存器、内存；第二个字符代表目的，可以是寄存器、内存。

	内存传送指令中的内存引用方式是简单的基址和偏移量形式`Offset(reg)`。不支持第二变址寄存器和寄存器的伸缩

* 有4个整数操作指令：`addq,subq,andq,xorq`，统称为`OPq`。它们**只对寄存器进行操作**

* 有7个跳转指令：`jmp,jle,jl,je,jne,jge,jg`，统称为`jXX`。

* 有6个条件传送指令：`cmovle,cmovl,cmove,cmovne,cmovge,cmovg`，统称为`cmovXX`。这些指令的格式与`rrmovq`一样，即**寄存器-寄存器**

* `call`指令将返回地址入栈，然后跳转到目的地址；

	`ret`指令从这样的调用中返回

* `pushq,popq`实现了入栈和出栈

* `halt`指令停止指令的执行，会导致处理器的停止，并将状态码设置为`HLT`

![Y86指令集](Tips.assets/Y86指令集.png)

###### 4.1.3：指令编码

**指令编码**

Y86-64指令集每条指令需要1~10个字节不等的编码。第一个字节表明指令的类型，高4位是`code`，低4位是`function`

![Y86指令集功能码](Tips.assets/Y86指令集功能码.png)

**寄存器编码**

![Y86指令集寄存器编码](Tips.assets/Y86指令集寄存器编码.png)

###### 4.1.4：Y86-64异常

![Y86状态码](Tips.assets/Y86状态码.png)

###### 4.1.6：一些Y86-64指令的详情

当执行`pushq %rsp`时，压入`%rsp`的原始值

当执行`popq %rsp`时，弹出内存中读出的值

#### 4.2：逻辑设计和硬件控制语言HCL

###### 4.2.1：逻辑门

在HCL中，位运算AND、OR、NOT分别用`&&,||,!`表示

###### 4.2.2：组合电路和HCL布尔表达式

* 每个逻辑门的输入必须连接到下列选项之一：（1）一个系统输入（称为主输入）（2）某个存储器单元的输出（3）某个逻辑门的输出
* 两个或多个逻辑门的输出不能连接在一起。否则它们可能会使线上信号矛盾，可能会导致一个不合法的电压或电路故障
* 这个网必须是无环的

例如`bool eq = (a && b) || (!a && !b);`

###### 4.2.3：字级的组合电路和HCL整数表达式

情况表达式通用格式

```
[
	select1	:	expr1;
	select2	:	expr2;
	...
	1		:	exprk;
]
```

从逻辑上讲，这些选择表达式是**顺序求值**的，第一个求值为1的情况会选中。即从上往下依次计算`select1,select2,...`。因此几乎所有情况表达式都是以1结尾，表明如果前面没有情况被选中，就选择最后一种情况

###### 4.2.4：集合关系

通用格式`iexpr in {iexpr1,iexpr2,...,iexprk}`，例如`bool s1 = code in {2,3}`

#### 4.3：Y86-64的顺序实现

###### 4.3.1：将处理组织成阶段

分为6个阶段

* **取指（fetch）**，从内存读取指令字节`icode:ifun`，地址为`PC`的值。

	可能取出一个寄存器指示字节`rA:rB`

	可能取出一个8字节常数`valC`

	按顺序方式计算当前指令的下一条地址`valP`

* **译码（decode）**，译码阶段从寄存器文件读入最多两个操作数，得到`valA`和（或）`valB`

* **执行（execute）**，在执行阶段，ALU要么执行`ifun`指明的操作，计算内存引用的有效地址，要么增加或减少栈指针。得到的结果为`valE`

	对一条跳转指令来说，这个阶段决定是否跳转

* **访存（memory）**，访存阶段将数据写入内存，或者从内存读出数据，读出的值为`valM`

* **写回（write back）**，写回阶段最多可以写两个结果到寄存器文件

* **更新PC（PC update）**将`PC`设置为下一条指令的地址

**算术、逻辑运算Ops和rrmovq，irmovq**

![Y86指令集微操作OPs](Tips.assets/Y86指令集微操作OPs.png)

**rmmovq和mrmovq**

![Y86指令集微操作rmmovq](Tips.assets/Y86指令集微操作rmmovq.png)

**进出栈指令**

![Y86指令集微操作进出栈](Tips.assets/Y86指令集微操作进出栈.png)

**跳转、调用和返回指令**

![Y86指令集微操作跳转调用返回](Tips.assets/Y86指令集微操作跳转调用返回.png)

###### 4.3.2：SEQ硬件结构

**总体结构**

![Y86SEQ的硬件实现](Tips.assets/Y86SEQ的硬件实现.png)

###### 4.3.4：SEQ阶段的实现

![Y86实现中HCL使用的常数](Tips.assets/Y86实现中HCL使用的常数.png)

* **取指阶段**

	![Y86SEQ取指阶段](Tips.assets/Y86SEQ取指阶段.png)

	`instr_valid`：是否为合法的Y86-64指令

	`need_regids`：是否包括一个寄存器指示符字节

	`need_valC`：是否包括一个常数

* **译码和写回阶段**

	![Y86SEQ译码和写回阶段](Tips.assets/Y86SEQ译码和写回阶段.png)

* **执行阶段**

	![Y86SEQ执行阶段](Tips.assets/Y86SEQ执行阶段.png)

* **访存阶段**

	![Y86SEQ访存阶段](Tips.assets/Y86SEQ访存阶段.png)

* **更新PC阶段**

	![Y86SEQ更新PC阶段](Tips.assets/Y86SEQ更新PC阶段.png)

#### 4.4：流水线的通用原理

流水线化的重要特性：提高了系统的**吞吐量**，轻微地增加**延迟**

###### 4.5.2：插入流水线寄存器

在`SEQ+`的各个阶段之间插入流水线寄存器，并对信号重新排列，得到`PIPE-`处理器，这里的`-`代表这个处理器和最终的处理器设计相比性能还要略差一些

![PIPE-硬件结构](Tips.assets/PIPE-硬件结构.png)

流水线寄存器按如下方式标号：

* **F**，保存程序计数器的预测值
* **D**，位于取指和译码阶段之间，保存关于最新取出的指令的信息，即将由译码阶段进行处理
* **E**，位于译码和执行阶段之间，保存关于最新译码的指令和从寄存器文件读出的值的信息，即将由执行阶段进行处理
* **M**，位于执行和访存阶段之间，保存关于最新执行的指令结果，即将由访存阶段进行处理。还保存关于用于处理条件转移的分支条件和分支目标的信息
* **W**，位于访存阶段和反馈路径之间，反馈路径将计算出来的值提供给寄存器文件写，而当完成`ret`指令时，它还要向`PC`选择逻辑提供返回地址

###### 4.5.3：对信号进行重新排列和标号

在命名系统中，大写的前缀`D,E,M,W`指的是流水线寄存器，例如`M_stat`指的是流水线寄存器`M`的状态码字段；小写的前缀`f,d,e,m,w`指的是流水线阶段，例如`m_stat`指的是在访存阶段中由控制逻辑块产生出的状态信号

###### 4.5.5：流水线冒险

指令间存在两种形式的相关：**数据相关**，下一条指令会用到这一条指令计算出的结果；**控制相关**，一条指令要确定下一条指令的位置。

存在两种形式的冒险：**数据冒险**和**控制冒险**

每类状态中出现冒险的可能性

* **程序寄存器**，寄存器文件的读写是在不同的阶段进行的，不同指令之间可能出现不希望的相互作用
* **程序计数器**，更新和读取程序计数器之间的冲突导致控制冒险
* **内存**，由于数据的读和写都发生在访存阶段。在访存阶段中写数据的指令和在取指阶段中读指令之间可能会发生冲突（程序修改自身）
* **条件码寄存器**，不会发生冒险
* **状态寄存器**，指令流经流水线的时候会影响程序状态，采用流水线的每条指令都和一个状态码相关联的机制。使得当异常发生时，处理器能够有条理地停止

（1）用**暂停（stall）**来避免数据冒险。让一组指令阻塞在它译码阶段，而允许其他指令继续通过流水线。暂停条件如下

* 源寄存器：当前指令的`srcA,srcB`都处于译码阶段
* 目的寄存器：
	* `dstE,dstM`域
	* 处于执行、访存和写回阶段的指令
* 特例：对于编号为`0xF`的寄存器不需要暂停

（2）用**转发**来避免数据冒险。将结果值直接从一个流水线阶段传到较早阶段的技术成为**数据转发**，也称为旁路技术

* 将指令生成的值直接传送到译码阶段，需要在译码阶段结束时有效
* 转发源可以是`e_valE,m_valM,M_valE,W_valM,W_valE`
* 转发目的可以是`val_A,val_B`

（3）加载、使用数据冒险。如下

```assembly
mrmovq	0(%rbx),%rax
addq	%ebx,%eax
```

可以将暂停和转发结合起来避免该冒险

* 在执行阶段检测到未选择该分支，则在紧接着的指令周期中，将处于执行和译码阶段的指令用气泡替换掉

（4）避免控制冒险

###### 4.5.6：异常处理

在流水线中，可能同时有多条指令会引起异常，基本原则是：由流水线中最深的指令引起的异常，优先级最高

* 异常事件不会对流水线中的指令流有任何影响，除了会禁止流水线中后面的指令更新程序员可见的状态（条件码寄存器和内存），直到异常指令到达最后的流水线阶段
* 此时可以保证第一条遇到异常的指令第一个到达写回阶段，此时程序执行停止，流水线寄存器`W`中的状态码会记录为程序状态
* 如果取出了某条指令，然后又取消了，那么所有关于这条指令的异常状态信息也都会被取消

###### 4.5.8：流水线控制逻辑

流水线的控制逻辑必须处理以下几种情况，是其他机制（如数据转发和分支预测）不能处理的

* **加载、使用冒险**，在一条从内存中读出一个值的指令和一条使用该值的指令之间，流水线必须暂停一个周期
* **处理ret**，流水线必须暂停知道`ret`指令到达写回阶段
* **预测错误的分支**，在分支逻辑发现不应该选择分支之前，分支目标处的几条指令已经进入流水线了。必须取消这些指令，并从跳转指令后面的那条指令开始取指
* **异常**，当一条指令导致异常，要禁止后面的指令更新程序员可见的状态，并在异常指令到达协会阶段时，停止执行

![PIPE流水线控制逻辑的检查条件](Tips.assets/PIPE流水线控制逻辑的检查条件.png)

![PIPE流水线控制逻辑的动作](Tips.assets/PIPE流水线控制逻辑的动作.png)

![PIPE特殊控制条件的流水线状态](Tips.assets/PIPE特殊控制条件的流水线状态.png)

![PIPE流水线组合AB控制条件](Tips.assets/PIPE流水线组合AB控制条件.png)

## 第5章：优化程序性能

#### 5.1：优化编译器的能力和局限性

（一）内存别名使用

```c
void twiddle1(long *xp, long *yp)
{
    *xp += *yp;
    *xp += *yp;
}
void twiddle2(long *xp, long *yp)
{
    *xp += 2* *yp;
}
```

当`*xp == *yp`时，两个函数会产生同样的行为，因此编译器不会做出该优化

（二）改变全局程序状态

```c
long counter = 0;
long f()
{
    return counter++;
}
long func1()
{
    return f() + f() + f() + f();
}
long func2()
{
    return 4 * f();
}
```

此时`func1`四次调用，`func2`仅一次调用，对全局状态`counter`产生了不同的作用，因此编译器不会做出该优化

#### 5.2：表示程序性能

引入度量标准**每元素的周期数（Cycles Per Element，CPE）**

#### 5.3：程序示例

定义如下向量结构和操作

```C
typedef struct
{
    long len;
    data_t *data;
}vec_rec, *vec_ptr;
vec_ptr new_vec(long len)
{
    vec_ptr result = (vec_ptr) malloc(sizeof(vec_rec));
    data_t *data = NULL;
    if(!result)
        return NULL;
    result->len = len;
    if(len > 0)
    {
        data = (data_t *)calloc(len, sizeof(data_t));
        if(!data)
        {
            free((void *) result);
            return NULL;
        }
    }
    result->data = data;
    return result;
}
int get_vec_element(vec_ptr v, long index, data_t *dest)
{
    if(index < 0 || index >= v->len)
    	return 0;
    *dest = v->data[index];
    return 1;
}
long vec_lenth(vec_ptr v)
{
    return v->len;
}
```

定义宏`IDENT`和`OP`，分别为结果初值和执行的操作

合并运算初始实现

```C
void combine1(vec_ptr v, data_t *dest)
{
    long i;
    *dest = IDENT;
    for(i = 0; i < vec_lenth(v); i++)
    {
        data_t val;
        get_vec_element(v, i, &val);
        *dest = *dest OP val;
    }
}
```

#### 5.4：消除循环的低效率

观察`combine1`可以发现，每次循环检查时`vec_lenth(v)`的值总是不变的，因此可以通过**代码移动**来进行优化

```C
void combine2(vec_ptr v, data_t *dest)
{
    long i;
    *dest = IDENT;
    long lenth = vec_lenth(v);
    for(i = 0; i < lenth; i++)
    {
        data_t val;
        get_vec_element(v, i, &val);
        *dest = *dest OP val;
    }
}
```

#### 5.5：减少过程调用

每次进行过程调用都会带来开销（如进栈出栈），而且妨碍大多数形式的程序优化

```C
void combine3(vec_ptr v, data_t *dest)
{
    long i;
    *dest = IDENT;
    long lenth = vec_lenth(v);
    data_t *data = get_vec_start(v);	// return v->data
    for(i = 0; i < lenth; i++)
    {
        *dest = *dest OP data[i];
    }   
}
```

#### 5.6：消除不必要的内存引用

对于`combine3`，可以发现循环中每次都要访问`dest`指向的地址，并将结果写入。可以设置临时变量先存储中间结果，再在循环结束后一次存入。因为内存别名使用的缘故，编译器很难自动优化

```C
void combine4(vec_ptr v, data_t *dest)
{
    long i;
    long lenth = vec_lenth(v);
    data_t *data = get_vec_start(v);	// return v->data
    data_t acc = IDENT;
    for(i = 0; i < lenth; i++)
    {
        acc = acc OP data[i];
    }   
    *dest = acc;
}
```

#### 5.7：理解现代处理器

两种下界描述了程序的最大性能。

当一系列操作必须按照严格顺序执行时，就会遇到**延迟界限**，因为在下一条指令开始之前，这条指令必须结束。当代码中的数据相关限制了处理器利用指令集并行的能力时，延迟界限能限制程序性能

**吞吐量界限**刻画了处理器功能单元的原始计算能力，这个界限是程序性能的终极限制

###### 5.7.3：处理器操作的抽象模型

对于`combine4`，有如下数据流动

![combine4数据流动](Tips.assets/combine4数据流动.png)

对于形成循环的代码片段，可以将访问到的寄存器分为4类

* **只读**，这些寄存器只用作源值，可以作为数据，也可用来计算地址，在循环中不会被修改。例如`combine4`中的`%rax`
* **只写**，作为数据传送操作的目的寄存器
* **局部**，在循环内部被修改和使用，迭代与迭代之间不相关。例如`combine4`中的条件码寄存器
* **循环**，对于循环来说，这些寄存器既作为源值，又作为目的，一次迭代中的值会在另一次迭代中用到。例如`combine4`中的`%rdx,%xmm0`

#### 5.8：循环展开

对`combine4`进行`2*1`循环展开（展开2次，并行累积1个值）

```C
void combine5(vec_ptr v, data_t *dest)
{
    long i;
    long lenth = vec_lenth(v);
    long limit = lenth - 1;
    data_t *data = get_vec_start(v);	// return v->data
    data_t acc = IDENT;
    for(i = 0; i < limit; i += 2)
    {
        acc = (acc OP data[i]) OP data[i+1];
    }
    for(; i < lenth; i++)				// finish the last data
    {
        acc = acc OP data[i];
	}
    *dest = acc;
}
```

#### 5.9：提高并行性

###### 5.9.1：多个累积变量

对于可结合和可交换的合并运算而言，可以通过将一组合并运算分割成两个或更多的部分，并在最后合并结果。例如计算
$$
P_n = \Pi{a_i}
$$
可以变成
$$
\begin{align}
PE_n &= \Pi{a_{2i}}	\\
PO_n &= \Pi{a_{2i+1}}	\\
P_n	&= PE_n + PO_n
\end{align}
$$
由此可以得到`combine6`

```C
void combine6(vec_ptr v, data_t *dest)
{
    long i;
    long lenth = vec_lenth(v);
    long limit = lenth - 1;
    data_t *data = get_vec_start(v);	// return v->data
    data_t acc0 = IDENT;
    data_t acc1 = IDENT;
    for(i = 0; i < limit; i += 2)
    {
        acc0 = acc0 OP data[i];
        acc1 = acc1 OP data[i+1];
    }
    for(; i < lenth; i++)				// finish the last data
    {
        acc0 = acc0 OP data[i];
	}
    *dest = acc0 OP acc1;
}
```

###### 5.9.2：重新结合变换

```C
void combine7(vec_ptr v, data_t *dest)
{
    long i;
    long lenth = vec_lenth(v);
    long limit = lenth - 1;
    data_t *data = get_vec_start(v);	// return v->data
    data_t acc = IDENT;
    for(i = 0; i < limit; i += 2)
    {
        acc = acc OP (data[i] OP data[i+1]);
    }
    for(; i < lenth; i++)				// finish the last data
    {
        acc = acc OP data[i];
	}
    *dest = acc;
}
```

## 第6章：存储器层次结构

#### 6.1：存储技术

###### 6.1.1：随机访问存储器

如果断电，DRAM和SRAM都会丢失他们的信息

![DRAM和SRAM特性](Tips.assets/DRAM和SRAM特性.png)

###### 6.1.2：磁盘存储

磁盘容量 = 每扇区字节数 × 平均每磁道扇区数 × 每表面磁道数 × 每盘片表面数 × 每磁盘盘片数

（其中，每个盘片一般有上下两个表面）

* 对于DRAM和SRAM相关的计量单位，`K,M,G`为二进制量词；

	对于磁盘和网络这样的IO设备容量相关的计量单位，通常

$$
K=10^3,M=10^6,G=10^9,T=10^{12}
$$

对一个扇区的访问时间有三个主要的部分：**寻道时间**，**旋转时间**，**传送时间**

* 寻道时间，移动传送臂所需的时间
* 旋转时间，一旦读写头定位到了期望的磁道，驱动器等待目标扇区的第一个位旋转到读写头下。最坏情况下需要旋转一圈，平均情况下为旋转半圈
* 传送时间，当目标扇区的第一个位位于读写头下时，驱动器就可以开始读或者写该扇区的内容。该时间依赖于旋转速度和每条磁道的扇区数目。粗略计算时相当于旋转一个扇区的用时

#### 6.3：存储器层次结构

###### 6.3.1：存储器层次结构中的缓存

缓存不命中的种类

* **强制性不命中**，访问到空的缓存
* **冲突不命中**，多个对象映射到同一缓存块
* **容量不命中**，缓存大小无法整个装下工作集

#### 6.4：高速缓存存储器

###### 6.4.5：有关写的问题

假设要写一个已经缓存了的字`w`

* **直写**，立即将`w`的高速缓存块写回到下级存储中。缺点是每次写都会引起总线流量
* **写回**，尽可能地推迟更新，只有当替换算法要驱逐这个更新过的块时，才写到下级存储。缺点是增加了复杂性，需要添加并维护修改位

处理写不命中

* **写分配**，加载相应的下级存储的块到高速缓存中
* **非写分配**，避开高速缓存，直接把这个字写到下级存储中

直写通常是非写分配的，写回通常是写分配的

###### 6.4.7：高速缓存参数的性能影响

衡量高速缓存性能的指标：**不命中率，命中率，命中时间，不命中处罚**

* **高速缓存大小的影响**

	一方面，较大的缓存可能会提高命中率；另一方面，较大的缓存通常会增加命中时间

* **块大小的影响**

	一方面，较大的块能利用程序中可能存在的空间局部性，帮助提高命中率

	另一方面，对于给定大小的高速缓存，更大的块意味着更少的行数，会损害时间局部性大于空间局部性的程序的命中率；且较大的块在不命中处罚时传送时间也会变长

	现代系统的块大小通常为64字节

* **相联度的影响**

	一方面，高相联度可以降低由于冲突不命中的抖动的可能性

	另一方面，较高的相联度会提高成本，不命中处罚也增加

* **写策略的影响**

	直写比较容易实现，能使用独立于高速缓存的写缓冲区用来更新内存，此外，因为不会触发内存写，所以读不命中开销没那么大

	写回高速缓存引起的传送较少，允许更多的到内存的带宽用于执行`DMA`。一般而言，越是低级存储，越可能使用写回

## 第9章：虚拟内存

#### 9.3：虚拟内存作为缓存的工具

在任意时刻，虚拟页面的集合分为三个不相交的子集：**未分配的，缓存的，未缓存的**

#### 9.6：地址翻译

###### 9.6.4：综合：端到端的地址翻译

虚拟地址和物理地址格式举例

![虚拟地址格式](Tips.assets/虚拟地址格式.png)

![物理地址格式](Tips.assets/物理地址格式.png)

#### 9.7：案例研究：Intel Core i7/Linux 内存系统

###### 9.7.2：Linux虚拟内存系统

Linux为每个进程维护了一个单独的虚拟地址空间。

![Linux进程的虚拟内存](Tips.assets/Linux进程的虚拟内存.png)

内核虚拟内存包括内核中的代码和数据结构。内核虚拟内存的某些区域被映射到所有进程共享的物理页面。
