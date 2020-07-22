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

# 1.1 Multiplication $Ax$ Using Columns of $A$
$$A\mathbf{x} = \begin{bmatrix} 2 & 3 \\ 2 & 4 \\ 3 & 7 \end{bmatrix}\begin{bmatrix} x_1\\x_2\end{bmatrix}$$

이 간단한 행렬 방정식을 보는 방식은 $2$가지가 있다. **행**(**row**)으로 보는 것과 **열**(**column**)로 보는 것.

**행**으로 보는 방식은 우리에게 익숙하다.

$$A\mathbf{x} = \begin{bmatrix} 2 & 3 \\ 2 & 4 \\ 3 & 7 \end{bmatrix}\begin{bmatrix} x_1\\x_2\end{bmatrix}=\begin{bmatrix} 2x_1+3x_2 \\ 2x_1+ 4x_2 \\ 3x_1+ 7x_2 \end{bmatrix}$$

**열**로 보는 방식은 익숙하지는 않지만 이해하기 쉽다.

$$A\mathbf{x} = \begin{bmatrix} 2 & 3 \\ 2 & 4 \\ 3 & 7 \end{bmatrix}\begin{bmatrix} x_1\\x_2\end{bmatrix}=\begin{bmatrix} 2 \\ 2 \\ 3 \end{bmatrix}x_1 + \begin{bmatrix} 3 \\ 4 \\ 7 \end{bmatrix}x_2$$

이 관점에서 접근하면 우리는 이제 $A\mathbf{x}=\mathbf{b}$가 해를 가지는지(**solvable**)에 대한 이야기를 다음과 같이 말할 수 있다.

$\mathbf{b}$가 $A$의 **열공간**(**column space**)안에 있다면, $A\mathbf{x}=\mathbf{b}$는 해를 가진다.

# 1.2 Matrix-Matrix Multiplication $AB$
이 절에서는 **행렬곱**(**matrix multiplicatoin**)을 앞에서 했던 $A\mathbf{x}$와 마찬가지로 **행** 관점과 **열** 관점으로 접근한다.

먼저 우리에게 익숙한 행 관점에서 행렬곱 $C=AB$를 계산해보자.

$$\begin{bmatrix} \cdot & \cdot & \cdot \\
a_{21} & a_{22} & a_{23} \\
\cdot & \cdot & \cdot \end{bmatrix}
\begin{bmatrix} \cdot & \cdot & b_{13} \\
\cdot & \cdot & b_{23} \\
\cdot & \cdot & b_{33} \end{bmatrix}=
\begin{bmatrix} \cdot & \cdot & \cdot \\
\cdot & \cdot & c_{23} \\
\cdot & \cdot & \cdot \end{bmatrix}$$

위 식은 행 관점의 행렬곱은 $c_{23}=(A의\,2행)\cdot (B의\,3행)$ 방식으로 계산한다는 것을 보여준다. **내적**(**inner product**)을 사용하는 것이다.

열 관점의 행렬곱을 계산하기 전에, 먼저 **외적**(**outer product**)에 대해서 짚고 넘어가자.

열벡터 $\mathbf{u}$와 행벡터 $\mathbf{v}^T$에 대해서, $\mathbf{uv}^T$는 행렬이 된다.

$$uv^T = 
\begin{bmatrix} 2\\ 2\\ 1 \end{bmatrix}
\begin{bmatrix} 3&4&6 \end{bmatrix}=
\begin{bmatrix} 6 & 8 & 12\\ 6 & 8 & 12\\ 3 & 4 & 6 \end{bmatrix}$$

이제 열 관점의 행렬 곱 $AB$를 계산해보자.

$$
AB = 
\begin{bmatrix}
  \vert & & \vert\\
  \mathbf{a}_1 & \cdots & \mathbf{a}_n\\
  \vert & & \vert
  \end{bmatrix}
\begin{bmatrix}
  -& \mathbf{b}^{*}_{1}&-\\
  -& \vdots &- \\
  -& \mathbf{b}^{*}_{n}&-
\end{bmatrix}
$$