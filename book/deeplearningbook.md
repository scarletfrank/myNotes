> Chapter 2-4 读后感：我的数学能力还远远不够啊
## 2. Linear Algebra
Book Recommendation: *The Matrix Cookbook*


- 概念：scalar, vector, matrix, tensor

最后一个指坐标超过两维。$m \times n$矩阵指的是m行n列

- 操作：transpose, broadcasting, matrix product

element-wise product or Hadamard product $A\odot B$

线性方程组 $A x = b$

- identity matrix, matrix inversion

为了分析方程有多少个解，我们可以将A的列向量看作从origin出发的不同方向。则每一个x分量代表这个方向走多远

- linear combination, span

column space of A or range of A is a special span which is made by column vector of A

矩阵A的列空间是整个R^m的要求，意味着A至少有m列，即 n >= m

linear dependence, linear independent

一个列向量线性相关的方阵(square)被称为奇异的(singular)

- Euclidean norm, max norm, **Frobenius norm**

Frobenius范数衡量矩阵的大小，

$$ ||A||_F = \sqrt{\sum_{i, j} A^2_{i,j}} $$

- diagonal matrix, symmetric matirx, orthogonal matrix

正交矩阵指行向量和列向量是分别标准正交(orthonormal)的方阵

- eigendecomposition

- singular value decomposition, SVD

- Moore-Penrose pseudoinverse

$$A^+ = \lim_{a \to 0}(A^T A + \alpha I)^{-1} A^T$$

可以把这个求逆看作具有权重衰减的线性回归。将伪逆解释为使用正则化来稳定欠定问题。（第七章）

- Trace

- Determinant

- principal components analysis

## 3. 概率与信息论

- frequentist | Bayesian probability

前者那种概率与事件发生的概率相联系，后者涉及确定性水平

- random variable: continuous | discrete

- probability distribution
    discrete: probability mass function
    continuous: probability density function

- marginal probability distribution

- conditional probabiltiy 

- chain rule or product rule of probability

- independent, conditionally independent

- Expectation, variance, covariance, correlation

如果两个变量相互独立，那么它们的协方差为零；如果两个变量的协方差不为零，那么它们一定是相关的

常用概率分布：
- Bernoulli distribution
- Multinoulli/Categorical distribution 
- Normal/Gaussian distribution
- Multivariate normal distribution
- Exponential distribution
- Laplace distribution
- Empirical distribution

常用函数:
- logistic sigmoid
- softplus

Bayes' rule
measure theory

Shannon entropy

$$ H(x) =  $$

对整个概率分布中的不确定性总量进行量化

KL散度 Kullback-Leibler divergence，衡量两个分布的差异。跟KL散度密切联系的是交叉熵(cross-entropy)

$$ D_{KL}(P||Q) $$


结构化概率模型，或者图模型


## 4. 数值计算

> 优化和线性方程组的求解

- underflow/overflow

e.g. softmax function

- 病态条件

条件数是函数相对于输入的微小变化而变化的快慢程度。比如求解线性方程组时，矩阵求逆，条件数为最大和最小特征值模之比。

- 基于梯度的优化方法

梯度是相对一个向量求导的倒数。包含所有偏导数的向量。

*Jacobian and Hessian Matrix*

对于输入和输出都为向量的函数的所有偏导数，包含所有这样的偏导数的矩阵被称为**Jacobian**矩阵；当我们的函数具有多维输入时，二阶导数也有很多，合并为一个矩阵为**Hessian**矩阵，等价于梯度的Jacobian矩阵

利用Hessian的特征值分解，可以将二阶导数测试拓展到多维情况。仅使用梯度信息的优化算法称为一阶优化算法，如梯度下降。使用Hessian矩阵的优化算法称为二阶最优化算法，如牛顿法。

常用假设：Lipschitz连续

约束优化，KKT方法。引入一个广义拉格朗日函数。

实例：线性最小二乘法

## 5. 机器学习基础

“学习”的定义，任务T和性能度量P，经验E。
样本 example，特征 feature

### .1

#### 任务

有很多种：分类、回归、

#### 性能度量

准确率、错误率、测试集

####  经验

无监督/监督学习
强化学习算法会和环境进行交互

**Linear Regression**

正规方程(normal equation)

### .2

独立同分布假设(i.i.d. assumption)：每个数据集中的样本都是彼此相互独立的，并且训练集和测试集是同分布的，采样自相同的分布

欠拟合和过拟合：指模型不能在训练集上获得足够低的误差，指训练误差和测试误差之间的差距太大

模型的容量(capacity)：拟合各种函数的能力

奥卡姆剃刀。

量化模型容量的方法：Vapnik-Chervonenkis维度，VC维

参数模型和非参数模型

没有免费午餐定理(no free lunch theorem)

正则化：给代价函数添加被称为正则化项的惩罚。正则化是指修改学习算法，使其降低泛化误差而非训练误差。

### .3

用于挑选超参数的数据子集被称为验证集。

### .4

> 用统计方法刻画泛化、欠拟合和过拟合

点估计是数据的任意函数。

偏差。

无偏估计量，渐进无偏估计量。unbiased, asymptotically unbiased

方差和标准差。

偏差度量着偏离真实函数或参数的误差期望，而方差度量着数据上任意特定采样可能导致的估计期望的偏差。

均方误差(mean squared error, MSE)与U型曲线

$$MSE = $$

### .5 最大似然估计

> 希望有些准则从不同模型中得到特定函数作为好的估计，最常用的准则是最大似然估计

使用似然对数不会改变其argmax，将乘积转化为求和形式。

$$\theta_{ML} = arg \max_{\theta} E_{x ~ \hat {p}_{data}} \log p_{model} (x; \theta) $$

一种解释最大似然估计的观点是将它看作最小化训练集上的经验分布和模型分布之间的差异，两者的差异程度可以通过KL散度度量。左边一项仅涉及数据生成过程。意味着最小化KL散度时，最小化右边一项。最小化KL散度其实就是在最小化分布之间的交叉熵。

$$D_{KL} (\hat {p}_{data}||p_{model}) = E_{x ~ \hat {p}_{data}} [\log \hat {p}_{data} (x) - \log p_{model} (x)]$$

