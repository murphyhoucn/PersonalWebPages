# 第一章 绪论

信息的定义

``` 
哈莱特：发信者所发出的信息，就是他在通信符号表中选择符号的具体方式。用自由度来度量时间。
维纳：信息是信息，不是物质也不是能量。
香农：信息是事物运动状态或存在方式的不确定性的描述。
	信息的根本问题是在某一点精确地或近似地重现另选则的一点的消息。
```

物质世界的三大支柱：物质，信息，能量

区分定义：

- 信息：**事物运动状态或存在方式的不确定性的描述**
- 消息：含有信息的语言，文字，图像等
- 信号： 
  - 信息的物理层表示，传递信息的载体
  - 消息的物理体现，光、点信号等



- 信息的特征
  - 不确定性：接收者在收到信息之前，对它的内容是不知道的
  - 信息可以使认识主体对某一事物的未知性或不确定性减少
  - 信息是可以度量的

信息论所研究的对象：

``` flow
op0=>operation: 信源
op1=>operation: 编码器
op2=>operation: 信道
op3=>operation: 译码器
op4=>operation: 信宿

op5=>operation: 噪声源


op0(right)->op1(right)->op2(right)->op3(right)->op4
op5->op2
```

噪声源：主要干扰信道

信息论研究的目的

- 可靠性$\stackrel{信道编码}{\longrightarrow}$多冗余
- 有效性$\stackrel{信源编码}{\longrightarrow}$少冗余
- 保密性
- 认证性

信息论的研究内容

- 狭义的信息论/经典信息论/香农基本理论
  - 信息的测度
  - 信道容量
  - 信源编码
  - 信道编码
- 一般信息论/工程信息论
- 广义信息论



香农信息论的建立和发展

**香农信息论的核心**

```
在通信系统中采用适当的编码后能够实现高效率和高可靠性地传输信息，并得出了信源编码定理和信道编码定理。
从数学上看，这些定理是最后编码存在定理。
从工程上看，这些定理不是结构性的，不能从定理的结果直接得出实现最优编码的具体途径。
然而它们给出了编码的性能极限。
```

- 无失真信源编码定理
- 信道纠错编码
- 限失真信源编码定理
- 多用户、网络信息论的发展
- 信息保密与安全定理



# 第二章 离散信源及其信息测度✔

## 2.1 信源的数学模型及其分类

信源是信息的来源，是产生消息或消息序列的源泉。

信息是抽象的，而消息是具体的。

消息不是信息本身，但它包含着和携带这消息。

**我们研究的是信源各种可能的输出以及输出各种可能消息的不确定性。**

信源的描述：用一个**样本空间及其概率测度**，也就是**概率空间**/**信源空间**。

根据消息的不用的随机性质来对信源进行分类：

-  信源输出的消息用随机变量描述
  - 信源可能输出的消息是有限的或可数的，并且每次只输出其中一个消息。

  - 信源的概率空间必定是一个完备集；

  - 离散信源

  - $$
    \begin{bmatrix}
    X\\
    P(x)\\
    \end{bmatrix}
    =
    \begin{bmatrix}
    a_1,&a_2,&\cdots,&a_q\\
    P(a_1),&P(a_2),&\cdots,&P(a_q)\\
    \end{bmatrix}
    $$

  - $$
    \sum\limits_{i=1}^qP(a_i)=1
    $$

  - 连续信源

  - $$
    \begin{bmatrix}
    A\\
    p(x)\\
    \end{bmatrix}
    =
    \begin{bmatrix}
    (a,b)\\
    p(x)\\
    \end{bmatrix}
    $$

  - $$
    \int_a^b {p(x)} \,{\rm d}x=1
    $$

  - ![image-20211105175349341](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211105175349341.png)

- 信源输出的消息用随机矢量描述
- 

- 信源输出的消息用随机过程描述

![信源的数学模型及分类](https://gitee.com/murphyhou/picgo/raw/master/image/%E4%BF%A1%E6%BA%90%E7%9A%84%E6%95%B0%E5%AD%A6%E6%A8%A1%E5%9E%8B%E5%8F%8A%E5%88%86%E7%B1%BB.png)

![image-20211021173814410](https://gitee.com/murphyhou/picgo/raw/master/learn/image-20211021173814410.png)

## 2.2 离散信源的信息熵

- 信息量的定义：

收到某信息获得的信息量（即收到某信息后获得关于某基本事件发生的信息量）

= 不确定性减少的量

= （收到此消息前关于某事件发生的不确定性）-（收到此消息后关于某事件发生的不确定性）



无噪声的情况下：收到某消息获得的信息量=收到消息前关于事件发生的不确定性=信源输出的某消息中所含有的信息量

<img src="https://gitee.com/murphyhou/picgo/raw/master/learn/image-20211021155556459.png" alt="image-20211021155556459" style="zoom:200%;" />

**信息量是事件发生的先验概率的函数——自信息量**

信息量的单位

- 以2为底：bit
- 以e为底：nat
- 以10为底：hart
- 换底公式

---

**信息熵**

自信息是信源发出某一消息所含有的信息量，信源所发出的消息不同，所含有的信息量也就不同。自信息就是一个随机变量，不能用来作为整个信源的信息测度

信息熵——信源的平均自信息：自信息的数学期望

单位：bit/符号——nat/符号——hart/符号



信息熵的物理含义

- 表示信源输出后，每个消息（符号）所提供的平均信息量
- 表输信源输出前，信源的平均不确定性
- 用来表征变量X的随机性

## 2.3 信息熵的基本性质

概率矢量——熵函数

<img src="https://gitee.com/murphyhou/picgo/raw/master/learn/image-20211021155621553.png" alt="image-20211021155621553" style="zoom: 200%;" />

![第二章： 信息熵的基本性质](https://gitee.com/murphyhou/picgo/raw/master/learn/%E7%AC%AC%E4%BA%8C%E7%AB%A0%EF%BC%9A%20%E4%BF%A1%E6%81%AF%E7%86%B5%E7%9A%84%E5%9F%BA%E6%9C%AC%E6%80%A7%E8%B4%A8.png)

## 2.5 离散无记忆信源的扩展信源

<img src="https://gitee.com/murphyhou/picgo/raw/master/learn/image-20211021160324381.png" alt="image-20211021160324381" style="zoom:200%;" />

![image-20211021162146280](https://gitee.com/murphyhou/picgo/raw/master/learn/image-20211021162146280.png)

![image-20211021162209890](https://gitee.com/murphyhou/picgo/raw/master/learn/image-20211021162209890.png)

## 2.6 离散平稳信源

**联合熵**

![image-20211021164222475](https://gitee.com/murphyhou/picgo/raw/master/learn/image-20211021164222475.png)

**条件熵**

![image-20211021164150338](https://gitee.com/murphyhou/picgo/raw/master/learn/image-20211021164150338.png)



贝叶斯公式

![image-20211021165835882](https://gitee.com/murphyhou/picgo/raw/master/learn/image-20211021165835882.png)



有限定条件的熵小于无限定条件的熵

熵的强可加性

![image-20211021170727577](https://gitee.com/murphyhou/picgo/raw/master/learn/image-20211021170727577.png)

![image-20211021170740145](https://gitee.com/murphyhou/picgo/raw/master/learn/image-20211021170740145.png)



---

离散平稳信源的极限熵

![image-20211021171029500](https://gitee.com/murphyhou/picgo/raw/master/learn/image-20211021171029500.png)

![image-20211021171336940](https://gitee.com/murphyhou/picgo/raw/master/learn/image-20211021171336940.png)

使用**条件熵**近似**极限熵**

![image-20211021171445412](https://gitee.com/murphyhou/picgo/raw/master/learn/image-20211021171445412.png)

**记忆长度为m（即某时刻输出什么符号只能与前m个符号有关），则得离散平稳信源得极限熵等于有限记忆长度为m的条件熵**

![image-20211021171841918](https://gitee.com/murphyhou/picgo/raw/master/learn/image-20211021171841918.png)

## 2.7 马尔可夫信源

马尔可夫信源——非平稳有记忆信源

**未来不依赖于过去的演变，只取决于现在**

有许多信源是非平稳信源，但在其输出的符号序列中符号之间的依赖关系是有限的

<img src="https://gitee.com/murphyhou/picgo/raw/master/learn/image-20211021174014771.png" alt="image-20211021174014771" style="zoom:200%;" />

**马尔可夫信源的定义**

![image-20211021174220227](https://gitee.com/murphyhou/picgo/raw/master/learn/image-20211021174220227.png)

**m阶马尔可夫信源**

![image-20211021174524581](https://gitee.com/murphyhou/picgo/raw/master/learn/image-20211021174524581.png)

状态转移图与一次转移概率

![image-20211021175446870](https://gitee.com/murphyhou/picgo/raw/master/learn/image-20211021175446870.png)

**时齐，遍历的马尔可夫信源的熵**

**时齐，遍历的m阶马尔可夫信源的熵**

<img src="https://gitee.com/murphyhou/picgo/raw/master/learn/image-20211021175200856.png" alt="image-20211021175200856" style="zoom:200%;" />



## 2.8 信源剩余度与自然语言的熵

<img src="https://gitee.com/murphyhou/picgo/raw/master/learn/image-20211021175547869.png" alt="image-20211021175547869" style="zoom:150%;" />

![image-20211021175602866](https://gitee.com/murphyhou/picgo/raw/master/learn/image-20211021175602866.png)

![image-20211021175619334](https://gitee.com/murphyhou/picgo/raw/master/learn/image-20211021175619334.png)













# 第三章 离散信道及其信道容量✔

```
3.1信道的数学模型及其分类
3.2平均互信息及平均条件互信息
3.3平均互信息的特性
3.4信道容量及其一般计算方法
3.6离散无记忆扩展信道及其信道容量
```

## 3.1信道的数学模型及其分类

![image-20211104161709790](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211104161709790.png)

![image-20211104161647533](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211104161647533.png)

![image-20211104161740811](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211104161740811.png)



### 二元对称信道

![image-20211104161436894](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211104161436894.png)



### 二元删除信道

![image-20211104161456192](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211104161456192.png)

### 四种概率

![image-20211104161525342](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211104161525342.png)

![image-20211104161801562](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211104161801562.png)

![image-20211104164155961](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211104164155961.png)



## 3.2平均互信息及平均条件互信息

### 四种熵

![image-20211104161842223](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211104161842223.png)

![image-20211104161911154](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211104161911154.png)

### 平均互信息

![image-20211104161940480](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211104161940480.png)

![image-20211104162013849](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211104162013849.png)

![image-20211104164238198](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211104164238198.png)



![image-20211104162128782](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211104162128782.png)

![image-20211111162730372](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211111162730372.png)

![image-20211105203206248](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211105203206248.png)

![image-20211104162159806](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211104162159806.png)

### 条件互信息

![image-20211104162214705](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211104162214705.png)



### 平均条件互信息

![image-20211104162226539](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211104162226539.png)



## 3.3平均互信息的特性

![image-20211104162302473](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211104162302473.png)

## 3.4信道容量及其一般计算方法

### 信道容量

![image-20211104162355930](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211104162355930.png)

<img src="https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211105203317905.png" alt="image-20211105203317905" style="zoom:150%;" />

### 无噪无损一一对应信道

![image-20211104162422686](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211104162422686.png)



### 有噪无损信道

![image-20211104162441185](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211104162441185.png)



### 无噪有损信道（确定信道）

![image-20211104162455091](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211104162455091.png)

### 对称离散信道

![image-20211104173557599](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211104173557599.png)



### 准对称信道

![image-20211104175101792](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211104175101792.png)

![image-20211104174830722](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211104174830722.png)

### 一般离散信道

![image-20211104175330014](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211104175330014.png)

![image-20211104174848018](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211104174848018.png)

（这个定理不懂）

## 3.6离散无记忆扩展信道及其信道容量



![image-20211105161949672](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211105161949672.png)

![image-20211105162003540](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211105162003540.png)

![image-20211105203407885](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211105203407885.png)

![image-20211105170405056](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211105170405056.png)

![image-20211105170433871](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211105170433871.png)





## 3.7 独立并联信道及其信道容量

![image-20211105203423844](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211105203423844.png)

![image-20211105174507437](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211105174507437.png)

![image-20211105174516865](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211105174516865.png)





## 3.8 串联信道的互信息和数据处理定理

![image-20211105174641080](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211105174641080.png)

![image-20211105174652219](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211105174652219.png)

![image-20211105174716362](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211105174716362.png)

## 3.9 信源与信道匹配



![image-20211105200158291](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211105200158291.png)







# 第四章 波形信源和波形信道

```
## 4.1 波形信源的统计特性和离散化
## 4.2连续波形信源和波形信源的信息测度
## 4.3 连续信源熵的性质及最大差熵定理
## 4.4 连续信源熵的变换
## 4.5 熵功率
## 4.6 连续信道和波形信道的分类
## 4.7 连续信道和波形信道的信息传输律
## 4.8 连续信道和波形信道的信道容量
```



## 4.1 波形信源的统计特性和离散化

随机波形信源输出的消息是随机的，因此，可以用随机过程{x(t)}来描述；

- 随机波形信源中的消息数是无限的；
- 对于随机波形信源，也用有限维概率密度函数族及与各维概率密度函数有关的统计量来描述；

就其统计特性来分类：平稳随机过程——非平稳随机过程

- 平稳随机过程：各维概率密度函数不随时间平移而发生变化的随机过程；
- 非平稳随机过程：

![image-20211111161525774](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211111161525774.png)

![image-20211111161600210](C:/Users/DELL/AppData/Roaming/Typora/typora-user-images/image-20211111161600210.png)

## 4.2连续波形信源和波形信源的信息测度

### 差熵

![image-20211111174646208](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211111174646208.png)

![image-20211111174706566](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211111174706566.png)

### 连续平稳信源的差熵

![image-20211111174748801](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211111174748801.png)

![image-20211111174808837](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211111174808837.png)

### 波形信源的差熵

![image-20211111174824633](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211111174824633.png)



### 特殊连续信源1——均匀分布连续信源的差熵

![image-20211111174901845](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211111174901845.png)

![image-20211111175019277](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211111175019277.png)

![image-20211111174957776](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211111174957776.png)

### 特殊连续信源2——高斯信源的差熵

![image-20211111175038509](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211111175038509.png)

![image-20211111175121203](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211111175121203.png)



## 4.3 连续信源熵的性质及最大差熵定理

### 可加性

![image-20211112095338788](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211112095338788.png)

### 上凸性

![image-20211112095352717](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211112095352717.png)



### 差熵可取负值

![image-20211112095400092](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211112095400092.png)



### 变换性

![image-20211112095416977](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211112095416977.png)



### 极值性（最大差熵定理）

![image-20211112095429101](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211112095429101.png)

![image-20211112223908130](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211112223908130.png)

### 峰值功率受限条件下信源的最大熵

![image-20211112095441143](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211112095441143.png)



### 平均功率受限条件下信源的最大熵

![image-20211112095453929](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211112095453929.png)

![image-20211112095503949](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211112095503949.png)



## 4.4 连续信源熵的变换



## 4.5 熵功率⭐（不是很懂）

![image-20211114191705406](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211114191705406.png)



![image-20211114191720076](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211114191720076.png)

![image-20211114191736931](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211114191736931.png)

![image-20211114191803009](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211114191803009.png)

![image-20211114180410720](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211114180410720.png)

## 4.6 连续信道和波形信道的分类

![image-20211230211709615](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211230211709615.png)

![image-20211230211748749](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211230211748749.png)

![image-20211230212005879](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211230212005879.png)

![image-20211230212050871](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211230212050871.png)

![image-20211230212200595](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211230212200595.png)

![image-20211230212213555](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211230212213555.png)





## 4.7 连续信道和波形信道的信息传输律

### 基本连续信道

![image-20211230212308544](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211230212308544.png)

### 多维连续信道

![image-20211230212349596](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211230212349596.png)

### 波形信道 
![image-20211230212424433](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211230212424433.png)



### 连续信道平均互信息的特性

![image-20211231105118884](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211231105118884.png)

![image-20211231105102184](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211231105102184.png)

![image-20211231105150992](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211231105150992.png)

![image-20211231105327978](https://gitee.com/murphyhou/picgo/raw/master/informationtheory/image-20211231105327978.png)

## 4.8 连续信道和波形信道的信道容量





​	

