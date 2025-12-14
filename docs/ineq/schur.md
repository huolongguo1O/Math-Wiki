# 舒尔不等式

## 一、引言

舒尔不等式是由数学家Issai Schur发现的一个关于非负实数的不等式。它在三元对称不等式中有着重要应用，常与其他不等式结合使用。

## 二、舒尔不等式的一般形式

### 定理1（舒尔不等式）
设 $a, b, c \ge 0$，$r$ 为实数，则
$$
\sum_{cyc} a^r (a-b)(a-c) \ge 0.
$$
这里 $\sum_{cyc}$ 表示循环和，即 $a^r(a-b)(a-c) + b^r(b-c)(b-a) + c^r(c-a)(c-b) \ge 0$。

### 证明
由于不等式是对称的，不妨设 $a \ge b \ge c \ge 0$。将左边记为 $S$，则
$$
S = a^r (a-b)(a-c) + b^r (b-c)(b-a) + c^r (c-a)(c-b).
$$
注意到 $(b-a) = -(a-b)$，$(c-a) = -(a-c)$，$(c-b) = -(b-c)$，所以
$$
S = a^r (a-b)(a-c) - b^r (b-c)(a-b) + c^r (a-c)(b-c).
$$
因式分解：
$$
\begin{aligned}
S &= (a-b)[a^r(a-c) - b^r(b-c)] + c^r (a-c)(b-c) \\\\
&= (a-b)[(a^r - b^r)(a-c) + b^r(a-b)] + c^r (a-c)(b-c) \quad (\text{因为 } a-c = (a-b)+(b-c)) \\\\
&= (a-b)^2 [a^r - b^r] + (a-b)b^r(a-b) + c^r (a-c)(b-c) \\\\
&= (a-b)^2 (a^r - b^r + b^r) + c^r (a-c)(b-c) \\\\
&= (a-b)^2 a^r + c^r (a-c)(b-c).
\end{aligned}
$$
由于 $a \ge b \ge c \ge 0$，所以 $(a-b)^2 \ge 0$，$a^r \ge 0$，$a-c \ge 0$，$b-c \ge 0$，$c^r \ge 0$，因此 $S \ge 0$。等号成立当且仅当 $a=b=c$，或者 $a=b, c=0$ 及其轮换（若 $r>0$，则还需 $c=0$；若 $r=0$，则等号当 $a=b$ 或 $b=c$ 或 $c=a$ 时成立）。

## 三、常见特例

### 1. $r = 1$ 的情形
$$
a^3 + b^3 + c^3 + 3abc \ge a^2(b+c) + b^2(c+a) + c^2(a+b).
$$
**证明：** 展开舒尔不等式：
$$
\sum_{cyc} a(a-b)(a-c) = \sum_{cyc} a(a^2 - ab - ac + bc) = \sum_{cyc} (a^3 - a^2b - a^2c + abc) = \sum_{cyc} a^3 - \sum_{cyc} a^2(b+c) + 3abc \ge 0.
$$
移项即得。

### 2. $r = 2$ 的情形
$$
a^4 + b^4 + c^4 + abc(a+b+c) \ge a^3(b+c) + b^3(c+a) + c^3(a+b).
$$
**证明：** 类似展开。

## 四、应用

### 例1
设 $a, b, c \ge 0$，证明：
$$
a^3 + b^3 + c^3 + 3abc \ge \sum_{cyc} ab(a+b).
$$
**证明：** 由舒尔不等式（$r=1$），
$$
a^3+b^3+c^3+3abc \ge \sum_{cyc} a^2(b+c) = \sum_{cyc} ab(a+b).
$$

### 例2（IMO 1984）
设 $x, y, z \ge 0$ 且 $x+y+z=1$，证明：
$$
0 \le xy+yz+zx - 2xyz \le \frac{7}{27}.
$$
**证明：** 左边：由舒尔不等式（$r=1$），
$$
x^3+y^3+z^3+3xyz \ge \sum_{cyc} x^2(y+z).
$$
利用 $x+y+z=1$，可化为 $xy+yz+zx \ge 2xyz$。

## 五、练习题

1. 设 $a, b, c \ge 0$，证明：$a^3+b^3+c^3+3abc \ge \sum_{cyc} a^2(b+c)$。
2. 设 $a, b, c \ge 0$，且 $a+b+c=1$，证明：$a^3+b^3+c^3+6abc \ge \frac{1}{4}$。
3. 设 $a, b, c$ 是三角形的三边长，证明：$a^3+b^3+c^3+3abc \ge \sum_{cyc} a^2(b+c)$。