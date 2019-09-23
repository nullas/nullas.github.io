---
title: Notes on ESLII

---

### 7.1

It suffices to prove $$\sum_{i=1}^{N}\text{Cov}(\hat{y}_i, y_i) = d \sigma^2_\epsilon$$. Assume the linear system to solve is 
$$
\begin{aligned}
X\beta=Y\end{aligned}\\
X\beta=\mathbf{f}(X)+\mathbf{\epsilon}.
$$
Thus, $$\hat{y}_i = X_i\beta=X_iX^+Y$$ and $$E[\hat{y}_i]=X_iX^+\mathbf{f}(X)$$ where $$X^+ = (X^*X)^{-1}X^*$$ is the pseudo inverse. It follows
$$\text{Cov}(\hat{y}_i, y_i) = E[\mathbf{\epsilon}^*_iX_iX^+\mathbf{\epsilon}].$$
Summer over $$i$$'s,
$$
\begin{aligned}
\sum_{i=1}^{N}\text{Cov}(\hat{y}_i, y_i)&=E[\mathbf{\epsilon}XX^+\mathbf{\epsilon}]\\
&=E[\text{tr}(\mathbf{\epsilon}^*XX^+\mathbf{\epsilon})]\\
&=E(\text{tr}(XX^+\mathbf{\epsilon}\mathbf{\epsilon}^*))\\
&=\text{tr}(XX^+E[\mathbf{\epsilon}\mathbf{\epsilon}^*])\\
&=\sigma_{\epsilon}^2\text{tr}(XX^+)\\
&=\sigma_{\epsilon}^2\text{tr}(X^+X)\\
&=\sigma_{\epsilon}^2\text{tr}(I_d)=d\sigma_{\epsilon}^2\\
\end{aligned}
$$


> Written with [StackEdit](https://stackedit.io/).

