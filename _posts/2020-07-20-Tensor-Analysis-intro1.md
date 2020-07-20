---
title:  "Tensor Analysis-Introduction(1)"
excerpt: "Tensor Ananlysis 소개"
read_time: false
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

주요 포인트는 matrix와 tensor와의 차이에 두면서 읽을 예정이다.

# 1. Introduction
## 1.1. Tensors (Hypermatrices)

일반적으로 **tensor** $\mathscr{A}=(a_{i_{1}\cdots i_{m}})$는 $a_{i_{1}\cdots i_{m}}\in \mathbf{F}:\textrm{field}$ where $i_{j}=1,\ldots,n_{j},\textrm{ for }j=1,\ldots,m$인 multi-array이다.

우리가 잘 아는 matrix로 예로 들어보자.

$$A = \begin{bmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \end{bmatrix}$$

Matrix $A=(a_{i_{1}i_{2}})$는 $i_1=1,2$, $i_2=1,2,3$ 인 **tensor**이다.