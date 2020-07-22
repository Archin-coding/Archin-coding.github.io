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
last_modified_at: 2020-07-22T11:30:00-35:00
---

Gilbert Strang 교수님의 "Linear Algebra and Learning from Data"에 대해서 공부하고 정리하여 포스팅 해보려고 한다.

필요하다면 [MIT Linear Algebra 강의](https://www.youtube.com/playlist?list=PLUl4u3cNGP61iQEFiWLE21EJCxwmWvvek)를 참고할 예정이다.

# 1.1 Multiplication $Ax$ Using Columns of $A$
$$A\bm{x} = \begin{bmatrix} 2 & 3 \\ 2 & 4 \\ 3 & 7 \end{bmatrix}\begin{bmatrix} x_1\\x_2\end{bmatrix}$$

이 간단한 행렬 방정식을 보는 방식은 $2$가지가 있다. **행**(**row**)으로 보는 것과 **열**(**column**)로 보는 것.

**행**으로 보는 방식은 우리에게 익숙하다.

$$A\bm{x} = \begin{bmatrix} 2 & 3 \\ 2 & 4 \\ 3 & 7 \end{bmatrix}\begin{bmatrix} x_1\\x_2\end{bmatrix}=\begin{bmatrix} 2x_1+3x_2 \\ 2x_1+ 4x_2 \\ 3x_1+ 7x_2 \end{bmatrix}$$

**열**로 보는 방식은 익숙하지는 않지만 이해하기 쉽다.

$$A\bm{x} = \begin{bmatrix} 2 & 3 \\ 2 & 4 \\ 3 & 7 \end{bmatrix}\begin{bmatrix} x_1\\x_2\end{bmatrix}=\begin{bmatrix} 2 \\ 2 \\ 3 \end{bmatrix}x_1 + \begin{bmatrix} 3 \\ 4 \\ 7 \end{bmatrix}x_2$$

이 관점에서 접근하면 우리는 이제 $A\bm{x}=\bm{b}$가 해를 가지는지(**solvable**)에 대한 이야기를 다음과 같이 말할 수 있다.

$\bm{b}$가 $A$의 **열공간**(**column space**)안에 있다면, $A\bm{x}=\bm{b}$는 해를 가진다.

