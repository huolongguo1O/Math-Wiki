# 琴生不等式

## 一、引言

琴生不等式（Jensen's inequality）是凸函数理论中的一个基本不等式，由丹麦数学家约翰·琴生发现。它在概率论、信息论、统计学和不等式理论中有广泛应用。

## 二、凸函数定义

### 定义1（凸函数）
设 $f: I \to \mathbb{R}$ 是定义在区间 $I$ 上的函数。若对任意 $x, y \in I$ 和任意 $\lambda \in [0,1]$，有
$$
f(\lambda x + (1-\lambda) y) \le \lambda f(x) + (1-\lambda) f(y),
$$
则称 $f$ 是 $I$ 上的凸函数。若不等式严格成立（当 $x \neq y$ 且 $\lambda \in (0,1)$），则称 $f$ 是严格凸的。

若不等号反向，则称 $f$ 是凹函数。

### 等价条件
若 $f$ 二阶可导，则 $f$ 是凸函数的充要条件是 $f''(x) \ge 0$ 对所有 $x \in I$ 成立。

## 三、琴生不等式（离散形式）

### 定理1（琴生不等式）
设 $f: I \to \mathbb{R}$ 是凸函数，$x_1, x_2, \dots, x_n \in I$，$\lambda_1, \lambda_2, \dots, \lambda_n \ge 0$ 且 $\sum_{i=1}^n \lambda_i = 1$，则
$$
f\left( \sum_{i=1}^n \lambda_i x_i \right) \le \sum_{i=1}^n \lambda_i f(x_i).
$$
若 $f$ 是严格凸的，则等号成立当且仅当所有 $x_i$ 相等。

### 证明
用数学归纳法。

**基础步骤：** $n=2$ 时就是凸函数的定义。

**归纳假设：** 假设对 $n-1$ 成立，证明对 $n$ 成立。

令 $\Lambda = \sum_{i=1}^{n-1} \lambda_i$。若 $\Lambda = 0$，则 $\lambda_n = 1$，不等式显然成立。若 $\Lambda > 0$，则
$$
\sum_{i=1}^n \lambda_i x_i = \Lambda \left( \sum_{i=1}^{n-1} \frac{\lambda_i}{\Lambda} x_i \right) + \lambda_n x_n.
$$
由凸函数定义，
$$
f\left( \sum_{i=1}^n \lambda_i x_i \right) \le \Lambda f\left( \sum_{i=1}^{n-1} \frac{\lambda_i}{\Lambda} x_i \right) + \lambda_n f(x_n).
$$
对 $f\left( \sum_{i=1}^{n-1} \frac{\lambda_i}{\Lambda} x_i \right)$ 应用归纳假设（因为 $\sum_{i=1}^{n-1} \frac{\lambda_i}{\Lambda} = 1$），得
$$
f\left( \sum_{i=1}^{n-1} \frac{\lambda_i}{\Lambda} x_i \right) \le \sum_{i=1}^{n-1} \frac{\lambda_i}{\Lambda} f(x_i).
$$
代入得
$$
f\left( \sum_{i=1}^n \lambda_i x_i \right) \le \Lambda \sum_{i=1}^{n-1} \frac{\lambda_i}{\Lambda} f(x_i) + \lambda_n f(x_n) = \sum_{i=1}^n \lambda_i f(x_i).
$$

**等号成立条件：** 若 $f$ 严格凸，则 $n=2$ 时等号成立当且仅当 $x_1 = x_2$。归纳时，等号成立要求
1. $f\left( \sum_{i=1}^{n-1} \frac{\lambda_i}{\Lambda} x_i \right) = \sum_{i=1}^{n-1} \frac{\lambda_i}{\Lambda} f(x_i)$（由归纳假设，所有 $x_i$（$i=1,\dots,n-1$）相等）；
2. $f\left( \Lambda \left( \sum_{i=1}^{n-1} \frac{\lambda_i}{\Lambda} x_i \right) + \lambda_n x_n \right) = \Lambda f\left( \sum_{i=1}^{n-1} \frac{\lambda_i}{\Lambda} x_i \right) + \lambda_n f(x_n)$（由凸函数定义，要求 $\sum_{i=1}^{n-1} \frac{\lambda_i}{\Lambda} x_i = x_n$）。
因此所有 $x_i$ 相等。

## 四、应用

### 1. 证明均值不等式

取 $f(x) = -\ln x$（在 $(0,\infty)$ 上是凸函数，因为 $f''(x) = 1/x^2 > 0$）。对任意 $x_i > 0$，$\lambda_i \ge 0$ 且 $\sum \lambda_i = 1$，由琴生不等式：
$$
-\ln\left( \sum \lambda_i x_i \right) \le -\sum \lambda_i \ln x_i = -\ln\left( \prod x_i^{\lambda_i} \right).
$$
取指数得加权算术-几何平均不等式：
$$
\sum \lambda_i x_i \ge \prod x_i^{\lambda_i}.
$$
特别地，取 $\lambda_i = 1/n$ 得
$$
\frac{x_1 + \dots + x_n}{n} \ge \sqrt[n]{x_1 \dots x_n}.
$$

### 2. 证明幂平均不等式

设 $r < s$，考虑函数 $f(x) = x^{s/r}$（当 $r>0$ 时，若 $s/r > 1$，则 $f$ 在 $(0,\infty)$ 上是凸函数）。对任意 $x_i > 0$，由琴生不等式：
$$
\left( \frac{1}{n} \sum x_i^r \right)^{s/r} \le \frac{1}{n} \sum (x_i^r)^{s/r} = \frac{1}{n} \sum x_i^s.
$$
两边取 $1/s$ 次幂（注意 $s>0$）得 $M_r \le M_s$。

## 五、练习题

1. 利用琴生不等式证明：对于 $a_i>0$，$p>1$，有
   $$
   \left( \frac{1}{n} \sum a_i^p \right)^{1/p} \ge \frac{1}{n} \sum a_i.
   $$
2. 设 $f: \mathbb{R} \to \mathbb{R}$ 是凸函数，证明：对任意 $x, y, z$，有
   $$
   f(x)+f(y)+f(z)+3f\left(\frac{x+y+z}{3}\right) \ge 2\left[f\left(\frac{x+y}{2}\right)+f\left(\frac{y+z}{2}\right)+f\left(\frac{z+x}{2}\right)\right].
   $$
3. 设 $p_i > 0$，$\sum p_i = 1$，$a_i > 0$，证明：
   $$
   \prod_{i=1}^n a_i^{p_i} \le \sum_{i=1}^n p_i a_i.
   $$