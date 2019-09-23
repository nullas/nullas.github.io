---
title: Notes on ESLII

---

### 7.1

It suffices to prove $\sum_{i=1}^{N}\text{Cov}(\${y}_i, y_i) = d \sigma^2_\epsilon$. Assume the linear system to solve is 
$$
\begin{aligned}
X\beta=Y\end{aligned}\\
X\beta=\bold{f}(X)+\bold{\epsilon}.
$$
Thus, $\${y}_i = X_i\beta=X_iX^+Y$ and $E[\${y}_i]=X_iX^+\bold{f}(X)$ where $X^+ = (X^*X)^{-1}X^*$ is the pseudo inverse. It follows
$$\text{Cov}(\${y}_i, y_i) = E[\bold{\epsilon}^*_iX_iX^+\bold{\epsilon}].$$
Summer over $i$'s,
$$
\begin{aligned}
\sum_{i=1}^{N}\text{Cov}(\${y}_i, y_i)&=E[\bold{\epsilon}XX^+\bold{\epsilon}]\\
&=E[\text{tr}(\bold{\epsilon}^*XX^+\bold{\epsilon})]\\
&=E(\text{tr}(XX^+\bold{\epsilon}\bold{\epsilon}^*))\\
&=\text{tr}(XX^+E[\bold{\epsilon}\bold{\epsilon}^*])\\
&=\sigma_{\epsilon}^2\text{tr}(XX^+)\\
&=\sigma_{\epsilon}^2\text{tr}(X^+X)\\
&=\sigma_{\epsilon}^2\text{tr}(I_d)=d\sigma_{\epsilon}^2\\
\end{aligned}
$$


> Written with [StackEdit](https://stackedit.io/).

