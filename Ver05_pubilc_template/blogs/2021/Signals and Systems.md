# 第一章 信号与系统



![第一章 信号与系统](https://gitee.com/murphyhou/picgo/raw/master/SS/%E7%AC%AC%E4%B8%80%E7%AB%A0%20%E4%BF%A1%E5%8F%B7%E4%B8%8E%E7%B3%BB%E7%BB%9F.png)

```
本章内容

- 信号的描述
- 信号的自变量变换
- 基本信号
- 系统机器数学模型
- 系统的性质
```

## 1.0 引言

信号

- 信号的定义：描述一定物理现象
- 信号的表示方式：函数
- 信号的分类、
  - 确知信号和随机信号
  - 连续时间信号和离散时间信号

**信号与系统不是讲数学，而是用数学的方法来解决信号处理的问题**

## 1.1 连续时间信号和离散时间信号

### 1.1.1 数学表示

连续时间信号（CTS）：自变量是连续可变的

离散时间信号（DTS）：仅仅定义在离散时刻点上

连续时间信号->离散时间信号?

- 连续时间信号在离散时刻点上的样本可以构成一个离散时间信号（采样）

### 1.1.2 信号的能量与功率

能量

平均功率

有限区间内CTS和DTS的总能量和平均功率的计算

无限区间内CTS和DTS的总能量和平均功率的计算

利用能量与功率将信号分为三类：

- 能量信号——信号具有有限的总能量
  - 信号的总能量有限
  - 平均功率为0
- 功率信号——信号具有无限的总能量但是平均功率有限
  - 信号的总能量有限
  - 平均功率为大于0，小于∞
- 非能量信号也非功率信号
  - 信号的总能量无穷大
  - 信号的平均功率无穷大

### 1.1.3 周期信号与非周期信号

$$
x(t)=x(t+nT)
$$

$$
x[n]=x[n+N]
$$



周期信号一定是功率信号

非周期信号，且能量有限的信号称为能量信号





## 1.2 自变量的变换

**自变量的变换必然会使得信号的特性相应地改变**

### 1.2.1 自变量变换

- 时移变换 shift of signals
  - 左加右减

- 时间反转 time reversal
  - 以纵轴为轴呈镜像对称

- 时间尺度变换 time scaling
  - 在时间常数上对时间做压缩或者扩展

### 1.2.2 周期信号

周期：T或N

基波周期：$T_0$或$N_0$

### 1.2.3 偶信号和奇信号

任何一个信号都能分解成两个信号之和，其中之一为偶信号，另一个为奇信号。

## 1.3 指数信号和正弦信号



## 1.4 单位冲激和单位阶跃函数（重要）

### 离散时间的单位脉冲和单位阶跃序列

### 连续时间单位冲激和单位阶跃函数

课本P19——重要内容

![image-20211109221845118](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211109221845118.png)

## 1.5 连续时间和离散时间系统



## 1.6 基本系统的性质

![系统的性质2](https://gitee.com/murphyhou/picgo/raw/master/SS/%E7%B3%BB%E7%BB%9F%E7%9A%84%E6%80%A7%E8%B4%A82.png)

# 第二章 线性时不变系统

## 离散线性时不变系统

![image-20211109222000602](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211109222000602.png)

## 连续时间线性时不变系统

![image-20211109222027637](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211109222027637.png)

## 线性时不变系统的性质

![image-20211109222109193](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211109222109193.png)

# 第三章 周期信号的傅里叶级数表示

## 线性时不变系统对复指数信号的响应

![image-20211109222225570](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211109222225570.png)

## 连续时间周期信号的傅里叶级数表示

### 成谐波关系的复指数信号的线性组合

![image-20211109222320380](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211109222320380.png)

### 连续时间周期信号傅里叶级数表示

![image-20211109222351587](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211109222351587.png)

## 傅里叶级数收敛

![image-20211109222418948](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211109222418948.png)

## 连续时间傅里叶级数性质

### 线性性质

![image-20211109222612727](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211109222612727.png)

### 时移性质

![image-20211109222621328](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211109222621328.png)



### 时间反转

![image-20211109222627507](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211109222627507.png)



### 时间尺度

![image-20211109222632824](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211109222632824.png)



### 相乘性质

![image-20211109222650906](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211109222650906.png)

### 共轭及其共轭对称

![image-20211109222703928](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211109222703928.png)



### 连续时间周期信号的帕斯瓦尔定理



![image-20211109222710690](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211109222710690.png)





## 总结：连续时间傅里叶级数性质

<img src="https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211114210912354.png" alt="image-20211114210912354" style="zoom:150%;" />

# 第四章 连续时间傅里叶变换

## 4.1非周期信号的表示



![image-20211114211601937](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211114211601937.png)

### 傅里叶变换的收敛

![image-20211114211612899](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211114211612899.png)



### 常见傅里叶变换举例子





## 4.2周期信号的傅里叶变换

![image-20211114211915489](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211114211915489.png)





## 4.3连续时间傅里叶变换性质



### 线性性质

![image-20211114212741940](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211114212741940.png)

### 时移性质

![image-20211114212751847](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211114212751847.png)



### 共轭和共轭对称性质

![image-20211114212821020](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211114212821020.png)

![image-20211114212840126](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211114212840126.png)

![image-20211114212852131](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211114212852131.png)

![image-20211114212902799](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211114212902799.png)



### 微分与积分性质

![image-20211114213056673](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211114213056673.png)



### 时间与频率的尺度变换

![image-20211114213226698](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211114213226698.png)



### 对偶性质

![image-20211229123027523](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211229123027523.png)

![image-20211229123037735](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211229123037735.png)



### 帕斯瓦尔定理

![image-20211114213349722](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211114213349722.png)



## 4.4 卷积性质

![image-20211229123050594](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211229123050594.png)



## 4.5 相乘性质

![image-20211229123057541](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211229123057541.png)



![image-20211206223140661](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211206223140661.png)



![image-20211206223723775](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211206223723775.png)



![image-20211206223223857](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211206223223857.png)

# 第五章 离散时间傅里叶变换

![image-20211229123158629](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211229123158629.png)

# 第六章 信号与系统的时域和频域特征

![image-20211229123248305](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211229123248305.png)

## 6.2 线性时不变系统频率响应的模和相位表示

![image-20211229123300715](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211229123300715.png)

### 群时延

![image-20211229123309034](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211229123309034.png)



### 对数模和相位图

![image-20211229123413689](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211229123413689.png)



## 6.3 理想频率选择器滤波器的时域特性

![image-20211229123429741](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211229123429741.png)

![image-20211229123436962](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211229123436962.png)









## 6.5 一阶连续时间系统

![image-20211229123456338](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211229123456338.png)





# 第七章 采样



## 7.1 用信号样本表示连续时间信号：采样定理

![image-20211228093508545](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211228093508545.png)

### 冲击串采样

![image-20211228093601348](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211228093601348.png)

![image-20211228093624672](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211228093624672.png)

![image-20211228093655083](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211228093655083.png)

![image-20211228093706888](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211228093706888.png)

### 零阶保持采样

![image-20211228093721826](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211228093721826.png)

## 7.2 利用内插由样本重建信号

![image-20211228093738455](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211228093738455.png)

## 7.3 欠采样的效果：混叠现象

![image-20211228093750160](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211228093750160.png)



## 7.4 连续时间信号的离散时间处理



## 7.5 离散时间信号采样



# 第八章 通信系统

## 8.0 引言

![image-20211229224835569](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211229224835569.png)

## 8.1 复指数载波

![image-20211229224855735](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211229224855735.png)

![image-20211229224912738](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211229224912738.png)

![image-20211229224933643](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211229224933643.png)

![image-20211229224939739](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211229224939739.png)





## 8.2 正弦载波

![image-20211229225014905](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211229225014905.png)

![image-20211229225022151](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211229225022151.png)



## 解调

![image-20211229225048457](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211229225048457.png)

![image-20211229225058364](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211229225058364.png)

![image-20211229225109153](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211229225109153.png)

![image-20211229225115240](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211229225115240.png)







## 8.3 频分多路复用

![image-20211229225121758](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211229225121758.png)

## 8.4 单边带正弦幅度调制

![image-20211229225132331](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211229225132331.png)

![image-20211229225139490](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211229225139490.png)

![image-20211229225148790](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211229225148790.png)

![image-20211229225156048](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211229225156048.png)

# 第九章 拉普拉斯变换



## 9.0 引言

连续时间傅里叶变换的推广——拉普拉斯变换

拉普拉斯变换和Z变换能用于很多不稳定系统的分析





## 9.1 拉普拉斯变换

![image-20211206200817398](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211206200817398.png)

![image-20211206200900094](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211206200900094.png)

![image-20211206201136022](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211206201136022.png)

## 9.2拉普拉斯变换的收敛域

![image-20211206201301335](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211206201301335.png)

![image-20211206201315072](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211206201315072.png)

![image-20211206201326783](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211206201326783.png)

![image-20211206201409322](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211206201409322.png)

![image-20211206201421000](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211206201421000.png)

![image-20211206201435902](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211206201435902.png)

![image-20211206201448097](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211206201448097.png)

![image-20211206201454653](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211206201454653.png)



## 9.3 拉普拉斯逆变换

![image-20211206201512087](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211206201512087.png)

部分分式展开

![image-20211206201550289](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211206201550289.png)

![image-20211206201611776](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211206201611776.png)

部分分式展开——重根的情况

![image-20211206203227393](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211206203227393.png)

## 9.4 由零-极点图对傅里叶变换进行几何求值

![image-20211229225335369](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211229225335369.png)











## 9.5 拉普拉斯变换的性质

![image-20211206210923272](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211206210923272.png)





![image-20211210115437813](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211210115437813.png)

## 9.6 常用拉普拉斯变换对

![image-20211206214129892](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211206214129892.png)

![image-20211206214147645](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211206214147645.png)



## 9.7 用拉普拉斯变换分析表征线性时不变系统

![image-20211206222523614](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211206222523614.png)

![image-20211206222533422](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211206222533422.png)

![image-20211206222546276](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211206222546276.png)

## 9.8 系统函数的代数属性与方框图表示

![image-20211206222744133](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211206222744133.png)



## 9.9 单边拉普拉斯变换

![image-20211230204045969](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211230204045969.png)

![image-20211230204106649](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211230204106649.png)

![image-20211230204119619](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211230204119619.png)


![image-20211206204658304](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211206204658304.png)

![image-20211230204135503](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211230204135503.png)

# 第十章 Z变换



## 10.1 z变换

![image-20211228092713865](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211228092713865.png)

![image-20211228092728208](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211228092728208.png)

![image-20211228092739098](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211228092739098.png)

![image-20211228092749702](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211228092749702.png)



## 10.2 z变换的收敛域

![image-20211228092821884](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211228092821884.png)

![image-20211228092838193](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211228092838193.png)

![image-20211228092852243](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211228092852243.png)

![image-20211228092907453](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211228092907453.png)





## 10.3 z逆变换

![image-20211228093019957](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211228093019957.png)

![image-20211228093040462](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211228093040462.png)







## 10.4 利用零极点图对傅里叶变换进行几何求值



一阶系统

二阶系统（可能要考）

## 10.5 z变换的性质

![image-20211228093105483](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211228093105483.png)

![image-20211228093118710](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211228093118710.png)

![image-20211228093137269](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211228093137269.png)

![image-20211228093151072](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211228093151072.png)

## 10.6 常见z变换对

![image-20211228093205083](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211228093205083.png)

![image-20211228093218685](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211228093218685.png)

![image-20211228093228078](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211228093228078.png)

![image-20211228093235884](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211228093235884.png)



## 10.7 利用z变换分析与表征线性时不变系统

![image-20211228093246260](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211228093246260.png)

![image-20211230204204723](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211230204204723.png)

![image-20211230204215018](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211230204215018.png)

![image-20211230204224534](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211230204224534.png)





## 10.8 系统函数的代数属性与方框图表示





## 10.9 单边z变换



![image-20211230204236350](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211230204236350.png)

![image-20211230204250144](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211230204250144.png)

![image-20211230204256194](https://gitee.com/murphyhou/picgo/raw/master/SS/image-20211230204256194.png)
