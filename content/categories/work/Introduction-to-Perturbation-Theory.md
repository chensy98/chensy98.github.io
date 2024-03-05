---
title: 'Introduction to Perturbation Theory'
date: 2024-03-05T08:36:10+08:00
draft: false
params:
  math: true
categories: "work"
tags: ["quantum mechanics"]
summary: "Fundamentals of the perturbation theory in quantum mechanics."
---

Perturbation theory is applicable when the Hamiltonian $H$ of the system being studied can be put in the form:
$$
H = H_{0} + W
$$
where the solutions of the Schrödinger equation for $H_{0}$, so-called "unperturbed Hamiltonian", are known, and $W$, the perturbation, is called a "*stationary perturbation*" when it's time-independent. Here, $W$ should be much smaller than $H_{0}$. To make this more explicit, one shall write $W$ as
$$
W = \lambda \hat{W},\quad \lambda\ll 1
$$
where $\hat{W}$ is an operator whose matrix elements are usually comparable to those of $H_{0}$. Note $\lambda$ is real. Thus, we can write
$$
H(\lambda)=H_{0}+\lambda \hat{W}
$$

## Stationary Perturbation

### General Statement

To solve the eigen equation of
$$
H(\lambda)\ket{\psi(\lambda)} = E(\lambda)\ket{\psi(\lambda)}
$$
one can expand terms with respective to $\lambda$ in the form:
$$
\begin{align*}
E(\lambda) &= \sum_{i=0}^\infty\varepsilon_{i}\lambda^i \\
\ket{\psi(\lambda)} &=\sum_{i=0}^\infty \lambda^i\ket{i}
\end{align*}
$$
Substituting into the original equation leads to:

- for the 0th order

$$
H_{0}\ket{0}  = \varepsilon_{0}\ket{0}
$$

- for the 1st order

$$
(H_{0} - \varepsilon_{0})\ket{1} +\left( \hat{W}-\varepsilon_{1} \right) \ket{0} =0
$$

- for the $q$-th order

$$
(H_{0}-\varepsilon_{0})\ket{q} + \left( \hat{W}-\varepsilon_{1} \right) \ket{q-1} -\varepsilon_{2} \ket{q-2}-\dots -\varepsilon_{q}\ket{0} =0
$$

For convenience, to make the solution unique, the phase is chosen so that $\braket{ 0 | \psi(\lambda) }$ is real. Due to $\braket{ \psi(\lambda) | \psi(\lambda) }=1$ and picking the coefficient $\braket{ 0 | 0 }=1$ and $\braket{ m | n }\in \mathbb{R}$, we can get:
$$
\begin{align*}
\braket{ \psi(\lambda) | \psi(\lambda) }  =& \braket{ 0 | 0 }  \\\\
 &+\lambda(\braket{ 0 | 1 } +\braket{ 1 | 0 } ) \\\\
 &+\lambda^2(\braket{ 0 | 2 } +\braket{ 1 | 1 } +\braket{ 2 | 0 } ) \\\\
 &+\dots \\\\
 &+\lambda^q(\braket{ q | 0 } +\braket{ q-1 | 1 } +\dots+\braket{ 1 | q-1 } +\braket{ 0 | q } ) \\\\
 &+\dots
\end{align*}
$$
All coefficients of the power of $\lambda$ must be zero. Then the problem can be solved completely.

### Perturbation for Non-Degenerate Level

Assuming the energy level of the unperturbed Hamiltonian is $E_{n}^0$, the corresponding state is non-degenerate with the eigenfunction $\ket{\varphi_{n}}$.

We choose that
$$
\begin{align*}
\varepsilon_{0} &=E_{n}^0 \\\\
\ket{0} &= \ket{\varphi_{n}}
\end{align*}
$$

#### First-order solution

From the general statement, we can write
$$
\bra{\varphi_{n}} (H_{0}-\varepsilon_{0})\ket{1} +\bra{\varphi_{n}} (\hat{W}-\varepsilon_{1})\ket{0} =0
$$
Thus, we obtain
$$
\begin{align*}
\varepsilon_{1} & = \bra{\varphi_{n}} \hat{W}\ket{0} =\bra{\varphi_{n}} \hat{W}\ket{\varphi}  \\\\
E_{n}(\lambda) & = E_{n}^0 + \bra{\varphi_{n}} W\ket{\varphi_{n}} +O(\lambda^2)
\end{align*}
$$

If we project the formula to the basis $\{\ket{\varphi_{p}^i}\}$ other than $\ket{\varphi_{n}}$ (index $i$ indicates that level $p$ can be degenerate), we obtain
$$
\bra{\varphi_{p}^i} (H_{0}-E_{n}^0)\ket{1} +\bra{\varphi_{p}^i} (\hat{W}-\varepsilon_{1})\ket{\varphi_{n}} =0,\quad p \neq n
$$
That is
$$
(E_{p}^0-E_{n}^0)\braket{ \varphi_{p}^i | 1 } +\bra{\varphi_{p}^i} \hat{W}\ket{\varphi_{n}} =0
$$
Finally, we get the correction for the eigen function
$$
\begin{align*}
\ket{1}  & =\sum_{p\neq n}\sum_{i}\frac{\bra{\varphi_{p}^i}\hat{W}\ket{\varphi_{n}} }{E_{n}^0-E_{p}^0}\ket{\varphi_{p}^i} \\\\
\ket{\varphi_{n}(\lambda)}  & = \ket{\varphi_{n}} + \sum_{p\neq n}\sum_{i}\frac{\bra{\varphi_{p}^i}W\ket{\varphi_{n}} }{E_{n}^0-E_{p}^0}\ket{\varphi_{p}^i} + O(\lambda^2)
\end{align*}
$$

#### Second-order solution

Using the same method as above, write
$$
\bra{\varphi_{n}} (H_{0}-E_{n}^0)\ket{2} +\bra{\varphi_{n}} (\hat{W}-\varepsilon_{1})\ket{1} -\varepsilon_{2} = 0
$$
Thus,
$$
\begin{align*}
\varepsilon_{2} & =\bra{\varphi_{n}} \hat{W}\ket{1} =\sum_{p\neq n}\sum_{i}\frac{\left|\bra{\varphi_{p}^i} \hat{W}\ket{\varphi_{n}}\right|^2}{E_{n}^0-E_{p}^0} \\\\
E_{n}(\lambda) & =E_{n}^0 + \bra{\varphi_{n}} W\ket{\varphi_{n}} + \bra{\varphi_{n}} \hat{W}\ket{1} =\sum_{p\neq n}\sum_{i}\frac{\left|\bra{\varphi_{p}^i} W\ket{\varphi_{n}}\right|^2}{E_{n}^0-E_{p}^0}
\end{align*}
$$

The correction of the 2nd order of the eigen function can also be calculated without any theoretical difficulty.

### Perturbation for Degenerate Level

Here we consider the influence of the perturbation on a specific energy level, rather a single unique state. In this case, $\varepsilon_{0}=E_{n}^0$ doesn't suffice to determine the vector $\ket{0}$ any more. We need to project the eigenvalue equation of the perturbation onto the subspace of energy level $n$. Assuming the degenerate degree is $g_{n}$, we can write:
$$
\sum_{i^\prime=1}^{g_{n}}\bra{ \varphi_{n}^i} \hat{W}\ket{\varphi_{n}^{i^\prime}} \braket{\varphi_{n}^{i^\prime} | 0 }=\varepsilon_{1}\braket{ \varphi_{n}^i | 0 }
$$
It's clearly that the solution of $\ket{0}$, the coefficient of $\braket{ \varphi_{n}^i | 0 }$ can be calculated by the solution of the eigenvalue equation of $\hat{W}$ confined into the subspace of $\{\ket{\varphi_{n}^i}\}$, denoted by $\mathcal{E}\_{n}^0$. We write such trimmed matrix $\hat{W}$ as $\hat{W}^{(n)}$, and thus the problem is now to solve the vector equation:
$$
\hat{W}^{(n)}\ket{0} =\varepsilon_{1}\ket{0}
$$

In other words, to calculate the eigenvalues (to first order) and the eigenstates (to zeroth order) of the Hamiltonian corresponding to a degenerate unperturbed state $E_{n}^0$, diagonalize the matrix $W^{(n)}$, which represents the perturbation $W$, inside the eigensubspace $\mathcal{E}_{n}^0$ associated with $E_{n}^0$.

The correction for the energy can be written by
$$
E_{n,j}(\lambda)=E_{n}^0+\lambda\varepsilon_{1}^j,\quad j=1,2,\dots,f_{n}^{(1)}\leq g_{n}
$$
Note here $f_{n}^{(1)}$ is the degenerate degree after the first order correction of the state is considered. Due to the perturbation, the degeneracy will be partially removed.

### Variational Method and Ritz Theorem

For an arbitrary ket $\ket{\psi}$ in the state space. Easy to verify that the average Hamiltonian $H$ satisfy:
$$
\langle H \rangle =\frac{\braket{ \psi | H|\psi } }{\braket{ \psi | \psi } }\geq E_{0}
$$
where $E_{0}$ is the energy of the ground state, i.e., the smallest eigenvalue of $H$.

More generally, known as the **Ritz theorem**, *the average value of the Hamiltonian is stationary in the neighbourhood of its discrete eigenvalues*. To prove this, we variate the ket $\ket{\psi}$ as $\ket{\psi}+\ket{\delta\psi}$ and the increment in the Hamiltonian is $\delta \langle H \rangle$. Stating with the equation:
$$
\langle H \rangle =\frac{\braket{ \psi | H|\psi } }{\braket{ \psi | \psi } }
$$
We obtain:
$$
\braket{ \psi | \psi } \delta \langle H \rangle =\braket{ \psi | [H-\langle H \rangle ]|\delta \psi } +\braket{ \delta \psi | [H-\langle H \rangle ]|\psi }
$$
If the state $\ket{\psi}$ is stationary, $\delta \langle H \rangle$ is zero. We set:
$$
\ket{\varphi} =[H-\langle H \rangle ]\ket{\psi}
$$
And set (note ket $\ket{\delta \psi}$ can be any infinitesimal ket):
$$
\ket{\delta \psi} =\delta \lambda \ket{\varphi}
$$
where $\delta \lambda$ is infinitely small real number. Thus,
$$
2\braket{ \varphi | \varphi } \delta \lambda=0
$$
It means that:
$$
H\ket{\psi} =\langle H \rangle \ket{\psi}
$$
Consequently, the average value $\langle H \rangle$ is stationary if and only if the state vector $\ket{\psi}$ to which it corresponds is an eigenvector of $H$, and the stationary values of $\langle H \rangle$are the eigenvalues of the Hamiltonian. Thus the theorem is proved.

## Approximation for Time-Dependent Problems

### General Statement

If the perturbation is time-dependent, we should write
$$
H(t)=H_{0}+W(t)=H_{0}+\lambda \hat{W}(t)
$$
The solution should be found in the Schrödinger equation
$$
i\hbar\frac{\mathrm{d}}{\mathrm{d}t}\ket{\psi(t)} =\left[ H_{0}+\lambda \hat{W}(t) \right] \ket{\psi(t)}
$$
Assume the initial condition
$$
\ket{\psi(t=0)} =\ket{\varphi_{i}}
$$
is unique and stationary with respective to the unperturbed Hamiltonian $H_{0}$. At time $t=0$, the perturbation is applied and the initial state is no longer stationary. Usually, we want to question the probability of another state $\ket{\varphi_{f}}$ after times, i.e.,
$$
\mathscr{P}\_{if}(t) = \left| \braket{ \varphi_{f} | \psi(t) } \right| ^2
$$

### Approximate Solution of Schrödinger Equation

Generally, we can expand the ket $\ket{\psi(t)}$ in the basis $\left\{ \ket{\varphi\_{n}} \right\}$:
$$
\ket{\psi(t)} =\sum_{n}c\_{n}(t)\ket{\varphi\_{n}}
$$
We use the annotations
$$
\begin{align*}
 & c\_{n}(t)=\braket{ \varphi_{n} | \psi(t) } \\\\
 & \bra{\varphi\_{n}} \hat{W}(t)\ket{\varphi\_{k}} =\hat{W}\_{nk}(t)
\end{align*}
$$
Recall that $H_{0}$ is represented in the basis $\left\{ \ket{\varphi_{n}} \right\}$ by a diagonal matrix, i.e.,
$$
\bra{\varphi\_{n}} H_{0}\ket{\varphi\_{k}} =E_{n}\delta\_{nk}
$$
Substituting into the Schrödinger equation, we get
$$
i\hbar\frac{\mathrm{d}}{\mathrm{d}t}c_{n}(t)=E_{n}c_{n}(t)+\sum_{k}\lambda \hat{W}_{nk}(t)c_{k}(t)
$$

When the perturbation is absent, the solution is simply
$$
c_{n}(t)=b_{n}\mathrm{e}^{-iE_{n}t/\hbar}
$$
Changing the functions, we write
$$
c_{n}(t) = b_{n}(t)\mathrm{e}^{-iE_{n}t/\hbar}
$$
Introduce the Bohr angular frequency between the states $n$ and $p$:
$$
\omega_{nk}=\frac{E_{n}-E_{k}}{\hbar}
$$
Thus, we obtain the general formula
$$
i\hbar \frac{\mathrm{d}}{\mathrm{d}t}b\_{n}(t)=\lambda \sum\_{k}\mathrm{e}^{i\omega\_{nk}t}\hat{W}\_{nk}(t)b_{k}(t)
$$

To solve this formula, expand $b_{n}(t)$ to the series of $\lambda$:
$$
b_{n}(t)=\sum_{r=0}^\infty \lambda^r b^{(r)}_{n}(t)
$$
Finally, we can obtain the equation for the coefficients:

- for $r=0$

$$
i\hbar\frac{\mathrm{d}}{\mathrm{d}t}b_{n}^{(0)}(t)=0
$$

- for $r\neq 0$

$$
i\hbar\frac{\mathrm{d}}{\mathrm{d}t}b_{n}^{(r)}(t)=\sum\_{k}\mathrm{e}^{i\omega\_{nk}t}\hat{W}\_{nk}(t)b_{k}^{(r-1)}(t)
$$

#### First-order solution

The initial condition follows that $b_{n}(t=0)=\delta_{ni}$. Consequently, the coefficients of the expansion obey
$$
\begin{align*}
 & b\_{n}^{(0)}(t=0)=\delta\_{ni} \\\\
 & b\_{n}^{(r)}(t=0)=0\quad \text{if }r\geq 1
\end{align*}
$$
Immediately, it yields for all positive $t$:
$$
b\_{n}^{(0)}(t) = \delta\_{ni}
$$
which completely determines the zeroth order solution.

Thus, the first order can now be derived by
$$
i\hbar\frac{\mathrm{d}}{\mathrm{d}t}b_{n}^{(1)}(t)=\sum\_{k}\mathrm{e}^{i\omega\_{nk}t}\hat{W}\_{nk}(t)\delta\_{ki}=\mathrm{e}^{i\omega \_{ni}t}\hat{W}\_{ni}(t)
$$
Taking into account the initial condition, we find
$$
b_{n}^{(1)}(t)=\frac{1}{i\hbar}\int \_{0}^t\mathrm{e}^{i\omega_{ni}t^\prime}\hat{W}\_{ni}(t^\prime) \mathrm{d}t'
$$
Thus, the probability of the desired eigenstate $f$ is
$$
\mathscr{P}\_{if}(t)=\frac{1}{\hbar^2}\left|\int \_{0}^t\mathrm{e}^{i\omega\_{fi}t'}W_{fi}(t') \mathrm{d}t' \right|^2
$$
