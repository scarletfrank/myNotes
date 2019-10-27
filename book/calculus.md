# 高等数学
> - [Markdown+Math Extension](https://marketplace.visualstudio.com/items?itemName=goessner.mdmath)
> - [MathJax Site Reference](http://www.onemathematicalcat.org/MathJaxDocumentation/TeXSyntax.htm)
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
满射、单射、双射
逆映射与复合映射

#### 函数

*函数概念*

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
