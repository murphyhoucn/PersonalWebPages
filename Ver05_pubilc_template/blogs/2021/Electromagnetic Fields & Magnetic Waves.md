# 绪论

![电磁学中的基本量](https://gitee.com/murphyhou/picgo/raw/master/EM/%E7%94%B5%E7%A3%81%E5%AD%A6%E4%B8%AD%E7%9A%84%E5%9F%BA%E6%9C%AC%E9%87%8F.png)

![1. 绪论](https://gitee.com/murphyhou/picgo/raw/master/EM/1.%20%E7%BB%AA%E8%AE%BA.png)

# 第一章 矢量分析

## 矢量加减法

---

---

## 矢量乘法

1标量与矢量的乘积

- 结果为矢量

2矢量与矢量的标量积（点乘）

- 结果为标量
- ![image-20211007180447503](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211007180447503.png)

3矢量与矢量的矢量积（叉乘）

- 结果为矢量
- 结果矢量的方向满足右手螺旋定则
- ![image-20211007181904006](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211007181904006.png)

4三矢量的乘积

- **标量三重积**
- ![image-20211007181919281](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211007181919281.png)
- **矢量三重积**
- ![image-20211007181936604](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211007181936604.png)

---

---

## 正交坐标系

### 直角坐标系

![image-20211023202905518](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211023202905518.png)

### 圆柱坐标系

![zhuzuobiao](https://gitee.com/murphyhou/picgo/raw/master/EM/zhuzuobiao.jpg)

### 球坐标系

![qiuzuobiao](https://gitee.com/murphyhou/picgo/raw/master/EM/qiuzuobiao.jpg)

### 坐标转换

![image-20211028173800846](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211028173800846.png)

![image-20211023203518366](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211023203518366.png)

---

---

## 矢量分析的数学基础

矢量场的散度唯一地确定场中任一点的通量源强度； 

场的旋度唯一地确定场中任一点的旋涡源强度.

从分量式上可以看出，散度取决于场分量的纵向变化率， 

而旋度取决于场的横向变化率； 

因而，散度和旋度完整地描述了场的分布特性。

```
• 梯度、散度或旋度都是微分运算，它们表示场在某点附近 的变化特性，场中各点的梯度、散度或旋度可能不同。

 • 梯度、散度及旋度描述的是场的点特性或称为微分特性。

 • 函数的连续性是可微的必要条件。因此在场量发生不连续 处，也就不存在前面定义的梯度、散度或旋度。
```

![2. 数学基础](https://gitee.com/murphyhou/picgo/raw/master/EM/2.%20%E6%95%B0%E5%AD%A6%E5%9F%BA%E7%A1%80.png)

---

---

## 标量场的等值面

![image-20211028203344951](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211028203344951.png)

---

---

## §1.0 哈密顿算子

### 哈密顿算子定义

性质：矢量性/微分性

![image-20211023205250358](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211023205250358.png)

![image-20220108085839928](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20220108085839928.png)

![image-20220108085903045](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20220108085903045.png)

![image-20220108090051818](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20220108090051818.png)

### 三种坐标系下散度计算公式

![image-20211023205336204](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211023205336204.png)

### 三种坐标系下旋度计算公式

![image-20211023205512112](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211023205512112.png)

### 含两点间距离的微分关系式

![image-20211028212351539](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211028212351539.png)

---

---

## §1.1 方向导数与梯度

### 方向导数定义—标量

![image-20211028203417644](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211028203417644.png)

![image-20211028203445399](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211028203445399.png)

<img src="https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211028181825761.png" alt="image-20211028181825761" style="zoom:150%;" />

### 梯度定义—矢量

标量场中某点梯度的大小为该点最大的方向导数， 其方向为该点所在等值面的法线方向。

梯度的方向就是等值面的法线方向

![image-20211028204042059](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211028204042059.png)

![image-20211028181920349](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211028181920349.png)

### 梯度的运算规则

![image-20211028204143782](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211028204143782.png)

---

---

## §1.2 通量与散度

矢线（场线）：在矢量场中，若一条曲线上每一点的切线方向与 场矢量在该点的方向重合，则该曲线称为矢线。

### 通量定义—标量

通量：如果在该矢量场中取一曲面S， 通过该曲面的矢线量称为通量。

![image-20211023204050022](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211023204050022.png)

![image-20211023204513566](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211023204513566.png)

![image-20211023204547206](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211023204547206.png)

### 散度定义—标量

通量反映了封闭面中源的总特性，但没有反映源的分布特性; 若要进一步描述源的分布特性，则要引入散度;

![image-20211023204942460](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211023204942460.png)

### 用哈密顿算子表示散度

![image-20211028171628316](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211028171628316.png)

### 散度的物理意义

散度是 矢量A 通过某点处单位体积的通量 （通量体密度）； 

它反映了 矢量A 在该点的通量源强度；

<img src="https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211023205204811.png" alt="image-20211023205204811" style="zoom: 67%;" />

![image-20211023205157973](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211023205157973.png)

### 散度的运算规则

![image-20211028170359525](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211028170359525.png)

### 散度定理

矢量场的散度代表其通量的体密度,因此从散度的定义出 发，散度的体积分等于穿过包围该体积封闭面的总通量

![image-20211028170424728](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211028170424728.png)

![image-20211028170446797](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211028170446797.png)

---

---

## §1.3 环量与旋度

不是所有的矢量场都由通量源激发。存在另一类不同于通量源的矢量源，它所激发的**矢量场的力线是闭合**的，**它对于任何闭合曲面的通量为零**。但在**场所定义的空间中闭合路径的积分不为零**。

### 环量定义—标量

![image-20211028182520858](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211028182520858.png)

### 环量密度—标量

<img src="https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211028183020351.png" alt="image-20211028183020351" style="zoom:150%;" />

![image-20211028195932542](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211028195932542.png)

### 旋度定义—矢量

矢量场的环流给出了矢量场与积分回路所围曲面内旋涡源 宏观联系。 

为了给出空间任意点矢量场与旋涡源的关系，引入 矢量场的旋度。

![image-20211028200117309](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211028200117309.png)

### 旋度的物理意义

![image-20211028200211651](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211028200211651.png)

### 旋度的计算式

![image-20211028200346789](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211028200346789.png)

### 哈密顿算子表示旋度

![image-20211028200406863](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211028200406863.png)

![image-20211028200421254](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211028200421254.png)

### 旋度的运算规则

![image-20211028200500907](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211028200500907.png)

### 静电场的是无旋场

静止点电荷产生的电场的旋度为0

![image-20211028201737832](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211028201737832.png)

---

---

## §1.4 斯托克斯定理

### 定义

![image-20211028201425556](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211028201425556.png)

### 物理意义

一个矢量场旋度的面积分等于该矢量沿此曲面周界的曲 线积分。

斯托克斯定理是闭合曲线积分与曲面积分之间的一个 变换关系式，在电磁理论中也有广泛的应用。

---

---

## §1.5 Green定理

### 两大定理

![image-20211028204300698](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211028204300698.png)

### Green定理的应用

- 将体积V中场的求解问题变换为边界S上场的求解问题。

- 已知其中一个场的分布，就可以用Green定理求解另一 场的分布特性。

---

---

## §1.6 场论重要公式

### 两个重要恒等式

梯无旋

旋无散

<img src="https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211028204937243.png" alt="image-20211028204937243" style="zoom:200%;" />

### 三个坐标系下的拉普拉斯算子

![image-20211028205000150](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211028205000150.png)

![image-20211028212501433](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211028212501433.png)

### 常用的矢量恒等式

![image-20211028205027039](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211028205027039.png)

---

---

## §1.7 亥姆霍兹定理

![image-20211028210149509](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211028210149509.png)

### 矢量场的惟一性定理

位于某一区域中的矢量场，当其散度、旋度以及边界 上场量的切向分量或法向分量给定后，则该区域中的矢 量场被惟一地确定。

已知散度和旋度代表产生矢量场的源，可见惟一性定 理表明，矢量场被其源及边界条件共同决定的。

---

---

## §1.8 矢量场按源分类

### 无旋场

<img src="https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211028210518584.png" alt="image-20211028210518584" style="zoom:200%;" />

### 无散场

<img src="https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211028210533779.png" alt="image-20211028210533779" style="zoom:200%;" />

### 无旋，无散场

<img src="https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211028210543512.png" alt="image-20211028210543512" style="zoom:200%;" />

### 有旋，有散场

<img src="https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211028210550203.png" alt="image-20211028210550203" style="zoom:200%;" />

---

---

---

---

---

# 第二章 电磁场基本方程

```
2.0 电荷、电流、电荷守恒定律
2.1 静态电磁场的基本定律
2.2 法拉第电磁感应定律和全电流定律
2.3 Maxwell方程组
2.4 电磁场的边界条件
2.5 坡印廷定理和坡印廷矢量
```

![image-20211028212835449](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211028212835449.png)

---

---

## §2.0 电荷、电流，电荷守恒定理

电荷是产生电场的源

电流是产生磁场的源

![电荷与电流](https://gitee.com/murphyhou/picgo/raw/master/EM/%E7%94%B5%E8%8D%B7%E4%B8%8E%E7%94%B5%E6%B5%81.png)

---

---

---

---

## §2.1 静态电磁场的基本定律和基本场矢量

```
• 库仑定律----- 电场强度
• 高斯定理------电通密度
• 比奥—沙伐定律-------磁通密度
• 磁通连续性原理-----安培环路定律-----磁场强度
```

### 库伦定律

![image-20211029201951045](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211029201951045.png)

---

### 电场强度

源点：场源所在位置

场点：场中任意空间位置

![image-20211029203002866](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211029203002866.png)

![电场类型](https://gitee.com/murphyhou/picgo/raw/master/EM/%E7%94%B5%E5%9C%BA%E7%B1%BB%E5%9E%8B.png)

---

### 真空中的高斯定理

![image-20211029210112164](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211029210112164.png)

---

### 电场强度的散度

![image-20211029210550383](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211029210550383.png)

---

### 电通密度

![image-20211029211320280](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211029211320280.png)

---

### 介质中的高斯定理

![image-20211029211333436](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211029211333436.png)

---

### 电通密度的散度

![image-20211029211430652](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211029211430652.png)

---

### 静电场常见问题

![静电场的常见问题](https://gitee.com/murphyhou/picgo/raw/master/EM/%E9%9D%99%E7%94%B5%E5%9C%BA%E7%9A%84%E5%B8%B8%E8%A7%81%E9%97%AE%E9%A2%98.png)

---

### 安培力定律

电流相互作用 力公式，称为安培力定律

![image-20211030145923231](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030145923231.png)

---

### 毕奥萨法尔定律

电流在其周围空间中产生磁场，描述磁场分布的基本物理量是**磁通密度 B（矢量）** ，单位为T（特斯拉）。

磁场的重要特征是对场中的电流磁场力作用，载流回路C_1对载流回路 C_2 的作用力是回路 C_1中的电流 I_1产生的磁场对回路 C_2中的电流 I_2的作用力。

![image-20211030152339567](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030152339567.png)

---

### 磁感应强度/磁通密度

![磁通密度](https://gitee.com/murphyhou/picgo/raw/master/EM/%E7%A3%81%E9%80%9A%E5%AF%86%E5%BA%A6.png)

![几种典型电流分布的磁感应强度](https://gitee.com/murphyhou/picgo/raw/master/EM/%E5%87%A0%E7%A7%8D%E5%85%B8%E5%9E%8B%E7%94%B5%E6%B5%81%E5%88%86%E5%B8%83%E7%9A%84%E7%A3%81%E6%84%9F%E5%BA%94%E5%BC%BA%E5%BA%A6.png)

![image-20211030153647451](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030153647451.png)

---

### 磁通连续性原理

因为自然界中并不存在任何单独的磁荷, 磁力线总是闭合的。

![image-20211030154251192](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030154251192.png)

---

### 磁场强度

![image-20211030160220426](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030160220426.png)

---

### 安培环路定理

![image-20211030160532859](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030160532859.png)

![image-20211030160241874](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030160241874.png)

![image-20211030161653036](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030161653036.png)

---

### 小结

![image-20211030162224008](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030162224008.png)

![image-20211030162852776](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030162852776.png)

---

---

## §2.2 法拉第电磁感应定律和全电流定律

```
• 电磁感应定律 —— 揭示时变磁场产生电场
• 位移电流 —— 揭示时变电场产生磁场
• 重要结论： 在时变情况下，电场与磁场相互激励，形成统一的电磁场。

2.2.1 电磁感应定律
2.2.2 位移电流和全电流定律
2.2.3 全电流连续性原理
```

### 法拉第电磁感定律

![image-20211030163915813](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030163915813.png)

![image-20211030164322868](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030164322868.png)

#### 引起回路中磁通变化的几种情况

![引起回路中磁通变化的几种情况](https://gitee.com/murphyhou/picgo/raw/master/EM/%E5%BC%95%E8%B5%B7%E5%9B%9E%E8%B7%AF%E4%B8%AD%E7%A3%81%E9%80%9A%E5%8F%98%E5%8C%96%E7%9A%84%E5%87%A0%E7%A7%8D%E6%83%85%E5%86%B5.png)

![image-20211030165732168](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030165732168.png)

### 位移电流于位移电流密度

![image-20211030170152296](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030170152296.png)

![image-20211030170517881](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030170517881.png)

![image-20211030170555953](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030170555953.png)

### 全电流连续性原理

![image-20211030170816398](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030170816398.png)

![image-20211030170858420](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030170858420.png)

![image-20211030171135109](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030171135109.png)

#### 传导电流与位移电流对比

![image-20211030171617563](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030171617563.png)

![image-20211030171628679](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030171628679.png)

---

---

## §2.3 麦克斯韦方程组⭐

[麦克斯韦方程组 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/123835582)

![image-20211021195815000](https://gitee.com/murphyhou/picgo/raw/master/learn/image-20211021195815000.png)

![image-20211030172530102](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030172530102.png)

全电流定律：磁场强度沿任意闭合曲线的环量，等于穿过以闭合曲线为周界的任意曲面的传导电流和位移电流之和；

电磁感应定律：电场强度沿任意闭合曲线的环量，等于穿过以闭合曲线为边界的任意曲面磁通量变化率的负值；

磁通连续性原理：穿过任意闭合曲面的磁感应强度的通量为0；

高斯定理：穿过任意闭合曲面的电位移的通量等于该闭合曲面所包围的自由电荷的代数和；

![image-20211030203138077](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030203138077.png)

![image-20211030203149283](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030203149283.png)

- 时变电场的激发源除了电荷以外，还有变化的磁场；而时变 磁场的激发源除了传导电流以外，还有变化的电场。电场和 磁场互为激发源，相互激发。
- 时变电磁场的电场和磁场不再相互独立，而是相互关联， 构成一个整体 —— 电磁场。电场和磁场分别是电磁场的两 个分量。
- 在离开辐射源（如天线）的无源空间中，电荷密度和电流密 度矢量为零，电场和磁场仍然可以相互激发，从而在空间形 成电磁振荡并传播，这就是电磁波。

### 本构关系

在有介质存在时，电场强度矢量和磁感应强度矢量 都与介质的特性有关，因此上述麦克斯韦方程组是不完 备的，还需要再补充描述介质性质的方程：

![image-20211030172809099](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030172809099.png)

### 波动方程

![image-20211030173008632](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030173008632.png)

![image-20211030173020672](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030173020672.png)

### 电磁场的位函数——洛伦兹规范

#### 矢量位函数

![image-20211030175539599](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030175539599.png)

#### 标量位函数

![image-20211030175601661](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030175601661.png)

#### 位函数的非齐次波动方程

![image-20211030203546162](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030203546162.png)

![image-20211030203614589](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030203614589.png)

### 泊松方程

![image-20211030202824868](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030202824868.png)

## §2.4 电磁场的边界条件

• 不同媒质的介电常数ε、磁导率μ、电导率σ不同，在分界面两侧的媒质参数有突变。 

• 边界上Maxwell方程组的微分失去意义 

• 从**积分形式的Maxwell方程组**出发推导边界两侧电磁场间的关系。

```
2.4.1 边界条件的一般表达式
2.4.2 两种常见的情况
```

### 边界条件的一般表达式

![image-20211030204118539](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030204118539.png)

---

### 电场和磁场切向和法向边界条件

![image-20211030204719454](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030204719454.png)

### 常见情形

#### 两种理想介质间的边界条件

![image-20211030205315843](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030205315843.png)

---

#### 理想介质与理想导体间的边界条件

![image-20211030205326976](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030205326976.png)

---

---

## §2.5 坡印廷定理和坡印廷矢量

```
⚫电磁场是具有能量的;
⚫时变电磁场中的能量守恒定律——坡印廷定理；
⚫坡印廷矢量是描述电磁场能量流动的物理量。
```

![image-20211030210217078](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030210217078.png)

### 坡印廷定理----表征电磁能量守恒关系的定理

![image-20211030210740593](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030210740593.png)

![image-20211030210751298](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030210751298.png)

### 坡印廷矢量（电磁能流密度矢量）

![image-20211030211046910](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030211046910.png)

### 场与路的一些对应关系

![image-20211030211132873](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030211132873.png)

## §2.6 惟一性定理

![image-20211030211431129](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030211431129.png)

## 总结

![image-20211030211506117](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211030211506117.png)

# 第三章 静电场及其边值问题的解法

![image-20211107170419954](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211107170419954.png)

静态场中的电场和磁场是彼此独立存在的。

静电场：第三章

恒定电场：第四章

恒定磁场：第四章

![image-20211113170525779](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113170525779.png)

```
一、静电场基本方程与电位方程
二、静电场中的介质
三、 静电场中的导体和电容
四．静电场的边界条件
五．静电场边值问题，惟一性定理
六、镜像法
七、分离变量法
```

## §3.1 静电场基本方程与电位方程

### 静电场的麦克斯韦方程组

![image-20211107172617518](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211107172617518.png)

### 静电场的无旋性

静电场中电场力作的功与路径无关, 只取决于始点和终点的位置； 

静电场是保守场, 也称位场；

### 电位

![image-20211107173350895](C:/Users/DELL/AppData/Roaming/Typora/typora-user-images/image-20211107173350895.png)

#### 电位参考点

![image-20211107173457448](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211107173457448.png)

#### 四种分布的电位表达式

![image-20211107173552128](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211107173552128.png)

#### 电位差U

![image-20211107173829189](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211107173829189.png)

### 电位方程——泊松方程与拉普拉斯方程

![image-20211107174134725](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211107174134725.png)

![image-20211112100207352](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112100207352.png)

### 电位的计算

![电位的计算](https://gitee.com/murphyhou/picgo/raw/master/EM/%E7%94%B5%E4%BD%8D%E7%9A%84%E8%AE%A1%E7%AE%97.png)

## §3.2 静电场中的介质

![image-20211112103145712](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112103145712.png)

![image-20211112103211475](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112103211475.png)

### 介质极化

![image-20211112103559654](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112103559654.png)

![image-20211112104054538](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112104054538.png)

### 极化强度

![image-20211112104214020](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112104214020.png)

![image-20211112104258553](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112104258553.png)

这类介质的极化强度与合成的电场强度的方向相同。 极化强度的某一坐标分量仅决定于相应的电场强度的坐标分量。 极化率与电场方向无关，这类介质称为各向同性介质。

介质的极化率与电场强度的方向有关，也就是极化特性与 电场强度方向有关，因此，这类介质称为各向异性介质。

![image-20211112104453482](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112104453482.png)

### 极化强度矢量与束缚电荷密度

![image-20211112104629429](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112104629429.png)

![image-20211112104639931](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112104639931.png)

### 高斯通量定理

#### 真空高斯定理

![image-20211112104923072](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112104923072.png)

#### 介质高斯定理

介质中的电通量密度（电位移矢量）的定义！！！

![image-20211112110304501](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112110304501.png)

![image-20211112105108812](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112105108812.png)

![image-20211112105122040](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112105122040.png)

![image-20211112105134211](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112105134211.png)

### 介质中高斯定理的应用

![image-20211112110544257](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112110544257.png)

![image-20211112110646088](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112110646088.png)

### 小结

#### 电磁场的基本方程与本构关系

![image-20211112163315649](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112163315649.png)

#### 场量

![image-20211112163450964](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112163450964.png)

#### 静电场中的两类基本问题

![image-20211112163705776](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112163705776.png)

## §3.3 静电场中的导体和电容

### 静电场中的导体——静电平衡

![image-20211112163911302](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112163911302.png)

![image-20211112164726977](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112164726977.png)

### 电容

电容的决定式

![image-20211112165447551](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112165447551.png)

电容的定义式：C=Q/U

![image-20211112164819718](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112164819718.png)

![image-20211112201919317](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112201919317.png)

![image-20211112201935602](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112201935602.png)

![image-20211112201950267](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112201950267.png)

```
电容是导体系统的一种基本属性，
是描述导体系统 储存电荷能力的物理量。
```

![image-20211112171426848](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112171426848.png)

```
孤立导体的电容
双导体的电容
多导体系统的分布电容
```

![image-20211112170910999](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112170910999.png)

### 电容计算的两种方法

![image-20211112171726394](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112171726394.png)

![image-20211112200551760](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112200551760.png)

## §3.4 静电场的边界条件

***转2.4 电磁场的边界条件***

### 场量的边界条件

![image-20211112202341412](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112202341412.png)

![image-20211112202624939](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112202624939.png)

![image-20211112203107180](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112203107180.png)

### 两种特殊的电场边界条件

#### 介质与导体间边界条件

![image-20211113105328107](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113105328107.png)

#### 两种介质间边界条件

![image-20211113110205940](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113110205940.png)

![image-20211113110221050](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113110221050.png)

### 电位φ满足的边界条件

![image-20211113110342034](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113110342034.png)

![image-20211113112201207](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113112201207.png)

![image-20211113114435906](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113114435906.png)

#### 介质与导体间的电位边界条件

![image-20211113114455038](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113114455038.png)

#### 介质与介质之间的电位边界条件

![image-20211113114512292](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113114512292.png)

**边界条件的重要性** 1. 构成边值问题必不可少的条件; 2. 判断不同媒质界面两侧场量的大小、方向及连续、突变

## §3.5 静电场边值问题，惟一性定理

```
一、静电场基本方程与电位方程
二、静电场中的介质
三、 静电场中的导体和电容
四．静电场的边界条件
五．静电场边值问题，惟一性定理
六．镜像法
七．分离变量法
```

![image-20211112212015897](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112212015897.png)

### 静电场边值问题及其分类

![image-20211112212210823](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112212210823.png)

![image-20211112212222736](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112212222736.png)

![image-20211112212238340](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112212238340.png)

### 边值问题的解法

![image-20211112212648119](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112212648119.png)

### 唯一性定理

![image-20211112212715704](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211112212715704.png)

## §3.6 镜像法

```
一．镜像法的基本原理
二．接地导体平面的镜像
三．点电荷对无限大介质平面的镜像
四．导体球面的镜像
五．导体圆柱面的镜像
六．线电流对无限大磁介质平面的镜像
```

### 镜像法的基本原理

非均匀感应电荷产生的电位很难求 解，可以用等效电荷的电位替代

所谓镜像法是将不均匀电荷分布的作用等效为点电荷 或线电荷的作用。

![image-20211113100843410](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113100843410.png)

![image-20211113101023703](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113101023703.png)

![image-20211113101905218](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113101905218.png)

### 接地导体平面的镜像

#### 点电荷对无限大接地导体平面的镜像

![image-20211113102506367](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113102506367.png)

![image-20211113103240360](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113103240360.png)

![image-20211113103545553](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113103545553.png)

#### 线电荷对无限大接地导体平面的镜像

![image-20211113143947632](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113143947632.png)

#### 点电荷对半无限大接地导体角域 (导体劈) 的镜像

![image-20211113144054432](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113144054432.png)

![image-20211113144136141](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113144136141.png)

![image-20211113144211584](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113144211584.png)

![image-20211113144302950](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113144302950.png)

### 点电荷对无限大介质平面的镜像

![image-20211113150130026](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113150130026.png)

![image-20211113150312323](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113150312323.png)

![image-20211113150344780](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113150344780.png)

### 导体球面的镜像

#### 接地导体球

![image-20211113155100047](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113155100047.png)

![image-20211113155256649](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113155256649.png)

![image-20211113151757430](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113151757430.png)

#### 导体球不接地、不带电荷

![image-20211113151823382](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113151823382.png)

![image-20211113151921860](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113151921860.png)

#### 导体球不接地、带电荷

![image-20211113151938225](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113151938225.png)

#### 接地导体球壳

![image-20211113160307469](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113160307469.png)

![image-20211113160327475](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113160327475.png)

### 导体圆柱面的镜像ppt 159

#### 线电荷对接地导体圆柱面的镜像

#### 平行圆柱导体的电轴

#### 半径不同的两平行圆柱导体问题

### 线电流对无限大磁介质平面的镜像（矢量位）

### 线电流对无限大磁介质平面的镜像（磁场强度）

### 镜像法 小结

![image-20211113161316255](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113161316255.png)

![image-20211113161415047](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113161415047.png)

## §3.7 分离变量法

![image-20211113161449821](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113161449821.png)

### 0.双曲函数

[双曲函数_百度百科 (baidu.com)](https://baike.baidu.com/item/双曲函数/8704306)

![image-20211113163125398](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113163125398.png)

![image-20211113163152889](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113163152889.png)

```
1. 分离变量法解题的基本步骤
2. 直角坐标系中的分离变量法
3. 圆柱坐标系中的分离变量法
4. 球坐标系中的分离变量法
5. 复变函数法
```

### 1. 分离变量法解题的基本步骤

![image-20211113162132408](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113162132408.png)

### 2. 直角坐标系中的分离变量法

#### 二维拉普拉斯方程

![image-20211113162155544](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113162155544.png)

![image-20211113162208994](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113162208994.png)

![image-20211113162223354](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113162223354.png)

![image-20211113162238219](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113162238219.png)

![image-20211113162254005](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113162254005.png)

#### 三维拉普拉斯方程

![image-20211113164652716](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113164652716.png)

![image-20211113164711143](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113164711143.png)

### 3. 圆柱坐标系中的分离变量法

![image-20211113164753029](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113164753029.png)

### 4. 球坐标系中的分离变量法

![image-20211113164820879](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113164820879.png)

### 5. 复变函数法

![image-20211113164858877](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113164858877.png)

# 第四章 恒定电场和恒定磁场

```
§4.1 恒定电场

§4.2 恒定磁场的基本方程和边界条件

§4.3 恒定磁场的矢量磁位

§4.4 电感Inductance
```

## §4.1 恒定电场

### 1. 恒定电场的基本方程 ⭐

![image-20211113171459132](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113171459132.png)

![image-20211113171749804](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211113171749804.png)

### 2. 恒定电场的边界条件

![image-20220115225219431](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115225219431.png)

![image-20220115225246330](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115225246330.png)

![image-20220115225251220](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115225251220.png)

![image-20220115225258622](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115225258622.png)







### 3. 静电比拟法

![image-20220115225209261](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115225209261.png)

![image-20220115225321844](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115225321844.png)

![image-20220115225327316](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115225327316.png)

## §4.2 恒定磁场的基本方程和边界条件

![image-20220115225351070](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115225351070.png)

![image-20220115225359342](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115225359342.png)











## §4.3 恒定磁场的矢量磁位

![image-20220115225453243](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115225453243.png)

![image-20220115225459232](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115225459232.png)

![image-20220115225509219](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115225509219.png)





## §4.4 电感Inductance

![image-20220115225522839](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115225522839.png)

![image-20220115225528702](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115225528702.png)

![image-20220115225532383](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115225532383.png)

![image-20220115225537311](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115225537311.png)

![image-20220115225541421](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115225541421.png)



![image-20220115225545132](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115225545132.png)



# 第五章 时变电磁场和平面电磁波

## §5.1 时谐电磁场的复数表示

![image-20211205162937027](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211205162937027.png)

![image-20211205162954483](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211205162954483.png)

![image-20211205163005230](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211205163005230.png)

## §5.2 复数形式Maxwell方程组

![image-20211205163116315](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211205163116315.png)

![image-20211205163621662](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211205163621662.png)

![image-20211205163648286](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211205163648286.png) 

![image-20211205163543134](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211205163543134.png)

## §5.3 复坡印廷矢量和复坡印廷定理

电磁场是具有能量的，时谐电磁场的能量在空间以电磁波形式传播

Poynting定理是时变电磁场中能量守恒定律的表达形式

![image-20211205171919922](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211205171919922.png)

![image-20211205172934251](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211205172934251.png)

## §5.4 理想介质中的平面波

![image-20211205175853218](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211205175853218.png)

### 均匀平面波满足一维波动方程

![image-20211205184247237](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211205184247237.png)

![image-20211212220519191](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211212220519191.png)

### 均匀平面波是横电磁波（TEM波）

![image-20211212221810798](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211212221810798.png)

![image-20211212221903605](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211212221903605.png)

![image-20211212221515813](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211212221515813.png)

### 波动方程的解

![image-20211212223852001](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211212223852001.png)

![image-20211212223914162](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211212223914162.png)

### 相位常数k

![image-20211212223629504](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211212223629504.png)

![image-20211212223653278](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211212223653278.png)

### 相速 v

![image-20211212223737222](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211212223737222.png)

### 介质的本质阻抗 η

![image-20211212223510695](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211212223510695.png)

## §5.5 导电介质中的平面波

![image-20220115232326569](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115232326569.png)

![image-20220115232407405](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115232407405.png)

### 复介电常数和复本质阻抗 

![image-20220115232548361](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115232548361.png)

### 相位常数和衰减系数 

![image-20220115232558326](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115232558326.png)

### 相速和色散现象 

![image-20220115232606654](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115232606654.png)

### 有耗媒质中电磁场表示 

![image-20220115232616032](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115232616032.png)

![image-20220115232623694](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115232623694.png)

### 有耗媒质中的坡印廷矢量

![image-20220115232631980](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115232631980.png)



### 趋肤效应和趋肤深度

![image-20220115233004769](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115233004769.png)

![image-20220115232642053](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115232642053.png)

![image-20220115232655844](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115232655844.png)

![image-20220115232703840](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115232703840.png)

![image-20220115232710784](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115232710784.png)



## §5.7 电磁波的极化

 ![image-20220115232055601](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115232055601.png)

### 极化的概念 

![image-20220115233154484](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115233154484.png)

![image-20220115233208237](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115233208237.png)

![image-20220115233224588](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115233224588.png)

### 线极化波  

![image-20220115233234040](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115233234040.png)





### 圆极化波 

![image-20220115233243205](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115233243205.png)

![image-20220115233250322](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115233250322.png)

![image-20220115233300384](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115233300384.png)

### 椭圆极化波 

![image-20220115233307644](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115233307644.png)

![image-20220115233315960](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115233315960.png)

### 极化波的分解

### 极化波的工程应用

![image-20220115233412119](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115233412119.png)













# 第六章 平面电磁波的反射和折射

![image-20211211170529332](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211211170529332.png)

平面波在边界上的反射及透射规律与媒质特性及边界形状有关。

仅讨论平面波在无限大的平面边界上的反射及透射特性

## §6.1  平面波对平面边界的垂直入射

入射波 (Incident Wave) 

反射波 (Reflected Wave) ---- 一部分能量被反射回来形成 

透射波 (Transmitted Wave) ---- 另一部分能量穿过边界形成

反射波与折射波的特性由分界面两侧媒质的参数确定。

### • 对理想导体的垂直入射

![image-20211212161626467](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211212161626467.png)

![image-20211212161641355](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211212161641355.png)

![image-20211212161655007](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211212161655007.png)

![image-20211212161723274](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211212161723274.png)

![image-20211212161815773](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211212161815773.png)

驻波

![image-20211212162303962](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211212162303962.png)

![image-20211212162316963](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211212162316963.png)

•空间各点的电场都随时间t按正弦规律变化，但是波腹和波节点的位置均固定不变。

•这种波与行波不同，它是驻立不动的，称之为驻波。 

•驻波就是波腹点和波节点固定不动的电磁波。

**磁场的波腹点是电场的波节点， 磁场的波节点是电场的波腹点。**

面电流

![image-20211212162458358](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211212162458358.png)

功率流密度

![image-20211212162932274](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211212162932274.png)

![image-20211212163002765](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211212163002765.png)

![image-20211212163108385](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211212163108385.png)

当均匀平面波垂直入射到理想导体表面时，在表面上发生全 反射，反射波与入射波的迭加在自由空间中形成驻波。

在理想导体表面上，电场为零，磁场为最大值。

![image-20211212163240126](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211212163240126.png)

![image-20211212163312227](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211212163312227.png)

YXR——PPT 6.1 P27例题   P31例题

### • 对理想介质的垂直入射

![image-20211212214859148](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211212214859148.png)

![image-20211212214916781](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211212214916781.png)

![image-20211212214928885](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211212214928885.png)

![image-20211212214936777](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211212214936777.png)

![image-20211212215313184](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211212215313184.png)

![image-20211212215736824](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211212215736824.png)

![image-20211212215806727](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211212215806727.png)

入射波能量、反射波能量和透射波能量间的关系——坡印廷矢量平均值

![image-20211212215941040](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211212215941040.png)

![image-20211212215950682](https://gitee.com/murphyhou/picgo/raw/master/EM/image-20211212215950682.png)

区域1中传输的合成场功率等于向区域2透射的功率

YXR_PPT_P53——例题

### • 对多层边界的垂直入射

PPT 58页

## §6.2  平面波对平面边界的斜入射

### 斜入射的概念 

![image-20220115233634212](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115233634212.png)

![image-20220115233641202](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115233641202.png)

![image-20220115233650466](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115233650466.png)

![image-20220115234341011](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115234341011.png)

![image-20220115234351315](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115234351315.png)









### 垂直极化波的斜入射

![image-20220115234401476](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115234401476.png)

![image-20220115234407183](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115234407183.png)

![image-20220115234412864](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115234412864.png)

![image-20220115234417762](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115234417762.png)

![image-20220115234425888](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115234425888.png)

![image-20220115234435648](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115234435648.png)

![image-20220115234442465](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115234442465.png)

![image-20220115234456158](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115234456158.png)

![image-20220115234502661](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115234502661.png)

![image-20220115234510130](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115234510130.png)

![image-20220115234517529](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115234517529.png)

![image-20220115234527346](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115234527346.png)





### 平行极化波的斜入射

![image-20220115234541775](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115234541775.png)

![image-20220115234547224](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115234547224.png)

![image-20220115234553207](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115234553207.png)

![image-20220115234601229](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115234601229.png)

![image-20220115234608655](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115234608655.png)

![image-20220115234617419](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115234617419.png)

![image-20220115234624647](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115234624647.png)

![image-20220115234630013](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115234630013.png)













## §6.3  全反射 全折射

### 全反射

![image-20220115234036598](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115234036598.png)

![image-20220115234053341](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115234053341.png)



![image-20220115234106066](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115234106066.png)









### 全折射

![image-20220115234113487](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115234113487.png)

![image-20220115234120337](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115234120337.png)

![image-20220115234130863](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115234130863.png)

![image-20220115234136186](https://gitee.com/murphyhou/picgo/raw/master/CEC/image-20220115234136186.png)
