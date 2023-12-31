---
title: 《通信原理》笔记
date: 2023-07-07T14:59:30.803Z
summary: 上海交通大学 《通信原理》课程不完全笔记
draft: false
featured: false
authors: []
tags: []
categories:
  - notes
image:
  filename: ""
  focal_point: ""
  preview_only: false
---
通信原理
===
11.14讲解期中考试，前三章可能要重新复习一下
# CH4
#### 斜率过载
习题4.16会出填空题
## 4.3 编码
### 常见二进制码
自然二进码：传统的二进制
折叠二进码：除了极性码（第一位）其他位对称
循环二进码：相邻码只有一位不同
### 逐次反馈比较法
通过正负判断$b_7$,比较样本值$I_s$和$I_w$
### 译码
给译码（分层）电平加上或减去$\delta_8$/2=量化电平，量化误差=$\delta_x$/2
### 均匀量化和非均匀量化的比较
- 非均匀量化编码位数少，因此设备简化
- 带宽有效性来说，码元数更小，带宽有效性更好

## 4.4 PCM通信系统（Pulse Code Modulation）
### 4.4.2 系统的传输指标
#### 1.传输速率（码元速率）
$R_B = L / T_s = Lf_s$
#### 2.（最小）传输带宽
- 矩形脉冲
- sinx/x脉冲

编码长度L增加，则信噪比增大，传输带宽B增大
### 4.4.3 PCM系统的噪声
两种噪声
$n_q,n_e$误码噪声和编码方式有关
#### 1.自然二进制码
误码信噪比：
- 均匀分布信号
- 均匀分布信号

#### 2.折叠二进制码
比自然二进制码多极性码的误码噪声
### 4.4.4 PCM时分复用(TDM)
帧：在一个Ts内，由所有各路信号的一个样本值所构成的二进制序列
时隙：每一路信号所占用的时间
难点：接收机中的分路器必须与发送端的取样开关保持严格同步

增量调制要掌握，差分编码调制只需要理解思路，不要求推导

#### PCM-30/32路数字复接的帧格式
复帧：很多个帧组成的更大的帧
- 帧同步时隙
- 信令时隙
- 话路时隙

#### 传输速率（基群速率）
#### PCM-24路数字复接
在每帧的末尾添加一位帧比特（F比特），用于区分各帧
### 4.5增量调制(DM)
#### 4.5.1 基本原理
优点：节省带通，实现简单，
缺点：要考虑量化间隔和采样频率的关系
#### 过载噪声
模拟信号变化率$|dx(t)/dt|_max<\delta f_s
正弦信号：临界过载输入电压有限制
信号频率$f$每增长一倍（每倍频程），过载电压将下降$6db$
### 4.5.2 量化噪声
e(t)在(-$\delta,\delta$)均匀分布，不是$\delta /2$
量化噪声功率谱密度$S_e(f)=\delta^2/3f_s$
量化噪声平均功率$N_q$
求信噪比时，信号功率用峰值功率
**需掌握：正弦信号的信噪比公式**
$(\frac{S}{N_q})_{dB}=30lgf_s-20lgf-10lgf_x-14(dB)$

### 4.5.3 改进型增量调制
了解即可
## 4.6 差分脉冲编码调制(DPCM)
了解即可
传递函数

## 总结
采样
量化 
编码

# CH5
$d_i$信息码
$a_i$传输码
获得同步信息根据跳变而来
数字通信系统原理
数字信号时判决检测过程
## 5.1 常用码型
传输码主要特征
### 5.1.1 基本码型
- 单（双）极性
- （不）归零码：占空比小于1的是归零码 缩写：(N)RZ
- 二（多）电平码
### 5.1.3 数字基带传输的常用码型
#### (1)差分码
编码：$a_k=d_k\oplus a_{k-1}$
译码：$\hat{d}_k =\hat{a}_k \oplus \hat{a}_{k-1}$
- 解决极性反转的问题
- 误码扩散，单极性码，有直流分量


#### (2)AMI(Alternate Mark Inversion)码
- 有前置码
- 无直流分量
- 有自检能力
- 连0时难以提取定时信息


#### (3) HDB3(High Density Bipolar-3 Zeros)码
- 连0个数不超过3个
- 有前置码
- 无直流分量
- 编译码复杂
- 误码扩散
- 误码自检

B是符合极性交替的传号码，V是破坏极性交替的传号码，相邻V符号的极性也满足极性交替规律（B码让任意两个相邻V符号之间非0符号数为奇数）
译码的时候，四位四位的看

#### (4)Manchester码（列相码）
了解即可
带宽大，利于提取定时分量，无直流分量
#### (5)Miller码
了解即可
用“00”和“11”的交替出现代表连“0”码

### 5.1.2 数字基带信号的功率谱密度
公式不需要记，希望离散谱小
**频谱特性要会画，pptCH5-30，离散谱+连续谱**
#### （1）二进制单极性波
#### （2）二进制双极性波
等概情况下，只有连续谱，没有离散谱
#### 关于位定时信息的提取
对等概的双极性脉冲，可将其变成单极性归零码
#### M进制随机基带脉冲序列的功率谱
了解即可，不考
连续谱很复杂，和前后码元相关。
### 常见码型的PSD
要掌握。
PSD是什么？
## 5.2 数据传输中的码间串扰(ISI)
总传输特性：$g(t)=g_T(t)\ast h_c(t)\ast h_R(t)$
$g_T(t)$波形设计（发送滤波器）
$h_c(t)$信道响应
$h_R(t)$接受滤波器

ISI原因：
- 有线传输信道带宽有限，从而使输出的码元波形在时域上扩展，对相邻码元的判决产生干扰
- 无线传输：多径传播

多径传播会造成窄带衰落和频率弥散，会产生频率选择性衰落

取样器输出=信息码+ISI+噪声

## 5.3 无ISI的带限信号设计－Nyquist第一准则
无码间串扰的时域条件
满足该条件的g(t)的波形不是唯一的
频域条件 注意f范围
Nyquist第一准则
### 5.3.1 最小带宽
$B_T<\frac{1}{2T}$
$B_T=\frac{1}{2T}$G(f)唯一，频带利用率最高
缺点：理想LPF不可实现，g(t)拖尾长，收敛速度慢，对定时误差要求高
$\frac{1}{2T}<B_T\leq \frac{1}{T}$G(f)关于f=0偶对称，G(f)滚降部分关于f=1/2T奇对称
实现角度：频带利用率下降，收敛速度快，易实现
### 5.3.2 升余弦谱
$\beta$过剩带宽：1/2T外的带宽
滚降特性
$\alpha =2T\beta$滚降系数
常用$\beta =1/2T$，出现更多零交点，方便减少ISI和定时。
带宽$B_T=$
频带利用率$$
### 补充
取样脉冲可以是矩形脉冲
二进制PAM信号无ISI的分析可以推广到M进制
## 5.4 部分响应信号－Nyquist第二准则
允许受控的ISI，保证频带利用率达到极限
### 5.4.1 双二进制系统
#### $b_k=a_k+a_{k-1}$
$b_k$时三电平序列
系统特性：带限余弦特性
- 对码元的ISI是由前一码元产生的（当前一码元确定时，该ISI可消除）
- 频带利用率最高
- G(f)物理可实现，单存在直流分量
- 译码时会产生误码扩散，可以预编码

#### 预编码
了解即可

### 5.4.2 修正双二进制系统
#### 1.$b_k=a_k-a_{k-2}$
$g_k$
最高的频带利用率
G(f)为正弦型，可实现，无直流分量
#### 2.预编码

### 5.4.3（一般的）部分响应系统
#### 1.相关编码
可用有限抽头的横向滤波器（TF）实现
频率响应$H_{TF}(f)$
抽样值电平数
### 最佳基带传输系统
流程
指标
波形
码型

## 5.5 时域均衡与其最佳准则
失真补偿
- 发端补偿
- 收发端补偿

### 频域均衡
#### 1.原理
使包括均衡器在内的整个系统的传输函数满足无失真传输的条件
#### 2.实现
线路均衡包括幅度均衡和相位均衡——校正传输线路引起的线性失真
用无源网络RLC或者有源网络（带反馈的云芳实现）
### 5.5.1 时域均衡器
#### 1.原理
使包括均衡器在内的整个系统的冲激响应满足无ISI的条件
#### 2.实现
横向滤波器（TF）
### 5.5.2 两种最佳准则
#### 1.最小峰值准则
忽略噪声，只考虑ISI
迫零算法
# 第8章
## 7.1 判决理论
最佳：误码率最小的接收准则
最大后验概率（Maximum A Posteriori, MAP）准则，与最小差错概率准则是等价的
PDF：概率密度函数（probability density function）
条件 PDF p(y/Hm)或它的任何单调函数通常称为似然函数
两个似然函数之比，称为似然比，记为$\lambda(y)$
先验概率之比，记$\lambda_0$，称为门限
似然比检验
哪个假设的似然函数大就选为该假设，称为最大似然准则下的检测
判决门限
虚警概率
漏警概率
## 7.2 确知信号的最佳接收
连续函数表示的似然函数
二进制信号相关接收机
相关接收的实现：
- 匹配滤波器
- 积分清洗接收

## 7.3 随相信号的最佳接收
正交接收机

## 7.4 准最佳接收