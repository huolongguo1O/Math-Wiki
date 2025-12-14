# Karamata不等式

## 一、引言

Karamata不等式，也称为主要化不等式（Majorization Inequality），是凸函数不等式的一个推广。由塞尔维亚数学家Jovan Karamata发现。它描述了如果一个向量优超于另一个向量，那么对于任意凸函数，前者的函数值之和不小于后者。

## 二、优超关系

### 定义1（优超）
设 $\mathbf{a} = (a_1, a_2, \dots, a_n)$ 和 $\mathbf{b} = (b_1, b_2, \dots, b_n)$ 是两个实数序列，且满足：
1. $a_1 \ge a_2 \ge \dots \ge a_n$，$b_1 \ge b_2 \ge \dots \ge b_n$；
2. $\sum_{i=1}^k a_i \ge \sum_{i=1}^k b_i$ 对 $k=1,2,\dots,n-1$；
3. $\sum_{i=1}^n a_i = \sum_{i=1}^n b_i$。
则称 $\mathbf{a}$ 优超于 $\mathbf{b}$，记作 $\mathbf{a} \succ \mathbf{b}$。

## 三、Karamata不等式

### 定理1（Karamata不等式）
设 $f: I \to \mathbb{R}$ 是一个凸函数，$\mathbf{a} = (a_1, a_2, \dots, a_n)$ 和 $\mathbf{b} = (b_1, b_2, \dots, b_n)$ 是两个序列，满足 $\mathbf{a} \succ \mathbf{b}$ 且所有分量都在 $I$ 中，则
$$
\sum_{i=1}^n f(a_i) \ge \sum_{i=1}^n f(b_i).
$$
如果 $f$ 是严格凸的，则等号成立当且仅当 $\mathbf{a} = \mathbf{b}$（即 $a_i = b_i$ 对所有 $i$）。

### 证明思路
1. 首先证明：若 $\mathbf{a} \succ \mathbf{b}$，则 $\mathbf{b}$ 可以由 $\mathbf{a}$ 通过一系列"Robin Hood"操作得到，即从较大的分量转移一部分到较小的分量，且保持排序。
2. 然后证明：每次这样的操作都会使 $\sum f(a_i)$ 减少（或不变），因为凸函数满足 $f(x) + f(y) \ge f(x-t) + f(y+t)$ 对 $x \ge y$ 和 $t \ge 0$ 成立。

**引理：** 设 $f$ 是凸函数，$x \ge y$，$t \ge 0$，则
$$
f(x) + f(y) \ge f(x-t) + f(y+t).
$$
**证明：** 令 $\lambda = \frac{t}{x-y+2t}$，则 $0 \le \lambda \le 1$，且
$$
x-t = \lambda x + (1-\lambda)(y+t), \quad y+t = (1-\lambda) y + \lambda (x-t).
$$
由凸性，
$$
f(x-t) \le \lambda f(x) + (1-\lambda) f(y+t), \quad f(y+t) \le (1-\lambda) f(y) + \lambda f(x-t).
$$
两式相加得 $f(x-t) + f(y+t) \le \lambda f(x) + (1-\lambda) f(y+t) + (1-\lambda) f(y) + \lambda f(x-t)$，整理即得 $f(x) + f(y) \ge f(x-t) + f(y+t)$。

## 四、应用

### 1. 证明其他不等式

由于许多常见的不等式都可以表示为优超关系，Karamata不等式可以统一证明它们。

#### 例：幂平均不等式
设 $x_1 \ge x_2 \ge \dots \ge x_n > 0$，令 $a_i = \ln x_i$，则对 $r < s$，有 $(a_1^r, a_2^r, \dots, a_n^r)$ 与 $(a_1^s, a_2^s, \dots, a_n^s)$ 满足某种优超关系，从而由 $f(x) = e^x$ 的凸性得到幂平均不等式。

## 五、练习题

1. 设 $x_i, y_i > 0$，且 $(x_1, \dots, x_n) \succ (y_1, \dots, y_n)$，证明：$\prod x_i \le \prod y_i$。（提示：取 $f(x) = -\ln x$）
2. 利用Karamata不等式证明：若 $a \ge b \ge c \ge 0$，且 $a+b+c=1$，则 $a^2+b^2+c^2 \ge \frac{1}{3}$。
3. 设 $a_1 \ge a_2 \ge \dots \ge a_n$，$b_1 \ge b_2 \ge \dots \ge b_n$，且 $\sum_{i=1}^k a_i \ge \sum_{i=1}^k b_i$ 对 $k=1,\dots,n$ 成立，证明：$\sum_{i=1}^n a_i^2 \ge \sum_{i=1}^n b_i^2$。