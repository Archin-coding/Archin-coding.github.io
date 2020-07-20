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
last_modified_at: 2020-07-20T11:30:00-35:00
---

Liqun Qi, Ziyan Lou의
**Tensor Analysis**-Spectral Theory and Special Tensors-
에 대해서 공부를 해보려고 한다.

사실 Tensor는 Hypermatrices로 어렴풋이 알고만 있었는데 matrix equation으로 설명할 수 없는 더 복잡한 문제를 tensor equation으로 표현할 수 있을 것 같다는 생각에 공부를 결심했다.

책은 천천히, 꾸준히 읽을 예정이다.

# 1. Introduction
## 1.1. Tensors (Hypermatrices)

일반적으로 **tensor** $\mathscr{A}=(a_{i_{1}\cdots i_{m}})$는 $a_{i_{1}\cdots i_{m}}\in \mathbf{F}:\textrm{field}$ where $i_{j}=1,\ldots,n_{j},\textrm{ for }j=1,\ldots,m$인 multi-array이다.

우리가 잘 아는 matrix로 예로 들어보자.

$$A = \begin{bmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \end{bmatrix}$$

Matrix $A=(a_{i_{1}i_{2}})$는 $i_1=1,2$, $i_2=1,2,3$ 인 **tensor**이다.

여기서 $m$은 **tensor**의 **위수**(**order**)이고, $(n_1,\ldots,n_m)$은 **tensor**의 **차원**(**dimension**)이다.

행렬 $A$의 크기가 $2\times 3=6$인 것 처럼, tensor $\mathscr{A}$의 **크기**(**size**)는 $n_1\times \cdots \times n_m$이다.

만약 $n_1=\cdots = n_m$이면, $\mathscr{A}$는 $m$th order $n$-dimensional tensor라고 한다.

그리고 $m$th order $n$-dimensional real tensor을 모두 모은 집합을 $T_{m,n}$라고 한다.

만약 $\mathscr{A}=(a_{i_{1}\cdots i_{m}}) \in T_{m,n}$의 모든 원소 $a_{i_{1}\cdots i_{m}}$가 인덱스들의 모든 **치환**(**permutation**)에 대해서 같다면, $\mathscr{A}$는 **대칭 텐서**(**symmetric tensor**)라고 한다.

모든 $m$th order $n$-dimensional real symmetric tensor들의 집합을 $S_{m,n}$라고 표기하자.

다음 Example들은 대칭 텐서의 응용이다.

> ### Example 1.1. Higher order derivatives of sufficiently differentiable multi-variable functions.
> $f:\mathbb{R}^n \rightarrow \mathbb{R}$ 함수가 $m$차 미분에 대해서 연속이라고 가정하자. 임의의 $\mathbf{x}\in \mathbb{R}^n$에 대해서 $m$th order derivative $\nabla^{(m)}f(\mathbf{x})$는 $m$th order $n$-dimensional real symmetric tensor가 된다.

> ### Example 1.2. Coefficient tensors of multi-variate homogeneous polynomial forms.
> 텐서 $\mathscr{A}=(a_{i_{1}\cdots i_{m}}) \in T_{m,n}$에 대해서 다음 동차 다항식 
$$f(\mathbf{x})=\sum\limits_{i_1,\ldots,i_m=1}^{n} a_{i_{1}\cdots i_{m}}x_{i_1}\cdots x_{i_m}$$을 만들 수 있다. 이 때 유일한 대칭 텐서 $\mathscr{B}=(b_{i_{1}\cdots i_{m}}) \in S_{m,n}$가 존재해서
$$f(\mathbf{x}) \equiv \sum\limits_{i_1,\ldots,i_m=1}^{n} b_{i_{1}\cdots i_{m}}x_{i_1}\cdots x_{i_m}$$가 된다.
$\mathscr{B}$는 $\mathscr{A}$의 **대칭화**(**symmetrization**)라고 하며 $\mathscr{B} = \mathrm{Sym}(\mathscr{A})$라고 한다.