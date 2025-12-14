# Abel变换

## 一、引言

Abel变换，也称为分部求和法或Abel求和公式，是数学分析中处理级数和积分的一种重要技巧。它类似于微积分中的分部积分法，由挪威数学家尼尔斯·亨利克·阿贝尔发现。

## 二、Abel变换公式

### 定理1（Abel变换，离散形式）
设有两个数列 $\{a_k\}$ 和 $\{b_k\}$，记 $B_k = b_1 + b_2 + \dots + b_k$（约定 $B_0 = 0$），则
$$
\sum_{k=1}^n a_k b_k = a_n B_n - \sum_{k=1}^{n-1} (a_{k+1} - a_k) B_k.
$$
或者等价地，
$$
\sum_{k=1}^n a_k b_k = a_n B_n - \sum_{k=1}^{n-1} B_k (a_{k+1} - a_k).
$$

### 证明
直接计算：
$$
\begin{aligned}
\sum_{k=1}^n a_k b_k &= \sum_{k=1}^n a_k (B_k - B_{k-1}) \\\\
&= \sum_{k=1}^n a_k B_k - \sum_{k=1}^n a_k B_{k-1} \\\\
&= \sum_{k=1}^n a_k B_k - \sum_{k=0}^{n-1} a_{k+1} B_k \quad (\text{令 } j=k-1, \text{则 } k=j+1) \\\\
&= a_n B_n + \sum_{k=1}^{n-1} a_k B_k - \sum_{k=1}^{n-1} a_{k+1} B_k \\\\
&= a_n B_n - \sum_{k=1}^{n-1} (a_{k+1} - a_k) B_k.
\end{aligned}
$$

### 另一种形式
如果记 $\Delta a_k = a_{k+1} - a_k$，则Abel变换公式可写为：
$$
\sum_{k=1}^n a_k b_k = a_n B_n - \sum_{k=1}^{n-1} B_k \Delta a_k.
$$

## 三、Abel引理

Abel引理是Abel变换的直接推论，用于估计部分和。

### 定理2（Abel引理）
设 $a_1, a_2, \dots, a_n$ 是单调数列（递增或递减），$b_1, b_2, \dots, b_n$ 是复数，记 $B_k = \sum_{i=1}^k b_i$，且存在 $M>0$ 使得 $|B_k| \le M$ 对所有 $k=1,2,\dots,n$ 成立，则
$$
\left| \sum_{k=1}^n a_k b_k \right| \le M (|a_1| + 2|a_n|).
$$
更精细的估计是：若数列 $a_k$ 单调递减且非负，则
$$
\left| \sum_{k=1}^n a_k b_k \right| \le M a_1.
$$

### 证明
由Abel变换，
$$
\sum_{k=1}^n a_k b_k = a_n B_n - \sum_{k=1}^{n-1} (a_{k+1} - a_k) B_k.
$$
取绝对值，利用三角不等式：
$$
\left| \sum_{k=1}^n a_k b_k \right| \le |a_n| |B_n| + \sum_{k=1}^{n-1} |a_{k+1} - a_k| |B_k| \le M |a_n| + M \sum_{k=1}^{n-1} |a_{k+1} - a_k|.
$$
由于数列 $\{a_k\}$ 单调，所以 $|a_{k+1} - a_k| = |a_{k+1}| - |a_k|$ 或 $|a_k| - |a_{k+1}|$，取决于单调性的方向。

**情况1：** 数列单调递减且非负，即 $a_1 \ge a_2 \ge \dots \ge a_n \ge 0$。则 $a_{k+1} - a_k \le 0$，所以 $|a_{k+1} - a_k| = a_k - a_{k+1}$。于是
$$
\sum_{k=1}^{n-1} |a_{k+1} - a_k| = \sum_{k=1}^{n-1} (a_k - a_{k+1}) = a_1 - a_n.
$$
因此，
$$
\left| \sum_{k=1}^n a_k b_k \right| \le M a_n + M (a_1 - a_n) = M a_1.
$$

**情况2：** 数列单调递增且非负，即 $0 \le a_1 \le a_2 \le \dots \le a_n$。则 $a_{k+1} - a_k \ge 0$，所以 $|a_{k+1} - a_k| = a_{k+1} - a_k$，求和得 $a_n - a_1$。于是
$$
\left| \sum_{k=1}^n a_k b_k \right| \le M a_n + M (a_n - a_1) = M (2a_n - a_1) \le 2M a_n.
$$

## 四、应用

### 1. 级数收敛性判别法

#### Dirichlet判别法
若数列 $\{a_n\}$ 单调趋于零，级数 $\sum b_n$ 的部分和有界，则级数 $\sum a_n b_n$ 收敛。

**证明：** 设 $B_n = \sum_{k=1}^n b_k$，由条件存在 $M>0$ 使得 $|B_n| \le M$。对任意 $n > m$，由Abel变换：
$$
\sum_{k=m+1}^n a_k b_k = a_n B_n - a_m B_m - \sum_{k=m}^{n-1} B_k (a_{k+1} - a_k).
$$
由于 $a_n \to 0$，所以对任意 $\varepsilon > 0$，存在 $N$ 使得当 $n > N$ 时 $|a_n| < \varepsilon$。于是
$$
\left| \sum_{k=m+1}^n a_k b_k \right| \le |a_n| |B_n| + |a_m| |B_m| + \sum_{k=m}^{n-1} |B_k| |a_{k+1} - a_k| \le M (|a_n| + |a_m|) + M \sum_{k=m}^{n-1} |a_{k+1} - a_k|.
$$
由于数列单调，$\sum_{k=m}^{n-1} |a_{k+1} - a_k| = |a_n - a_m| \le |a_n| + |a_m|$。所以
$$
\left| \sum_{k=m+1}^n a_k b_k \right| \le 2M (|a_n| + |a_m|).
$$
当 $m, n$ 充分大时，$|a_n|, |a_m| < \varepsilon$，从而 $\left| \sum_{k=m+1}^n a_k b_k \right| < 4M \varepsilon$，由Cauchy准则知级数收敛。

## 五、练习题

1. 利用Abel变换证明：若 $\{a_n\}$ 单调有界，$\sum b_n$ 收敛，则 $\sum a_n b_n$ 收敛。
2. 计算 $\sum_{k=1}^n k^2 q^k$（$q \neq 1$）。
3. 设 $a_n = \frac{1}{n}$，$b_n = (-1)^n$，利用Abel引理估计 $\left| \sum_{k=1}^n a_k b_k \right|$。