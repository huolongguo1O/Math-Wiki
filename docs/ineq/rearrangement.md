# 排序不等式与切比雪夫不等式

## 一、排序不等式

### 定理1（排序不等式）
设 $a_1 \le a_2 \le \dots \le a_n$ 和 $b_1 \le b_2 \le \dots \le b_n$ 是两个实数序列，则
$$
a_1 b_n + a_2 b_{n-1} + \dots + a_n b_1 \le a_1 b_{\sigma(1)} + a_2 b_{\sigma(2)} + \dots + a_n b_{\sigma(n)} \le a_1 b_1 + a_2 b_2 + \dots + a_n b_n,
$$
其中 $\sigma$ 是 $\{1,2,\dots,n\}$ 的任一排列。即：反序和 ≤ 乱序和 ≤ 同序和。

### 证明
我们证明同序和最大，反序和最小的证明类似。

考虑两个排列 $\sigma$ 和 $\tau$，其中 $\tau$ 是恒等排列（即同序）。若 $\sigma$ 不是恒等排列，则存在 $i < j$ 使得 $\sigma(i) > \sigma(j)$。交换 $\sigma(i)$ 和 $\sigma(j)$ 得到一个新的排列 $\sigma'$，我们来比较和式的变化。

令 $S = \sum_{k=1}^n a_k b_{\sigma(k)}$，交换后和式为 $S' = S - a_i b_{\sigma(i)} - a_j b_{\sigma(j)} + a_i b_{\sigma(j)} + a_j b_{\sigma(i)} = S + (a_j - a_i)(b_{\sigma(i)} - b_{\sigma(j)})$。由于 $a_i \le a_j$，$b_{\sigma(j)} \le b_{\sigma(i)}$（因为 $\sigma(i) > \sigma(j)$，且 $b$ 序列递增），所以 $(a_j - a_i)(b_{\sigma(i)} - b_{\sigma(j)}) \ge 0$，即 $S' \ge S$。

通过有限次这样的交换，可以将 $\sigma$ 变为恒等排列，且每次交换和式不减少，因此同序和最大。

等号成立当且仅当所有 $a_i$ 相等或所有 $b_i$ 相等。

## 二、切比雪夫不等式

### 定理2（切比雪夫不等式，离散形式）
设 $a_1 \le a_2 \le \dots \le a_n$ 和 $b_1 \le b_2 \le \dots \le b_n$ 是两个实数序列，则
$$
\frac{1}{n} \sum_{i=1}^n a_i b_i \ge \left( \frac{1}{n} \sum_{i=1}^n a_i \right) \left( \frac{1}{n} \sum_{i=1}^n b_i \right) \ge \frac{1}{n} \sum_{i=1}^n a_i b_{n+1-i}.
$$
如果其中一个序列反序排列（即递减），则不等号反向。

### 证明
由排序不等式，同序和最大，所以
$$
\sum_{i=1}^n a_i b_i \ge \sum_{i=1}^n a_i b_{\sigma(i)} \quad \text{对任意排列 } \sigma.
$$
特别地，取所有排列的平均，有
$$
\sum_{i=1}^n a_i b_i \ge \frac{1}{n!} \sum_{\sigma \in S_n} \sum_{i=1}^n a_i b_{\sigma(i)} = \frac{1}{n!} \sum_{i=1}^n a_i \sum_{\sigma} b_{\sigma(i)} = \frac{1}{n!} \sum_{i=1}^n a_i \cdot (n-1)! \sum_{j=1}^n b_j = \frac{1}{n} \sum_{i=1}^n a_i \sum_{j=1}^n b_j.
$$
因此
$$
\frac{1}{n} \sum_{i=1}^n a_i b_i \ge \left( \frac{1}{n} \sum_{i=1}^n a_i \right) \left( \frac{1}{n} \sum_{i=1}^n b_i \right).
$$
同理，反序和最小，可得右边不等式。

等号成立当且仅当所有 $a_i$ 相等或所有 $b_i$ 相等。

## 三、应用

### 例1
设 $a, b, c > 0$，证明：
$$
\frac{a}{b+c} + \frac{b}{c+a} + \frac{c}{a+b} \ge \frac{3}{2}.
$$
**证明：** 不妨设 $a \ge b \ge c > 0$，则 $\frac{1}{b+c} \ge \frac{1}{c+a} \ge \frac{1}{a+b}$。由切比雪夫不等式，
$$
\frac{a}{b+c} + \frac{b}{c+a} + \frac{c}{a+b} \ge \frac{1}{3} (a+b+c) \left( \frac{1}{b+c} + \frac{1}{c+a} + \frac{1}{a+b} \right).
$$
再由柯西不等式或均值不等式，$\frac{1}{b+c} + \frac{1}{c+a} + \frac{1}{a+b} \ge \frac{9}{2(a+b+c)}$，代入即得。

## 四、练习题

1. 设 $a, b, c > 0$，证明：$\frac{a}{b+c} + \frac{b}{c+a} + \frac{c}{a+b} \ge \frac{3}{2}$。
2. 设 $x_1 \le x_2 \le \dots \le x_n$，$y_1 \le y_2 \le \dots \le y_n$，证明切比雪夫不等式。
3. 利用切比雪夫不等式证明：若 $a, b, c > 0$，则

   $$
   \frac{a^3}{b^2} + \frac{b^3}{c^2} + \frac{c^3}{a^2} \ge \frac{a^2}{b} + \frac{b^2}{c} + \frac{c^2}{a}.
   $$