---
title:  "Linear Algebra and Learning from Data(1)"
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
last_modified_at: 2020-07-21T11:30:00-35:00
---

Gilbert Strang 교수님의 "Linear Algebra and Learning from Data"에 대해서 공부하고 정리하여 포스팅 해보려고 한다.

필요하다면 [MIT Linear Algebra 강의](https://www.youtube.com/playlist?list=PLUl4u3cNGP61iQEFiWLE21EJCxwmWvvek)를 참고할 예정이다.
# Introduction
## 1.1 Multiplication $Ax$ Using Columns of $A$
\\[A\mathbf{x} = \begin{bmatrix} 2 & 3 \\\ 2 & 4 \\\ 3 & 7 \end{bmatrix}\begin{bmatrix} x_1\\\x_2\end{bmatrix}\\]

이 간단한 행렬 방정식을 보는 방식은 $2$가지가 있다. **행**(**row**)으로 보는 것과 **열**(**column**)로 보는 것.

**행**으로 보는 방식은 우리에게 익숙하다.

\\[A \mathbf{x} = \begin{bmatrix} 2 & 3 \\\ 2 & 4 \\\ 3 & 7 \end{bmatrix} \begin{bmatrix} x_1 \\\ x_2 \end{bmatrix}=\begin{bmatrix} 2x_1+3x_2 \\\ 2x_1+ 4x_2 \\\ 3x_1+ 7x_2 \end{bmatrix}\\]

**열**로 보는 방식은 익숙하지는 않지만 이해하기 쉽다.

\\[A\mathbf{x} = \begin{bmatrix} 2 & 3 \\\ 2 & 4 \\\ 3 & 7 \end{bmatrix}\begin{bmatrix} x_1\\\ x_2\end{bmatrix}=\begin{bmatrix} 2 \\\ 2 \\\ 3 \end{bmatrix}x_1 + \begin{bmatrix} 3 \\\ 4 \\\ 7 \end{bmatrix}x_2\\]

이 관점에서 접근하면 우리는 이제 $A\mathbf{x}=\mathbf{b}$가 해를 가지는지(**solvable**)에 대한 이야기를 다음과 같이 말할 수 있다.

$\mathbf{b}$가 $A$의 **열공간**(**column space**)안에 있다면, $A\mathbf{x}=\mathbf{b}$는 해를 가진다.

### Independent Columns and Rank of $A$
**일차 독립**(**independence**)의 개념을 기억하며 $A$를 분해해보자.

방법은 다음과 같다.
> $A$의 $1$열이 $\mathbf{0}$이 아니라면 $C$에 추가한다.  
> $A$의 $2$열이 $1$열의 배수가 아니라면, $C$에 추가한다.  
> $A$의 $3$열이 $1$열과 $2$열의 일차결합이 아니라면, $C$에 추가한다. (계속)

이 과정을 반복하면 $C$는 $r(\leq n)$개의 열을 가지게 된다.

간단한 예를 들어보자.

\\[A = \begin{bmatrix}
  1 & 3 & 8 \cr
  1 & 2 & 6 \cr
  0 & 1 & 2 
\end{bmatrix}\\]

에 대해서 , 

\\[C =  \begin{bmatrix} 1 & 3 \\\ 1 & 2 \\\ 0 & 1 \end{bmatrix}\\]

가 된다. 따라서 $A$를 분해하면 다음과 같다.

\\[A = \begin{bmatrix} 1 & 3 & 8 \\\ 1& 2 & 6 \\\ 0 & 1 & 2 \end{bmatrix} = \begin{bmatrix} 1 & 3 \\\ 1 & 2 \\\ 0 & 1 \end{bmatrix} \begin{bmatrix} 1 & 0 & 2 \\\ 0 & 1 & 2 \end{bmatrix} = CR\\]

## 1.2 Matrix-Matrix Multiplication $AB$
이 절에서는 **행렬곱**(**matrix multiplicatoin**)을 앞에서 했던 $A\mathbf{x}$와 마찬가지로 **행** 관점과 **열** 관점으로 접근한다.

먼저 우리에게 익숙한 행 관점에서 행렬곱 $C=AB$를 계산해보자.

\\[\begin{bmatrix} \cdot & \cdot & \cdot \cr
a_{21} & a_{22} & a_{23} \cr
\cdot & \cdot & \cdot \end{bmatrix}
\begin{bmatrix} \cdot & \cdot & b_{13} \cr
\cdot & \cdot & b_{23} \cr
\cdot & \cdot & b_{33} \end{bmatrix}=
\begin{bmatrix} \cdot & \cdot & \cdot \cr
\cdot & \cdot & c_{23} \cr
\cdot & \cdot & \cdot \end{bmatrix}\\]

위 식은 행 관점의 행렬곱은 $c_{23}=(A의\,2행)\cdot (B의\,3행)$ 방식으로 계산한다는 것을 보여준다. **내적**(**inner product**)을 사용하는 것이다.

열 관점의 행렬곱을 계산하기 전에, 먼저 **외적**(**outer product**)에 대해서 짚고 넘어가자.

열벡터 $\mathbf{u}$와 행벡터 $\mathbf{v}^T$에 대해서, $\mathbf{uv}^T$는 행렬이 된다.

\\[uv^T = 
\begin{bmatrix} 2\cr 2\cr 1 \end{bmatrix}
\begin{bmatrix} 3&4&6 \end{bmatrix}=
\begin{bmatrix} 6 & 8 & 12\cr 6 & 8 & 12\cr 3 & 4 & 6 \end{bmatrix}\\]

이제 열 관점의 행렬 곱 $AB$를 계산해보자.

<!-- \\[AB = 
\begin{bmatrix}
  \vert & & \vert \cr
  \mathbf{a}_1 & \cdots & \mathbf{a}_n \cr
  \vert & & \vert
  \end{bmatrix}
\begin{bmatrix}
  -& \mathbf{b}^{T}_{1}&- \cr
  & \vdots & \cr
  -& \mathbf{b}^{T}_{n}&-
\end{bmatrix} =
\sum\limits_{i=1}^{n} \mathbf{a}_{i} 
\mathbf{b}^{T}_{i}
\\] -->

$(m\times n)$행렬 $\times$ $(n\times p)$행렬의 계산수는 둘다 $mnp$번으로 같다.

\\[
\begin{cases}
\text{행 관점 : } & mp번의\, 내적,& 각각\, n 번의\, 곱셈 &= mnp\cr
\text{열 관점 : } & n번의\, 외적,& 각각\, mp 번의\, 곱셈 &= mnp\cr
\end{cases}
\\]

이 책에서는 열 관점의 곱셈을 채택할 것이다.

### Insight from Column times Row

위에서 행렬 $A$를 $A=CR$로 분해하는 방법에 대해서 소개했었다.

이제 행렬 분해의 역사에 대해서 알아보자.

#### LU Factorization $A = LU$

행렬 방정식 $A\mathbf{x}=\mathbf{b}$에서 가우스 소거법을 이용하여 $A=LU$로 분해하여 방정식을 푼다.

여기서 $L$은 대각성분이 모두 $1$인 **하삼각행렬**(**lower triangular matrix**)이고, $U$는 **상삼각행렬**(**upper triangular matrix**)이다.

\\[A\mathbf{x} = \mathbf{b} \rightarrow (A = LU) \rightarrow LU\mathbf{x} = \mathbf{b} \rightarrow (\mathbf{y}=U\mathbf{x}) \rightarrow L\mathbf{y} = \mathbf{b}\\]

#### QR Factorization $A=QR$

$A$의 열들을 $1$열부터 그람-슈미트(Gram-Schmidt) 정규직교화를 거쳐서 얻은 직교행렬 $Q$와 상삼각행렬 $R$의 곱인 $A=QR$로 분해할 수 있다.

#### Digonalization $A=X\Lambda X^{-1}$

행렬의 분해와 뗄래야 뗄 수 없는게 행렬의 고윳값과 특잇값이다.

\\[A\mathbf{x} = \lambda \mathbf{x}\\]

행렬의 고유값들 $\lambda_1,\ldots,\lambda_n$과 $\mathbf{x}_1,\ldots,\mathbf{x}_n$에 대해서 $\Lambda$와 $X$를 다음과 같이 정의한다.

\\[
\Lambda=
\begin{bmatrix}
  \lambda_1 & \cdots & 0 \cr
  \vdots & \ddots & \vdots \cr
  0 & \cdots & \lambda_n
\end{bmatrix},
X = 
\begin{bmatrix}
  \vert &  & \vert \cr
  \mathbf{x}_1 & \cdots & \mathbf{x}_n \cr
  \vert &  & \vert
\end{bmatrix}
\\]

$A$와 $X$를 곱해보자.

\\[
AX=A
\begin{bmatrix}
  \vert &  & \vert \cr
  \mathbf{x}_1 & \cdots & \mathbf{x}_n \cr
  \vert &  & \vert
\end{bmatrix}=
\begin{bmatrix}
  \vert &  & \vert \cr
  \lambda_1\mathbf{x}_1 & \cdots & \lambda_n\mathbf{x}_n \cr
  \vert &  & \vert
\end{bmatrix}=
\begin{bmatrix}
  \vert &  & \vert \cr
  \mathbf{x}_1 & \cdots & \mathbf{x}_n \cr
  \vert &  & \vert
\end{bmatrix}
\begin{bmatrix}
  \lambda_1 & \cdots & 0 \cr
  \vdots & \ddots & \vdots \cr
  0 & \cdots & \lambda_n
\end{bmatrix}=
X\Lambda
\\]

$AX = X\Lambda$ $X^{-1}$을 곱해주면 행렬의 **대각화**(**Diagonalization**)을 유도할 수 있다.

행렬의 대각화는 유용한 도구이지만 식에서부터 알 수 있듯, $X$가 invertible해야 한다는 제약조건이 있고, 실제로 분해할 때에도 $X$의 역행렬을 구해야 한다는 단점이 있다.

이것은 computational 관점에서는 치명적인 단점이기 때문에 수학자들은 다음과 같은 행렬 분해를 고안해냈다.

#### Schur Decomposition $A = QTQ^*$

슈어 분해(Schur decomposition)는 행렬의 대각화와 형태가 비슷해보이지만 $Q$가 **유니터리 행렬**(**Unitary matrix**$Q^{-1}=Q^*$)이고 $T$가 대각 행렬이 아니라 상삼각행렬이라는 점이 다르다.

식에서부터 알 수 있듯 $Q$가 유니터리 행렬이기 때문에 $Q^{-1}$을 구할 필요가 없다는 장점이 있지만 $T$가 행렬의 대각화의 $\Lambda$와는 달리 대각행렬이 아니라서 $T$를 구해야한다는 단점이 있다.

이 $T$가 $\Lambda$가 되기 위해서는 $A$가 **대칭행렬**(**Symmetric matrix**)여야 한다.

#### Singular Value Decomposition $A = U\Sigma V^T$

지금까지 소개했던 행렬의 분해는 모두 **정사각행렬**(**Square matrix**)에만 적용할 수 있었다. 하지만 분해하고자 하는 행렬이 $n\times n$ 행렬이 아니라 $m\times n$ 행렬이라면 어떨까?

이러한 행렬을 분해하고자 고안된 것이 바로 **특이값분해**(**Singular Value Decomposition**(**SVD**))이다.

SVD의 장점은 **모든 행렬**에 대해서 사용할 수 있다는 것이다.

\\[A = U\Sigma V^T\\]

$\Sigma$는 대각행렬로 각 성분에 $A$의 특이값 $\sigma_1,\ldots,\sigma_r$이 온다. 그리고 $U$와 $V$에는 정규직교 특이벡터(Orthonomal singular vector)가 온다.