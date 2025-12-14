# 均值不等式

## 一、引言
均值不等式是初等数学中最基本、最重要的一组不等式，它揭示了算术平均、几何平均、调和平均以及平方平均之间的大小关系。

## 二、二元均值不等式

### 定理1（基本形式）
对于任意两个正实数 \( a, b \)，有：
$$
\frac{a+b}{2} \geq \sqrt{ab} \geq \frac{2}{\frac{1}{a}+\frac{1}{b}}
$$
等号成立当且仅当 \( a = b \)。

### 证明

此不等式证明方法颇多，这里进列举常见的几个，详见小蓝本第四册。
#### 方法1：代数证明
$$
\frac{a+b}{2} - \sqrt{ab} = \frac{(\sqrt{a}-\sqrt{b})^2}{2} \geq 0
$$
因此 \(\frac{a+b}{2} \geq \sqrt{ab}\)。

同理，由 \(\sqrt{ab} \geq \frac{2}{\frac{1}{a}+\frac{1}{b}}\) 等价于：
$$
\sqrt{ab}(\frac{1}{a}+\frac{1}{b}) \geq 2 \Leftrightarrow \sqrt{\frac{a}{b}} + \sqrt{\frac{b}{a}} \geq 2
$$
令 \( t = \sqrt{\frac{a}{b}} > 0 \)，则 \( t + \frac{1}{t} \geq 2 \)，显然成立。

#### 方法2：几何证明
构造以 \( a+b \) 为直径的半圆，利用相似三角形性质证明。

## 三、n元均值不等式

### 定理2（一般形式）
设 \( a_1, a_2, \dots, a_n > 0 \)，定义：
- 算术平均：\( A_n = \frac{a_1 + a_2 + \dots + a_n}{n} \)
- 几何平均：\( G_n = \sqrt[n]{a_1 a_2 \dots a_n} \)
- 调和平均：\( H_n = \frac{n}{\frac{1}{a_1} + \frac{1}{a_2} + \dots + \frac{1}{a_n}} \)

则有：
$$
A_n \geq G_n \geq H_n
$$
等号成立当且仅当 \( a_1 = a_2 = \dots = a_n \)。

### 证明（倒向归纳法）

#### 第一步：先证明 \( A_n \geq G_n \)

**引理**：若不等式对 \( n=2 \) 成立，且对某个 \( n \) 成立，则对 \( 2n \) 也成立。

由归纳假设，对 \( 2n \) 个数：
$$
\frac{a_1+\dots+a_{2n}}{2n} = \frac{1}{2}\left(\frac{a_1+\dots+a_n}{n} + \frac{a_{n+1}+\dots+a_{2n}}{n}\right)
\geq \sqrt{\frac{a_1+\dots+a_n}{n} \cdot \frac{a_{n+1}+\dots+a_{2n}}{n}}
$$
又由 \( n \) 元均值不等式：
$$
\frac{a_1+\dots+a_n}{n} \geq \sqrt[n]{a_1\dots a_n}, \quad \frac{a_{n+1}+\dots+a_{2n}}{n} \geq \sqrt[n]{a_{n+1}\dots a_{2n}}
$$
故：
$$
\frac{a_1+\dots+a_{2n}}{2n} \geq \sqrt[2n]{a_1\dots a_{2n}}
$$

**反向归纳**：若对 \( n \) 成立，则对 \( n-1 \) 也成立。

取 \( a_n = \frac{a_1+\dots+a_{n-1}}{n-1} \)，代入 \( n \) 元不等式即可得证。

#### 第二步：证明 \( G_n \geq H_n \)
对 \( \frac{1}{a_1}, \frac{1}{a_2}, \dots, \frac{1}{a_n} \) 应用 \( A_n \geq G_n \) 即得。

## 四、幂平均不等式

### 定义
设 \( a_1, a_2, \dots, a_n > 0 \)，定义 \( r \) 次幂平均：

$$
M_r = 
\begin{cases}
\left(\frac{a_1^r + a_2^r + \dots + a_n^r}{n}\right)^{1/r}, & r \neq 0 \\
\sqrt[n]{a_1 a_2 \dots a_n}, & r = 0
\end{cases}
$$

### 定理3（幂平均不等式）
若 \( r < s \)，则 \( M_r \leq M_s \)，等号成立当且仅当所有 \( a_i \) 相等。

### 证明思路
1. 先证明 \( M_r \) 是 \( r \) 的增函数
2. 利用凸函数性质（Jensen不等式）
3. 特殊情形：\( M_{-1} \leq M_0 \leq M_1 \leq M_2 \) 即：

$$
\frac{n}{\frac{1}{a_1}+\dots+\frac{1}{a_n}} \leq \sqrt[n]{a_1\dots a_n} \leq \frac{a_1+\dots+a_n}{n} \leq \sqrt{\frac{a_1^2+\dots+a_n^2}{n}}
$$

## 五、加强均值不等式

### 定理4（加权均值不等式）
设 \( a_i > 0 \), \( w_i > 0 \) (\( i=1,\dots,n \))，且 \( \sum_{i=1}^n w_i = 1 \)，则：
$$
\prod_{i=1}^n a_i^{w_i} \leq \sum_{i=1}^n w_i a_i
$$
等号成立当且仅当所有 \( a_i \) 相等。

### 证明
取对数后利用对数函数的凹性，或使用数学归纳法。