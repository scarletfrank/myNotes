# 高等数学
> - [Markdown+Math Extension](https://marketplace.visualstudio.com/items?itemName=goessner.mdmath)
> - [MathJax Site Reference](http://www.onemathematicalcat.org/MathJaxDocumentation/TeXSyntax.htm)
> changelog: 同济高数第七版和第六版
## 函数与极限

### 映射与函数

#### 集合
*定义*

全体非负整数即自然数的集合记作$N$，

$$ N = \lbrace 0, 1, 2, \cdots, n, \cdots \rbrace$$
全体正整数的集合 $N^+$，全体整数的集合记为 $Z$，全体有理数的集合记作 $Q$，$R^*$为排除数0的实数集

A是B的子集或A包含于B，记作 $A \subset B$。
A是B的真子集，记作 $A \subsetneqq B$

*运算*

$A \cup B$ $A \cap B$ $A \backslash B$

补集 $A^C$

直积或笛卡尔（Descartes）乘积

$$ A \times B $$

开区间闭区间

$$ (a, b) = \lbrace x |a \lt x \lt b\rbrace$$
$$ [a, b] = \lbrace x | a \leq x \leq b \rbrace$$

$\delta$邻域，去心$\delta$领域

$$ U(a, \delta) = \{ x | a - \delta \lt x \lt a + \delta \}$$
$$ \mathring U (a, \delta) = \{ x | 0 \lt |x-a| \lt \delta \}$$

#### 映射

$$ f \colon X \to Y $$
$$ f \circ g \colon X \to Z$$

构成映射的三个要素：集合X，即定义域$D_f = X$；集合Y，即值域的范围：$R_f \subset Y$；对应法则，使每个$x \in X$，有唯一确定的$y=f(x)$与之对应

x的像是唯一的，y的原像不一定是唯一的。*满射、单射、双射*

Summary: 映射又称为算子：
- 从非空集X到数集Y的映射又称为X上的泛函
- 从非空集X到它自身的映射又称为X上的变换
- 从实数集（或其子集）X到实数集Y的映射通常称为定义在X上的函数

逆映射，只有单射才存在逆映射 $g \colon R_f \to X$

构成复合映射的条件是：$g$的值域$R_g$必须在$f$的定义域内，即$R_g \in D_f$

#### 函数

*函数概念*： $D \subset R$

*函数性质*
- 有界性
- 单调性
- 奇偶性
- 周期性

*反函数和复合函数*

*函数的运算*

*初等函数*

幂函数：$y=x^{\mu}(\mu \in R)$

指数函数：$y=a^x(a \gt 0 \text{且} a \neq 1)$

对数函数: $y = log_a x (a \gt 0 \text{且} a \neq 1)$

三角函数: $y = \sin x | \cos x | \tan x | \csc x | \sec x | \cot x$ 

反三角函数：$y = \arcsin x | \arccos x | \arctan x$ 

双曲正弦 $sh x = \frac {e^x - e^{-x}} {2}$

双曲余弦 $ch x = \frac {e^x + e^{-x}} {2}$ 

双曲正切 $th x = \frac {sh x} {ch x} = \frac {e^x - e^{-x}} {e^x + e^{-x}}$


### 数列的极限

$$ \lim_{n \to \infty} x_n = a \Longleftrightarrow \forall \varepsilon > 0, \exists \text{ positive integer } N, \text{ when } n>N, |x_n - a | \lt \varepsilon$$

收敛数列的性质：
- 极限的唯一性
- 收敛数列的有界性

    如果数列无界，那么数列一定发散。数列有界是数列收敛的必要条件，但不是充分条件
- 收敛数列的保号性

    推论：如果数列从某项起有大于/小于等于0，且极限也具有同样性质
- 收敛数列与其子数列间的关系

    如果数列有两个子数列收敛于不同的极限，那么数列是发散的。一个发散的数列也有可能有收敛的子数列

### 函数的极限

自变量的变化过程：
1. 自变量x任意地接近于有限值或者说趋于有限值时
2. 自变量x的绝对值无限增大即趋于无穷大时
    *水平渐近线*

在这个过程中，对应的函数值$f(x)$的变化情形

$$ \lim_{x \to x_0} f(x) = A \Longleftrightarrow \forall \varepsilon > 0, \exists \delta > 0 , \text{ when } 0 < | x-x_0 | < \delta, |f(x) -A| \lt \varepsilon$$
$$ \lim_{x \to \infty} f(x) = A \Longleftrightarrow \forall \varepsilon > 0, \exists X > 0 , \text{ when } |x| \gt X, |f(x) -A| \lt \varepsilon$$

函数极限的性质

- 函数极限的唯一性
- 函数极限的局部有界性
- 函数极限的局部保号性
- 函数极限与数列极限的关系

### 无穷小与无穷大

- 无穷小

- 无穷大
    铅直渐近线

### 极限运算法则

1. 两个无穷小的和是无穷小
2. 有界函数与无穷小的乘积是无穷小
3. 四则运算法则