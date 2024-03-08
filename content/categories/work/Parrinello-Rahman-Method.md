---
title: 'Parrinello-Rahman Method'
date: 2024-03-07T08:08:29+08:00
draft: false
params:
  math: true
categories: "work"
tags: ["molecular dynamics"]
summary:
---
## Equations of Motion in Parrinello-Rahman Method

Parrinello-Rahman method is an Andersen-style barostat, which introduce an extra degree of freedom bound with the volume. PR (for ease of writing) method generalizes Andersen barostat to an arbitary simulation box. Such box is described by a matrix \(\mathbf{h}=\{\mathbf{a},\mathbf{b},\mathbf{c}\}\). Then the volume \(\Omega\) is \(\|\mathbf{h}\|=\mathbf{a}\cdot(\mathbf{b}\times\mathbf{c})\). We write all other quantities in this type. For the reduced coordinates \((x_i,y_i,z_i)\) of the particle \(\mathbf{r}_i\),
$$
\mathbf{r}_i = \mathbf{h}\mathbf{s}_i=x\mathbf{a}+y\mathbf{b}+z\mathbf{c}.
$$
For the distance between \(i\) and \(j\),
$$
r_{ij}^2=\mathbf{s}_{ij}^\text{T}\mathbf{G}\mathbf{s}_{ij},
$$
where \(\mathbf{s}_{ij}=\mathbf{s}_i-\mathbf{s}_j\), \(\mathbf{G}\) is metric matrix which can be calculated by \(\mathbf{G}=\mathbf{h}^\text{T}\mathbf{h}\). To complete the notation, we note the reciprocal space by the vectors
$$
\frac{2\pi}{\Omega}\{\mathbf{b}\times\mathbf{c},\mathbf{c}\times\mathbf{a},\mathbf{a}\times\mathbf{b}\}
=\frac{2\pi}{\Omega}\boldsymbol{\sigma},
$$
where easily to find that the matrix \(\boldsymbol{\sigma}=\Omega(\mathbf{h}^\text{T})^{-1}\).

Now, similarly to Andersen barostat, we just write, not by strict derivation (of course it can be proved that in this way a NPH ensemble can be established), the Lagrangian as
$$
\mathcal{L}=\frac{1}{2}\sum_i^N m_i\dot{\mathbf{s}}_i^\text{T}\mathbf{G}\dot{\mathbf{s}}_i - \sum_{i<j}^N\phi(r_{ij}) + \frac{1}{2}W\mathrm{Tr}(\dot{\mathbf{h}}^\text{T}\dot{\mathbf{h}})-p\Omega,
$$
where \(p\) is the external pressure, \(\phi\) is pair potential, \(W\) is a virtual mass bound with \(\mathbf{h}\). Thus, the equations of motion can be obtained directly by the Lagrangian equation. We get
$$
\ddot{\mathbf{s}}_i=-\sum_{j\neq i}^Nm_i^{-1}\frac{\phi^\prime}{r_{ij}}\mathbf{s}_{ij}-\mathbf{G}^{-1}\mathbf{G}\dot{\mathbf{s}}_i,\quad i=1,...N,
$$

$$
W\ddot{\mathbf{h}}=\sum_i^N m_i\mathbf{h}\dot{\mathbf{s}}_i\dot{\mathbf{s}}_i^\text{T}-\sum_{i<j}^N \frac{\phi^\prime}{r_{ij}}\mathbf{h}\mathbf{s}_{ij}\mathbf{s}_{ij}^\text{T}-p\|\mathbf{h}\|(\mathbf{h}^{-1})^\text{T}=(\boldsymbol{\pi}-p)\boldsymbol{\sigma},
$$
where, by writing \(\dot{\mathbf{v}}_i=\mathbf{h}\dot{\mathbf{s}}_i\), \(\boldsymbol{\pi}\) can be written by
$$
\Omega\boldsymbol{\pi}=\sum_i^N m_i\mathbf{v}_i\mathbf{v}_i^\text{T}-\sum_{i<j}^N\frac{\phi^\prime}{r_{ij}}\mathbf{r}_{ij}\mathbf{r}_{ij}^\text{T},
$$
which shows that \(\boldsymbol{\pi}\) is exactly the virial tensor.

> Here the derivative involves the matrices. As for the term \(\phi(r_{ij})\), we can write it in term of \(\phi(\sqrt{\mathbf{s}_{ij}^\text{T}\mathbf{G}\mathbf{s}_{ij}})\).

## Additional Bias on Box

In enhanced sampling, sometimes the bias has effects on box. From the above discussion, the "virtual" force on the degree of freedom of volume must be a tensor. For example, as for a bias only dependent on volume, we have
$$
-\frac{\partial V_\text{bias}(\|\mathbf{h}\|)}{\partial \mathbf{h}} = -V_\text{bias}^\prime\|\mathbf{h}\|(\mathbf{h}^{-1})^\text{T}=-V_\text{bias}^\prime\boldsymbol{\sigma}.
$$

## Reference

1. Parrinello, Michele, and Aneesur Rahman. "Polymorphic transitions in single crystals: A new molecular dynamics method." _Journal of Applied physics_ 52.12 (1981): 7182-7190.
