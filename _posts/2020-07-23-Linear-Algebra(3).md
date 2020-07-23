---
title:  "Linear Algebra and Learning from Data(3)"
excerpt: "Gilbert Strang 교수님의 Linear Algebra and Learning from Data"
use_math: true
toc: true
toc_sticky: true
toc_label: "페이지 주요 목차"
categories:
  - Linear Algebra
tags:
  - Linear Algebra
header:
  teaser: /assets/images/linearalgebra.png
last_modified_at: 2020-07-23T11:30:00-35:00
---

# Introduction
## 1.5 Orthogonal Matrices and Subspaces

우리가 일반적으로 알고 있는 **직교**(**orthogonal**)라는 단어는 두 벡터 사이의 관계 중 하나지만 이것을 확장하려고 한다.

### 1. 두 벡터 $\mathbf{x},\mathbf{y}$가 orthogonal
$\mathbf{x}^T\mathbf{y}=0$ (in real), $\overline{\mathbf{x}}^T\mathbf{y}=0$ (in complex)
### 2. Orthogonal basis of subspaces
$\forall \mathbf{v}_i,\mathbf{v}_j\in {\rm Basis}, \mathbf{v}_i^T\mathbf{v}_j=0$ if $\mathbf{v}_i^T\mathbf{v}_i=1$ for all $i$, it is called *orthonormal basis*.
### 3. Subspaces $R$과 $N$이 orthogonal
$\forall \mathbf{x}\in R,\, \forall \mathbf{y}\in N,\, \mathbf{x}^T\mathbf{y}=0$

2의 *orthonormal basis*의 **일부**를 열로 가지는 행렬$Q$를 생각해보자.
### 4. $Q^TQ=I$
$\\| Q\mathbf{x} \\| = \\| \mathbf{x} \\|$가 된다.
$(\because (Q\mathbf{x})^T(Q\mathbf{x})=\mathbf{x}^T Q^T Q \mathbf{x}=\mathbf{x}^T\mathbf{x})$

이제 *orthonormal basis*의 **전부**를 열로 가지는 행렬$Q$을 생각해보자.
### 5. Orthogonal matrices
$Q^TQ=QQ^T=I$
$(\because (Q^TQ)^T=QQ^T=I \Rightarrow Q^T=Q^{-1})$

orthogonal objects의 Example을 몇 개 살펴보자.

### Examples
#### Example of Orthogonal basis
**아다마르 행렬**(**Hadamard matrices**)
아다마르 행렬은 모든 원소가 $1,-1$이고, 행벡터와 열벡터들이 각각 orthogoanl한 행렬이다. 예시를 하나 들어보자.
$$H_2=
\begin{bmatrix}
    1 & 1 \\ 1 & -1
\end{bmatrix}
$$
$H_2$의 모든 행과 열은 각각 $\mathbb{R}^2$위에서 orthogonal이다. $H_2$를 만들었다면 $H_4$는 더 쉽게 만들 수 있다.
$$H_4=
\begin{bmatrix}
    H_2 & H_2 \\ H_2 & -H_2
\end{bmatrix}
$$

$n\times n$크기의 아다마르 행렬이 존재할 필요충분조건을 찾는 문제는 아직까지 풀리지 않은 난제중 하나이다.

**베르누이 행렬(bernoulli matrix) 문제**
베르누이 행렬은 아다마르 행렬과 비슷하게 모든 성문이 $1,-1$인 행렬이다. 사실 아다마르 행렬이 특별한 베르누이 행렬이다.

이 베르누이 행렬에 대해서도 풀리지 않은 난제가 있다. 무작위 $n\times n$ 베르누이 행렬의 열공간이 $\mathbb{R}^{n-1}$의 부분공간이 될 확률을 구하는 것이다.

$3$차원 공간을 생각해보자. 모든 가능한 벡터는 다음과 같다.

$\begin{bmatrix} 1 & 1 & 1 \end{bmatrix},\begin{bmatrix} 1 & 1 & -1 \end{bmatrix},\begin{bmatrix} 1 & -1 & 1 \end{bmatrix},\begin{bmatrix} 1 & -1 & -1 \end{bmatrix},$
$\begin{bmatrix} -1 & 1 & 1 \end{bmatrix},\begin{bmatrix} -1 & 1 & 1 \end{bmatrix},\begin{bmatrix} -1 & 1 & -1 \end{bmatrix},\begin{bmatrix} -1 & -1 & -1 \end{bmatrix}$

$8$개의 벡터중 무작위로 $3$개를 뽑았을 때 세 벡터가 모두 indepencence할 확률을 계산하면 $\frac{5}{8}$이다. $n$차원 공간에서는 어떨까?

#### Example of Orthogonal subspaces
Strang 교수님의 Linear algebra의 **Big picture**을 떠올려보자.

![](https://raw.githubusercontent.com/Archin-coding/Archin-coding.github.io/master/assets/images/linearalgebra/20200722_5.png) 

