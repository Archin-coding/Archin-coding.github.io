---
title:  "Tensor Analysis-Eigenvalues of Tensors(2)"
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
  - characteristic polynomial
header:
  teaser: /assets/images/tensorimg.png
last_modified_at: 2021-01-19T11:30:00-35:00
---

지난 시간에는 텐서의 고윳값과 고유 벡터, H-eigenvalue, H-eigenvector에 대해서 이야기를 했었다.
고윳값과 고유 벡터는 characteristic value, characteristic vector 라고 불리기도 한다. 우리는 행렬 $A$의 고윳값과 고유벡터가 만족시키는

\\[ A\mathbf{x} = \lambda \mathbf{x}\\]

의 관계에서부터

\\[ \det (A- \lambda I ) = 0 \\]

를 쉽게 유추할 수 있고, 이 식을 만족시키는 $\lambda$와 그 때의 $\mathbf{x}$를 찾는 방법으로 행렬 $A$의 고윳값과 고유벡터를 구한다.

이 때 $\det (A- \lambda I )$를 $A$의 특성 다항식(characteristic polynomial)이라 하고 $p_{A} (\lambda )$로 표기한다. 
즉, $A$의 고윳값은 특성 방정식 $p_{A} (\lambda ) = 0$의 해가 된다.

그렇다면, 텐서 $\mathscr{A}$의 특성 다항식은 어떤 형태를 하고, 어떤 성질을 가지고 있을까?

# 2.1. Eigenvalues and H-Eigenvalues

## 2.1.3. Characteristic Polynomial

이 책에서는 텐서의 특성 다항식을 **resultant**로 정의하고 있다.
정확히 말하면 텐서의 고윳값을 구하는 식인  

\\[\left(\mathscr{A}\mathbf{x}^{m-1} \right)_i = \lambda x_i^{m-1}\\]

에서 $n$개의 homogeneous polynomials의 resultant로 정의하고 있다.
이를 직관적으로 이해하자면, $n$개의 homogeneous polynomials의 각각의 근을 모두 가지는 어떠한 polynomial을 상상하면 충분할 것 같다.
이를 행렬의 경우와 비슷하게 $\phi_{\mathscr{A}} (\lambda )$로 표기한다.

잠깐 아주 간단한 행렬의 케이스로 돌아가보자.

\\[ A = \begin{bmatrix} a & b \cr c & d \end{bmatrix} \\]

우리는 이 행렬의 행렬식 $\det (A) = ad - bc$ 라는 것을 너무나도 잘 알고 있다.
그럼 이 $A$의 특성 다항식을 생각해보자.

\\[ \begin{align\*} p_{A} (\lambda ) &= \det (A - \lambda I) \cr
&= det \left( \begin{bmatrix} a - \lambda & b \cr c & d - \lambda \end{bmatrix} \right) \cr 
&= (a - \lambda)(d - \lambda) - bc  \cr 
&= \lambda^{2} -(a+d)\lambda +(ad-bc) \end{align\*}\\]

뭔가 감이 오는가? 
행렬 $A$의 행렬식은 특성 다항식 $p_{A} (\lambda )$의 상수항, 즉 $p_{A} (\lambda )$에 $\lambda = 0$을 대입한, 또 다른 표현으로는

\\[ A\mathbf{x} = 0 \\]

의 resultant가 된다.

이와 마찬가지로 텐서 $\mathscr{A}$의 determinant는 텐서의 특성 다항식 $\phi_{\mathscr{A}} (\lambda )$의 상수항, 즉 $\phi_{\mathscr{A}} (0 )$ 이다.
이를 $\det (\mathscr{A})$로 표기한다.

그리고 행렬의 대각합(trace) $\mathrm{tr} (A)$ 와 똑같이, 텐서의 대각합은 다음과 같다.

\\[ \mathrm{tr} (\mathscr{A}) = \sum\limits_{i=1}^{n} a_{ii\cdots i} \\]

행렬의 경우와 마찬가지로, 텐서의 characteristic polynomial, determinant, trace의 관계에 관한 몇 가지 중요한 성질이 있다.

### Theorem 2.12.
Suppose that $\mathscr{A} \in T_{m,n}$. Then we have the following conclusions:

1. A complex number $\lambda$ is an eiganvalue of $\mathscr{A}$ if and only if it is a root if the chatacteristic polynomial $\pi_{\mathscr{A}} (\lambda)$.
2. The number of eigenvalues of $\mathscr{A}$ is $d = n(m-1)^{n-1}$. their product is equal to $\det (\mathscr{A})$.
3. If $\mathscr{A}$ is diagonal, then $\mathscr{A}$ has $n$ H-eigenvalues, which are its diagonal entries, with corresponding unit vectors as theig H-eigenvectors. Each of these H-eigenvalues is of multiplicity $(m-1)^{n-1}$, and $\mathscr{A}$ has no N-eigenvalues.
4. The sum of all the eigenvalues of $\mathscr{A}$ is
 \\[ (m-1)^{n-1} \mathrm{tr} (\mathscr{A}) \\]

### Theorem 2.13.
Suppose that $\mathscr{A} \in T_{m,n}$. Then we have the following conclusions.

1. The eigenvalues of $\mathscr{A}$ lie in the union of n disks in $\mathbb{C}$. These $n$ disks have the diagonal entries of $\mathscr{A}$ as their centers, and the sums of the asolute values of the off-diagonal entries as their radii.
2. If ons of these $n$ disks is disjoint with the order $n-1$ disks, then there are exactly $(m-1)^{n-1}$ eigenvalues which lie in this disk, and when $m$ is even there is at least one H-eigenvalue which lies in this disk.
3. If $k$ of these $n$ disks are connected but disjoint with the order $n-k$ disks, then there are axactly $k(m-1)^{n-1}$ eigenvalues which lie in the union of there $k$ disks. Moreover when $m$ is even at least one H-eigenvalue lies in this union if one of the following three conditions holds:
   1. $k$ is odd;
   2. $k$ is even and the other $n-k$ disks are on the left side of this union;
   3. $k$ is even and the other $n-k$ disks are on the right side of this union.


## 2.1.4. Some Properties of Determinants
이 절에서는 텐서의 determinant의 몇 가지 기본적인 성질들을 소개한다.

### Proposition 2.14.
For any $\mathscr{A} \in T_{m,n}$, the determinant of $\mathscr{A}$, termed $\det (\mathscr{A})$, is a homogeneous polynomial is the entries of $\mathscr{A}$, with the degree $d=n(m-1)^{n-1}$. The degree of $a_{i\cdots i}$ in $\det (\mathscr{A})$ is not greater than $(m-1)^{n-1}$.

### Corollary 2.15.
For any real number $\alpha$, $\det (\alpha \mathscr{A}) = \alpha^{n(m-1)^{n-1}} \det (\mathscr{A})$.

### Proposition 2.16.
For any $\mathscr{A} \in T_{m,n}$, $\prod\limits_{i=1}^{n} a_{i\cdots i}^{(m-1)^{n-1}}$ is a term of the homogeneous polynomial $\det (\mathscr{A})$.
In partidular, is $\mathscr{A}$ is diagonal, then

\\[ \det (\mathscr{A}) = \prod\limits_{i=1}^{n} a_{i\cdots i}^{(m-1)^{n-1}} \\]

### Proposition 2.17.
In the expression of $\det (\mathscr{A})$, except for the term

\\[ \prod\limits_{i=1}^{n} a_{i\cdots i}^{(m-1)^{n-1}} \\]

as specified by Proposition 2.16, the total degree with respect to $a_{1\cdots 1}, a_{2\cdots 2}, \ldots , a_{n\cdots n}$ is not greater than $n(m-1)^{n-1}-2$.


**Next : E-Eigenvalues and Z-Eigenvalues**