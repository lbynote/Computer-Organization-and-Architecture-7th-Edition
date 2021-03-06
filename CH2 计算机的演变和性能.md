# 2.1 计算机简史
## 2.1.1 第一代：真空管
1. ENIAC  
ENIAC是世界上第一台通用电子数字计算机，是一台十进制机器。
2. 冯·诺依曼机  
    又被称为IAS机。  
    IAS的普通结构：
    1. 主存储器：用于存储数据和指令。
    2. 能够操作二进制数的算数逻辑单元（ALU）。
    3. 控制器：负责翻译内存中的指令并执行。
    4. 用控制器控制的输入输出设备(I/O)。

    IAS机相关论述：
    1. 由于这台设备主要是一台计算机，因此它必须能够执行最繁琐的基本算数运算。它们是加、减、乘、除，应该为这些运算配备专门的器件。（CA）
    2. 设备中控制操作时序的逻辑控制部分，能够由中央控制器最有效地实现。（CC）
    3. 任何执行长而复杂的操作（特别是计算）序列的机器都必须有大量的存储器。（M）  
    △：设备必须具有与相同类型的特定媒体持续输入和输出接触的能力。这种媒体被称为设备的外部记录媒体。（R）
    4. 设备必须有从R到特定的C和M传送信息的器件。（I）
    5. 设备必须有从它的特定部分C和M传送信息到R的器件。（O）

    无论控制器还是ALU都包含存储区域，它们被称为寄存器(register)。  
    定义如下:
    1. 存储缓冲寄存器(MBR)：含有将要写到存储器中或从存储器中接收到的一个字。
    2. 存储地址寄存器(MAR)：指定将要读到MBR或从MBR写到存储器的字的地址。
    3. 指令寄存器(IR)：含有将要执行的8位操作码指令。
    4. 指令缓冲寄存器(IBR)：用来暂存来自内存某个字的右边的一条指令。
    5. 程序计数器(PC)：存放将要从内存中获取的下一对指令的地址。
    6. 累加器(AC)和乘商寄存器(MQ)：用来暂存ALU运算的操作数和结果。例如。两个40位的数相乘，结果是一个80位的数--高40位放在AC中，低40位放在MQ中。 

    △：区别：
    1. PC：存储下一条要被执行或解码的指令地址。
    2. IR：存储正在被执行或解码的指令地址。
    3. MAR：存储正在执行的指令所需数据的地址。 

    IAS通过反复执行指令周期(instruction cycle)来运行。每个指令周期由取值周期(fetch cycle)和执行周期(execute cycle)组成。

    IAS计算机共有21条指令，可以分为以下几类：
    1. 数据传送：在存储器和ALU的寄存器之间，或在两个ALU寄存器之间传送数据。
    2. 无条件转移：通常，控制器顺序执行存储器中的指令。这一顺序能通过跳转指令加以改变。它便于执行重复的操作。
    3. 条件转移：可以依据条件来决定是否跳转，这样就允许选择从何处跳转。
    4. 算数运算：有ALU完成的操作。
    5. 地址修改：允许在ALU中计算地址，并将它插入存储器的指令中，为程序寻址带来很大的灵活性。
3. 商用计算机
略

## 2.1.2 第二代：晶体管
IBM 7094和IAS计算机的区别中最重要的是它使用了数据通道(data channel)：数据通道是独立的I/O模块，具有自己的处理器和指令集。这些指令存在于主存储器中，由数据通道中的一个专用处理器执行。CPU通过给数据通道发送一个控制信号来初始化I/O操作，只是它执行内存中的一串指令。数据通道独立地执行它的任务，并在操作完成时通知CPU。  
另一个特点是多路器(multiplexer)：它是数据通道、CPU、内存的中心连接点。多路器调度CPU和数据通道对内存的访问，允许这些设备独立运行。

## 2.1.3 第三代：集成电路
### 1. 微电子技术
### 2. IBM System、360
IBM系列机具有下列特征：
1. 相同或相似的指令集。
2. 相似或相同的操作系统。
3. 更高的速度。
4. 更多的I/O端口数。
5. 更大的内存容量。
6. 成本增加。
### 3. DEC公司的PDP-8

## 2.1.4 后续的几代
### 1. 半导体存储器
### 2.微处理器

# 2.2 性能设计
## 2.2.1 微处理器的速度
当代处理器所包含的提高速度的技术：
1. 转移预测(branch prediction)：处理器提前考察取自内存的指令代码并预测哪条分支指令或哪组指令将会被执行。
2. 数据流分析(data flow analysis)：处理器通过分析哪一条指令依赖其他的结果或者数据，来优化指令调度。事实上，准备好的指令就可以执行，不必按照原来程序的顺序，这减少了不必要的延时。
3. 推测执行(speculative execution)：使用转移预测和数据流分析，一些处理器让指令在程序实际执行之前就“推测执行”，并把结果暂时存储起来。

## 2.2.2 性能平衡
当处理器的性能飞速发展时，计算机的其他关键部件并没有跟上。  
**处理器和主存储器的接口问题**是这些不匹配问题中最重要的。  
另一个设计焦点是I/O设备的处理。（处理器和外设之间传送数据）

## 2.2.3 芯片组织和体系结构的改进
有三种方法可实现处理器的提速：
1. 提高处理器硬件速度：这个提速基本上要归功于处理器芯片上逻辑门的尺寸减小，这样更多的门能更紧密地组装在一起；也要归功于时钟速率的提升。
2. 提高插入在处理器和主存之间Cache的容量和速度。尤其是，将处理器芯片自身的一部分用作Cache，Cache存取时间会显著降低。
3. 改变处理器的组织和体系结构以提高指令执行的有效速度。

然而，随着时钟速率和逻辑密度的提高，几个障碍变得更加显著：
1. 功率。
2. RC延迟：电子在芯片上各晶体管间的流速受限于连接它们金属线的电阻和电容；特别是，延迟是随着RC之积增长而增长的。
3. 存储器滞后：存储器速度落后于处理器速度。

进一步提升性能还有两种主要策略：
1. 增加Cache容量。
2. 处理器指令执行逻辑变得越来越复杂，以允许处理器内指令并行执行。两个值得重视的办法是流水化和超标量化。指令流水允许不同指令的不同执行步骤同时在流水各段上进行。本质上讲，超标量办法是允许单一处理器内有多条指令流水；这样，彼此无关的指令能够并行执行。

考虑到所有这些困难，设计者已转向一种根本性的新办法来改善性能：在同一芯片上安排多个处理器并带有大的共享Cache。（multiple cores）

# 2.3 Pentium和PowerPC的发展
略

# 2.4 推荐的参考文献和Web站点
略