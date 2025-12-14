# Muirhead不等式

## 一、引言

Muirhead不等式是处理对称多项式不等式的一个有力工具，由英国数学家Muirhead发现。它可以看作Karamata不等式在对称和情形下的特例。

## 二、基本概念

### 定义1（序列的优超）
设 $\alpha = (\alpha_1, \alpha_2, \dots, \alpha_n)$ 和 $\beta = (\beta_1, \beta_2, \dots, \beta_n)$ 是两个非负实数序列，且满足：
1. $\alpha_1 \ge \alpha_2 \ge \dots \ge \alpha_n$，$\beta_1 \ge \beta_2 \ge \dots \ge \beta_n$；
2. $\sum_{i=1}^k \alpha_i \ge \sum_{i=1}^k \beta_i$ 对 $k=1,2,\dots,n-1$；
3. $\sum_{i=1}^n \alpha_i = \sum_{i=1}^n \beta_i$。
则称 $\alpha$ 优超于 $\beta$，记作 $\alpha \succ \beta$。

### 定义2（对称和）
设 $a_1, a_2, \dots, a_n$ 是正实数，$\alpha = (\alpha_1, \alpha_2, \dots, \alpha_n)$ 是非负实数序列，定义对称和：
$$
\sum_{\text{sym}} a_1^{\alpha_1} a_2^{\alpha_2} \dots a_n^{\alpha_n} = \sum_{\sigma \in S_n} a_{\sigma(1)}^{\alpha_1} a_{\sigma(2)}^{\alpha_2} \dots a_{\sigma(n)}^{\alpha_n},
$$
其中 $S_n$ 是 $n$ 个元素的对称群。

## 三、Muirhead不等式

### 定理1（Muirhead不等式）
设 $a_1, a_2, \dots, a_n$ 为正实数，$\alpha$ 和 $\beta$ 是两个非负实数序列，且 $\alpha \succ \beta$，则
$$
\sum_{\text{sym}} a_1^{\alpha_1} a_2^{\alpha_2} \dots a_n^{\alpha_n} \ge \sum_{\text{sym}} a_1^{\beta_1} a_2^{\beta_2} \dots a_n^{\beta_n}.
$$
等号成立当且仅当 $\alpha = \beta$，或者 $a_1 = a_2 = \dots = a_n$。

### 证明思路
利用Karamata不等式。考虑函数 $f(x) = e^x$，取 $x_i = \ln a_i$。则对称和可以写成 $\sum_{\sigma} \exp(\sum \alpha_i x_{\sigma(i)})$。通过排序和优超关系，可以证明不等式。

## 四、常见特例

### 1. 算术-几何平均不等式
取 $\alpha = (1,0,\dots,0)$，$\beta = \left( \frac{1}{n}, \frac{1}{n}, \dots, \frac{1}{n} \right)$。容易验证 $\alpha \succ \beta$。计算对称和：
$$
\sum_{\text{sym}} a_1^1 a_2^0 \dots a_n^0 = (n-1)! \sum_{i=1}^n a_i,
$$
$$
\sum_{\text{sym}} a_1^{1/n} a_2^{1/n} \dots a_n^{1/n} = n! (a_1 a_2 \dots a_n)^{1/n}.
$$
由Muirhead不等式，
$$
(n-1)! \sum a_i \ge n! (\prod a_i)^{1/n} \quad \Rightarrow \quad \frac{1}{n} \sum a_i \ge (\prod a_i)^{1/n}.
$$

## 五、应用

### 例1
证明：对任意正实数 $a, b, c$，有
$$
a^3+b^3+c^3 \ge a^2b+b^2c+c^2a.
$$
**证明：** 考虑指数向量 $(3,0,0)$ 和 $(2,1,0)$。由于 $(3,0,0) \succ (2,1,0)$（因为 $3 \ge 2$，$3+0 \ge 2+1$，$3+0+0=2+1+0$），由Muirhead不等式，
$$
\sum_{\text{sym}} a^3 b^0 c^0 \ge \sum_{\text{sym}} a^2 b^1 c^0.
$$
计算对称和：左边 = $2!(a^3+b^3+c^3) = 2(a^3+b^3+c^3)$，右边 = $(a^2b + a^2c + b^2c + b^2a + c^2a + c^2b)$。所以
$$
2(a^3+b^3+c^3) \ge a^2b+a^2c+b^2c+b^2a+c^2a+c^2b,
$$
即
$$
a^3+b^3+c^3 \ge \frac{1}{2} \sum_{\text{sym}} a^2 b = a^2b+b^2c+c^2a + \frac{1}{2}(a^2c+b^2a+c^2b).
$$

## 六、练习题

1. 设 $a, b, c > 0$，证明：$a^2b^2+b^2c^2+c^2a^2 \ge abc(a+b+c)$。
2. 设 $a, b, c > 0$，且 $abc=1$，证明：$a^3+b^3+c^3 \ge a^2+b^2+c^2$。
3. 证明：对于正实数 $a, b, c$，有
   $$
   a^4+b^4+c^4 \ge a^3b+b^3c+c^3a.
   $$