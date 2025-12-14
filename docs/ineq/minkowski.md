# 闵可夫斯基不等式

## 一、引言

闵可夫斯基不等式是数学分析中的一个重要不等式，由德国数学家赫尔曼·闵可夫斯基提出。这个不等式是三角不等式在$L^p$空间中的推广，在泛函分析、概率论和调和分析等领域有广泛应用。

## 二、离散形式的闵可夫斯基不等式

### 定理1（离散形式）
设 $a_1, a_2, \dots, a_n$ 和 $b_1, b_2, \dots, b_n$ 是非负实数（或复数），$p \ge 1$，则
$$
\left( \sum_{i=1}^n (a_i + b_i)^p \right)^{1/p} \le \left( \sum_{i=1}^n a_i^p \right)^{1/p} + \left( \sum_{i=1}^n b_i^p \right)^{1/p}.
$$
等号成立当且仅当存在非负常数 $\lambda$（不全为零），使得对每个 $i$ 有 $a_i = \lambda b_i$（或者 $b_i = 0$ 对全体 $i$）。

### 证明

**情况1：** $p = 1$

当 $p=1$ 时，不等式化为：
$$
\sum_{i=1}^n (a_i + b_i) = \sum_{i=1}^n a_i + \sum_{i=1}^n b_i,
$$
显然成立，且等号恒成立。

**情况2：** $p > 1$

令 $q = \frac{p}{p-1}$，则 $\frac{1}{p} + \frac{1}{q} = 1$。考虑和式：
$$
S = \sum_{i=1}^n (a_i + b_i)^p.
$$
将其写为：
$$
S = \sum_{i=1}^n (a_i + b_i)(a_i + b_i)^{p-1} = \sum_{i=1}^n a_i (a_i + b_i)^{p-1} + \sum_{i=1}^n b_i (a_i + b_i)^{p-1}.
$$

对右端两个和式分别应用赫尔德不等式：

对于第一个和式：
$$
\sum_{i=1}^n a_i (a_i + b_i)^{p-1} \le \left( \sum_{i=1}^n a_i^p \right)^{1/p} \left( \sum_{i=1}^n ((a_i + b_i)^{p-1})^q \right)^{1/q} = \left( \sum_{i=1}^n a_i^p \right)^{1/p} \left( \sum_{i=1}^n (a_i + b_i)^p \right)^{1/q},
$$
其中用到了 $(p-1)q = p$。

同理，对于第二个和式：
$$
\sum_{i=1}^n b_i (a_i + b_i)^{p-1} \le \left( \sum_{i=1}^n b_i^p \right)^{1/p} \left( \sum_{i=1}^n (a_i + b_i)^p \right)^{1/q}.
$$

将两个不等式相加，得到：
$$
S \le \left[ \left( \sum_{i=1}^n a_i^p \right)^{1/p} + \left( \sum_{i=1}^n b_i^p \right)^{1/p} \right] \left( \sum_{i=1}^n (a_i + b_i)^p \right)^{1/q}.
$$

由于 $S = \sum_{i=1}^n (a_i + b_i)^p$，若 $S = 0$，则不等式显然成立；若 $S > 0$，两边同时除以 $\left( \sum_{i=1}^n (a_i + b_i)^p \right)^{1/q}$，并注意到 $1 - \frac{1}{q} = \frac{1}{p}$，即得
$$
\left( \sum_{i=1}^n (a_i + b_i)^p \right)^{1/p} \le \left( \sum_{i=1}^n a_i^p \right)^{1/p} + \left( \sum_{i=1}^n b_i^p \right)^{1/p}.
$$

**等号成立条件：** 由赫尔德不等式等号成立的条件，需要存在常数 $\lambda_1$ 和 $\lambda_2$，使得对于每个 $i$，
$$
a_i^p = \lambda_1 (a_i + b_i)^p \quad \text{且} \quad b_i^p = \lambda_2 (a_i + b_i)^p.
$$
若 $a_i + b_i > 0$，则 $a_i = \lambda_1^{1/p} (a_i + b_i)$，$b_i = \lambda_2^{1/p} (a_i + b_i)$，于是 $a_i$ 与 $b_i$ 成比例。若某个 $a_i + b_i = 0$，则 $a_i = b_i = 0$。因此，等号成立当且仅当序列 $\{a_i\}$ 和 $\{b_i\}$ 成比例。

## 三、积分形式的闵可夫斯基不等式

### 定理2（积分形式）
设 $(X, \mathcal{F}, \mu)$ 是一个测度空间，$f, g: X \to \mathbb{R}$ 是可测函数，$p \ge 1$，则
$$
\left( \int_X |f+g|^p \, d\mu \right)^{1/p} \le \left( \int_X |f|^p \, d\mu \right)^{1/p} + \left( \int_X |g|^p \, d\mu \right)^{1/p}.
$$
等号成立当且仅当存在非负常数 $\alpha, \beta$（不全为零），使得 $\alpha f(x) = \beta g(x)$ 几乎处处成立。

### 证明

**情况1：** $p = 1$

由三角不等式 $|f+g| \le |f| + |g|$ 积分即得。

**情况2：** $p > 1$

令 $q = \frac{p}{p-1}$，则 $\frac{1}{p} + \frac{1}{q} = 1$。若 $\int |f+g|^p d\mu = 0$，不等式显然成立。否则，计算：
$$
\int |f+g|^p d\mu = \int |f+g| \cdot |f+g|^{p-1} d\mu \le \int (|f|+|g|) |f+g|^{p-1} d\mu.
$$
由赫尔德不等式，
$$
\int |f| |f+g|^{p-1} d\mu \le \left( \int |f|^p d\mu \right)^{1/p} \left( \int |f+g|^{(p-1)q} d\mu \right)^{1/q} = \left( \int |f|^p d\mu \right)^{1/p} \left( \int |f+g|^p d\mu \right)^{1/q},
$$
类似地，
$$
\int |g| |f+g|^{p-1} d\mu \le \left( \int |g|^p d\mu \right)^{1/p} \left( \int |f+g|^p d\mu \right)^{1/q}.
$$
相加得
$$
\int |f+g|^p d\mu \le \left[ \left( \int |f|^p d\mu \right)^{1/p} + \left( \int |g|^p d\mu \right)^{1/p} \right] \left( \int |f+g|^p d\mu \right)^{1/q}.
$$
两边除以 $\left( \int |f+g|^p d\mu \right)^{1/q}$ 即得结论。

等号成立条件：需要赫尔德不等式等号成立，即存在常数 $\lambda_1, \lambda_2$ 使得 $|f|^p = \lambda_1 |f+g|^p$ 和 $|g|^p = \lambda_2 |f+g|^p$ 几乎处处成立，所以 $f$ 和 $g$ 几乎处处成比例。

## 四、应用举例

### 例1
证明：对于任意实数 $a_i, b_i$，有
$$
\left( \sum_{i=1}^n |a_i + b_i|^2 \right)^{1/2} \le \left( \sum_{i=1}^n |a_i|^2 \right)^{1/2} + \left( \sum_{i=1}^n |b_i|^2 \right)^{1/2}.
$$
这就是欧几里得范数的三角不等式。

### 例2
设 $f, g \in L^p(\mathbb{R})$，证明 $\|f+g\|_p \le \|f\|_p + \|g\|_p$。这是泛函分析中 $L^p$ 空间成为赋范线性空间的基础。

## 五、练习题

1. 设 $a_i, b_i > 0$，$p \ge 1$，证明：
   $$
   \left( \sum_{i=1}^n (a_i + b_i)^p \right)^{1/p} \ge \left( \sum_{i=1}^n a_i^p \right)^{1/p} - \left( \sum_{i=1}^n b_i^p \right)^{1/p}.
   $$
2. 设 $f, g$ 在区间 $[0,1]$ 上连续，证明：
   $$
   \left( \int_0^1 |f(x)+g(x)|^3 dx \right)^{1/3} \le \left( \int_0^1 |f(x)|^3 dx \right)^{1/3} + \left( \int_0^1 |g(x)|^3 dx \right)^{1/3}.
   $$