### 7.1

It suffices to prove $\sum_{i&#x3D;1}^{N}\text{Cov}(\hat{y}_i, y_i) &#x3D; d \sigma^2_\epsilon$. Assume the linear system to solve is 
$$
\begin{aligned}
X\beta&#x3D;Y\end{aligned}\\
X\beta&#x3D;\bold{f}(X)+\bold{\epsilon}.
$$
Thus, $\hat{y}_i &#x3D; X_i\beta&#x3D;X_iX^+Y$ and $E[\hat{y}_i]&#x3D;X_iX^+\bold{f}(X)$ where $X^+ &#x3D; (X^*X)^{-1}X^*$ is the pseudo inverse. It follows
$$\text{Cov}(\hat{y}_i, y_i) &#x3D; E[\bold{\epsilon}^*_iX_iX^+\bold{\epsilon}].$$
Summer over $i$&#x27;s,
$$
\begin{aligned}
\sum_{i&#x3D;1}^{N}\text{Cov}(\hat{y}_i, y_i)&amp;&#x3D;E[\bold{\epsilon}XX^+\bold{\epsilon}]\\
&amp;&#x3D;E[\text{tr}(\bold{\epsilon}^*XX^+\bold{\epsilon})]\\
&amp;&#x3D;E(\text{tr}(XX^+\bold{\epsilon}\bold{\epsilon}^*))\\
&amp;&#x3D;\text{tr}(XX^+E[\bold{\epsilon}\bold{\epsilon}^*])\\
&amp;&#x3D;\sigma_{\epsilon}^2\text{tr}(XX^+)\\
&amp;&#x3D;\sigma_{\epsilon}^2\text{tr}(X^+X)\\
&amp;&#x3D;\sigma_{\epsilon}^2\text{tr}(I_d)&#x3D;d\sigma_{\epsilon}^2\\
\end{aligned}
$$


&gt; Written with [StackEdit](https://stackedit.io/).

