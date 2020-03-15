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

$$||A||_F = \sqrt{\sum_{i, j} A^2_{i,j}}$$

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
