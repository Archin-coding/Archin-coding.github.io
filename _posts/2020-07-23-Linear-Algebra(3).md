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
2. Orthogonal basis
$\forall v_i,v_j\in {\rm Basis}, $