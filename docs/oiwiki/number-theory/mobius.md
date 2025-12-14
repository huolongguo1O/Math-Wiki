author: hydingsy, hyp1231, ranwen, 383494

前置知识：[数论分块](./sqrt-decomposition.md)、[狄利克雷卷积](./dirichlet.md#dirichlet-卷积)

莫比乌斯反演是数论中的重要内容．对于一些函数 $f(n)$，如果很难直接求出它的值，而容易求出其倍数和或约数和 $g(n)$，那么可以通过莫比乌斯反演简化运算，求得 $f(n)$ 的值．

## 莫比乌斯函数

莫比乌斯函数（Möbius 函数）定义为

$$
\mu(n)=
\begin{cases}
1,&n=1,\\
0,&n\text{ is divisible by a square }>1,\\
(-1)^k,&n\text{ is the product of }k\text{ distinct primes}.\\
\end{cases}
$$

具体地，假设正整数 $n$ 有素因数分解 $n=\prod_{i=1}^kp_i^{e_i}$，其中，$p_i$ 是素数，$e_i$ 是正整数．那么，三种情形分别对应：

1.  $\mu(1) = 1$；
2.  当存在 $i$ 使得 $e_i > 1$，即存在任何素因数出现超过一次时，$\mu(n)=0$；
3.  否则，对于所有 $i$ 都有 $e_i = 1$，即任何素因数都只出现一次时，$\mu(n)=(-1)^k$，其中，$k$ 就是互异素因子的个数．

### 性质

根据定义容易验证，莫比乌斯函数 $\mu(n)$ 是积性函数，但不是完全积性函数．除此之外，最为重要的性质是下述恒等式：

???+ note "性质"
    对于正整数 $n$，有
    
    $$
    \sum_{d\mid n}\mu(d) = [n = 1] =
    \begin{cases}
    1,&n=1,\\
    0,&n\neq 1.\\
    \end{cases}
    $$
    
    其中 $[\cdot]$ 是 Iverson 括号．

??? note "证明"
    令 $n=\prod_{i=1}^kp_i^{e_i}$，设 $n' = \prod_{i=1}^kp_i$．根据 [二项式定理](../combinatorics/combination.md#二项式定理)，有
    
    $$
    \sum_{d\mid n}\mu(d) = \sum_{d\mid n'}\mu(d) = \sum_{i=0}^k\binom{k}{i}(-1)^i = (1 + (-1))^k = [k = 0] = [n = 1].
    $$

利用 Dirichlet 卷积，该表达式可以写作 $\varepsilon = 1 * \mu$．也就是说，莫比乌斯函数是常值函数 $1$ 的 Dirichlet 逆．

这一性质有一个很常见的应用：

$$
[i\perp j] = [\gcd(i,j) = 1] = \sum_{d\mid\gcd(i,j)} \mu(d) = \sum_{d}[d\mid i][d\mid j]\mu(d).
$$

它将互素的条件转化为关于莫比乌斯函数的求和式，方便进一步推导．


## 莫比乌斯反演

莫比乌斯函数最重要的应用就是莫比乌斯反演．

???+ note "莫比乌斯反演"
    设 $f(n),g(n)$ 是两个数论函数．那么，有
    
    $$
    f(n) = \sum_{d\mid n}g(d) \iff g(n) = \sum_{d\mid n}\mu\left(\dfrac{n}{d}\right)f(d).
    $$

??? note "证明一"
    直接验证，有：
    
    $$
    \begin{aligned}
    \sum_{d\mid n}\mu\left(\dfrac{n}{d}\right)f(d)
    &= \sum_{d\mid n}\mu\left(\dfrac{n}{d}\right)\sum_{k\mid d}g(k)\\
    &= \sum_{k\mid n}g(k)\sum_d[k\mid d\mid n]\mu\left(\dfrac{n}{d}\right)\\
    &= \sum_{k\mid n}g(k)\sum_{d\mid n}\left[\frac{n}{d}\mid\frac{n}{k}\right]\mu\left(\dfrac{n}{d}\right)\\
    &= \sum_{k\mid n}g(k)\left[\frac{n}{k} = 1\right] \\
    &= g(n).
    \end{aligned}
    $$
    
    式子变形的关键在于交换求和次序，并注意到 $k\mid d\mid n$ 就等价于 $\dfrac{n}{d}\mid\dfrac{n}{k}$．倒数第二个等号相当于对 $\dfrac{n}{k}$ 的因子 $\dfrac{n}{d}$ 处的莫比乌斯函数求和，所以就等于 $\left[\dfrac{n}{k} = 1\right]$．这一表达式仅在 $n=k$ 处不是 $0$，最后就会得到 $g(n)$．

??? note "证明二"
    利用 Dirichlet 卷积，命题等价于
    
    $$
    f = 1 * g \iff g = \mu * f.
    $$
    
    利用 $1 * \mu = \varepsilon$，在左式的等号两侧同时对 $\mu$ 做卷积，就得到
    
    $$
    f * \mu = (1 * g) * \mu = (1 * \mu) * g = \varepsilon * g = g.
    $$

在涉及各种整除关系的数论函数求和中，莫比乌斯反演是有力的变形工具．

???+ example "例子"
    1.  [欧拉函数](./euler-totient.md) $\varphi(n)$ 满足关系式 $n = \sum_{d\mid n}\varphi(d)$，亦即 $\mathrm{id}=1*\varphi$．对它进行反演，就得到 $\varphi = \mu * \mathrm{id}$，亦即
    
        $$
        \varphi(n) = \sum_{d\mid n}d\mu\left(\dfrac{n}{d}\right).
        $$
    2.  除数函数 $\sigma_k(n) = \sum_{d\mid n}d^k$，亦即 $\sigma_k = 1 * \mathrm{id}_k$．对它进行反演，就得到 $\mathrm{id}_k = \mu * \sigma_k$，亦即
    
        $$
        n^k = \sum_{d\mid n}\mu\left(\dfrac{n}{d}\right)\sigma_k(d).
        $$
    3.  互异素因子数目函数 $\omega(n)=\sum_{d\mid n}[d\in\mathbf P]$，亦即 $\omega = 1* \mathbf{1}_{\mathbf P}$，其中 $\mathbf{1}_{\mathbf P}$ 是素数集 $\mathbf P$ 的指示函数．对它进行反演，就得到 $\mathbf{1}_{\mathbf P} = \mu * \omega$，亦即
    
        $$
        [n\in\mathbf P] = \sum_{d\mid n}\mu\left(\dfrac{n}{d}\right)\omega(d).
        $$
    4.  考察满足 $\log n = \sum_{d\mid n}\Lambda(d)$ 的数论函数 $\Lambda(n)$．它就是对数函数的莫比乌斯反演，也称为 von Mangoldt 函数：
    
        $$
        \Lambda(n) = \sum_{d\mid n}\mu\left(\dfrac{n}{d}\right)\log d = 
        \begin{cases}
        \log p, & n = p^e,~p\in\mathbf P,~e\in\mathbf N_+, \\
        0, &\text{otherwise}.
        \end{cases}
        $$

??? note "附：$\Lambda(n)$ 表达式的证明"
    对于素数幂 $n=p^e~(e\in\mathbf N_+)$，有
    
    $$
    \Lambda(n) = \sum_{i=0}^e\mu(p^{e-i})\log p^i = \log p^{e} - \log p^{e-1} = \log p.
    $$
    
    对于 $n=1$，显然有 $\Lambda(n)=\log 1=0$．对于其他合数 $n$，有
    
    $$
    \Lambda(n) = \sum_{d\mid n}\mu(d)(\log n-\log d) = \left(\sum_{d\mid n}\mu(d)\right)\log n-\sum_{d\mid n}\mu(d)\log d.
    $$
    
    根据莫比乌斯函数的性质，$\log n$ 一项的系数为 $[n=1]=0$．对于后面的一项，可以进一步将 $d$ 分解为素因数之积．对于任何素数 $p\mid n$，考察 $\log p$ 的系数，都有：
    
    $$
    -\sum_{p\mid d\mid n}\mu(d) = \sum_{(d/p)\mid(n/p)}\mu\left(\dfrac{d}{p}\right) = \left[\dfrac{n}{p}=1\right]=0.
    $$
    
    由此，对于不止一个素因子的合数 $n$，都有 $\Lambda(n)=0$．

### 拓展形式

除了上述基本形式外，莫比乌斯反演还有一些常见的拓展形式．首先，可以考虑它的倍数和形式．

???+ note "拓展一"
    设 $f(n),g(n)$ 是两个数论函数．那么，有
    
    $$
    f(n) = \sum_{n\mid d}g(d) \iff g(n) = \sum_{n\mid d}\mu\left(\dfrac{d}{n}\right)f(d).
    $$

??? note "证明"
    直接验证，有：
    
    $$
    \begin{aligned}
    \sum_{n\mid d}\mu\left(\dfrac{d}{n}\right)f(d)
    &= \sum_{n\mid d}\mu\left(\dfrac{d}{n}\right)\sum_{d\mid k}g(k)\\
    &= \sum_{n\mid k}g(k)\sum_{d}[n\mid d\mid k]\mu\left(\dfrac{d}{n}\right)\\
    &= \sum_{n\mid k}g(k)\sum_{n\mid d}\left[\dfrac{d}{n}\mid\dfrac{k}{n}\right]\mu\left(\dfrac{d}{n}\right)\\
    &= \sum_{n\mid k}g(k)\left[\dfrac{k}{n}=1\right]\\
    &= g(n).
    \end{aligned}
    $$
    
    这和基本形式的推导完全对偶．

其次，莫比乌斯反演并不仅限于加法，它实际上对于任何 [Abel 群](../algebra/basic.md#群) 中的运算都成立．例如，它有如下的乘法形式：

???+ note "拓展二"
    设 $f(n),g(n)$ 是两个数论函数．那么，有
    
    $$
    f(n) = \prod_{d\mid n}g(d) \iff g(n) = \prod_{d\mid n}f(d)^{\mu(n/d)}.
    $$

??? note "证明"
    直接验证，有：
    
    $$
    \begin{aligned}
    \prod_{d\mid n}f(d)^{\mu(n/d)}
    &= \prod_{d\mid n}\left(\prod_{k\mid d}g(k)\right)^{\mu(n/d)}\\
    &= \prod_{k\mid n}g(k)\uparrow\left(\sum_d[k\mid d\mid n]\mu\left(\dfrac{n}{d}\right)\right)\\
    &= \prod_{k\mid n}g(k)\uparrow\left(\sum_{d\mid n}\left[\frac{n}{d}\mid\frac{n}{k}\right]\mu\left(\dfrac{n}{d}\right)\right)\\
    &= \prod_{k\mid n}g(k)\uparrow\left[\frac{n}{k} = 1\right] \\
    &= g(n).
    \end{aligned}
    $$
    
    其中，$a\uparrow b = a^b$ 是 Knuth 箭头．对比基本形式的证明可以发现，唯一的区别就是加法换成了乘法，且乘法换成了取幂．

从 Dirichlet 卷积的角度看，莫比乌斯反演只是利用了「莫比乌斯函数是常值函数的 Dirichlet 逆」这一点．容易想象，类似莫比乌斯反演的关系对于一般的 [Dirichlet 逆](./dirichlet.md#dirichlet-卷积) 同样成立．

???+ note "拓展三"
    设 $f(n),g(n),\alpha(n)$ 都是数论函数，且 $\alpha^{-1}(n)$ 是 $\alpha(n)$ 的 Dirichlet 逆，即
    
    $$
    [n=1] = \sum_{d\mid n}\alpha\left(\dfrac{n}{d}\right)\alpha^{-1}(d).
    $$
    
    那么，有
    
    $$
    f(n) = \sum_{d\mid n}\alpha\left(\dfrac{n}{d}\right)g(d) \iff g(n) = \sum_{d\mid n}\alpha^{-1}\left(\dfrac{n}{d}\right)f(d).
    $$

??? note "证明"
    直接验证，有：
    
    $$
    \begin{aligned}
    \sum_{d\mid n}\alpha^{-1}\left(\dfrac{n}{d}\right)f(d)
    &= \sum_{d\mid n}\alpha^{-1}\left(\dfrac{n}{d}\right)\sum_{k\mid d}\alpha\left(\dfrac{d}{k}\right)g(k)\\
    &= \sum_{k\mid n}g(k)\sum_d[k\mid d\mid n]\alpha\left(\dfrac{d}{k}\right)\alpha^{-1}\left(\dfrac{n}{d}\right)\\
    &= \sum_{k\mid n}g(k)\sum_{d\mid n}\left[\frac{n}{d}\mid\frac{n}{k}\right]\alpha\left(\dfrac{d}{k}\right)\alpha^{-1}\left(\dfrac{n/k}{d/k}\right)\\
    &= \sum_{k\mid n}g(k)\left[\frac{n}{k} = 1\right] \\
    &= g(n).
    \end{aligned}
    $$
    
    和基本形式的证明相比较，只需要将倒数第二个等号替换成 Dirichlet 逆的定义式．

???+ note "推论"
    设 $f(n),g(n)$ 是数论函数，且 $t(n)$ 是完全积性函数．那么，有
    
    $$
    f(n) = \sum_{d\mid n}t\left(\dfrac{n}{d}\right)g(d) \iff g(n) = \sum_{d\mid n}\mu\left(\dfrac{n}{d}\right)t\left(\dfrac{n}{d}\right)f(d).
    $$

??? note "证明"
    由 Dirichlet 卷积的 [性质](./dirichlet.md#性质) 可知，对于完全积性函数 $t(n)$，它的 Dirichlet 逆就是 $\mu(n)t(n)$．

最后，莫比乌斯反演还可以推广到 $[1,+\infty)$ 上的复值函数，而不仅仅局限于数论函数．基本形式的莫比乌斯反演可以看作是复值函数在所有非整数点处均取零值的特殊情形．

???+ note "拓展四"
    设 $F(x)$ 和 $G(x)$ 都是 $[1,+\infty)$ 上的复值函数．那么，有
    
    $$
    F(x) = \sum_{n = 1}^{\lfloor x\rfloor}G\left(\dfrac{x}{n}\right) \iff G(x) = \sum_{n = 1}^{\lfloor x\rfloor}\mu(n)F\left(\dfrac{x}{n}\right).
    $$

??? note "证明"
    不妨对 $F$ 和 $G$ 补充定义，设当 $x < 1$ 时，恒有 $F(x)=G(x)=0$．那么，命题就等价于：
    
    $$
    F(x) = \sum_n G\left(\dfrac{x}{n}\right) \iff G(x) = \sum_n \mu(n)F\left(\dfrac{x}{n}\right).
    $$
    
    这些求和式都是对 $n\in\mathbf N_+$ 求和．
    
    直接验证，有：
    
    $$
    \begin{aligned}
    \sum_n \mu(n)F\left(\dfrac{x}{n}\right)
    &= \sum_n\mu(n)\sum_d G\left(\dfrac{x/n}{d}\right)\\
    &= \sum_k G\left(\dfrac{x}{k}\right)\sum_{n\mid k}\mu(n)\\
    &= \sum_k G\left(\dfrac{x}{k}\right)[k=1]\\
    &= G(x).
    \end{aligned}
    $$
    
    其中，为得到第二个等号，需要令 $k = nd$．

???+ note "推论"
    设 $f(n),g(n)$ 是数论函数．那么，有
    
    $$
    f(n) = \sum_{k=1}^ng\left(\left\lfloor\dfrac{n}{k}\right\rfloor\right) \iff g(n)=\sum_{k=1}^n\mu(k)f\left(\left\lfloor\dfrac{n}{k}\right\rfloor\right).
    $$

??? note "证明"
    只需要取 $F(x)=f(\lfloor x\rfloor)$ 和 $G(x)=g(\lfloor x\rfloor)$ 即可．

这些拓展形式之间可以互相组合，进而得到更为复杂的反演关系．

### Dirichlet 前缀和

前置知识：[前缀和与差分](../../basic/prefix-sum.md)

考虑基本形式的莫比乌斯反演关系：

$$
f(n) = \sum_{d\mid n}g(d) \iff g(n) = \sum_{d\mid n}\mu\left(\dfrac{n}{d}\right)f(d).
$$

左侧等式中，$f(n)$ 的值是 $n$ 的所有因数处 $g(n)$ 的值之和．如果将 $a\mid b$ 理解为 $a$ 排在 $b$ 之前，那么 $f(n)$ 就可以理解为某种意义下 $g(n)$ 的前缀和．因此，在国内竞赛圈，由 $\{g(k)\}_{k=1}^n$ 求出 $\{f(k)\}_{k=1}^n$ 的过程也称为 **Dirichlet 前缀和**，相应的逆过程则称为 Dirichlet 差分．这些方法大多出现在需要预处理某个数论函数在前 $N$ 个点处取值的情形．

接下来，讨论 Dirichlet 前缀和的计算．如果将每一个素数都看作一个维度，这就是一种高维前缀和．回忆高维前缀和的 [逐维前缀和算法](../../basic/prefix-sum.md#逐维前缀和)：逐个遍历所有的维度，并将每个位置的值都累加到该位置在该维度上的后继位置．对于数论函数，这相当于说，从小到大遍历所有素数 $p$，并将 $n$ 处的函数值累加到 $np$ 处．这和 [Eratosthenes 筛法](./sieve.md#埃拉托斯特尼筛法) 的遍历顺序是一致的．因此，这一算法可以在 $O(n\log\log n)$ 时间内计算出长度为 $n$ 的数列的 Dirichlet 前缀和．类似地，利用逐维差分就可以在相同时间复杂度内求出数列的 Dirichlet 差分．

???+ example "参考实现"
    === "Dirichlet 前缀和"
        ```cpp
        --8<-- "docs/math/code/mobius/mobius-func-3.cpp:presum"
        ```
    
    === "Dirichlet 差分"
        ```cpp
        --8<-- "docs/math/code/mobius/mobius-func-3.cpp:diff"
        ```

这一计算方法可以推广到倍数和（拓展一）、乘积形式（拓展二）、利用完全积性函数代替常值函数（拓展三的推论）等拓展形式中．


## 参考文献

-   [Möbius function - Wikipedia](https://en.wikipedia.org/wiki/M%C3%B6bius_function)
-   [Möbius inversion formula - Wikipedia](https://en.wikipedia.org/wiki/M%C3%B6bius_inversion_formula)
-   [Von Mangoldt function - Wikipedia](https://en.wikipedia.org/wiki/Von_Mangoldt_function)
-   [algocode 算法博客](https://web.archive.org/web/20190523150159/https://algocode.net/2018/04/18/20180418-KB-Mobius-Inversion-Formula/)
