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

1. 두 벡터 $\mathbf{x},\mathbf{y}$가 orthogonal
$\mathbf{x}^T\mathbf{y}=0$ (in real), $\overline{\mathbf{x}}^T\mathbf{y}=0$ (in complex)
2. Orthogonal basis of subspaces
$\forall \mathbf{v}_i,\mathbf{v}_j\in {\rm Basis}, \mathbf{v}_i^T\mathbf{v}_j=0$ if $\mathbf{v}_i^T\mathbf{v}_i=1$ for all $i$, it is called *orthonormal basis*.
3. Subspaces $R$과 $N$이 orthogonal
$\forall \mathbf{x}\in R,\, \forall \mathbf{y}\in N,\, \mathbf{x}^T\mathbf{y}=0$
2의 *orthonormal basis*를 열로 가지는 행렬$Q$을 생각해보자.
4. $Q^TQ=I$
$\Rightarrow (Q^TQ)^T=QQ^T=I \Rightarrow Q^T=Q^{-1}$
심지어 $\\| Q\mathbf{x} \\| = \\| \mathbf{x} \\|$가 된다.
$(\because (Q\mathbf{x})^T(Q\mathbf{x})=\mathbf{x}^T Q^T Q \mathbf{x}=\mathbf{x}^T\mathbf{x})$