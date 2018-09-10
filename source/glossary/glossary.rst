.. _glossary:

名词术语
========

.. glossary::
   :sorted:

   Markup Language
      标记语言（也称置标语言、标记语言、标志语言、标识语言）是一种将文本（Text）以及文本相关的其他信息结合起来, 展现出关于文档结构和数据处理细节的计算机文字编码. 与文本相关的其他信息（包括例如文本的结构和表示信息等）与原来的文本结合在一起, 但是使用标记（markup）进行标识. 当今广泛使用的标记语言是超文本标记语言（HyperText Markup Language, HTML）和可扩展标记语言（eXtensible Markup Language, XML）. 标记语言广泛应用于网页和网络应用程序. 标记最早用于出版业, 是作者、编辑以及出版商之间用于描述出版作品的排版格式所使用的.

   Board Support Package
      板级支持包 (Board Support Package, BSP) 是介于主板硬件和操作系统中驱动层程序之间的一层, 一般认为它属于操作系统一部分, 主要是实现对操作系统的支持, 为上层的驱动程序提供访问硬件设备寄存器的函数包, 使之能够更好的运行于硬件主板. 在嵌入式系统软件的组成中, 就有BSP. BSP是相对于操作系统而言的, 不同的操作系统对应于不同定义形式的BSP,例如VxWorks的BSP和Linux的BSP相对于某一CPU来说尽管实现的功能一样, 可是写法和接口定义是完全不同的, 所以写BSP一定要按照该系统BSP的定义形式来写（BSP的编程过程大多数是在某一个成型的BSP模板上进行修改）. 这样才能与上层OS保持正确的接口, 良好的支持上层OS.

   Cross Compiling
      简单地说, 就是在一个平台上生成另一个平台上的可执行代码. 包含两个概念: 体系结构 (Architecture) 和 操作系统 (Operating System). 同一体系结构可以运行不同的操作系统；同样, 同一操作系统也可以在不同的体系结构上运行. 举例来说, 我们常说的x86 Linux平台实际上是Intel x86体系结构和Linux for x86操作系统的统称；而x86 WinNT平台实际上是Intel x86体系结构和Windows NT for x86操作系统的简称. 对于嵌入式Linux开发中的交叉编译, 一般是指, 在Linux PC机上, 利用交叉编译器 `arm-linux-gcc` , 编译生成Linux ARM上的可执行程序.

   Architecture
      体系结构

   MIPS
      每秒百万条指令（Million Instructions executed Per Second，MIPS），用来计算同一秒内系统的处理能力，即每秒执行了多少百万条指令.

   DMIPS
      即 Dhrystone Million Instructions executed Per Second, Dhrystone是一种整数运算测试程序, DMIPS表示了在Dhrystone这样一种测试方法下的MIPS. 举例来说, 如果某处理器性能为: 2DMIPS/MHZ, 那么对于主频为1000MHz即1GHz的处理器, 其计算能力为2000DMIPS.

      CPU性能评估采用综合测试程序, 较流行的有Whetstone 和 Dhrystone 两种. Dhrystone主要用于测整数计算能力, 计算单位就是DMIPS. 采用Whetstone 主要用于测浮点计算能力, 计算单位就是MFLOPS. DMIPS只适宜于评估标量机, 不能用于评估向量机. 而MFLOPS则比较适用于衡量向量机的性能.


   GUI
      图形用户界面（Graphical User Interface, 简称 GUI, 又称图形用户接口）是指采用图形方式显示的计算机操作用户界面.

   OpenCL
      开放计算语言(Open Computing Language, OpenCL), 是一个为异构平台编写程序的框架, 此异构平台可由CPU、GPU、DSP、FPGA或其他类型的处理器与硬件加速器所组成. OpenCL由一门用于编写kernels（在OpenCL设备上运行的函数）的语言（基于C99）和一组用于定义并控制平台的API组成. OpenCL提供了基于任务分区和数据分区的并行计算机制.

      OpenCL类似于另外两个开放的工业标准OpenGL和OpenAL, 这两个标准分别用于三维图形和计算机音频方面. OpenCL扩充了GPU图形生成之外的能力. OpenCL由非盈利性技术组织Khronos Group掌管.

   GPU
      图形处理单元(Graphic Processing Unit, GPU)

   Thread Processor Cluster
      线程处理器簇 (Thread Processor Cluster, TPC)

   Stream Multiprocessor
      流处理器 (Stream Multiprocessor, SM)

   Stream Processor
      流处理器 (Stream Processor, SP)


   Xilinx Software Development Kit
      赛灵思软件开发套件 (Xilinx Software Development Kit, SDK)

   XDC
      赛灵思设计约束 (Xilinx Design Constraints, XDC)

   XADC
      赛灵思模拟到数字转换器 (Xilinx Analogue to Digital Converter, XADC)

   Real Time multi-tasking Operation System
      实时多任务操作系统 (Real Time multi-tasking Operation System, RTOS) . 在嵌入式应用中通常注重其实时性.

   Embedded Operating System
      嵌入式操作系统（Embedded Operating System, 简称：EOS）是指用于嵌入式硬件系统的操作系统. 嵌入式操作系统是一种用途广泛的系统软件, 通常包括与硬件相关的底层驱动软件、系统内核、设备驱动接口、通信协议、图形界面、标准化浏览器等. 嵌入式操作系统负责嵌入式系统的全部软、硬件资源的分配、任务调度, 控制、协调并发活动. 它必须体现其所在系统的特征, 能够通过装卸某些模块来达到系统所要求的功能. 目前在嵌入式领域广泛使用的操作系统有：嵌入式实时操作系统µC/OS-II、嵌入式Linux、Windows Embedded、VxWorks等, 以及应用在智能手机和平板电脑的Android、iOS等.

   Embedded Real-time Operation System
      嵌入式实时操作系统 (Embedded Real-time Operation System, EROS) , 具备实时性的嵌入式操作系统.

   Processing System
      处理系统 (Processing System, PS), 在 Xilinx Zynq 系列设备中,  SOC被分成 PS (ARM部分) 与 PL (FPGA部分).

   Programmable Logic
      可编程逻辑 (Programmable Logic, PL), 在 Xilinx Zynq 系列设备中, SOC被分成 PS (ARM部分) 与 PL (FPGA部分).