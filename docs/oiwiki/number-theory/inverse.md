本文介绍模意义下乘法运算的逆元，并讨论它的常见求解方法。

## 基本概念

非零实数 $a\in\mathbf R$ 的乘法逆元就是它的倒数 $a^{-1}$。类似地，数论中也可以定义一个整数 $a$ 在模 $m$ 意义下的逆元 $a^{-1}\bmod m$，或简单地记作 $a^{-1}$。这就是 **模逆元**（modular multiplicative inverse），也称作 **数论倒数**。

???+ abstract "逆元"
    对于非零整数 $a,m$，如果存在 $b$ 使得 $ab\equiv 1\pmod m$，就称 $b$ 是 $a$ 在模 $m$ 意义下的 **逆元**（inverse）。

这相当于说，$b$ 是线性同余方程 $ax\equiv 1\pmod m$ 的解。根据 [线性同余方程](./linear-equation.md) 的性质可知，当且仅当 $\gcd(a,m)=1$，即 $a,m$ 互素时，逆元 $a^{-1}\bmod m$ 存在，且在模 $m$ 的意义下是唯一的。

