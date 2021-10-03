## 第1章：n阶行列式

#### 1.2：行列式的性质

**性质1.1**，行列式与它的转置行列式相等

**性质1.2**，互换行列式的两行（列），行列式变号

**推论1.1**，如果行列式有两行（列）完全相同，则此行列式为零

**性质1.3**，
$$
\begin{vmatrix}
a_{11}	&	a_{12}	&	\cdots	&	a_{1n}	\\
\vdots	&	\vdots	&		&	\vdots	\\
ka_{i1}	&	ka_{i2}	&	\cdots	&	ka_{in}	\\
\vdots	&	\vdots	&		&	\vdots	\\
a_{n1}	&	a_{n2}	&	\cdots	&	a_{nn}	\\
\end{vmatrix}
=
k\begin{vmatrix}
a_{11}	&	a_{12}	&	\cdots	&	a_{1n}	\\
\vdots	&	\vdots	&		&	\vdots	\\
a_{i1}	&	a_{i2}	&	\cdots	&	a_{in}	\\
\vdots	&	\vdots	&		&	\vdots	\\
a_{n1}	&	a_{n2}	&	\cdots	&	a_{nn}	\\
\end{vmatrix}
$$
**推论1.2**，若行列式中有两行（列）元素成比例，则行列式等于零

**性质1.4**，
$$
\begin{align}
&
\begin{vmatrix}
a_{11}	&	a_{12}	&	\cdots	&	a_{1n}	\\
\vdots	&	\vdots	&		&	\vdots	\\
a_{i1}+a'_{i1}	&	a_{i2}+a'_{i2}	&	\cdots	&	a_{in}+a'_{in}	\\
\vdots	&	\vdots	&		&	\vdots	\\
a_{n1}	&	a_{n2}	&	\cdots	&	a_{nn}	\\
\end{vmatrix}	\\
=	&	
\begin{vmatrix}
a_{11}	&	a_{12}	&	\cdots	&	a_{1n}	\\
\vdots	&	\vdots	&		&	\vdots	\\
a_{i1}	&	a_{i2}	&	\cdots	&	a_{in}	\\
\vdots	&	\vdots	&		&	\vdots	\\
a_{n1}	&	a_{n2}	&	\cdots	&	a_{nn}	\\
\end{vmatrix}
+
\begin{vmatrix}
a_{11}	&	a_{12}	&	\cdots	&	a_{1n}	\\
\vdots	&	\vdots	&		&	\vdots	\\
a'_{i1}	&	a'_{i2}	&	\cdots	&	a'_{in}	\\
\vdots	&	\vdots	&		&	\vdots	\\
a_{n1}	&	a_{n2}	&	\cdots	&	a_{nn}	\\
\end{vmatrix}
\end{align}
$$
**性质1.5**，行列式某一行（列）的倍数加到另一行（列），行列式不变

#### 1.3：行列式的展开定理

余子式$M_{ij}$​​和代数余子式$A_{ij}$​​有$A_{ij} = (-1)^{i+j}M_{ij}$​；

范德蒙德（Vandermonde）行列式
$$
\begin{vmatrix}
1	&	1	&	\cdots	&	1	\\
x_1	&	x_2	&	\cdots	&	x_n	\\
x^2_1	&	x^2_2	&	\cdots	&	x^2_n	\\
\vdots	&	\vdots	&		&	\vdots	\\
x^n_1	&	x^n_2	&	\cdots	&	x^n_n	\\
\end{vmatrix}
=
\prod_{1\leq j<i\leq n}(x_i - x_j)
$$
**定理1.3**，行列式$D$的任一行（列）元素与另一行（列）对应元素的代数余子式成绩之和为零

#### 1.4：Cramer法则

设方程组
$$
\left\{
\begin{array}{c}
a_{11}x_1 + a_{12}x_2 + \cdots + a_{1n}x_n = b_1	\\
a_{21}x_1 + a_{22}x_2 + \cdots + a_{2n}x_n = b_2	\\
\vdots	\\
a_{n1}x_1 + a_{n2}x_2 + \cdots a_{nn}x_n = b_n	\\
\end{array}
\right.
$$
记
$$
D = 
\begin{vmatrix}
a_{11}	&	a_{12}	&	\cdots	&	a_{1n}	\\
\vdots	&	\vdots	&		&	\vdots	\\
a_{i1}	&	a_{i2}	&	\cdots	&	a_{in}	\\
\vdots	&	\vdots	&		&	\vdots	\\
a_{n1}	&	a_{n2}	&	\cdots	&	a_{nn}	\\
\end{vmatrix}
$$
则有
$$
x_1=\frac{D_1}{D},x_2=\frac{D_2}{D},\cdots,x_n=\frac{D_n}{D}
$$
其中，$D_j$为$D$的第$j$​列用$\vec{b}$替换得到
$$
D_j = 
\begin{vmatrix}
a_{11}	&	\cdots	&	a_{1,j-1}	&	b_1	&	a_{1,j+1}	&	\cdots	&	a_{1n}	\\
a_{21}	&	\cdots	&	a_{2,j-1}	&	b_2	&	a_{2,j+1}	&	\cdots	&	a_{2n}	\\
\vdots	&		&	\vdots	&	\vdots	&	\vdots	&	&	\vdots	\\
a_{n1}	&	\cdots	&	a_{n,j-1}	&	b_n	&	a_{n,j+1}	&	\cdots	&	a_{nn}	\\
\end{vmatrix}
$$

## 第2章：矩阵

#### 2.2：矩阵的运算

###### 2.2.1：矩阵的加法

$$
\begin{align}
&A+B=B+A	\\
&(A+B)+C=A+(B+C)	\\
&A+0_{m\times n}=A	\\
&A+(-A)=0_{m\times n}
\end{align}
$$

###### 2.2.2：数与矩阵相乘

$$
\begin{align}
&(kl)A=k(lA)	\\
&(k+l)A=kA+lA	\\
&k(A+B)=kA+kB	\\
&1A=A
\end{align}
$$

###### 2.2.3：矩阵与矩阵相乘

$$
\begin{align}
&(AB)C=A(BC)	\\
&A(B+C)=AB+AC,\quad (A+B)C=AC+BC	\\
&k(AB)=(kA)B=A(kB)	\\
&E_mA=AE_n=A	\\
&0_{p\times n}A=0_{p\times n},\quad A0_{n\times q}=0_{m\times q}
\end{align}
$$

矩阵乘法不满足交换律；

$AB=AC$​不能推出$B=C$​

$AB=0$​不能推出$A=0$​或$B=0$​；

###### 2.2.4：方阵的幂

$$
\begin{align}
&A^kA^l=A^{k+l}	\\
&(A^k)^l=A^{kl}	\\
\end{align}
$$

一般情况下，$(AB)^k=ABAB\cdots AB\neq A^kB^k$​（矩阵乘法不满足交换律）​

###### 2.2.5：方阵的行列式及行列式的乘法公式

$$
\begin{align}
&|kA|=k^n|A|	\\
&|AB|=|A||B|	\\
\end{align}
$$

###### 2.2.6：矩阵的转置

$$
\begin{align}
&(A')'=A	\\
&(A+B)'=A'+B'	\\
&(kA)'=kA'	\\
&(AB)'=B'A'	\\
&|A'|=|A|
\end{align}
$$

**定义2.7**，设$A=(a_{ij})$是复矩阵，用$\overline{a_{ij}}$表示$a_{ij}$的共轭复数，称$\overline{A}=(\overline{a_{ij}})$为$A$的共轭矩阵
$$
\begin{align}
&\overline{A+B}=\overline{A}+\overline{B}	\\
&\overline{kA}=\overline{k}+\overline{A}	\\
&\overline{AB}=\overline{A}\times\overline{B}	\\
&|\overline{A}|=\overline{|A|}
\end{align}
$$

#### 2.3：可逆矩阵

###### 2.3.1：逆矩阵的定义

若$k_1,k_2,\cdots,k_n$都不为零
$$
\begin{pmatrix}
k_1	&	&	&	\\
	&	k_2	&	\\
	&	&	\ddots	&		\\
	&	&	&	k_n
\end{pmatrix}^{-1}
=
\begin{pmatrix}
\frac{1}{k_1}	&	&	&		\\
	&	\frac{1}{k_2}	&		\\
	&	&	\ddots	&	\\
	&	&	&	\frac{1}{k_n}
\end{pmatrix}
$$
若$A$可逆，则$A^{-1}$也可逆，且$(A^{-1})^{-1}=A$；

若$A$可逆，$k\neq 0$，则$kA$可逆，且$(kA)^{-1}=\frac{1}{k}A^{-1}$；

若$A,B$是同阶可逆方阵，则$AB$可逆，且$(AB)^{-1}=B^{-1}A^{-1}$；

若$A$可逆，则$A'$可逆，且$(A')^{-1}=(A^{-1})'$；

###### 2.3.2：方阵A可逆的充分必要条件、用伴随矩阵求逆矩阵

设$n$阶方阵
$$
A = 
\begin{pmatrix}
a_{11}	&	a_{12}	&	\cdots	&	a_{1n}	\\
a_{21}	&	a_{22}	&	\cdots	&	a_{2n}	\\
\vdots	&	\vdots	&			&	\vdots	\\
a_{n1}	&	a_{n2}	&	\cdots	&	a_{nn}	\\
\end{pmatrix}
$$
将$|A|$中诸元$a_{ij}$求代数余子式$A_{ij}$，令$A^*=(A_{ji})$，即
$$
A^* = 
\begin{pmatrix}
A_{11}	&	A_{21}	&	\cdots	&	A_{n1}	\\
A_{12}	&	A_{22}	&	\cdots	&	A_{n2}	\\
\vdots	&	\vdots	&			&	\vdots	\\
A_{1n}	&	A_{2n}	&	\cdots	&	A_{nn}	\\
\end{pmatrix}
$$
注意，$A^*$第$i$行第$j$列元素为$A_{ji}$；

**引理2.1**，设$A$是数域$F$上的$n$阶方阵，则
$$
A^*A=AA^*=|A|E_n
$$
**定理2.2**，设$A$​是数域$F$​上的$n$​阶方阵，则$A$​可逆的充要条件是$|A|\neq 0$​​，此时，
$$
A^{-1}=\frac{1}{|A|}A^*
$$
对于可逆矩阵$A$
$$
\begin{align}
&(A^*)^{-1}=(A^{-1})^*	\\
&A^*=|A|A^{-1}	\\
&(kA)^*=k^{n-1}A^*	\\
&|A^*|=|A|^{n-1}
\end{align}
$$

#### 2.4：矩阵的初等变换

###### 2.4.1：矩阵初等变换的概念

**定义2.9**，下面三种变换称为矩阵的初等行变换

（1）对调两行；

（2）以$k\neq0$乘某一行；

（3）把某一行的$k$倍加到另一行；

同理可得初等列变换，统称为初等变换。

如果$A$经过有限次初等变换得到$B$，则称$A$与$B$​等价；

###### 2.4.2：矩阵在初等变换下的化简

称矩阵$A$为行阶梯形矩阵，如果$A$满足

（1）若$A$有零行，则零行全部位于非零行的下方；

（2）各个非零行的左起第一个非零元的列号，从上往下递增；

称$A$为最简形矩阵，如果

（1）$A$是行阶梯形矩阵；

（2）$A$的非零行的左起第一个非零元都是$1$，并且这些$1$是他们所在列的唯一非零元

任意矩阵$A$​都可经过初等变换化成标准型
$$
A \overset{初等变换}{\longrightarrow}
\begin{pmatrix}
E_r	&	0	\\
0	&	0
\end{pmatrix}
$$
（1）任一矩阵$A$都可经初等行变换得到行阶梯形矩阵；

（2）任一矩阵$A$都可经初等行变换得到行最简形；

（3）任一矩阵$A$都可经初等变换得到标准型

#### 2.5：矩阵的秩

###### 2.5.1：矩阵的秩的概念

**定义2.10**，矩阵$A$的非零子式的最高阶数叫做矩阵$A$的秩，记为$R(A)$；

（1）$0\leq R(A) \leq min\{m,n\}$；

（2）$R(A')=R(A)$；

（3）$R(kA)=\begin{cases}0,&k=0\\ R(A),&k\neq0\end{cases}$​

（4）$R(A_1)\leq R(A)$，$A_1$为$A$​的任意一个子矩阵

（5）若$A$可逆，则$r(AB)=r(B);r(BA)=r(B)$

**定理2.3**，矩阵经初等变换后，其秩不变。

该定理表明，$R(A)=r$的充要条件是$A \overset{初等变换}{\longrightarrow}
\begin{pmatrix}
E_r	&	0	\\
0	&	0
\end{pmatrix}$​

###### 2.5.2：求矩阵秩的方法

（1）$n$​​阶方阵$A$​​的秩$R(A)=n\Longleftrightarrow A\overset{初}{\longrightarrow}E_n$​；

（2）$m\times n$​​矩阵$A$​​的秩是列满秩阵$\Longleftrightarrow A\overset{初}{\longrightarrow} \begin{pmatrix}E_n\\0\end{pmatrix}$​​

（3）$m\times n$​​​​矩阵$A$​​​​的秩是行满秩阵$\Longleftrightarrow A\overset{初}{\longrightarrow} \begin{pmatrix}E_m&0\end{pmatrix}$​​​​

#### 2.6：初等矩阵

###### 2.6.1：初等矩阵的概念

（1）单位矩阵第$i,j$两行（列）对换，记为$E(i,j)$；

（2）以数$k\neq 0$​乘单位矩阵的第$i$行（列），记为$E(i(k))$​；

（3）以数$k$乘单位矩阵的第$j$行加到第$i$行，记为$E(i,j(k))$；​

###### 2.6.2：初等矩阵的概念

（1）初等矩阵都是可逆矩阵，且初等矩阵的逆也是初等矩阵，事实上
$$
\begin{align}
&E^{-1}(i,j)=E(i,j)	\\
&E^{-1}(i(k))=E(i(\frac{1}{k}))	\\
&E^{-1}(i,j(k))=E(i,j(-k))
\end{align}
$$
（2）初等矩阵的转置还是初等矩阵
$$
\begin{align}
&E'(i,j)=E(i,j)	\\
&E'(i(k))=E(i(k))	\\
&E'(i,j(k))=E(j,i(k))
\end{align}
$$
（3）设$m\times n$矩阵$A$

对$A$​实行一次初等行变换，等价于相应初等矩阵左乘$A$；​

对$A$​实行一次初等列变换，等价于相应初等矩阵右乘$A$​；

注意，以$E(i,j(k))$右乘矩阵$A$，其效果相当于把$A$的第$i$列乘$k$加到第$j$列

###### 2.6.3：矩阵等价的充要条件

**定理2.4**，矩阵$A$可逆的充要条件是存在有限个初等矩阵$P_1,P_2,\cdots,P_k$使得$A=P_1P_2\cdots P_k$

**推论2.1**，两个$m\times n$矩阵$A,B$等价的充要条件是存在$m$阶可逆矩阵$P$和$n$阶可逆矩阵$Q$，使得$PAQ=B$

**推论2.2**，设$A$​是$m\times n$​矩阵，$P$​是$m$​​阶可逆矩阵，$Q$​是$n$阶可逆矩阵，则有$R(PA)=R(AQ)=R(PAQ)=R(A)$。因为初等变换不影响矩阵的秩；

###### 2.6.4：初等变换法求可逆矩阵的逆矩阵

对矩阵$\left( \begin{array}{c|c}A&E\end{array}\right)$​使用初等行变换，当其中的$A$化成$E$，$E$就化成了$A^{-1}$

#### 2.7：分块矩阵的概念及其运算

###### 2.7.2：分块矩阵的运算

**分块矩阵的行列式**
$$
\begin{align}
\begin{vmatrix}
A_{11}	&	A_{12}	&	\cdots	&	A_{1n}	\\
0	&	A_{22}	&	\cdots	&	A_{2n}	\\
\vdots	&	\vdots	&			&	\vdots	\\
0	&	0	&	\cdots	&	A_{nn}	\\
\end{vmatrix}
=
|A_{11}||A_{21}|\cdots|A_{nn}|	\\

\begin{vmatrix}
A_{11}	&	0	&	\cdots	&	0	\\
A_{21}	&	A_{22}	&	\cdots	&	0	\\
\vdots	&	\vdots	&			&	\vdots	\\
A_{n1}	&	A_{n2}	&	\cdots	&	A_{nn}	\\
\end{vmatrix}
=
|A_{11}||A_{21}|\cdots|A_{nn}|	\\
\end{align}
$$
**分块矩阵的逆矩阵**
$$
\begin{align}
\begin{pmatrix}
A_{1}	&		&		&		\\
	&	A_{2}	&		&		\\
	&		&	\ddots	&		\\
	&		&		&	A_{n}	\\
\end{pmatrix}^{-1}
=
\begin{pmatrix}
A^{-1}_{1}	&		&		&		\\
	&	A^{-1}_{2}	&		&		\\
	&		&	\ddots	&		\\
	&		&		&	A^{-1}_{n}	\\
\end{pmatrix}	\\

\begin{pmatrix}
	&		&		&	A_1	\\
	&		&	A_2	&		\\
	&	\cdots	&		&		\\
A_{n}	&		&		&		\\
\end{pmatrix}^{-1}
=
\begin{pmatrix}
	&		&		&	A^{-1}_n	\\
	&		&	A^{-1}_{n-1}	&		\\
	&	\cdots	&		&		\\
A^{-1}_{1}	&		&		&		\\
\end{pmatrix}	\\
\end{align}
$$

#### 2.8：分块矩阵的初等变换

###### 2.8.2：利用分块矩阵的初等变换计算矩阵的秩

（1）$R\begin{pmatrix}A&0\\0&B\end{pmatrix}=R(A)+R(B)$；

（2）$R\begin{pmatrix}A&C\\0&B\end{pmatrix}\geq R(A)+R(B)$​；

（3）$R(A|B)\leq R(A)+R(B)$；

（4）$R(A+B)\leq R(A)+R(B)$；

（5）$R(AB)\leq min\{R(A),R(B)\}$；

（6）$A$为$m\times n$矩阵，$B$为$n\times p$矩阵，则
$$
R(AB)\geq R(A)+R(B)-n
$$
特别地，当$AB=0$，此时$R(A)+R(B)\leq n$

## 第3章：几何向量

#### 3.2：几何向量的数量积、向量积和混合积

###### 3.2.3：几何向量的向量积

**定义3.3**，若$\vec{a},\vec{b}$不平行，则

（1）$|\vec{a}\times\vec{b}|=|\vec{a}||\vec{b}|\sin{\theta},\theta=<\vec{a},\vec{b}>$

（2）$\vec{a}\times\vec{b}\bot \vec{a},\vec{a}\times\vec{b}\bot\vec{b}$​

（3）向量$\vec{a},\vec{b},\vec{a}\times\vec{b}$构成右手系

几何向量的向量积的性质

（1）$\vec{a}\times\vec{b}=-\vec{b}\times\vec{a}$；

（2）$(k\vec{a})\times\vec{b}=k(\vec{a}\times\vec{b})=\vec{a}\times(k\vec{b})$​；

（3）
$$
\begin{align}
&(\vec{a}+\vec{b})\times{\vec{c}}=(\vec{a}\times\vec{c})+(\vec{b}\times\vec{c})	\\
&\vec{a}\times(\vec{b}+\vec{c})=(\vec{a}\times\vec{b})+(\vec{a}\times\vec{c})	\\
\end{align}
$$

###### 3.2.4：几何向量的混合积

**定义3.4**，$[\vec{a}\vec{b}\vec{c}]=(\vec{a}\times\vec{b})\cdot \vec{c}$

###### 3.2.6：几何向量的坐标运算

$$
\begin{align}
&
\vec{a}\times\vec{b}=
\begin{vmatrix}
\vec{i}	&	\vec{j}	&	\vec{k}	\\
a_x	&	a_y	&	a_z	\\
b_x	&	b_y	&	b_z	\\
\end{vmatrix}	\\
&
[\vec{a}\vec{b}\vec{c}]=
\begin{vmatrix}
a_x	&	a_y	&	a_z	\\
b_x	&	b_y	&	b_z	\\
c_x	&	c_y	&	c_z	\\
\end{vmatrix}	\\
\end{align}
$$

#### 3.3：空间中的平面与直线

###### 3.3.1：空间中平面的方程

**点法式方程**

设平面$\pi$过点$M_0(x_0,y_0,z_0)$，垂直于$\vec{n}=(A,B,C)$，则平面的点法式方程为$A(x-x_0)+B(y-y_0)+C(z-z_0)=0$​；

**三点式方程**

设平面$\pi$过点$M_1(x_1,y_1,z_1),M_2(x_2,y_2,z_2),M_3(x_3,y_3,z_3)$

则有
$$
\begin{vmatrix}
x-x_1	&	y-y1	&	z-z_1	\\
x_2-x_1	&	y_2-y_1	&	z_2-z_1	\\
x_3-x_1	&	y_3-y_1	&	z_3-z_1	\\
\end{vmatrix}=0
$$
**截距式方程**

设平面$\pi$与坐标轴分别交于$P(a,0,0),\quad Q(0,b,0),\quad R(0,0,c)$

则有
$$
\frac{x}{a}+\frac{y}{b}+\frac{z}{c}=1
$$

###### 3.3.2：空间中直线的方程

**标准方程**

直线$L$过点$M_0(x_0,y_0,z_0)$，且有方向向量$\vec{s}=(m,n,p)$

则有
$$
\frac{x-x_0}{m}=\frac{y-y_0}{n}=\frac{z-z_0}{p}
$$
**二点式方程**

直线$L$过点$M_0(x_0,y_0,z_0),\quad M_1(x_1,y_1,z_1)$

则有
$$
\frac{x-x_0}{x_1-x_0}=\frac{y-y_0}{y_1-y_0}=\frac{z-z_0}{z_1-z_0}
$$

###### 3.3.3：位置关系

**平面的位置关系**
$$
\begin{align}
&\pi_1:A_1x+B_1y+C_1z+D_1=0	\\
&\pi_2:A_2x+B_2y+C_2z+D_2=0
\end{align}
$$
当两平面重合时，有
$$
\frac{A_1}{A_2}=\frac{B_1}{B_2}=\frac{C_1}{C_2}=\frac{D_1}{D_2}
$$
当两平面平行时，有
$$
\frac{A_1}{A_2}=\frac{B_1}{B_2}=\frac{C_1}{C_2}\neq\frac{D_1}{D_2}
$$
且设两平面夹角为$\varphi$​，则有
$$
\cos{\varphi}=\frac{|A_1A_2+B_1B_2+C_1C_2|}{\sqrt{A_1^2+B_1^2+C_1^2}\sqrt{A_2^2+B_2^2+C_2^2}}
$$
**直线的位置关系**
$$
\begin{align}
&L_1:\frac{x-x_1}{m_1}=\frac{y-y_1}{n_1}=\frac{z-z_1}{p_1}	\\
&L_2:\frac{x-x_2}{m_2}=\frac{y-y_2}{n_2}=\frac{z-z_2}{p_2}	\\
\end{align}
$$
重合和平行同平面关系类似；

两直线交于一点的充要条件是是混合积$[\vec{s_1}\vec{s_2}\overrightarrow{M_1M_2}]=0$且$\vec{s_1},\vec{s_2}$不平行；

两直线异面的充要条件是混合积$[\vec{s_1}\vec{s_2}\overrightarrow{M_1M_2}]\neq0$

夹角计算同平面类似

###### 3.3.4：距离

**点到平面的距离**

$M_0(x_0,y_0,z_0),\quad \pi:Ax+By+Cz+D=0$

则有
$$
d=\frac{|Ax_0+By_0+Cz_0+D|}{\sqrt{A^2+B^2+C^2}}
$$
**点到直线的距离**

设$L:\frac{x-x_0}{m}=\frac{y-y_0}{n}=\frac{z-z_0}{p}$过点$M_0(x_0,y_0,z_0)$，直线外一点$M_1(x_1,y_1,z_1)$

则有
$$
d=\frac{|\vec{s}\times\overrightarrow{M_0M_1}|}{|\vec{s}|}
$$

## 第4章：n维向量

#### 4.2：向量组线性相关与线性无关

**定义4.5**，设有$n$维向量组$\alpha_1,\alpha_2,\cdots,\alpha_m$，若存在一组不全为零的数$k_1,k_2,\cdots,k_m$，使得
$$
k_1\alpha_1+k_2\alpha_2+\cdots+k_m\alpha_m=0
$$
则该向量组线性相关，否则，该向量组线性无关；

###### 4.2.3：线性相关的判定

**矩阵判别法**

设有$n\times m$矩阵$A$，分为$m$个列向量，这些列向量线性无关的充要条件是$R(A)=m$；

这些列向量线性相关的充要条件是$R(A)<m$；

**推论4.1**

设
$$
\alpha_i=
\begin{pmatrix}
a_{1i}	&	a_{2i}	&	\cdots	&	a_{ri}
\end{pmatrix}^T	\\
\beta_i=
\begin{pmatrix}
a_{1i}	&	a_{2i}	&	\cdots	&	a_{ri}	&	a_{r+1,i}	&\cdots	&	a_{r+s,i}
\end{pmatrix}^T
$$
若$r$维向量组$\alpha_1,\alpha_2,\cdots,\alpha_m$​线性无关，则$r+s$​维向量组$\beta_1,\beta_2,\cdots,\beta_m$也线性无关；

**推论4.2**

设$\alpha_1,\alpha_2,\cdots,\alpha_m$是$m$个$n$维向量，若$m>n$，则该向量组线性相关

#### 4.3：向量组的秩

## 第5章：线性方程组

#### 5.1：线性方程组有解的充要条件

###### 5.1.2：非齐次线性方程组有解的充要条件

对于非齐次线性方程组$AX=\beta$​及其对应的齐次线性方程组$AX=O$

* 有解的充要条件是$R(A)=R(B)$​。即系数矩阵的秩等于增广矩阵的秩
* 齐次线性方程组的解集合$N(A)$是向量空间，维数是$n-R(A)$
* 有无穷多解的充要条件是$R(A)=R(B)<n$​
* 有唯一解的充要条件是$R(A)=R(B)=n$。

