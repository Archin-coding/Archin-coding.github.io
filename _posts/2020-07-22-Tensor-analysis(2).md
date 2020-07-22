---
title:  "Tensor Analysis-Introduction(2)"
excerpt: "Tensor Multiplications 소개"
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
last_modified_at: 2020-07-22T14:30:00-35:00
---

# 1. Introduction
## 1.2 Tensor Multiplication
이 절에서는 여러가지 **텐서곱**(**tensor multiplication**)에 대해서 설명한다.

> ### Tensor Outer Product
> 두 텐서 $\mathscr{A}=(a_{i_{1}\cdots i_{m}})\in T_{m,n}$과 $\mathscr{B}=(b_{i_{1}\cdots i_{p}})\in T_{p,n}$에 대해서 $\mathscr{A} \otimes \mathscr{B}$는 다음과 같이 계산된다.
$$\mathscr{A}\otimes \mathscr{B} = \left(a_{i_{1}\cdots i_{m}}b_{i_{m+1}\cdots i_{m+p}}\right)\in T_{m+p,n}$$

왜 이름이 outer product인지 두 벡터 $\mathbf{x}=\begin{bmatrix}x_1 & x_2\end{bmatrix}$와 $\mathbf{y}=\begin{bmatrix}y_1 & y_2\end{bmatrix}$의 tensor outer product를 해보자.

$$\mathbf{x}\otimes\mathbf{y} = (x_{i_1}y_{i_2})=\begin{bmatrix} x_1y_1 & x_1y_2\\ x_2y_1 & x_2y_2\end{bmatrix}$$

