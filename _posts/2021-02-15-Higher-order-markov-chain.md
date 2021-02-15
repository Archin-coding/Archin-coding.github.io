---
title:  "Transition probability tensor of a higher-order Markov chain"
excerpt: "Tensor와 higher-order Markov chain에 관한 논문"
use_math: true
toc: true
toc_sticky: true
categories:
  - paper
  - Tensor
  - Higher order Markov chain
tags:
  - Higher order Markov chain
  - Tensor
header:
  teaser: /assets/images/blog.png
last_modified_at: 2021-02-15T23:20:00-21:00
---
# 1. Introduction
미래를 예측하는 것은 언제나 인간이 가장 하고 싶어하는 일이다. 
유효한 방법 중 하나가 바로 Markov chain을 사용하는 것이다.
그리고 쉽게 찾아볼 수 있는 Markov chain의 응용은 대부분 First-order Markov chains이다.
좋은 정리들이 이미 잘 연구되어있기도 할 뿐더러, 이 정리들은 아직 higher-order Markov chains로 확장되어 연구되지 않았다.
혹은 할 수 없거나.
때문에 higher-order Markov chains은 First-order Markov chains로 근사되어 종종 사용되어 왔다.
Tensor가
## 1.1. Markov chains
우리는 Matrix가 First-order Markov chains과 깊은 관련이 있다는 것을 충분히 알고 있다.
First-order Markov chains과 transition matrix의 정의를 다시 짚고 넘어가자.

### Definition 1
Suppose $\\{X_n \\}, n\in \mathbb{Z},$ is a sequence of stochastic functions with the same probability distribution and $i_j \in S$($S$ is state space) such that
\\[ P(X_n = i_n| X_{n-1} = i_{n-1}, X_{n-2} = i_{n-2},\ldots X_0 = i_0) = P(X_n = i_n | X_{n-1}=i_{n-1}) \\]
then  we call $\\{X_n\\}$ a first-order Markov chain.

Let $p(x,y) = P(X_n = x\| X_{n-1} = y)$, $p^n(x,y) = P(X_n = x\| X_0 = y)$ and call $p$ a transition probability matrix.

예를 들면, 다음과 같은 상태 모델이 있다고 하자.

 ![](https://raw.githubusercontent.com/Archin-coding/Archin-coding.github.io/master/assets/images/markov1.png)

### Theorem 1 (Chapman–Kolmogorov equation)
Let $\\{X_n \\}$ be a first-order Markov chain and $m,n \in \mathbb{N}$, then 
\\[
  p^{m+n}(x,y) = \sum\limits_{k\in S}p^m(x,k) p^n(k,y)
  \\]
