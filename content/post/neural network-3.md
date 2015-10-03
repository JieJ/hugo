+++
date = "2015-09-08T14:23:15+08:00"
draft = false
title = "neural network--backpropagation"

+++

#### How the backpropagation algorithm works

###### 1. Warm up: a fast matrix-based approach to computing the output from a neural network
基于矩阵前向计算神经网络输出。

###### 2. The two assumptions we need about the cost function
* cost function can be written as an average
$$ C = \frac {1}{n} \sum_xC_x $$
* cost function can be written as a function of the outputs from the neural network
$\begin{eqnarray} C = \frac{1}{2} \|y-a^L\|^2 = \frac{1}{2} \sum_j (y_j-a^L_j)^2,\tag{27}\end{eqnarray}$
对于输出层来说，我们就是这么做的。
但是对于隐藏层，如何将损失函数写成是关于这一层输出的函数呢？

##### 3. The Hadamard product, s⊙t
elementwise multiplication
$\begin{eqnarray}
\\left[\begin{array}{c} 1 \\ 2 \end{array}\right] 
  \odot \left[\begin{array}{c} 3 \\ 4\end{array} \right]
= \left[ \begin{array}{c} 1 * 3 \\ 2 * 4 \end{array} \right]
= \left[ \begin{array}{c} 3 \\ 8 \end{array} \right].
\tag{28}\end{eqnarray}$

##### 4. The four fundamental equations behind backpropagation

首先计算神经元残差 $\delta^l_j$
再将残差与梯度 $\partial C/ \partial w^l_{jk}$ 与 $\partial C/ \partial b^l_j$ 联系起来。
$\partial C/ \partial w^l_{jk}$