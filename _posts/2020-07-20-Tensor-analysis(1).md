---
title:  "Tensor Analysis-Introduction(1)"
excerpt: "Tensor Ananlysis 소개"
use_math: true
toc: true
toc_sticky: true
toc_label: "페이지 주요 목차"
categories:
  - Tensor
tags:
  - Tensor
header:
  teaser: /assets/images/tensorimg.png
last_modified_at: 2020-07-20T11:30:00-35:00
---

Liqun Qi, Ziyan Lou의
**Tensor Analysis**-Spectral Theory and Special Tensors-라는 책을 공부 해보려고 한다.

사실 Tensor는 Hypermatrices로 어렴풋이 알고만 있었는데 matrix equation으로 설명할 수 없는 더 복잡한 문제를 tensor equation으로 표현할 수 있을 것 같다는 생각에 공부를 결심했다.

책은 천천히, 꾸준히 읽을 예정이다.

# 1. Introduction
## 1.1. Tensors (Hypermatrices)

일반적으로 **텐서**(**tensor**) $\mathscr{A}=(a_{i_{1}\cdots i_{m}})$는 $a_{i_{1}\cdots i_{m}}\in \mathbf{F}:\textrm{field}$ where $i_{j}=1,\ldots,n_{j},\textrm{ for }j=1,\ldots,m$인 multi-array이다.

우리가 잘 아는 matrix로 예로 들어보자.

\\[ A = \begin{bmatrix} 1 & 2 & 3 \cr 4 & 5 & 6 \end{bmatrix} \\]

Matrix $A=(a_{i_{1}i_{2}})$는 $i_1=1,2$, $i_2=1,2,3$ 인 **텐서**이다.

여기서 $m$은 **텐서**의 **위수**(**order**)이고, $(n_1,\ldots,n_m)$은 **텐서**의 **차원**(**dimension**)이다.

행렬 $A$의 크기가 $2\times 3=6$인 것 처럼, tensor $\mathscr{A}$의 **크기**(**size**)는 $n_1\times \cdots \times n_m$이다.

만약 $n_1=\cdots = n_m$이면, $\mathscr{A}$는 $m$th order $n$-dimensional tensor라고 한다.

그리고 $m$th order $n$-dimensional real tensor을 모두 모은 집합을 $T_{m,n}$라고 한다.

만약 $\mathscr{A}=(a_{i_{1}\cdots i_{m}}) \in T_{m,n}$의 모든 원소 $a_{i_{1}\cdots i_{m}}$가 인덱스들의 모든 **치환**(**permutation**)에 대해서 같다면, $\mathscr{A}$는 **대칭 텐서**(**symmetric tensor**)라고 한다.

모든 $m$th order $n$-dimensional real symmetric tensor들의 집합을 $S_{m,n}$라고 표기하자.

다음 Example들은 대칭 텐서의 응용이다.

직관적인 이해를 위해서 Example의 Example로써 우리에게 익숙한 행렬을 들 것이다.

> ### Example 1.1. Higher order derivatives of sufficiently differentiable multi-variable functions.
> $f:\mathbb{R}^n \rightarrow \mathbb{R}$ 함수가 $m$차 미분에 대해서 연속이라고 가정하자. 임의의 $\mathbf{x}\in \mathbb{R}^n$에 대해서 $m$th order derivative $\nabla^{(m)}f(\mathbf{x})$는 $m$th order $n$-dimensional real symmetric tensor가 된다.

미분은 선형 연산자이기 때문에 교환법칙이 성립한다. 따라서 $\nabla^{(m)}f(\mathbf{x})$의 원소는 임의의 permutation에 대해서 동일하고, $\nabla^{(m)}f(\mathbf{x})$는 symmertic tensor가 된다.

행렬로 예를 들기 위해서 $f:\mathbb{R}^n \rightarrow \mathbb{R}$ 함수가 $2$차 미분에 대해서 연속이라고 가정하자.

\\[\nabla^{(2)}f(\mathbf{x})=\begin{bmatrix} \frac{\partial ^2 f}{\partial x_1 \partial x_1}(\mathbf{x}) & \cdots & \frac{\partial ^2 f}{\partial x_1 \partial x_n}(\mathbf{x})\cr \vdots & \ddots & \vdots \cr \frac{\partial ^2 f}{\partial x_n \partial x_1}(\mathbf{x}) & \cdots & \frac{\partial ^2 f}{\partial x_n \partial x_n}(\mathbf{x}) \end{bmatrix}\\]

$\nabla^{(2)}f(\mathbf{x})$가 대칭 행렬이라는 것을 알 수 있다.

> ### Example 1.2. Coefficient tensors of multi-variate homogeneous polynomial forms.
> 텐서 $\mathscr{A}=(a_{i_{1}\cdots i_{m}}) \in T_{m,n}$에 대해서 다음 동차 다항식 
>$f(\mathbf{x})=\sum\limits_{i_1,\ldots,i_m=1}^{n} a_{i_{1}\cdots i_{m}}x_{i_1}\cdots x_{i_m}$
을 만들 수 있다. 이 때 유일한 대칭 텐서 $\mathscr{B}=(b_{i_{1}\cdots i_{m}}) \in S_{m,n}$가 존재해서
>$f(\mathbf{x}) \equiv \sum\limits_{i_1,\ldots,i_m=1}^{n} b_{i_{1}\cdots i_{m}}x_{i_1}\cdots x_{i_m}$
가 된다.
$\mathscr{B}$는 $\mathscr{A}$의 **대칭화**(**symmetrization**)라고 하며 $\mathscr{B} = \mathrm{Sym}(\mathscr{A})$라고 한다.

임의의 텐서 $\mathscr{A}$에 대해서 $\mathscr{B} =\mathrm{Sym}(\mathscr{A})$를 직접 구할 수 있다. 이 과정에서 실수의 성질에 의해서 유일성 또한 보장된다.

$(i_1,\ldots,i_m)$에 대해서 가능한 모든 치환의 집합을 $P$라고 하자. $\forall (i_1,\ldots,i_m)\in P$에 대해서 $b_{i_{1}\cdots i_{m}}$를 다음과 같이 정의하자.

\\[b_{i_{1}\cdots i_{m}} = \frac{\sum\limits_{(i_1,\ldots,i_m) \in P}a_{i_{1}\cdots i_{m}}}{\|P\|}\\]

$\mathscr{B}=(b_{i_{1}\cdots i_{m}})$는 대칭 텐서이다.

다시 행렬로 대칭화를 이해해보자.

\\[A=\begin{bmatrix} 1 & 3 & 5 \cr 9 & 2 & 1 \cr 3 & 3 & 3 \end{bmatrix} \\]

라 하자. $B=(b_{ij})=\mathrm{Sym}(A)$의 각 원소는 $b_{ij}=\frac{a_{ij}+a_{ji}}{2}$이고 따라서 $B=\mathrm{Sym}(A)$ 다음과 같다.

\\[B=\begin{bmatrix} 1 & 6 & 4 \cr 6 & 2 & 2 \cr 4 & 2 & 3 \end{bmatrix}\\]

### Notation
앞으로 우리는 많은 요소들을 다룰 예정이다. 스칼라, 벡터, 행렬 그리고 텐서.

표기의 통일성과 편의를 위해서 다음 Notation을 사용하자.

1. $x,y,a,b,\ldots$ : scalars.
2. $\mathbf{x}, \mathbf{y}, \ldots$ : vectors.
3. $A, B, C, \ldots$ : matrices.
4. $\mathscr{A}, \mathscr{B}, \mathscr{C}, \ldots$ : tensors.
5. $\mathbf{0}$ : zero vector, $\mathbf{1}$ : all $1$ vector, $\mathbf{1}^{(j)}$ : $j$th unit vector.
6. $[n]= \\{1,\ldots,n \\}$.
7. $\forall \mathbf{x} \in \mathbb{R}^n$ , $\mathrm{supp}(\mathbf{x}) =$ $\\{ j \in [n] : x_j \neq 0 \\}$.
8. $\|S\|$ : cardinality where $S$ : finite set.
9. $\mathscr{O}$ : zero tensor in $T_{m,n}$, $\mathscr{I}$ : all $1$ tensor in $T_{m,n}$.