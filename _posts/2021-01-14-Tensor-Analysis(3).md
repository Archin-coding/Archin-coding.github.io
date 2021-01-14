---
title:  "Tensor Analysis-Eigenvalues of Tensors(1)"
excerpt: "Tensor의 고윳값과 고유 벡터"
use_math: true
toc: true
toc_sticky: true
toc_label: "페이지 주요 목차"
categories:
  - Tensor
tags:
  - Tensor
  - eigenvalue
  - eigenvector
header:
  teaser: /assets/images/tensorimg.png
last_modified_at: 2021-01-14T11:30:00-35:00
---

오랜만에 Tensor analysis 관련 포스팅을 한다. 산업수학 관련 프로젝트, 논문 세미나가 때문에 2학기가 너무나도 바빴다. 겨울 방학이 되어서야 겨우 공부를 다시 시작한다.

잡설은 이쯤 하고, 오늘 정리할 내용은 텐서의 고윳값과 고유 벡터에 관한 여러가지 정의와 정리이다.

# 2.1 Eigenvalues and H-Eigenvalues

시작하기 전에, 행렬의 고유값을 구하는 과정을 떠올려보자.

$A\mathbf{x} = \lambda \mathbf{x}$

위 일차 연립 방정식의 해가 되는 영 아닌 벡터 $\mathbf{x}$와 그 때의 $\lambda$가 각각 행렬의 고유 벡터, 고윳값이 된다.

정리한지는 오래 되었지만 행렬은 order가 $2$인 텐서이다. order가 $m$인 텐서에 대해서는 고윳값과 고유 벡터가 어떻게 정의되어야 행렬의 그것으로부터 *자연스럽게* 확장될까?

## 2.1.1. Definitions and Basic Properties

다시 고윳값과 고유 벡터를 구하기 위한 행렬 방정식 $A\mathbf{x} = \lambda \mathbf{x}$로 돌아와보자. 좌변은 행렬과 벡터가 곱해져서 벡터가 되었고, 우변은 스칼라와 벡터가 곱해져서 벡터가 된다. 이 좌변과 우변의 관계를 텐서의 관점에서 *자연스럽게* 확장 시켜보자.

다행스럽게도, 우리는 텐서에 벡터를 곱해서 벡터가 되는 곱을 알고 있다. 바로 **$k$-mode product**이다.

$\left(\mathscr{A}\mathbf{x}^{m-1} \right)_i = \lambda x_i^{m-1}$

위 식을 만족하는 $\mathbf{x}$와 그 때의 $\lambda$를 우리는 $\mathscr{A}$의 고유 벡터와 고윳값으로 부르자.

그리고 벡터 $\mathbf{x}$의 각각의 원소를 $m-1$ 제곱한 벡터를 $\mathbf{x}^{[m-1]}$로 표기하면 식은 다음과 같아진다.

$\mathscr{A}\mathbf{x}^{m-1}  = \lambda \mathbf{x}^{[m-1]}$

행렬의 경우와 마찬가지로, $\mathscr{A}$의 모든 고윳값들의 집합을 **spertrum**라고 하며, 가장 크기가 큰(norm이 큰) 고윳값을 $\mathscr{A}$의 **spectral radius**라고 하며 $\rho (\mathscr{A})$로 표기한다.

또한, $\mathscr{A}$의 eigenpair $(\lambda, \mathbf{x})$와 모든 실수 $\alpha$에 대해서 $(\alpha \lambda, \mathbf{x})$ 또한 $\mathscr{A}$의 eigenpair가 된다. 또한, 행렬의 경우와 마찬가지로 항등 텐서 $\mathscr{I}$에 대해서 다음 성질을 가진다.

### Proposition 2.1
Let $\mathscr{A}\in T_{m,n}$ and $\alpha, \beta \in \mathbb{R}$. If $(\lambda, \mathbf{x})$ is an eiganpair of $\mathscr{A}$, then $(\alpha\lambda + \beta, \mathbf{x})$ is an eigenpair of $\alpha \mathscr{A} + \beta \mathscr{I}$.

### H-Eigenvalues and H-Eigenvectors
텐서 $\mathscr{A}$가 **H-eigenvalue**를 가진다는 것은 실 고유 벡터를 가진다는 말과 같다. 즉,

$\mathscr{A}\mathbf{x}^{m-1}  = \lambda \mathbf{x}^{[m-1]}$

를 만족하는 실 벡터 $\mathbf{x}$가 존재할 때, $\mathbf{x}$와 그 때의 $\lambda$를 각각 **H-eigenvector**, **H-eigenvalue**라고 한다. 텐서 $\mathscr{A}$와 벡터 $\mathbf{x}$가 둘 다 실수이기 때문에, $\mathscr{A}\mathbf{x}^{m-1}$ 또한 실수이고, 따라서 고윳값 $\lambda$ 또한 실수가 된다.

H-eigenvalue가 아닌 다른 고윳값들은 **N-eigenvalue**라고 하고, 이것과 pair를 이루는 고유 벡터를 **N-eigenvector**라고 한다.

H-eigenvalue의 존재성에 대한 유용한 정리가 있다. 

### Theorem 2.2
Suppose that $\mathscr{A}\in S_{m,n}$ and $m$ is even. Then $\mathscr{A}$ **always** has H-eigenvalues, and $\mathscr{A}$ is positive definite (semidefinite) if and only if its smallest H-eigenvalue $\lambda_{H \min }(\mathscr{A})$ is positive (nonnegative).

증명은 간단하다.

다음 minimization problem을 생각해보자.

$\min \mathscr{A} \mathbf{x}^m$ subject to $\sum\limits_{i=1}^{n} x_i^m = 1, \mathbf{x} \in \mathbb{R}$.

$m$이 짝수이기 때문에 $\mathbf{x}$는 compact set위에 모두 있고, $\mathscr{A} \mathbf{x}^m$는 연속 함수이다. 따라서 $\mathscr{A} \mathbf{x}^m$를 최소화시키는 $\mathbf{x}^{\*}$는 반드시 존재한다. 따라서 $\mathscr{A}\mathbf{x}^{m-1}  = \lambda \mathbf{x}^{[m-1]}$를 만족하는 $\lambda_{\*}$와 $\mathbf{x}^{\*}$ optimal Lagrange multiplier $\lambda_{\*}$가 존재한다.

이는 $m$이 짝수일 때만 성립한다. 만약 $m$이 홀수가 되면 $\mathbf{x}$의 제약조건인 $\sum\limits_{i=1}^{n} x_i^m = 1$ 의 영역이 compact가 아니게 된다. 즉, $\mathscr{A} \mathbf{x}^m$의 최소값의 존재를 보장할 수 없다.

짝수 order뿐만 아니라 nonnegative tensor에 대한 정리도 있다.

### Theorem 2.4
Let $\mathscr{A}\in T_{m,n}$ be a nonnegative tensor. Then $\mathscr{A}$ has at least one H-eigenvalue and

$\lambda_{H\max}(\mathscr{A}) = \rho (\mathscr{A})$

Furthermore, the H-eigenvalue $\lambda_{H\max}(\mathscr{A})$ has a nonnegative H-eigenvector.

### Corollary 2.5
Essentially nonnegative tensors and Z-tensors always have H-eigenvalues.

증명은 생략하겠다.

다음은 행렬의 게르시고린의 정리(Gershgorin's theorem, Gershgorin circle theorem)를 텐서 버전으로 확장시킨 텐서 고윳값 분포에 대한 기본적인 성질이다.

### Proposition 2.6
Let $\mathscr{A}\in T_{m,n}$.  Then the eigenvalues of $\mathscr{A}$ lie in the union of $n$ disks in $\mathbb{C}$. These n disks have the diagonal entries of $\mathscr{A}$ as their centers, and the sums of the absolute values of the off-diagonal entries as their radii.

앞에서 정리하지는 않았지만 책의 1장에는 **diagonally dominated**라는 성질을 다음과 같이 정의한다.

### Diagonally Dominated Tensors
Let $\mathscr{A}\in T_{m,n}$. We say that $\mathscr{A}$ is **diagonally dominated** if for any $i\in [n]$ we have

$2a_{i\cdots i} \geq \sum\limits_{i_2,\ldots , i_m=1}^{n} \| a_{i i_2 \cdots i_m} \|$.

그럼 **diagonally dominated**과 **Proposition 2.6**으로부터 다음과 같은 Corollary들을 얻을 수 있다.

### Corollary 2.7. 
An even-order symmetric, diagonally dominated tensor is positive semidefinite. An even-order symmetric, diagonally strictly dominated tensor is positive definite.

### Corollary 2.8.
Suppose that $\mathscr{A}\in T_{m,n}$ is a nonnegative tensor with an equal row sum $r$. Then $r$ is the spectral radius of $\mathscr{A}$.

Next : Characteristic Polynomials