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

