---
title: Notes on numerical linear algebra
layout: page

---

### 4.1
- (a) $\begin{bmatrix}
3 & 0 \\
0 & -2
\end{bmatrix}=
\begin{bmatrix}
1 & 0 \\
0 & -1
\end{bmatrix}
\begin{bmatrix}
3 & 0 \\
0 & 2
\end{bmatrix}
\begin{bmatrix}
1 & 0 \\
0 & 1
\end{bmatrix}$;

- (b) $\begin{bmatrix}
2 & 0 \\
0 & 3
\end{bmatrix}=
\begin{bmatrix}
0 & 1 \\
1 & 0
\end{bmatrix}
\begin{bmatrix}
3 & 0 \\
0 & 2
\end{bmatrix}
\begin{bmatrix}
1 & 0 \\
0 & 1
\end{bmatrix}$;

- \(c\) $\begin{bmatrix}
0 & 2 \\
0 & 0 \\
0 & 0
\end{bmatrix}=
\begin{bmatrix}
1 & 0 & 0 \\
0 & 1 & 0\\
0 & 0 & 1
\end{bmatrix}
\begin{bmatrix}
2 & 0 \\
0 & 0 \\
0 & 0
\end{bmatrix}
\begin{bmatrix}
0 & 1 \\
1 & 0
\end{bmatrix}$;

- (d) $\begin{bmatrix}
1 & 1 \\
0 & 0
\end{bmatrix}=
\begin{bmatrix}
1 & 0  \\
0 & 1
\end{bmatrix}
\begin{bmatrix}
\sqrt{2} & 0 \\
0 & 0
\end{bmatrix}
\begin{bmatrix}
\frac{\sqrt{2}}{2} & \frac{\sqrt{2}}{2} \\
\frac{\sqrt{2}}{2} & -\frac{\sqrt{2}}{2}
\end{bmatrix}$;

- (e) $\begin{bmatrix}
1 & 1 \\
1 & 1
\end{bmatrix}=
\begin{bmatrix}
\frac{\sqrt{2}}{2} & \frac{\sqrt{2}}{2}  \\
\frac{\sqrt{2}}{2} & -\frac{\sqrt{2}}{2}
\end{bmatrix}
\begin{bmatrix}
2 & 0 \\
0 & 0
\end{bmatrix}
\begin{bmatrix}
\frac{\sqrt{2}}{2} & \frac{\sqrt{2}}{2} \\
\frac{\sqrt{2}}{2} & -\frac{\sqrt{2}}{2}
\end{bmatrix}$.

### 4.2
Let $A=U\Sigma V^*$, and
$$R = \begin{bmatrix}0 & \dots & 1\\ \vdots & \ddots & \vdots \\ 1 & \dots & 0 \end{bmatrix}$$
is reverse diagonal. $\text{rotate90}(A)=A^*R=V\Sigma^*(UR)^*$.  Note that $RV$ is unitary because $(UR)^*(UR)=R^*U^*UR=R^*R=I$.

### 4.3
```python
import numpy as np
import scipy as sp
import matplotlib.pyplot as plt

def show_svd(A):
	r = np.r_[-np.pi:np.pi:100j]
	circle = np.r_['0,2', np.cos(r), np.sin(r)]
	mapped = np.matmul(A, circle)
	u, s, vh = sp.linalg.svd(A)
	plt.figure(figsize=(8, 8))
	plt.plot(circle[0, :], circle[1, :])
	plt.quiver([0, 0], [0, 0], [vh[:, 0]], [vh[:, 1]], pivot='tail', angles='xy', scale_units='xy', scale=1.)
	plt.axis('equal')
	plt.xlim(-3, 3)
	plt.ylim(-3, 3)
	plt.figure(figsize=(8, 8))
	plt.plot(mapped[0, :], mapped[1, :])
	helper = np.matmul(u, np.diag(s))
	plt.quiver([0, 0], [0, 0], [helper[0, :]], [helper[1, :]], pivot='tail', angles='xy', scale_units='xy', scale=1.)
	plt.xlim(-3, 3)
	plt.ylim(-3, 3)
	plt.axis('equal')

show_svd(np.r_[[[1, 2],[0, 2]]])
```

### 4.4
False. Let $A=\begin{bmatrix}1 & 0\\ 0 & 1\end{bmatrix}$ and  $B=\begin{bmatrix}1 & 0\\ 0 & -1\end{bmatrix}$. They have the same singular values 1 and 1. But there is no $Q$ such that $A=QBQ^*$ because, otherwise, $1=det(A)=det(QBQ^*)=det(QQ^*B)=det(B)=-1$.

### 4.5
For $A \mathcal{Real} v_1+iA\mathcal{Img} v_1=\sigma_1 \mathcal{Real} u_1+i\sigma_1\mathcal{Img} u_1$, thus $A \mathcal{Real} v_1=\sigma_1 \mathcal{Real} u_1$. We can set $u_1=\mathcal{Real}u_1$.

### 5.1
$$det A = 2 = \sigma_{min} * \sigma_{max}$$
and
$$\|A\|_F=\sqrt{9}=\sqrt{\sigma_{max}^2 + \sigma_{min}^2}$$
then
$$\sigma_{max} = \frac{\sqrt{13}+\sqrt{5}}{2} \approx 2.9208$$

### 5.2
Let the rank of $A$ be $r$. $A=U\Sigma V^*$ and $\Sigma = \begin{bmatrix}\sigma_1 & & & & &\\ & \sigma_2 &  &  &\\ & & \sigma_r 
 & & \\ & & & 0 & \\  & & & & \ddots \end{bmatrix}$. Let $A_n = U\Sigma_n V^*$ where $\Sigma_n = \begin{bmatrix}\sigma_1 + 1/n & & & & &\\ & \sigma_2 &  &  &\\ & & \sigma_r 
 & & \\ & & & 1/n & \\  & & & & \ddots  \\ & & & & & 1/n\end{bmatrix}$. $\|A-A_n\|_2 = 1/n$ when $1/n < \sigma_r$.

### 5.3

$
