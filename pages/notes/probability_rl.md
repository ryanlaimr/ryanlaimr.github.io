# Probability Theory for Reinforcement Learning

## The Inequalities of Markov and Chebyshev

For any random variable $X$ and $\epsilon>0$, the following holds:

- (Markov's Inequality): $\mathbb{P}(|X|\ge\epsilon)\le\frac{\mathbb{E}[|X|]}{\epsilon}$.
- (Chebyshev's Inequality): $\mathbb{P}([X-\mathbb{E}[X]|\ge\epsilon)\le\frac{\mathbb{V}[X]}{\epsilon^2}]$.

Combing the two inequalities: $\mathbb{P}(|\hat\mu-\mu|\ge\epsilon)\le\frac{\sigma^2}{n\epsilon^2}$.

Recall the **Central Limit Theorem** (CLT). Let $S_n=\sum_{t=1}^n(X_t-\mu)$. The CLT says that under no additional assumptions than the existence of the variance, the limiting distribution of $\frac{S_n}{\sqrt{n\sigma^2}}$ as $n\to\infty$ is a Gaussian with mean zero and unit variance. If $Z\sim N(0,1)$, then $$\mathbb{P}(Z\ge\mu)=\int_u^\infty\frac{1}{\sqrt{2\pi}}\exp(-\frac{x^2}{2})dx\le\frac{1}{u\sqrt{2\pi}}\int_u^\infty x\exp(-\frac{x^2}{2})dx=\sqrt{\frac{1}{2\pi u^2}}\exp(-\frac{u^2}{2}),$$ which gives $$\mathbb{P}(\hat\mu\ge\mu+\epsilon)=\mathbb{P}(S_n/sqrt(\epsilon^2n)\ge\epsilon\sqrt{n/\epsilon^2})\approx\mathbb{P}(Z\ge\epsilon\sqrt{n/\sigma^2})\le\sqrt{\frac{\sigma^2}{2\pi n\epsilon^2}}\exp(-\frac{n\epsilon^2}{2\sigma^2})$$.

## The Cramer-Chernoff Method and Subgaussian Random Variables

(**Subgaussianity**): A random variable $X$ is $\sigma$-subgaussian if for all $\lambda\in\mathbb{R}$, it holds that $\mathbb{E}[\exp(\lambda X)]\le\exp(\lambda^2\sigma^2/2)$.

**Moment-generating function**: $M_X:\mathbb{R}\to\mathbb{R}$ defined by $M_X(\lambda)=\mathbb{E}[\exp(\lambda X)]$.

**Cumulant-generating function**: $\psi_X(\lambda)=\log M_X(\lambda)\le\frac{1}{2}\lambda^2\sigma^2$ for all $\lambda\in\mathbb{R}$.

**THM**: If $X$ is $\sigma$-subgaussian, then for any $\epsilon\ge0$, $\mathbb{P}(X\ge\epsilon)\le\exp(-\frac{\epsilon^2}{2\sigma^2})$.

Proof (**Cramer-Chernoff Method**): $$\begin{align}\mathbb{P}(X\ge\epsilon) &= \mathbb{P}(\exp(\lambda X)\ge\exp(\lambda\epsilon))\\ &\le\mathbb{E}[\exp(\lambda X)]\exp(-\lambda\epsilon)\text{ (Markov's Ineq.)}\\&\le\exp(\frac{\lambda^2\epsilon^2}{2}-\lambda\epsilon).\text{ (Def. of subgaussianity)}\end{align}$$  Choosing $\lambda=\epsilon/\sigma^2$ completes the proof. $\Box$

Therefore, $\mathbb{P}(X\ge\sqrt{2\sigma^2\log(1/\delta)})\le\delta$, hence $X$ takes values in the interval $(-\sqrt{2\sigma^2\log(2/\delta)},\sqrt{2\sigma^2\log(2/\delta)})$.

**Properties**: Suppose that $X$ is $\sigma$-subgaussian and $X_1$, $X_2$ are independent and $\sigma_1$ and $\sigma_2$-subgaussian, then:

* $\mathbb{E}[X]=0$ and $\mathbb{V}[X]\le\sigma^2$.
* $cX$ is $|c|\sigma$-subgaussian for all $c\in\mathbb{R}$.
* $X_1+X_2$ is $\sqrt{X_1^2+X_2^2}$-subgaussian.

**Corollary**: Assume that $X_i-\mu$ are independent, $\sigma$-subgaussian random variables. Then $\forall\epsilon\ge0$, $\mathbb{P}(\hat\mu\ge\mu+\epsilon)\le\exp(-\frac{n\epsilon^2}{2\sigma^2})$$ and $$\mathbb{P}(\hat\mu\le\mu-\epsilon)\le\exp(-\frac{n\epsilon^2}{2\sigma^2})$, where $\hat\mu=\frac{1}{n}\sum_{t=1}^nX_t$.

## References

* Lattimore, T., & Szepesvári, C. (2020). _Bandit algorithms._ Cambridge University Press.