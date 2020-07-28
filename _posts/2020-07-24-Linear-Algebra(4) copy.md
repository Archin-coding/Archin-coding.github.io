---
title:  "Linear Algebra and Learning from Data(4)"
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
last_modified_at: 2020-07-27T11:30:00-35:00
---
# Introduction
## 1.6 Eigenvalues and Eigenvectors

정방행렬 $A$에 대해서 $A$의 **고유벡터**(**eigenvector**)는 $A$에 곱해도 단지 벡터의 **크기만 변할 뿐 방향은 변하지 않는** 특성이 있다. 이 때 이 **변하는 정도**가 바로 **고유값**(**eigenvalue**)이다.

고유벡터는 $A$에 의존하는 특별한 벡터이다. 만약 $n\times n$ 행렬 $A$의 고유벡터 $\mathbf{x}_1,\ldots , \mathbf{x}_n$이 일차독립이라면, 모든 $n$차원 벡터 $\mathbf{v}$는 다음과 같이 표현할 수 있다.

$\begin{cases}\mathbf{v} = c_1\mathbf{x}_1 + \cdots + c_n\mathbf{x}_n \\ A\mathbf{v} = c_1\lambda_1\mathbf{x}_1 + \cdots + c_n\lambda_n\mathbf{x}_n\\ A^k\mathbf{v} = c_1\lambda^k_1\mathbf{x}_1 + \cdots + c_n\lambda^k_n\mathbf{x}_n\end{cases}$

> #### Example
> 회전변환 $Q=\begin{bmatrix} 0 & -1 \\ 1 & 0 \end{bmatrix}$의 고유값은 $i ,-i$이다.
> $Q\begin{bmatrix} 1 \\ -i \end{bmatrix} = \begin{bmatrix} 0 & -1 \\ 1 & 0 \end{bmatrix} \begin{bmatrix} 1 \\ -i \end{bmatrix}=(i)\begin{bmatrix} 1 \\ -i \end{bmatrix}$
> $Q\begin{bmatrix} 1 \\ i \end{bmatrix} = \begin{bmatrix} 0 & -1 \\ 1 & 0 \end{bmatrix} \begin{bmatrix} 1 \\ i \end{bmatrix}=(-i)\begin{bmatrix} 1 \\ i \end{bmatrix}$

> #### 주의할 점
> 1. $A + B$의 고윳값은 일반적으로 $\lambda(A)$와 $\lambda(B)$의 합과 다르다.
> 2. $AB$의 고윳값은 일반적으로 $\lambda(A)$와 $\lambda(B)$의 곱과 다르다.
> 3. 중복된 고윳값 $\lambda_1 = \lambda_2$ 는 일차독립인 2개의 고유벡터가 있을 수도 있고 없을 수도 있다.
> 4. 실수행렬 $A$의 고유벡터가 직교하는 것과 $A^TA = AA^T$ 는 동치이다.

#### 행렬과 연립미분방정식

### Computing the Eigenvalues (by hand)
고유값과 고유벡터의 관계식에서
$$A\mathbf{x} = \lambda \mathbf{x} \Rightarrow (A-\lambda I)\mathbf{x} = \mathbf{0}$$
임을 쉽게 알 수 있다.

이 말은 $A-\lambda I$가 **singular**, 즉 $\det (A-\lambda I)=0$이 되어야 한다.

> 만약 $A$가 $A+s I$가 된다면 어떻게 될까?
> 고유벡터 $\mathbf{x}$는 그대로, 모든 고유값 $\lambda$는 $\lambda + s$가 된다.
> $\because (A+sI)\mathbf{x} = \lambda \mathbf{x} + s\mathbf{x} = (\lambda + s)\mathbf{x}$

### Similar Matrices
모든 가역행렬 $B$에 대해서, $BAB^{-1}$의 고유값은 $A$의 고유값과 같다. 각 $\lambda$에 대한 $BAB^{-1}$의 고유벡터는 $A$의 각 $\lambda$에 대한 고유벡터 $\mathbf{x}$에 $B$를 곱한 $B\mathbf{x}$가 된다.

$$\because (BAB^{-1})(B\mathbf{x} ) = BA\mathbf{x} = B\lambda \mathbf{x} = \lambda (B\mathbf{x} )$$

이 때 우리는 $BAB^{-1}$는 $A$와 **닮음**(**similar**)이라 한다.$\det (A-\lambda I)$를 구하기 어려울 때 이 아이디어를 활용하여 $A$를 점차 삼각 행렬로 만든다. 이를 **삼각화**(**triangularization**)라고 한다.

하지만 이 아이디어 또한 $B^{-1}$를 계산해야 한다는 한계점이 존재한다. 우리는 항상 더 편한 것을 추구하므로, 어떻게 하면 $B^{-1}$를 직접 계산하지 않고 행렬의 삼각화를 할 수 있을지 고민해야 한다. 다행히, 수학자들이 이미 충분히 좋은 방법을 찾았다.

> #### Schur triangularization theorem
> Every square complex matrix $A$ is unitarily similar to an upper-triangular matrix, i.e., there exists a unitary matrix $U$ such that $T = U^∗AU$ is triangular.

$A$의 삼각화 $UAU^{-1}$에서 $U$가 **유니터리 행렬**(**unitary matrix**), 즉 $U^*=U$일 때 $A$가 unitarily similar라 한다. 이 정리를 간단하게 증명해보자

proof) We use mathematical induction on size of $A$.
($n=1$) trivial.
Assume that  $n>1$, and the result holds for all matrices of size less than $n$. n. Since every complex matrix has an eigenvalue, choose an eigenvalue $\lambda$ of $A$ and an associated eigenvector $\mathbf{v}=(v_1,\ldots,v_n)$. 
Let $\mathbf{x} = \frac{\bar{v1} \mathbf{v}}{\\|\bar{v1} \mathbf{v} \\|}$ and set $u = \mathbf{x} - e_1$. And we will put $Q$ in some cases.

$$\begin{cases} Q :\text{Householder matrix associated with } u & (\mathbf{x}\neq e_1)\\Q = I & (\mathbf{x}=e_1) \end{cases}$$

Then $\mathbf{x} = Qe_1$, it means that the first column of $Q$ is $\mathbf{x}$. We already know that every householder matrix is unitary and hermitian. So $ x^{*} $ is first row of $Q^{*}$. Since $Q^{-1}=Q^{*}=Q$, $Q = \begin{bmatrix} \mathbf{x} |  V \end{bmatrix} =\begin{bmatrix} \mathbf{x}^{*} \\ V^*\end{bmatrix}$. Therefore,
$$QAQ = QA = \begin{bmatrix} \mathbf{x} |  V \end{bmatrix}= Q \begin{bmatrix} \lambda \mathbf{x} |  AV \end{bmatrix}= \begin{bmatrix} \lambda e_1 |  \begin{bmatrix} \mathbf{x}^{*} \\ V^{*}\end{bmatrix} AV \end{bmatrix}=\begin{bmatrix} \lambda & \mathbf{x}^*AV\\ \mathbf{0} & V^{*}AV \end{bmatrix}.$$
The size of $V^{*} AV$ is $(n-1)\times (n-1)$, so we can apply the induction, there exists unitary matrix $R$ such that $T_{n-1} = R^{*} (V^{*} AV)R$ is upper triangular matrix. Let
$$U = Q\begin{bmatrix} 1 & \mathbf{0} \\ \mathbf{0} & R \end{bmatrix},$$
then 
$$U^{*} U = \begin{bmatrix} 1 & \mathbf{0} \\ \mathbf{0} & R^{*} \end{bmatrix} Q^{*} Q\begin{bmatrix} 1 & \mathbf{0} \\ \mathbf{0} & R \end{bmatrix} = I.$$
So $U$ is unitary. Hence,
$T = U^{*} AU = \begin{bmatrix} 1 & \mathbf{0} \\ \mathbf{0} & R^* \end{bmatrix} QAQ \begin{bmatrix} 1 & \mathbf{0} \\ \mathbf{0} & R \end{bmatrix}$