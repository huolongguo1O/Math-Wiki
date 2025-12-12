# 柯西不等式

## 引言
柯西不等式是数学中最重要的不等式之一，由法国数学家奥古斯丁·路易·柯西于1821年提出，在分析学、线性代数、概率论等领域有广泛应用。

## 一般形式

### 定理1（柯西不等式）
设 \( a_1, a_2, \dots, a_n \) 和 \( b_1, b_2, \dots, b_n \) 是实数，则：
\[
\left(\sum_{i=1}^n a_i^2\right)\left(\sum_{i=1}^n b_i^2\right) \geq \left(\sum_{i=1}^n a_i b_i\right)^2
\]
等号成立当且仅当 \( a_i \) 与 \( b_i \) 成比例，即存在常数 \( k \) 使得 \( a_i = k b_i \) (对所有 \( i \))，或所有 \( b_i = 0 \)。

## 证明方法

### 证明1：判别式法
考虑二次函数：
\[
f(x) = \sum_{i=1}^n (a_i x - b_i)^2 = \left(\sum_{i=1}^n a_i^2\right)x^2 - 2\left(\sum_{i=1}^n a_i b_i\right)x + \sum_{i=1}^n b_i^2 \geq 0
\]
由于 \( f(x) \geq 0 \) 对任意实数 \( x \) 成立，故判别式：
\[
\Delta = 4\left(\sum_{i=1}^n a_i b_i\right)^2 - 4\left(\sum_{i=1}^n a_i^2\right)\left(\sum_{i=1}^n b_i^2\right) \leq 0
\]
即得不等式。

### 证明2：拉格朗日恒等式
直接计算：
\[
\left(\sum_{i=1}^n a_i^2\right)\left(\sum_{i=1}^n b_i^2\right) - \left(\sum_{i=1}^n a_i b_i\right)^2 = \sum_{1 \leq i < j \leq n} (a_i b_j - a_j b_i)^2 \geq 0
\]
这个恒等式称为拉格朗日恒等式。

### 证明3：向量内积
在欧几里得空间中，由内积性质：
\[
|\vec{a} \cdot \vec{b}| \leq \|\vec{a}\| \cdot \|\vec{b}\|
\]
即：
\[
\left|\sum_{i=1}^n a_i b_i\right| \leq \sqrt{\sum_{i=1}^n a_i^2} \cdot \sqrt{\sum_{i=1}^n b_i^2}
\]

## T2引理

此引理在国内一般被称为柯西不等式的变形。

## 向量形式

### 定理2（向量形式）
设 \( \vec{a} = (a_1, a_2, \dots, a_n) \), \( \vec{b} = (b_1, b_2, \dots, b_n) \) 为 \( n \) 维实向量，则：
\[
|\vec{a} \cdot \vec{b}| \leq \|\vec{a}\| \cdot \|\vec{b}\|
\]
等号成立当且仅当 \( \vec{a} \) 与 \( \vec{b} \) 线性相关。

## 积分形式

### 定理3（积分形式）
设 \( f(x), g(x) \) 在区间 \([a,b]\) 上可积，则：
\[
\left(\int_a^b f(x)g(x)dx\right)^2 \leq \int_a^b f^2(x)dx \cdot \int_a^b g^2(x)dx
\]
等号成立当且仅当存在常数 \( k \) 使得 \( f(x) = k g(x) \) 几乎处处成立。

### 证明
考虑积分：
\[
\int_a^b [f(x) - \lambda g(x)]^2 dx \geq 0
\]
展开后得到关于 \( \lambda \) 的二次式，判别式非正。

## 拉格朗日恒等式

### 定理4（拉格朗日恒等式）
\[
\left(\sum_{i=1}^n a_i^2\right)\left(\sum_{i=1}^n b_i^2\right) - \left(\sum_{i=1}^n a_i b_i\right)^2 = \sum_{1 \leq i < j \leq n} (a_i b_j - a_j b_i)^2
\]

### 几何意义
在三维空间中，该恒等式等价于：
\[
|\vec{a}|^2 |\vec{b}|^2 - (\vec{a} \cdot \vec{b})^2 = |\vec{a} \times \vec{b}|^2
\]
即向量模的平方与夹角正弦的关系。

## 赫尔德不等式（推广）

### 定理5（赫尔德不等式）
设 \( a_i, b_i > 0 \) (\( i=1,\dots,n \))，\( p,q > 1 \) 且 \( \frac{1}{p} + \frac{1}{q} = 1 \)，则：
\[
\sum_{i=1}^n a_i b_i \leq \left(\sum_{i=1}^n a_i^p\right)^{\frac{1}{p}} \left(\sum_{i=1}^n b_i^q\right)^{\frac{1}{q}}
\]
等号成立当且仅当 \( a_i^p \) 与 \( b_i^q \) 成比例。

### 证明思路
1. 利用加权均值不等式
2. 或利用凸函数性质

### 特殊情形
当 \( p = q = 2 \) 时，即为柯西不等式。

### 积分形式
\[
\int_a^b |f(x)g(x)|dx \leq \left(\int_a^b |f(x)|^p dx\right)^{\frac{1}{p}} \left(\int_a^b |g(x)|^q dx\right)^{\frac{1}{q}}
\]

## 闵可夫斯基不等式（进一步推广）

### 定理6（闵可夫斯基不等式）
设 \( a_i, b_i > 0 \) (\( i=1,\dots,n \))，\( p \geq 1 \)，则：
\[
\left(\sum_{i=1}^n (a_i + b_i)^p\right)^{\frac{1}{p}} \leq \left(\sum_{i=1}^n a_i^p\right)^{\frac{1}{p}} + \left(\sum_{i=1}^n b_i^p\right)^{\frac{1}{p}}
\]
等号成立当且仅当 \( a_i \) 与 \( b_i \) 成比例。

### 几何意义
在 \( L^p \) 空间中，这是三角不等式的形式。

## 应用

### 应用1：证明不等式
例：证明 \( (a^2 + b^2 + c^2)(x^2 + y^2 + z^2) \geq (ax + by + cz)^2 \)

### 应用2：极值问题
例：求 \( \sqrt{x^2 + y^2 + z^2} \) 在约束 \( ax + by + cz = d \) 下的最小值。

### 应用3：概率论
在概率论中，柯西不等式导出协方差与方差的关系：
\[
|\text{Cov}(X,Y)| \leq \sqrt{\text{Var}(X) \cdot \text{Var}(Y)}
\]
