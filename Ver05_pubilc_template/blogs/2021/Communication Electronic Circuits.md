# 第一章 绪论

![第一章绪论](https://gitee.com/murphyhou/picgo/raw/master/CEC/%E7%AC%AC%E4%B8%80%E7%AB%A0%E7%BB%AA%E8%AE%BA.png)

## 1.1 通信系统的概念

- 信息源
- 发送设备
- 信道（噪声源）
- 接收设备
- 收信装置



## 1.2 无线电波的传播特性

不同频段的无线电信号，其传播特性不同。

同一信道对不同频率的信号传播特性是不同的。

传播方式

- 绕射——超视距通信
  - 地波
  - 中长波信号
- 折射与反射——超视距通信
  - 利用电离层
  - 天波
  - 短波
- 直射——视距通信
  - 超短波
  - 对流层散射
    - 散射通信已经成为超短波甚至微波的长距离通信的有力手段





**只有当天线的尺寸大到可以与信号的波长相比拟时，天线才具有较高的辐射效率。**

## 1.3 无线电波的频段划分

波长λ

频率f

电磁波传播速度c

c=λ*f

| **波段（频段）** | **符号** | **波长范围**  | **频率范围** | **应用范围**                                                 |
| ---------------- | :------: | ------------- | ------------ | ------------------------------------------------------------ |
| 超长波（甚低频） |   VLF    | 100000-10000m | 3-30kHz      | 1.海岸——潜艇通信；2.海上导航。                               |
| 长波（低频）     |    LF    | 10000-1000m   | 30-300kHz    | 1.大气层内中等距离通信；2.地下岩层通信；3.海上导航。         |
| 中波（中频）     |    MF    | 1000-100m     | 300kHz-3MHz  | 1.广播；2.海上导航。                                         |
| 短波（高频）     |    HF    | 100-10m       | 3-30MHz      | 1.远距离短波通信；2.短波广播。                               |
| 超短波（甚高频） |   VHF    | 10-1m         | 30-300MHz    | 1.电离层散射通信（30-60MHz）；2.流星余迹通信（30-100MHz）；3.人造电离层通信（30-144MHz）；4.对大气层内、外空间飞行体（飞机、导弹、卫星）的通信；电视、雷达、导航、移动通信。 |
| 分米波（特高频） |   UHF    | 1-0.1m        | 300-3000MHz  | 1.对流层工散射通信（700-1000MHz）；2.小容量（8-12路）微波接力通信（352-420MHz）；3.中容量（120路）微波接力通信（1700-2400MHz）。 |
| 厘米波（超高频） |   SHF    | 10-1cm        | 3-30GHz      | 1.大容量（2500路、6000路）微波接力通信（3600-4200MHz，5850-8500MHz）；2.数字通信；3.卫星通信；4.波导通信。 |
| 毫米波（极高频） |   EHF    | 10-1mm        | 30-300GHz    | 穿入大气层时的通信                                           |

## 1.4 调制的通信系统（难点） 

-  无线电广播发射系统
- 超外差式接受系统

![CEC](https://gitee.com/murphyhou/picgo/raw/master/CEC/CEC.jpg)

![CEC2](https://gitee.com/murphyhou/picgo/raw/master/CEC/CEC2.jpg)

![CEC3](https://gitee.com/murphyhou/picgo/raw/master/CEC/CEC3.jpg)







# 第二章 小信号调谐放大电路

```
主要是接收信号部分的电路，与接受天线相连
```



![第二章 引言](https://gitee.com/murphyhou/picgo/raw/master/CEC/%E7%AC%AC%E4%BA%8C%E7%AB%A0%20%E5%BC%95%E8%A8%80.png)

## 2.2 LC谐振回路

 ![QQ图片20211008112640](https://gitee.com/murphyhou/picgo/raw/master/CEC/QQ%E5%9B%BE%E7%89%8720211008112640.jpg)

![第二章 LC谐振回路](https://gitee.com/murphyhou/picgo/raw/master/CEC/%E7%AC%AC%E4%BA%8C%E7%AB%A0%20LC%E8%B0%90%E6%8C%AF%E5%9B%9E%E8%B7%AF.png)

## 2.3 放大器

![第二章 放大器](https://gitee.com/murphyhou/picgo/raw/master/CEC/%E7%AC%AC%E4%BA%8C%E7%AB%A0%20%E6%94%BE%E5%A4%A7%E5%99%A8.png)





# 第三章  高频功率放大器

## 3.1 概述

```
主要是发射信号部分的电路，与发射天线相连
```

![第三章 概述](https://gitee.com/murphyhou/picgo/raw/master/CEC/%E7%AC%AC%E4%B8%89%E7%AB%A0%20%E6%A6%82%E8%BF%B0.png)



## 3.2 高频调谐功率放大器的工作原理

![高频调谐功率放大器电路](https://gitee.com/murphyhou/picgo/raw/master/CEC/%E9%AB%98%E9%A2%91%E8%B0%83%E8%B0%90%E5%8A%9F%E7%8E%87%E6%94%BE%E5%A4%A7%E5%99%A8%E7%94%B5%E8%B7%AF.jpg)



![image-20211010203806166](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211010203806166.png)

输出的电压信号和输入的电压信号同频，但是幅值变大

输出的电流信号：尖顶余弦脉冲

![image-20211010205100710](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211010205100710.png)

![3.2高频调谐功率放大器的工作原理](https://gitee.com/murphyhou/picgo/raw/master/CEC/3.2%E9%AB%98%E9%A2%91%E8%B0%83%E8%B0%90%E5%8A%9F%E7%8E%87%E6%94%BE%E5%A4%A7%E5%99%A8%E7%9A%84%E5%B7%A5%E4%BD%9C%E5%8E%9F%E7%90%86.png)

## 3.3 功率和效率

![3.3 功率和效率](https://gitee.com/murphyhou/picgo/raw/master/CEC/3.3%20%E5%8A%9F%E7%8E%87%E5%92%8C%E6%95%88%E7%8E%87.png)

## 3.4 高频调谐功率放大器的工作状态分析

![3.4 高频调谐功率放大器的工作状态分析](https://gitee.com/murphyhou/picgo/raw/master/CEC/3.4%20%E9%AB%98%E9%A2%91%E8%B0%83%E8%B0%90%E5%8A%9F%E7%8E%87%E6%94%BE%E5%A4%A7%E5%99%A8%E7%9A%84%E5%B7%A5%E4%BD%9C%E7%8A%B6%E6%80%81%E5%88%86%E6%9E%90.png)

## 3.7 倍频器

![3.5 倍频器](https://gitee.com/murphyhou/picgo/raw/master/CEC/3.5%20%E5%80%8D%E9%A2%91%E5%99%A8.png)





# 第四章 正弦波振荡器

## 4.1 概述

![4.1 概述](https://gitee.com/murphyhou/picgo/raw/master/CEC/4.1%20%E6%A6%82%E8%BF%B0.png)



## 4.2 反馈型正弦自激振荡器基本原理

![image-20211023143502233](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211023143502233.png)

![4.2 反馈型正弦波自激振荡器基本原理](https://gitee.com/murphyhou/picgo/raw/master/CEC/4.2%20%E5%8F%8D%E9%A6%88%E5%9E%8B%E6%AD%A3%E5%BC%A6%E6%B3%A2%E8%87%AA%E6%BF%80%E6%8C%AF%E8%8D%A1%E5%99%A8%E5%9F%BA%E6%9C%AC%E5%8E%9F%E7%90%86.png)



## 4.3 三点式LC振荡器

![4.3 三点式LC振荡器](https://gitee.com/murphyhou/picgo/raw/master/CEC/4.3%20%E4%B8%89%E7%82%B9%E5%BC%8FLC%E6%8C%AF%E8%8D%A1%E5%99%A8.png)

## 4.4 改进型电容三点式振荡器

## 4.5 振荡器的频率稳定

![4.4 改进型电容三点式振荡器](https://gitee.com/murphyhou/picgo/raw/master/CEC/4.4%20%E6%94%B9%E8%BF%9B%E5%9E%8B%E7%94%B5%E5%AE%B9%E4%B8%89%E7%82%B9%E5%BC%8F%E6%8C%AF%E8%8D%A1%E5%99%A8.png)



## 4.6 石英晶体振荡器

LC振荡器的频率稳定度不能做的很高，主要原因是LC回路的Q值不能做的很高

石英晶体振荡器是以石英晶体谐振器取代LC振荡器中构成谐振回路的电感，电容元件所组成的正弦波振荡，频率稳定度高

石英片是从石英晶体柱中切割下来的一种弹性体，有一 固有振动频率，其值与石英片的形状、尺寸、切型有关。

当 外加交流电压的频率等于晶体固有频率时，晶体片的机械振 动最大，晶体表面电荷量最多，外电路中的交流电流最强， 于是产生了谐振。



![](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211031142136753.png)

![image-20211031142113658](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211031142113658.png)

晶片可用一个串联LC回路表示，L_q为动态电感，C_q为动态电容，r_q为动态电阻

切片与金属极板构成的静电电容C_0，即使石英晶片不震动，C_0仍然存在！

![image-20211114144254883](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211114144254883.png)

![image-20211031142136753](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211031142136753.png)

![image-20211031143346149](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211031143346149.png)

![image-20211031143414023](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211031143414023.png)

![image-20211114144323874](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211114144323874.png)

![image-20211114144343687](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211114144343687.png)

![image-20211114144406406](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211114144406406.png)

## 4.7 石英晶体振荡器电路









# 第五章 振幅调制与解调

![5.1 调制与解调](https://gitee.com/murphyhou/picgo/raw/master/CEC/5.1%20%E8%B0%83%E5%88%B6%E4%B8%8E%E8%A7%A3%E8%B0%83.png)

## 5.2 调幅信号的分析

![5.2 调幅信号的分析](https://gitee.com/murphyhou/picgo/raw/master/CEC/5.2%20%E8%B0%83%E5%B9%85%E4%BF%A1%E5%8F%B7%E7%9A%84%E5%88%86%E6%9E%90.png)

### 5.2.1 普通调幅波

#### 调幅波的表达式

![image-20211114145422863](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211114145422863.png)

![image-20211203154930691](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211203154930691.png)



![image-20211113230535442](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211113230535442.png)

![image-20211114150501235](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211114150501235.png)



#### 调幅波的频谱

![image-20211114152207017](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211114152207017.png)

![image-20211114152223582](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211114152223582.png)

#### 调幅波的功率

![image-20211114153355502](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211114153355502.png)

### 5.2.2 抑制载波双边带调幅（DSB）

由于载波不携带信息，因此为了节省发射功率，可以只发送含有信息的上下两个边带，而不发送载波；

可将调制信号和载波信号直接加到乘法器或者平衡调幅器电路得到；

![image-20211114155420246](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211114155420246.png)

![image-20211114154901811](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211114154901811.png)

相位发生180°突变的原因是，调制信号的由正变成负或者说由负变成正；

对于正弦信号而言，系数变为原来的相反数，等效与加了一个180°的相位；

特点:

- DSB信号的幅值仍然随调制信号而变化，但与普通调制不同的是，DSB的包络不再反映调制信号的形状，仍保持调幅波频谱搬移的特征
- 在调制信号的正负半周，载波的相位反相；
- 信号仍然集中在载频ω_c附近，所占频带B=2*F_max



### 5.2.3 抑制载波单边带调幅(SSB)

- 减小了发射功率
- 减小了频带宽度



获得单边带的方法

- 滤波法
- 相移法

![image-20211114161159957](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211114161159957.png)



![113645865](https://gitee.com/murphyhou/picgo/raw/master/CEC/113645865.jpg)

## 5.3 调幅波产生的原理的理论分析

![image-20211114162048640](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211114162048640.png)



### 幂级数分析法（泰勒展开）

![image-20211203163137776](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211203163137776.png)

### 线性时变分析法

---

### 指数函数分析法

---

### 开关函数分析法

![image-20211203163150671](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211203163150671.png)





## 5.4 普通调幅波产生电路

![5.3 普通调幅波的产生电路](https://gitee.com/murphyhou/picgo/raw/master/CEC/5.3%20%E6%99%AE%E9%80%9A%E8%B0%83%E5%B9%85%E6%B3%A2%E7%9A%84%E4%BA%A7%E7%94%9F%E7%94%B5%E8%B7%AF.png)

![5.4 普通调幅波的解调电路](https://gitee.com/murphyhou/picgo/raw/master/CEC/5.4%20%E6%99%AE%E9%80%9A%E8%B0%83%E5%B9%85%E6%B3%A2%E7%9A%84%E8%A7%A3%E8%B0%83%E7%94%B5%E8%B7%AF.png)

![image-20211114162933771](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211114162933771.png)

![image-20211114162957234](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211114162957234.png)



![image-20211114163053057](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211114163053057.png)

![image-20211114163442288](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211114163442288.png)



![image-20211203161147505](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211203161147505.png)





![MD_2022-01-14_20-58-26](https://gitee.com/murphyhou/picgo/raw/master/CEC/MD_2022-01-14_20-58-26.png)



# 第六章 角度调制与解调



## 6.2 角度调制信号分析

![image-20211205184659352](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211205184659352.png)

### 调幅推导

![image-20211213194014046](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211213194014046.png)

### 调频推导（角度调制）

![image-20211205184746597](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211205184746597.png)

### 调相推导（角度调制）

![image-20211205184804574](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211205184804574.png)

![MS_2022-01-14_21-19-24](https://gitee.com/murphyhou/picgo/raw/master/CEC/MS_2022-01-14_21-19-24.png)

## 6.3 调频信号的产生



## 6.4 调频电路

### 直接调频电路

![image-20211213214052716](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211213214052716.png)

![image-20211213214110648](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211213214110648.png)

![image-20211213214124187](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211213214124187.png)

![MS_2022-01-14_20-51-50](https://gitee.com/murphyhou/picgo/raw/master/CEC/MS_2022-01-14_20-51-50.png)

![image-20211213213838548](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211213213838548.png)

![image-20211213213851813](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211213213851813.png)

高频电路部分，工作在谐振频率w_c频率处

### 间接调频

![image-20211213221429473](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211213221429473.png)

![faabrwvgeth](https://gitee.com/murphyhou/picgo/raw/master/CEC/faabrwvgeth.jpg)



<img src="https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211213222143670.png" alt="image-20211213222143670" style="zoom:200%;" />





## 6.5 调频波的解调

### 鉴频

#### 直接鉴频

![image-20211213222649985](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211213222649985.png)

#### 间接鉴频

![image-20211213230211347](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211213230211347.png)

![image-20211213230225517](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211213230225517.png)

![image-20211213230241571](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211213230241571.png)

---

---





### 鉴相

相位鉴频器：LC失谐

![image-20211213223112508](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211213223112508.png)

#### 乘积鉴相

![image-20211213225921699](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211213225921699.png)

![image-20211213225940985](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211213225940985.png)

![image-20211213230049346](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211213230049346.png)

#### 叠加鉴相

![image-20211213230107462](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20211213230107462.png)

---

---

# 第七章 变频器

![image-20220114221448695](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220114221448695.png)

![image-20220114221844995](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220114221844995.png)

 

![image-20220114222219113](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220114222219113.png)

![image-20220114222647124](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220114222647124.png) 

![image-20220114222840694](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220114222840694.png)

变频和混频的区别：本振是否由单独的电路产生

本振由非线性元件产生——变频器

本振由单独的电路产生——混频器

实际情况不用区分两者，认为相同就行

![image-20220114223135336](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220114223135336.png)

 

![image-20220114223420769](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220114223420769.png)

![image-20220114223440058](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220114223440058.png)

![image-20220114223725558](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220114223725558.png)

变频器在频域中起加法器和减法器的作用

## 7.4 晶体管变频电路

共射电路——用于频率较低

共基电路——频率较高



## 7.6 环形混频器





## 7.9 变频干扰

### 7.9.1 信号与本振的自身组合频率干扰

### 7.9.2 外来干扰和本振频率产生的副波道干扰

1. 中频干扰
2. 镜频干扰
3. 组合副波道干扰



### 7.9.3 交调和互调干扰

1. 交调干扰
1. 互调干扰





 







# 第八章 锁相环

![MS_2022-01-14_22-48-08](https://gitee.com/murphyhou/picgo/raw/master/CEC/MS_2022-01-14_22-48-08.png)

![image-20220114224947240](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220114224947240.png)

 ![MS_2022-01-14_22-58-24](https://gitee.com/murphyhou/picgo/raw/master/CEC/MS_2022-01-14_22-58-24.png)

![MS_2022-01-14_22-58-31](https://gitee.com/murphyhou/picgo/raw/master/CEC/MS_2022-01-14_22-58-31.png)
