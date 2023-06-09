# Ⅰ、接口综述

存储器可以直接挂在到系统总线上，外设不能直接挂在系统总线上

## 接口的基本功能
``` markdown
数据的缓冲与暂存
信号电平与类型的转换
增加信号的驱动能力
对外设进行监测、控制与管理、中断
```

## CPU与IO设备之间的信号

### ①数据信息
``` markdown
数字量
模拟量
开关量
```
### ②状态信息
``` markdown
外设->CPU
    - BUSY
    - READY
```
### ③控制信息
``` markdown
CPU->外设：控制外设的工作
```
## 接口的功能
CPU和外设之间的数据传送方式—>解决CPU与外设之间数据传输时速度不匹配问题

### ①**程序方式**
#### 无条件传送方式
``` markdown
如果CPU能够确信一个外设已经准备就绪，那就不必查询外设的状态而直接进行数据传输，这就是无条件传送方式
只适用于简单的外设的操作：开关，数码管
输入需要缓冲，输出需要锁存
```



#### 条件传送方式
``` markdown
又名“查询方式”
用条件传送方式时，CPU通过执行程序不断读取并测试外设的状态，当外设处于READY或空闲状态时，CPU输入输出指令与外设进行数据交换
在查询方式下，CPU不断读取状态字和检测状态字，如状态字表明外设并未准备好，则CPU等待，占用CPU的时间
```

### ②中断方式
``` markdown
由外设中断CPU的工作，CPU暂停执行当前程序，而去执行一个数据输入输出的程序，此程序称为中断处理子程序或中断服务子程序，中断子程序执行完后，CPU又转回来执行原来的程序
外设主动发起中断请求
CPU本身的功能：
    每条指令执行完后，如有中断请求，那么在中断允许标志位为1的情况下，CPU保留下一条指令的地址和当前的标志，转去执行中断服务子程序
多个中断源产生中断，中断优先级问题？
```

### ③DMA（直接存储器存取方式）

# Ⅱ、串行接口和串行通信

数据是一位一位进行传输的

每一位数据占用一个固定的时间长度

## 空间

``` markdown
全双工
半双工
单工
```

## 时间

``` 
异步方式：收发双方不用统一时钟进行定时
两个字符之间的传输间隔是任意的，每一个字符的前后都要用一些数位来作为分隔位
起始位：每个字符开始传送的标志，起始位采用逻辑0电平
数据位：数据位紧跟着起始位传送；由5-8个二进制位阻成，低位先传；
校验位：奇校验，偶校验，不传送校验位
停止位：表示该字符传送结束。停止位采用逻辑电平1，可选择1，1.5或2位
---------------------------------------------------------------------------------------------------------------
同步方式：收发双方采用同一个时钟信号定时
以一个固定长度的字符阻成的数据块为传输单位，每个数据块附加一个或两个同步字符，最后以校验字符结束
```

## 串行通信的传输率

``` markdown
波特率：指的单位时间内传送二进制数据的位数，单位为位/秒（bps）

发送时钟：决定数据位宽度的时钟

接收时钟：用与测定每一位输入数据位宽度的时钟

发送/接收时钟=n*波特率

- n为波特率因子，表征多少个时钟周期传输一个bit
- n=1或16或32或64
- 接收端一般n远大于1
```



# Ⅲ、8251A

## 1.基本性能

可以工作在同步或异步方式
![1](IO.assets/1.png)

## 2.基本工作原理

<img src="IO.assets/2.png" alt="2" style="zoom:80%;" />

### 七个模块

``` markdown
接收缓冲器
	从RXD引脚上接收串行数据，并按照相应的格式将串行数据转换成并行数据

接收控制电路
	对接收的数据进行检测，检测起始位，校验位，停止位等

发送缓冲器
	把来自CPU的并行数据加上相应的控制信息，然后转换成串行数据从TXD引脚发送出去

发送控制电路
	控制插入起始位，校验位，停止位，同步字符等

数据总线缓冲器
	把8251和系统总线相连，在CPU执行输入/输出指令时，游数据总线缓冲器发送和接收数据
	控制字，命令字和状态信息也通过数据总线缓冲区传输

读/写控制逻辑电路

    接收写信号 /WR，并将来自数据总线的数据和控制字写入8251A
    接收读信号 /RD，并将数据或状态字从8251A送往数据总线
    - C//D：控制/数据信号；C//D   /WR   /RD三个信号组合起来通知8251A当前读写的是数据，控制字，还是状态字
    - CLK：时钟信号
    - RESET：复位信号

调制/解调控制电路
	实现 8251A与调制/解调器的连接
```

### 8251A的发送和接收

#### 异步方式
``` markdown
接收

    在异步方式准备接收一个字符的时候，RxD就在线上检测低电平（没有检测的时候就是高电平），假如这个时候检测到了低电平，8251A就会以这个低电平作为起始位，并且启动内部定时计数器，当计数器到一半数位传输时间（比如初始设置时间脉冲为波特率的16倍），则定时器到第八个脉冲的时候，又重新对RxD进行取样，如果仍为低电平就确定是一个有效的起始位，（如果这个时候为高电平了，8251A会认为刚刚低电平是一个干扰信号，这个过程就重头开始了），8251就开始进行常规取样并进行字符装配（就是每隔一段时间对RxD进行采样）数据进入移位寄存器后（并进行去掉奇偶校验位和停止位），变成并行数据，在通过内部总线送到数据输入寄存器，同时发出RxRDY信号到CPU，表示外设的数据已经收到了，是可用的。对于少于八位的，高位自动填零

发送

    当程序把TxEn（允许发送信号）和CTS#（清除请求发送信号，不懂的朋友再仔细看看上文）后就开始发送。在发送的时候，发送器自动添加1个起始位，再按照初始化的格式添加奇偶校验位，停止位。数据及起始位，校验位，停止位总是在发送时钟的TxC下降沿时发出
```
#### 同步方式

``` markdown
接收

    其实和异步也差不多，就是RxD先进行搜索同步字符，找到第一个数据了，送到移位寄存器移位，然后和同步字符的内容进行比较，相等就是找到了，SYNRET=1；开始接收数据块，不相等就重新来（双同步也差不多，就是第一次找到了再来一次，第二次找不到重头开始找第一个字符）,如果是外同步的话，如果SYNDET=1；的时候，直接开始，RxD就不用找起始位了直接开始采样数据块。
    实现同步之后，就利用时钟信号对RxD进行数据采样，送到移位寄存器移位，然后从RxRDY引脚发出一个信号，表示已经收到了一个字符，一旦CPU读完之后，这个RxRDY=0；

发送

    发送也差不多，程序先对TxEN和CTS#初始化了，这个时候就开始发送，程序会先发1/2个同步字符，然后发送数据块，发送数据块的时候，发送器自动按初始化要求添加奇偶校验位（没有就不加）。如果8251正在发送的时候CPU来不及发送数据了（比如说遇到了中断之类的），那么就会重新发1/2个同步字符，等待CPU。满足了同步字符之间没有空隙。
```


## 3.8251A的对外信号



### 8251A和CPU之间的连接信号

![3](IO.assets/9.png)

``` markdown

片选信号

	/CS：CS#，片选信号，由M/IO#和地址译码器得到

数据信号

    - D0-D7：D0-D7        数据传输信号
    8251A的8根数据线D7-D0与8086的数据总线相连

读/写控制信号

    /RD：RD# 读信号，CPU从8251A中读信息
    /WD：WR# 写信号，CPU写入8251A

    8251只有两个端口地址，数据端口是偶地址（输入输出是一个端口），控制信息是奇地址，在8086中是用A1来区分奇偶地址的，如果A1是0，就是偶地址，A1为1就是奇地址，这刚好和C/D#对应了，所以A1脚通常连接C/D#

    | C//D    | /RD     | /WD     | 操作                   |
    |—————————|—————————|—————————|————————————————————————|
    | 0       | 0       | 1       | CPU从8251A输入数据      |
    | 0       | 1       | 0       | CPU往8251A输出数据      |
    | 1       | 0       | 1       | CPU读取8251A的状态      |
    | 1       | 1       | 0       | CPU往8251A写入控制命令  |

收发联络信号

    - TXRDY：发送准备好信号，用来通知CPU，8251A已经准备好发送一个字符

    - TxRDY：发送器准备好，输出，high，表示发送器已经准备好了，这表示发送数据缓冲器空的（没空怎么发啊），CPU可以向8251A发送数据。如果用中断形式的话，这个TxRDY也可以做中断请求信号，如果是查询方式就不断查询它就完事了

    - TxE 发送空信号，输出，high，表示并串转化器为空（数据要经过并串转化器把并行数据转化成串行数据才能发送）。如果8251获得一个数据，TxE就为低。在同步方式下不允许字符串有间隔，但如果CPU来不及给8251A发送数据，则TxE就为1，插入同步字符

    - RxRDY，表示接受器准备好了，可以接受数据了，如果从外设接收到一个数据，等待CPU处理，当然也可以用中断了，把这个当成中断请求信号，程序查询就查他就完事了

    - SYNDET：同步检测信号（只用于同步方式）
    		同步检测/断电检测信号，高有效，输出/输入 同步方式时表示同步检测，如果为内同步，作为输出，输出为1，表示找到同步字了；在外同步的时候，作为输入，变高后，在RxC#（接收器时钟）的下一个下降沿装配字符，在异步方式下，作为空白检测信号，输出，如果接收到全0的字符，输出高电平
```

### 8251A与外设的连接信号

![3](IO.assets/3.png)

``` markdwon
数据信号
    - TXD
    发送数据信号TXD用来输出数据，CPU送往8251A的并行数据转换为串行数据后，通过TXD送往外设
    - RXD
    接收数据信号RXD用来接收外设送来的串行数据，数据进入8251A后，转换为并行方式

和外设的联络信号
    - DTR#  数据终端准备好了，由8251A发给外设，表示CPU准备就绪
    - DER#  数据设备请求好了，由外设发给8251A，表示外设已经准备就绪
    - RTS#  请求发送信号，由8251A发送给外设，表示CPU已经准备好发送
    - CTS#  清除请求发送信号，由外设发送8251A，表示可以往外设发送数据
    - CLK          8251A的内部时序时钟，同步要求是波特率的30倍，异步的话要求波特率的4.5倍
    - TxC，发送时钟，输入，控制字符的发送速度，同步是等于字符传送的波特率，异步方式是初始化定义的
    - RxC，和TxC差不多，是控制接受端的接受速度

时钟、电源、地
    - CLK：用来产生8251A器间的内部时序
    - TXC:发送器时钟输入，用来控制发送字符的速度
    - RXC:接收器时钟输入，用来控制接收字符的速度
    - VCC
    - GND
```
## 4.编程

![4](IO.assets/4.png)

### 8251A的初始化

8251A有一个奇一个偶两个端口地址；

``` markdown
偶地址端口对应数据输入寄存器和数据输出寄存器；
奇地址端口对应状态寄存器，模式寄存器，控制寄存器，同步字符寄存器
```

#### 用偶地址端口时(A1=0)
``` markdown
写入：数据输入寄存器
读出：数据输出寄存器
```

#### 用奇地址端口时（A1=1)(8251A初始化的约定)
``` markdown
第一种描述方法（来自课本）
    芯片复位以后，第一次用奇地址端口写入的值作为模式字送入模式寄存器
    如果模式字中规定了8251A工作在同步模式，那么，CPU接着往奇地址端口输出的就是同步字符，同步字符被写入同步字符寄存器。如此前规定同步字符为两个，则会按先后次序分别写入第一个同步字符寄存器和第二个同步字符寄存器
    此后，只要不是复位命令，不管是同步模式，还是异步模式，由CPU往奇地址端口写入的值都将作为控制字送到控制寄存器，而往偶地址端口写入的值将作为数据，送到数据发送缓冲器

第二种描述方法（来自网络）
    芯片复位之后，第一次用奇地址写控制字，在控制字中规定是同步还是异步；
    如果是同步方式，CPU会接着发1或者2个字节就是同步字符，写入同步字符寄存器，然后再把控制命令字写入奇端口；
    如果是异步方式，CPU往奇端口输出的一个字就是命令控制字；
    在相关命令设置好了之后，只要不复位，用奇端口写控制字，偶端口写的是数据，送到数据输出缓冲器中
```
####  地址说明
``` markdown
- 关于8位接口芯片和16位数据总线的连接问题
    - 8086CPU有一个必须遵守的约定，即低八位数据线总是与偶地址存储单元或端口关联；
    - 而高八位数据线总是与奇地址存储单元或端口关联；
    - 为了满足这一个要求，连接时在硬件上将总线的A1与8251A的C//D引脚相连接，而在软件设计的时候，用连续的偶地址代替端口的奇偶地址，就解决了8位接口芯片与16位数据总线的连接
```
#### 初始化的概述

``` markdown
- 模式字决定了8251A将工作在同步模式还是异步模式，如果工作在同步模式，还会指出同步字符的个数是一个还是两个；同步字符被写入同步字符寄存器
- 如果是异步模式，则在设置完模式字后，接着便要设置控制字
控制字的主要含义相同，控制字就是各种控制命令，包括复位命令
- CPU向8251A发送控制字之后，8251A首先判断控制字是否为复位命令：如果是复位命令，则返回重新接收模式字；如果不是复位命令，则8251A开始进行数据传输。
```
### 模式寄存器的格式

模式字**8位**

#### 异步模式

需要考虑的量：停止位/校验位/校验允许位/数据位的数目/波特率因子

![5](IO.assets/5.png)
``` markdown
（从高到低）
前两位是停止位的数目，00非法，01是1位，10是1.5位，11是2位停止位
第三位是EP（奇偶校验类型），0为奇校验，1为偶校验
第四位是有无校验，0是无，1是有
第五第六位是数据的大小，00是5位，01是6位，10是7位，11是8位
最后两位是决定波特率因子（不能是00，00就表示同步通信了），01表示波特率因子为1，10表示波特率因子为16，11表示波特率因子为64
举个例子，异步通信，1个停止位，无校验，8个数据位（刚好最近在做单片机的串口通信，这就是8N1格式）波特率因子为16，则应该向奇端口（假设还是FFF2H吧）写入01001110B，HEX格式为4EH、
- MOV DX,       FFFEH（端口地址）
- MOV AL, 4EH（模式字）
- OUT DX, AL


波特率
同步模式下，发送和接收的波特率分别和/TxC引脚，/RxC引脚上的输入时钟的频率相同
异步模式下，要用模式寄存器中的最低2位来确定波特率因子，
此时满足: /TxC引脚，/RxC引脚上的输入时钟的频率=波特率因子*波特率
```
#### 同步模式

需要考虑的量:同步字符的数目/同步方式/奇偶校验/奇偶校验允许位/数据位的数目/同步模式
![6](IO.assets/8.png)
``` markdown
（从高到低）
第一位是同步字符的位数，0是2个同步字符，1是1个同步字符
第二位决定是内同步还是外同步，0是内同步，1是外同步
第三位是奇偶校验位，0是奇校验，1是偶校验
第四位是有没有校验，0是没有校验，1是有校验
第五第六位是决定数据块的位数，00是5位，01是6位，10是7位，11是8位
最后两位必定是00
举个例子，比如说现在要求发送的是同步方式，1个同步字符外同步，偶校验，数据位是8位，那么初始化命令字就应该向奇端口（假如为FFF2H）写01111100B，换成16进制就是79H
汇编初始化就应该是
- MOV DX FFF2H
- MOV AL 79H
- OUT DX AL
````
### 控制寄存器的格式

![6](IO.assets/6.png)
``` markdown
从高到低
第七位：检索同步字符，只用在内同步模式，为1时，8251A会对同步字符进行检索
第六位：使8251A复位，从而重新进入初始化流程
第五位：用来设置发送请求，此位置为1会使得/RTS引脚输出为低电平
第四位：1将清楚状态寄存器中所有的出错指示位
第三位：为1使得引脚TxD变为低电平，于是输出一个空白字符
第二位：接收允许信号，在CPU从8251A接收数据前，先使此位为1
第一位：DTR
第零位：发送允许信号，只有将此位是1时，才能使数据从8251A接口往外设传输
```
### 状态寄存器的格式

![7](IO.assets/7.png)
``` markdown
当需要检测8251A的工作状态时，需要用到状态字。
状态字存放在状态寄存器中。
```

## 应用举例

### 异步模式下的初始化程序举例

设8251A工作在**异步模式**，波特率系数(因子)为16，7个数据位/字符，偶校验，2个停止位，发送、接收允许，设端口地址为0042H。完成初始化程序。
``` assembly
;- 模式字：1111010B->FAH
;- 控制字：00110111B->37H (?)
;- 端口地址:对于CPU来说是偶地址，对于接口是奇地址

;- 初始化：
MOV AL,0FAH;送模式字
OUT 42H,AL ;异步方式，7位字符，偶校验,2个停止位  
MOV AL,37H;设置控制字，使发送、接收允许，清出错标志，使 /RTS和/DTR有效 
OUT 42H,AL ;送控制字
```


### 同步模式下初始化程序举例 

设端口地址为42H，采用内同步方式，2个同步字符（设同步字符为16H），偶校验，7位数据位/字符 

``` assembly
;- 模式字00111000B 即38H
;- 控制字为：10010111B 即97H（？）。它使8251A对同步字符进行检索；同时使状态寄存器中的3个出错标志复位；此外，使8251A的发送器启动，接收器也启动；控制字还通知8251A，CPU当前已经准备好进行数据传输。 

;具体程序段如下：  
MOV AL，38H  ;设置模式字，同步模式，  用2个同步字符，
OUT 42H，AL   ; 7个数据位，偶校验
MOV AL，16H  
OUT 42H，AL   ;送同步字符16H
OUT 42H，AL    ;同步字符有两个一样的，因此送两次
MOV AL， 97H   ;设置控制字，使发送器和接收器启动
OUT 42H，AL
```
### 利用状态字进行编程的举例 

先对8251A进行初始化，然后对状态字进行测试，以便输入字符。本程序段用来输入80个字符。

分析：8251A的控制和状态端口地址为42H，数据输入和输出端口地址为40H。字符输入后，放在BUFFER标号所指的内存缓冲区中。
``` assembly
;具体的程序段如下：
    MOV AL,0FAH 
    OUT 42H,AL
    MOV AL,35H
    OUT 42H,AL
    MOV DI,0
    MOV CX,80
B：
    IN AL,42H
    TEST AL,02H
    JZ B  
    IN AL,40H
    MOV BX,OFFSET BUFFER
    MOV [BX+DI],AL
    INC DI
    IN AL,42H
    TEST AL,38H 
    JNZ E
    LOOP B
    JMP EXIT
E： 
    CALL ERR-OUT      
    EXIT:... ...
```


# Ⅳ、并行接口和并行芯片


- 并行通信就是把一个字符的各位用几条线同时进行传输；

-  ![10](IO.assets/10.png)

``` markdown
- 控制寄存器

	- - 用来接收CPU的控制命令

- 状态寄存器

	- - 提供各种状态位供CPU查询

- 输入缓冲寄存器

- 输出缓冲寄存器

```


# Ⅴ、8255A

可编程并行通信接口8255A

## 1.8255A的内部结构

![11](IO.assets/11.png)

### ①数据端口A,B,C

``` markdown
- Port A
    端口A具有一个8位数据输入锁存器和一个数据输出锁存器/缓冲器；
    用端口A做输入口或输出口时，数据均受到锁存

- Port B
    端口B具有一个8位数据输入缓冲器和一个数据输出锁存器/缓冲器；

- Port C
    端口C具有一个8位数据输入缓冲器和一个数据输出锁存器/缓冲器，一般作为控制或状态信息端口
    当端口C作为输入口时，对数据不锁存
    当端口C作为输出口时，对数据进行锁存

使用中，A，B口为两个独立的数据输入输出端口，C口配合A口和B口的工作
C口常常通过控制命令被分成2个四位的端口，分别用来为端口A和B提供控制信号和状态信号
```

### ②A组控制和B组控制

``` markdown
控制端口A与端口C的高4位（PC7-PC4）
控制端口B与端口C的低4位（PC3-PC0）
```

### ③读/写控制逻辑电路

```markdown
功能：管理数据传输过程。

CS#-片选信号

A0、A1-端口选择信号

RD#-读信号

WR#-写信号

RESET-复位信号

读写控制逻辑：接收/CS信号以及来自地址总线的选择端口信号（A2 A1），还接收控制总线的信号/WR,/RD,REST，并将其组合成A和B组的控制信号
```


### ④数据总线缓冲器

```markdown
双向三态的8位数据缓冲器，8255A正是通过它与系统数据总线相连
```

## 2.芯片引脚信号

### 和外设相连的信号

```markdown
PA0－PA7：A口的8条输入输出信号线。
PB0－PB7：B口的8条输入输出信号线。
PC0－PC7：C口的8条输入输出信号线。
```

### 和CPU相连的信号


```markdown
D0－D7：双向数据信号线。和系统总线相连
/RD：读信号线。
/WR：写信号线。
/CS：片选信号线。当片选信号有效时，读信号和写信号才对8255A有效
A1、A0：口地址选择信号线。8255A有四个端口地址
00--A端口；01--B端口；10--C端口；11--控制口。
RESET：复位输入信号，复位时内部寄存器都被清除，同时，三个数据端口自动置为输入口
```

![12](IO.assets/12.jpg)

### 端口地址举例说明

![13](IO.assets/13.png)

## 3.控制字

控制字分为两类：各端口的方式选择控制字和C端口的按位置1/置0控制字

```markdown
控制字的D7位称为标识位
D7=1--->方式选择控制字的标识符
D7=0--->C端口的按位置1/置0控制字的标识符
```

### 方式选择控制字

方式选择控制字的格式

![](IO.assets/14.jpg)

说明

```markdown
8255A的[三种工作方式]
    方式0：基本的输入/输出方式
    方式1：选通的输入/输出方式
    方式2：双向传输方式

端口A可以工作在三种工作方式的任意一种，端口B只能工作在方式0或方式1，端口C则常配合端口A和B的工作，为这两个端口的输入/输出提供控制信号和状态信号
归为同一组的两个端口可以分别工作在输入或输出方式，不要求其工作同输入或输出
```



### 端口C置1/置0控制字

![15](IO.assets/15.jpg)

```markdown
○ 8255A的端口C的各位均可用置1/置0控制字单独设置，因此C端口很适合做控制位使用
○ 当8255A收到控制字时，就对最高位即标识位进行检测，D7=1，将此字节作为方式选择控制字写入控制寄存器，D7=0，将此字节作为端口C置1/置0控制字
○ C端口的按位置1/置0控制字注意：
    § C端口的按位置1/置0控制字尽管时对C端口进行操作，但必须写入控制端口，而不是写入C端口
    § D0位决定置1或置0 ，D0=0置0; D0=1置1
    § D3、D2、D1位决定了对C端口中的哪一位操作 
    § D4 5 6无影响
    § D7位必须为0 
```



## 4.工作方式

```
方式0：基本输入输出方式	适用于无条件传送和查询方式的接口电路（传输方式转8086页面）
方式1：选通输入输出方式	适用于查询和中断方式的接口电路
方式2：双向选通传送方式	适用于双向传送数据的外设	适用于查询和中断方式的接口电路
```

### ①方式0

基本的输入/输出方式

特点

```
- PA和PB可通过方式选择控制字规定为输入或者输出端口- PC分为两个四位端口，高四位一个端口，第四位一个端口；这两个四位端口，也可以通过方式选择控制字规定为输入或输出端口端口可作为输入口，也可作为输出口，各端口之间没有规定必然的联系。可以有16种不同的组合，适用于多种不同的场合。 


8255A中方式0对输出进行锁存（和总线相连肯定要锁存的），输入不锁存
8255A中没有时钟输入信号，所有的时序都是由引脚控制信号定时的
当CPU执行IN指令的时候，产生RD#信号，控制8255A从端口读取外设的输入数据，然后从D0-D7中输入到CPU
当CPU执行OUT指令的时候，产生WD#信号，完成CPU从端口向外传输数据
```

时序

输入（CPU从8255A读取数据）时序要求

```
发出读信号前，先发出地址信号，从而使得8255A的片选信号和端口选择信号A1         A0有效，于是启动8255A输入数据要领先于读信号（要求在CPU发出读信号之前，外设已经将数据送到8255A的输入缓冲器中） 
```

输出（将数据有效传输到8255A）时序要求

```
略
```

应用

```
用于连接简单外设。适用于：（1）无条件输入输出方式。（2）查询输入输出方式：A、B口作为8位数据的输入或输出口，C口的高/低4位分别定义为A、B口的控制位和状态  位，作为A（B）的应答信号。应答信号不固定，可自由定义应用实例：作为主机和打印机的接口
```



### ②方式1

选通的输入/输出方式

特点

```
- PA和PB用方式1进行输入/输出，端口C自动提供选通信号和应答信号
- PA和PB端口只有一个工作在方式1，那么PC一个端口中有3位被规定为配合方式1工作的信号，PC的另一个端口可以工作在方式0，PC的其他位以可工作在方式0，即作为输入/输出
- PA和PB都工作在方式1，那么PC中就需要6位用来作为配合方式1工作的信号，剩下的两位可以作为输入和输出




方式1是单方向的输入/输出工作模式

将3个端口分成两组，端口A和B可以两个数据口，分别工作在方式1，而端口C用来配合端口A和B在方式1下进行工作，作为选通信号

注：

A口工作于方式1输入，固定用PC5-PC3作联络信号线；

A口工作在方式1输出的时候，PC7，PC6和PC3作为选通信号

B口工作于方式1输入输出的时候，固定用PC2-PC0作联络信号线。

如果AB都用方式1进行传输，C口剩下的两位可以工作在方式0下
```

时序

输入信号和输入时序

 ![16](IO.assets/16.jpg)

```
所用到的控制信号的定义如下：

  ① STB为低电平有效的输入选通信号，由外设提供的输入信号，当它有效时，把输入装置来的数据送入输入锁存器。

  ② IBF为高电平有效的输入缓冲器满信号，通知外设送来的数据已被接收，由STB信号的前沿产生。当CPU用输入指令读走数据后，此信号被清除。 

  ③ INTR为中断请求信号，高电平有效。CPU响应中断请求后在服务程序中读走数据时，由RD信号将其清除。

  ④ INTE为中断允许状态，可事先用位控方式写入。
```

输出信号和输出时序

 ![17](IO.assets/17.jpg)

```
当CPU相应了8255的中断后，发出WD#信号，输出数据到锁存器中。输送完了之后，WD有效的时候，打开OBF#为0，缓冲器满，告诉CPU不要写数据到8255A了，（OBF#也是外设的选通信号）同时INTR为0（已经响应了中断）。当外设读完了数据，WD为1，发送响应信号ACK#，ACK#的上升沿也把OBF置为1，缓冲器空，INTR为1，发送下一个中断，可以读下一个数据了
```



应用

```markdown

```



### ③方式2
双向传输方式

特点

```
方式2将方式1的选通输入输出功能组合成一个双向数据端口，可以发送数据和接收数据；只有端口A可以工作于方式2，需要利用端口C的5个信号线，其作用与方式1相同；方式2的数据输入过程与方式1的输入方式一样；方式2的数据输出过程与方式1的输出方式有一点不同：数据输出时8255A不是在OBF#有效时向外设输出数据，而是在外设提供响应信号ACK#时才送出数据

当A端口工作方式2的时候（需要PC3-PC7），B口还可以工作在方式1（需要PC0-PC2）和方式0（PC0-PC2可以在方式0啦）
```

时序

![18](IO.assets/18.png)

``` 
如果A口外设输入数据到8255中的时候，STB#有效，外设数据输入到A的PA0-PA7，输完数据后，STB为1，同时IBF为1，触发中断，INTR为1，CPU响应中断，发出IN指令，RD为0，当RD有效的时候，INTR为0（表示已经响应了中断），数据传输到数据总线中，读完后，INFA为0，继续开始读取数据

如果8255发送了一个中断，CPU响应了中断，发出WR#信号，数据从总线中到锁存器中，在WR有效的时候清除INTR（响应了中断）。同时让OBFA为0（PC7），告诉外设要读数据了，外设读完后发出响应信号ACK#，ACK上升沿恢复为1的时候，触发OBFA为1，又触发了中断

注意，由于A口的输入锁存器和输出锁存器是互相独立的，故当CPU向A口输出数据时，外部设备也可同时向A口输入数据。反之亦然。
```
应用

```
磁盘驱动器
```



## 5.应用举例


# Ⅵ、8259A

``` 
中断控制器的功能：
    接收外部的中断请求，进行判断，选中优先级最高的中断请求，送到CPU的INTR端；CPU响应中断进入中断子程序时，负责对外部中断请求管理，可实现中断嵌套。

8259A的工作特点： 

    ① 能管理8级中断，可与其它8个8259A芯片组成主从式中断系统，实现64级中断源控制；

    ② 可编程使用，非常灵活；

    ③ 只需一组5V电源。
```

## 1.外部信号和含义

![19](IO.assets/19.png)

```
① D7～D0 数据线：在系统中，他们和数据总线相连

② INT 中断请求信号：和CPU的INTR端相连，向CPU发送中断请求

③ INTA# 中断应答信号：接收来自CPU的中断应答信号，如果CPU接收到中断请求信号，而此时中断允许位标志为1，并且正好一条指令执行完毕，那么在当前总线周期和下一个总线周期中，CPU将在/TNTA引脚上分别分发一个负脉冲作为中断响应信号，在第二个/INTA脉冲结束时，CPU读取8259A送到数据总线上的中断类型号

④ RD# 读出信号：将8259A某个内部寄存器的内容送达数据总线

⑤ WR# 写入信号：使8259A从数据总线上接收数据

⑥ CS# 片选信号

⑦ A0 端口选择信号：8259A有两个端口地址，一个为奇地址，一个为偶地址，奇地址较高，偶地址较低

⑧ IR7～IR0 I/O中断请求信号：与IO设备相连或者说连接从片的INT引脚，接收其中断请求

⑨ CAS2～CAS0 从片选择信号

⑩ SP#/EN# 主片和从片的选择和驱动信号

    /SP//EN：双功能引脚

    （1）输出，低电平有效

        8259A工作在缓冲方式时，该引脚输出低电平控制信号，用来使能系统总线与8259A数据引脚之间的数据缓冲器，使中断向量码能在第二个INTA周期正常从8259A输出。

    （2）输入

        当8259A工作在主从级联方式时，该引脚为输入：

        SP=1，设定8259A为主片；

        SP=0，设定8259A为从片
        
        
```





## 2.编程结构和工作原理

<img src="IO.assets/20.jpg" alt="20" style="zoom:50%;" />

<img src="IO.assets/22.jpg" alt="22" style="zoom:80%;" />

### 组成
```
	控制部分——7个寄存器（八位的寄存器）

    初始化命令字ICW（1-4）
    	功能：决定8259A的工作方式
         通常是在计算机系统启动时在初始程序设置，一旦设定，一般在系统工作过程不再改变。
    操作命令字OCW（1-3）
        功能:在应用程序中设定，动态地控制CPU处理中断的过程
        中断屏蔽寄存器IMR（OCW1）
        保存对中断请求信号IR的屏蔽状态,Di位为1表示IRi中断被屏蔽（禁止）；为0表示允许

	处理部件（8位的寄存器）

    功能：接收和处理从IR0-IR7进入的中断
    - IRR——中断请求寄存器
        保存8个外界中断请求信号IR0～IR7的请求状态
        - Di位为1表示IRi引脚有中断请求；为0表示无请求
        
    - PR——中断优先级裁决器

    - ISR——当前中断服务寄存器
        保存正在被8259A服务着的中断状态
        Di位为1表示IRi中断正在服务中；为0表示没有被服务
```
### 工作原理

<img src="IO.assets/21.jpg" alt="21" style="zoom: 67%;" />

（1）接收、处理外设中断申请，决定是否向CPU发中断申请信号。
（2）若CPU响应中断，则在CPU中断响应周期送出中断类型号。

```
中断请求寄存器IRR接收外部中断请求，IRR有8位，分别和引脚IR7-IR0相对应;
接收来自某一引脚的中断请求后，IRR寄存器的对应位置便置1，即对此中断请求锁存;
此后，逻辑电平根据中断屏蔽寄存器IMR中对应位决定时候让此请求通过;
决定IRR中的中断申请是否进入优先级裁决器PR。
    IMR对应位为0，允许中断申请进入优先级裁决器，
    IMR对应位为1，不允许进入，中断申请被IMR屏蔽。
```

```
中断优先级裁决器PR把新进入的中断请求和当前正在处理的中断比较，从而决定哪一个优先级更高
当前中断服务寄存器 ISR 记录CPU正在响应的中断。
- ISR中的某位为1，表示CPU正在响应此级中断，即正在执行此中断源的中断子程；
- ISR中的某位为 0，表示CPU没有或已响应完此级中断，即不在执行此中断源的中断子程

如果进入的中断申请比ISR中记录的中断优先级高，则通过8259A的INT引脚 CPU发出中断请求信号；
如果进入的中断申请不比 ISR 中记录的中断优先级高，     同级或低级，则不向 CPU 发中断请求信号。
```

```
如果CPU的中断允许标志位IF为1,那么CPU执行完当前指令后，就可响应中断，这时，CPU从/INTA端往8259A送出两个负脉冲:


第一个负脉冲到达时，8259A完成三个动作
    - 使IRR锁存功能失效。对IR7-IR0线上的中断请求信号就不再接收；直到第二个负脉冲到达时，才使IRR锁存功能有效
    - 使当前中断服务服务器ISR中的相应位置1，以便中断优先级裁决寄存器以后的工作提供判断依据
    - 使IRR寄存器中的相应位清零（之前接收中断请求时设置的1，现在需要清零）


第二个负脉冲到达时，8259A完成两个动作
    - 将中断类型寄存器中的内容ICW2送到数据总线的D7-D0，CPU将此作为中断类型号
    - 如ICW4中的中断自动结束位为1，则将当前中断服务寄存器ISR的相应位清零
```
## 3.工作方式

### 设置优先级的方式

#### 全嵌套方式
```
最常用的方式

8259A的中断优先权顺序固定不变，从高到低依次为IR0、IR1、IR2、……IR7。0级优先级最高
中断请求后，8259A对当前请求中断中优先权最高的中断IRi予以响应，将其中断类型码送上数据总线，对应ISR的Di位置位，直到中断结束（ISR的Di位复位）。
在ISR的Di位置位期间，禁止再发生同级和低级优先权的中断，但允许高级优先权中断的嵌套。
```
#### 特殊全嵌套方式
```
与全嵌套方式基本相同，只有一点不同：当处理某一级中断时，如果有同级的中断请求，也会给予响应。

特殊全嵌套方式一般用在8259A级联系统中。

一方面，CPU对于优先级别较高的主片的中断输入是允许的；
另一方面，CPU对于来自同一从片的优先级别较高（但对于主片来讲，优先级别是相同的）的中断也是允许、能够响应的。
```
#### 优先级自动循环方式
```
适用场合：系统中多个中断源优先级相等。
初始优先级队列规定为：IR0~IR7。从IR0～IR7引入的中断轮流具有最高优先权。当任何一级中断被处理完，它的优先级别就被改变为最低，而最高优先级分配给该中断的下一级中断。
例如：现正为IR3引入的中断服务，若服务完毕，IR3为最低优先级，IR4有最高优先级，优先级顺序为 IR4,IR5,IR6,…IR2,IR3。
优先级自动循环方式——由OCW2决定
```
#### 优先级特殊循环方式
```
与优先级自动循环方式相比，只有一点不同：初始优先级是由编程决定的。
例如：编程确定IR5为最低优先级，则IR6为最高优先级，初始优先级顺序为IR6,IR7,IR0…IR4,IR5。
优先级特殊循环方式——由OCW2决定
```
### 屏蔽中断源的方式

#### 普通屏蔽方式
```
8259A的每个中断请求输入端都可通过对应屏蔽位的设置而被屏蔽

将OCW1（IMR）的Di位置1，则对应的中断IRi被屏蔽，该中断请求不能从8259A送到CPU。
如果OCW1（IMR）的Di位置0，则允许IRi中断产生。
撤销屏蔽：可以再程序中根据需要设置OCW1（IMR）寄存器的值。
```
#### 特殊屏蔽方式
```
将OCW1（IMR）的Di位置1，对应的中断IRi被屏蔽的同时，使ISR的Di位置0；
开放了其他级别较低的中断。

特殊屏蔽是在中断处理程序中使用的，用了这种方式之后，尽管系统正在处理高级中断，但对外界来讲，只有同级中断被屏蔽，而允许其它任何级别的中断请求。
应用场合： 一个中断服务程序的运行过程中，需要动态地改变系统中的中断优先级结构，即：在中断处理的一部分，禁止低级中断嵌套；而在中断处理的另一部分，允许低级中断嵌套
```
### 结束中断处理的方式
```
中断结束是什么：

CPU响应某级中断后，8259A自动将ISR的对应位置1，如果CPU已执行完中断子程，而ISR中的对应位仍为1,8259A的优先级裁决器仍会据ISR的内容做裁决，从而会屏蔽同级或低级的中断申请。在中断响应后，对 ISR中相应位的清0很重要，  它是8259A认为中断结束的标志。
```
#### 中断自动结束方式
```
适用于系统中只有一片8259A且多个中断不会嵌套的情况。
系统进入中断过程，8259A就自动将当前中断服务寄存器中对应位ISn清除。
方法：ICW4中AEOI位为1。
```
#### 中断一般结束方式
```
配合全嵌套优先权方式使用。
当CPU用输出指令往8259A发出一般中断结束命令（EOI）时，8259A就会把当前中断服务寄存器优先权最高的IS位复位。
方法:在程序中，往8259A的偶地址端口输出一个操作命令字OCW2,OCW2的EOD=1,SL=0,R=0z
```
#### 特殊的中断结束方式
```
配合非全嵌套方式使用。
- CPU在程序中向8259A发送一条特殊中断结束命令（SEOI），这个命令中指出了要清除哪个IS位。
方法：OCW2中的EOI=1,SL=1,R=0

8259A级联方式下，一般采用非自动结束方式。CPU应发出两个中断结束命令，一个送主8259A，用来将其主8259A的ISR寄存器相应位清“0”；另一个送从8259A，用来将其从8259A中的ISR寄存器相应位清“0”。
```
### 连接系统总线的方式

#### 缓冲方式
```
8259A的数据线需加总线驱动器予以驱动。
8259A把 SP#/EN#       引脚作为输出端，输出允许信号（低电平），作为总线驱动器的启动信号。

由ICW4设置
```
#### 非缓冲方式
```
8259A直接与数据总线相连。
- SP#/EN#引脚为输入端。
若8259A级联，由其确定是主片（SP#/EN#       为高）或从片 （SP#/EN# 为低）。

由ICW4设置
```
### 引入中断请求方式

#### 边沿触发方式
```
8259A将中断请求输入端出现的上升沿作为中断请求信号。

- ICW1设置
```
#### 电平触发方式
```
中断请求端出现的高电平是有效的中断请求信号。

- ICW1设置
```
#### 中断查询方式
```
中断查询方式的特点：
    - 8259A不使用INT向CPU发中断请求信号。
    - CPU内部的中断允许触发器复位，禁止外部对CPU的中断请求。
    - CPU要使用软件查询来确认中断源。

查询软件：关中断、送查询命令、读取查询字。
```
## 4.初始化

```
8259A的命令控制字包括两类

初始化命令字和操作命令字

初始化命令字：一般在系统复位后的初始化编程中设置，用于确定8259A的基本工作方式，设置以后一般保持不变

初始化编程：指系统在上电或复位后对可编程器件进行控制字设定的一段程序

操作命令字：是在初始化以后应用程序随时写入的，它实现对8259A的状态，中断方式和过程的动态控制，在工作中可随时写入操作命令字，以修改某些控制方式
```

### 初始化编程
```
8259A开始工作前，必须进行初始化编程；
给8259A写入初始化命令字ICW。
```
### 中断操作编程
```
在8259A工作期间；
可以写入操作命令字OCW将选定的操作传送给8259A，使之按新的要求工作；
还可以读取8259A的信息，以便了解它的工作状态。
```
## 5.初始化命令字
```
8259A有两个连续的端口地址
偶地址较低，奇地址较高

初始化命令字ICW1～ICW4必须按照顺序填写；
- ICW1写入偶地址端口，ICW2～ICW4写入奇地址端口。
```
### ICW1:（*芯片控制初始化命令字*） 

![23](IO.assets/23.png)

```
- A0=0 偶地址端口
- D7       D6 D5 ：8086系统中不使用，设置1和0都可以
- D4：D4=1，作为OCW1的标识位，用与区分OCW2和OCW3，因为二者也是写到偶地址端口的
- D3：设置中断请求方式。边沿触发/电平触发
- D2：8086系统中不使用，设置1和0都可以
- D1：规定单片或级联方式：SNGL＝1，单片方式；SNGL＝0，级联方式
- D0：8086系统中设置为1，用来指出后面还将要设置ICW4
```
### ICW2（中断类型号初始化命令字）

![23](IO.assets/24.png)

```
中断类型号的高五位也就是ICW2的高五位，低三位的值则却决于引入中断的引脚序号
 ICW2是任选的；一旦ICW2确定下来，IR0-IR7所对应的八个中断类型号也就确定了
 ICW2高5位影响中断类型码，而中断类型码的低3位由IR0～IR7决定。

例：ICW2为20H，8259A的IR0-IR7的中断类型码为20H,21H,22H…,27H
```
### ICW3（主片/从片初始化命令字）



```
系统中包含多片8259A时，才需要ICW3。
由ICW1的D1位（SNGL）指示，SNGL=0时，才需要设置ICW3。
```
如是主片,则ICW3的格式如下： 

![25](IO.assets/25.png)


```
IRi＝1说明对应的IRi引脚上接有从片；

IRi＝0则表示IRi没有连接从片
```
如是从片，则ICW3的格式如下： 

![26](IO.assets/26.png)


```
ID2～ID0编码说明从片INT引脚接到主片哪个IR引脚
```
### ICW4（方式控制初始化命令字）

![27](IO.assets/27.png)

```
- ICW1的第D0位为1时，才写入ICW4；
16位或32位系统必须设置ICW4。
```


```
- D7-D5:全为0，作为ICW4的标识码

- D4:嵌套方式:

    特殊全嵌套方式（SFNM＝1）
    普通全嵌套方式（SFNM＝0）

- D3:数据线的缓冲方式：

    缓冲方式（BUF＝1）
    非缓冲方式（BUF＝0） 

- D2:

    BUF=0时,M/S#不起作用

    BUF=1时主片/从片选择：

    主片（M/S#=1）
    从片（M/S#=0）

- D1:中断结束方式：

    自动中断结束（AEOI＝1）
    非自动中断结束（AEOI＝0）

- D0:微处理器类型：

    16位或32位系统（mPM＝1）
    8位系统8080/8085（mPM＝0）
```
### 初始化流程
```
8259A在进入工作之前，必须先使用初始化命令字将每片8259A进行初始化。8259A的初始化流程应该遵循固定的次序

① ICW1写入偶端口，ICW2～ICW4写入奇端口；

② ICW1～ICW4的设置次序固定；

③ ICW1和ICW2必须设置，ICW3和ICW4非必须 ；16位和32位系统中ICW4必须设置，多8259A级联时，ICW3要设置

④ 在级联时，主片和从片各设置ICW3；注意其ICW3的格式并不相同
```
## 6.操作命令字
```
操作命令字是在应用程序中设置的

设置次序没用要求

- OCW1写入奇地址端口

- OCW2 OCW3写入偶地址端口
```
### OCW1（中断屏蔽操作命令字）

![28](IO.assets/28.png)

```
中断屏蔽操作命令字：内容写入中断屏蔽寄存器IMR
- Di＝Mi对应IRi为1禁止IRi中断；为0允许IRi中断。各位互相独立。
```
### OCW2（优先级循环方式和中断结束方式操作命令字）

![29](IO.assets/29.png)

```
- R、SL和EOI配合使用产生中断结束EOI命令和改变优先权顺序
- D4D3=00  为OCW2的标志位
- L2～L0的3位编码指定IR引脚 
```

![30](IO.assets/30.jpg)

### OCW3（状态操作命令字）

![31](IO.assets/31.png)

```
（1）设置和撤销特殊屏蔽方式

（2）设置中断查询方式

（3）设置对内部寄存器的读出命令
```

```
- ESMM称为SMM的允许位
    - SMM为特殊屏蔽模式位
    - ESMM为特殊屏蔽模式允许位
```
![32](IO.assets/32.jpg)

P：查询方式位

![33](IO.assets/33.jpg)

RR RIS

![34](IO.assets/34.jpg)


## 7.使用举例


# Ⅶ、8253

## 定时信号
```markdown
一般来说，定时信号可用软件和硬件两种方法得到

软件定时:

根据所需要的时间常数来设计一个延时子程序；
当延时时间较长时，可循环该延时子程序

硬件定时

计数器/定时器：计数时不会占用CPU的资源
```

## 工作原理

![](IO.assets/8253_1.png)

```markdown

计数器：在设置好计数初值（即定时常数）后，便开始减1计数，减为0时，输出一个信号

计数器在减到0以后，输出一个信号便结束了，除非重新触发
--------------------------------------------
定时器：在设置好定时常数后，便进行减1计数，并按定时常数不断地输出为时钟周期整数倍的定时间隔

定时器减到0以后，自动恢复初值重新奇数，并不断产生信号


3个独立的16位计数器通道；
共用1个控制寄存器和1个状态寄存器（只有8254有状态寄存器）。
每个计数器有6种工作方式；
按二进制或十进制（BCD码）计数。
```


## 编程结构

8253 内部没有状态寄存器

![](IO.assets/8253_2.png)

### 计数器
```markdown

8253内部有三个计数器：计数器0，计数器1，计数器2，其结构完全相同

每个计数器的输入和输出都决定于设置控制寄存器中的控制字，他们共用一个控制寄存器，但相互之间完全独立

内部结构

    三个引脚：时钟输入CLK,门控信号输入端GATE,输出端OUT
    内部部件：16位计数初值寄存器CR,计数执行部件CE,输出锁存器OL

    执行部件实际上就是一个16位的减法计数器，其起始值就是初值寄存器的值，初值寄存器的值是通过程序设置的

    输出锁存器OL用来锁存计数执行部件CE的内容，从而使得CPU可对此进行读操作

    - CE CR OL 都是十六位的寄存器，但也可用作为8位寄存器来用

    计数器的工作方式决定于控制寄存器中的控制字
```

### 工作过程
```markdown

\1. 设置8253\8254的工作方式；

\2. 设置计数初值到计数初值寄存器CR；

\3. 第一个CLK信号使计数初值寄存器的内容置入

计数执行部件CE；

\4. 以后每来一个CLK信号，CE减1； 

\5. OUT端输出一特殊波形的信号；

注：以上计数过程中还受到GATE信号的控制。
```


## 外部信号
```markdown

- CLK0-CLK2：三个计数器的时钟信号

- GATE0-GATE2：三个计数器的门控信号

- OUT0-OUT2：三个计数器的输出信号

- A1,A0：地址线，对三个计数器和控制寄存器进行寻址

        8253有四个端口地址

        - A1A0=00,计数器0
        - A1A0=01，计数器1
        - A1A0=10，计数器2
        - A1A0=11，控制端口

/RD，/RD有效时，CPU对8253的输出锁存器进行读操作

/WR,/RD有效时，CPU对8253的一个计数器写入计数初值或对控制寄存器写入控制字

- CS：/CS有效时，/WR,/RD才会有效
```

## 控制寄存器与控制字

8253内部的三个寄存器共用一个控制寄存器，通过对控制寄存器写入控制字，就可使得三个计数器处于不同的工作模式，控制端口是只写的；

### 模式设置控制字

模式控制字：用来设置三个计数器的工作模式

![](IO.assets/8253_3.png)


```markdown
- BCD位：计数初值的格式

此位为0，后面设置的计数初值为BCD码格式，0-9999；
此位为1，后面设置的计数初值为二进制格式，为0-FFFFH

- M2 M1 M0：模式选择位

000 模式0
001 模式1
X10 模式2
X11 模式3
100 模式4
101 模式5

- RW1 RW0 读写指示位

00 对计数器进行锁存操作，使当前计数值在输出锁存器中锁定，以便读出
01 只读/只写低八位
10 只读/只写高八位
11 先读/写低八位，再读/写高八位

- SC1 SC0 选择计数器

设置模式控制器字时，指出时对哪一个计数器进行设置

00 计数器0
01 计数器1
10 计数器2
11 读出控制字的标识码
```

### 关于的控制字说明
```markdown
1、8253/8254只有一个工作方式控制字，但是对每个计数器而言，它们的工作方式控制字内容一定各不相同（前两位不同），所用各计数器的控制字需要分别设置，先后不计。

2、在工作方式控制字被设置之后，随后必须紧接着给计数器预设置计数初值，计数器方可开始工作。

8253/8254初始化的工作有两个内容：

（1）首先向控制寄存器写入控制字，以选择计数器（3个计数器之一），确定工作方式（6种方式之一），指定计数器计数初值的长度和装入顺序以及计数值的码制（BCD或二进制码）。

（2）然后向已选定的计数器按控制字要求写入计数初值。
```


### 读出控制字

读出控制字：用来读取计数器当前的计数值
```markdown
每个计数器的当前计数值可以被读取，因为计数值是不断变化的，所以在读取前要先进行锁存。读出控制字就是起锁存作用的，所以也叫做锁存命令
- D6 D7 D0：D7D6=11为读出控制字的标识码；D0=0必须是这样设置
/COUNT：如果为0，则将所选计数器的当前计数值进行锁存，以便后面读取
/STATUS：如果为零，则将所选计数器的状态进行锁存
- D3D2D1：分别对应于计数器2，1，0。在一个时刻只能对一个计数器进行锁存
```


## 编程命令

对8253的编程没有顺序规定，非常灵活

### 三条原则

```
对计数设置初值前必须先写控制字
初值设置时，要符合控制字中的格式规定
要读计数器的当前值和和状态字，必须用控制字先进行锁存
```

### 编程命令

#### 写入命令——针对控制寄存器
```markdown
设置控制字命令，设置初值命令，锁存命令
一个计数器在工作之前，需要先设置控制字对所选择的计数器设定工作模式和计数格式；
设置初值命令用来给出计数的初值
锁存命令是配合读出命令使用的。在读取计数值时，必须先用锁存命令将当前计数值在输出锁存器中锁住，否则，在读数时，计数器的值在变化，就得到一个不确定的结果
当锁存命令到来时，计数执行部件到某一个值，因为锁存器是跟随计数执行部件工作的，所以锁存器中为同一值，此时这一计数被锁住
- CPU将此锁定值读走之后，锁存器自动失效，于是又跟随计数执行部件变化。
在锁存和读出计数值的过程中，计数执行部件仍在不停地作减一计数
```
#### 读出命令——针对计数器
```markdown
读出命令用来读取8253的某个计数器的当前计数值
读取计数器的值之前必须先锁存，再读取
```
## 工作模式

### 基本原则
```markdown
写入控制字时，所有的控制逻辑电路立即复位，输出端OUT进入初始状态（高或低电平）
初始值写入之后，要经过一个时钟上升沿和一个下降沿，计数执行部件才开始计数
通常，在时钟脉冲CLK上升沿时，门控信号GATE被采样
在时钟脉冲的下降沿，计数器作减一操作。

其中0是最大初值，1是最小初值；
```
### 模式0——计数结束产生中断

不是连续波形，产生中断；计数期间为低电平，结束为高电平。

![](IO.assets/8253_00.png)

```markdown
①控制字写入之后，OUT变低；初值装入后，要经过1个CLK的周期（1个上升沿和1个下降沿）后，计数器才开始计数，所以，输出OUT要经过N+1个时钟周期后才有输出；

②输出OUT的有效电平为高电平，并可同时触发中断请求；

③门控GATE的作用：高电平时计数，低电平或下降沿时停止计数；

④CW为写入控制字，N=4表示写入初值，计数值一次有效。
```



### 模式1：可编程单稳态触发器

周期性波形，计数期间为低电平，其余为高电平。

![](IO.assets/8253_11.png)

```markdown
①控制字和初值装入后，OUT变高，在门控GATE的上升沿触发下，经过1个CLK的上升沿和1个下降沿后，计数器开始从初值减1计数，同时使OUT=0；当计数结束（归0）时，OUT=1，使输出产生1个宽度为TW=N×TCLK的负脉冲——单稳态触发器。

②在GATE的上升沿触发下，输出可再次产生1个宽度为TW负脉冲——可重复触发。
```
### 模式2：分频器

连续波形产生负脉冲，在最后一个计数期间为低电平，其余为高电平。

![](IO.assets/8253_22.png)

```markdown
①控制字装入后，OUT=1为初始状态。

②初值装入后，经过1个CLK的周期，计数器开始从初值减1计数，计到1（不是0）时，使输出OUT=0并保持1个CLK周期，然后OUT=1，开始下一个新的计数周期，使输出为CLK的时钟1/N分频信号，占空比q=（N-1）/N。

③门控GATE的作用：高电平时计数，低电平停止计数；GATE再次变高后从初始值重新计数；而在GATE=1时，计数完成之后自动重新装入初值，循环计数。

④如果计数过程中写入新值.不影响当前计数.完成后重新装入新值
```
### 模式3：方波发生器

周期性方波（占空比1:1）。

![](IO.assets/8253_33.png)

```markdown
特点与方式2类似，主要区别：输出方波，其占空比q为

①当N为偶数时，q=0.5；

②当N为奇数时，q=(N+1)/2N。
```





### 模式4：软件触发的选通信号发生器

单次波形输出，计数结束后输出一个CLK周期的低电平，其余为高电平，不能自动循环。

![](IO.assets/8253_44.png)

```markdown
①初值装入后，经过1个CLK的周期，计数器开始从初值减1计数，计数结束（归0）时，使输出OUT产生一个宽度为1个CLK周期的负脉冲——选通信号。

②（用指令）重新装入初值后，经过N+1个CLK周期，又可使OUT产生一个选通信号——（用软件）可重复触发。

③门控GATE的作用：高电平时计数，低电平时停止计数。
```

### 模式5：硬件触发的选通信号发生器

单次波形输出，波形特征同方式4，但重置初值和GATE上升沿之后可重新计时。

![](IO.assets/8253_55.png)

```markdown
①初值装入后，在GATE的上升沿的触发下，经过1个CLK的周期，计数器开始从初值减1计数，计数结束（归0）时，使输出OUT产生一个宽度为1个CLK周期的负脉冲——选通信号。

②用GATE的上升沿可重新触发，使OUT产生一个选通信号——（用硬件）可重复触发。
```



### 8253工作模式小结
```markdown
模式2、4、5的输出波形是相同的，都是宽度为一个CLK周期的负脉冲。

但模式2是连续工作，模式4由软件（设置计数值）触发启动，模式5由门控脉冲触发启动

写入计数值后才能开始计数

模式0、2、3、4在写入计数值后，计数过程就开始了

模式1、5需要外部触发启动，才开始计数

6种方式中只有方式2、3是连续计数，其他4种方式都是一次计数，要继续工作需要重新启动，方式0、4由写入计数值（软件）启动，方式1、5要由外部信号（硬件）启动。

```

## 应用举例

```assembly
;假设端口是
0123H;control
0120H;0
0121H;1
0122H


CNT0：
MOV DX,0123H            ;初始化
MOV AL,34H
OUT DX,AL
MOV DX,0120H            ;写入计数初值
MOV AX,20000            ;使用AX寄存器，分为低8位和高8位，即AL和AH
OUT DX,AL
MOV AL,AH
OUT DX,AL


CNT1：
MOV DX,0123H            ;初始化
MOV AL,56H
OUT DX,AL
MOV DX,0121H            ;写入计数初值
MOV AX,200              ;这里AX可以直接写AL,200用八位寄存器就够   
OUT DX,AL


CNT2：
MOV DX,0123H            ;初始化
MOV AL,B0H
OUT DX,AL
MOV DX,0122H            ;写入计数初值
MOV AX,10000
OUT DX,AL
MOV AL,AH
OUT DX,AL

```

