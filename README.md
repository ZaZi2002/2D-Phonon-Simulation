# 2D Longitudinal Acoustic and Optical Phonon Simulation

## Overview

This repository presents a two–dimensional lattice dynamics simulation of **longitudinal acoustic (LA)** and **longitudinal optical (LO)** phonon modes in a diatomic crystal with unequal atomic masses and a single nearest-neighbor harmonic spring constant.

The project combines:

- Analytical dispersion relations  
- Real-space displacement formulation  
- Time-dependent lattice animation  
- Exportable GIF visualization  

The simulation illustrates the physical distinction between acoustic and optical branches.

![2D_LA_LO](https://github.com/user-attachments/assets/bf9c8a9e-b056-4e65-b890-bdd3902d510b)

---

# Lattice Geometry

We consider a two-dimensional Bravais lattice with lattice constant $a$.

Each unit cell contains two atoms with masses:

$$
M \quad \text{and} \quad m.
$$

The equilibrium lattice positions are

$$
\mathbf{R}_{nm} = (n a, m a),
$$

where $n,m \in \mathbb{Z}$.

The second atom is shifted row-wise by $a/2$, producing a staggered two-atom basis.

---

# Harmonic Approximation

Atoms interact via a nearest-neighbor harmonic spring constant $K$.

Within the harmonic approximation, the equation of motion is

$$
M \ddot{\mathbf{u}}_M = -K \sum_{\text{n.n.}} (\mathbf{u}_M - \mathbf{u}_m),
$$

$$
m \ddot{\mathbf{u}}_m = -K \sum_{\text{n.n.}} (\mathbf{u}_m - \mathbf{u}_M).
$$

Assuming plane-wave solutions,

$$
\mathbf{u}(\mathbf{R}, t) =
\mathbf{\hat{k}}\, u_0
\cos(\mathbf{k}\cdot\mathbf{R} - \omega t),
$$

where

- $\mathbf{k} = (k_x, k_y)$ is the wavevector  
- $\mathbf{\hat{k}} = \dfrac{\mathbf{k}}{|\mathbf{k}|}$ is the longitudinal polarization  
- $u_0$ is the amplitude  

---

# Dispersion Relation

The longitudinal phonon frequencies satisfy

$$
\omega^2 = \frac{A}{2}
\pm
\sqrt{
\left(\frac{A}{2}\right)^2 - B
}.
$$

where

$$
A = 2K\left(1-\cos(ka)\right)
\left(
\frac{1}{M} + \frac{1}{m}
\right),
$$

$$
B =
\frac{
4K^2
\left(1-\cos(ka)\right)^2
}{Mm}.
$$

The two branches correspond to:

- $-$ Acoustic branch  
- $+$ Optical branch  

---

# Long-Wavelength Limit

For small wavevector $k \to 0$:

### Acoustic Mode

$$
\omega_{\text{ac}} \approx v_s k,
$$

where $v_s$ is the sound velocity.

### Optical Mode

$$
\omega_{\text{op}}(k \to 0) =
\sqrt{
2K
\left(
\frac{1}{M} + \frac{1}{m}
\right)
}
$$

Thus:

- The acoustic branch is gapless.
- The optical branch has a finite frequency at the Brillouin zone center.

---

# Atomic Displacements

The displacement fields for the two branches are:

### Longitudinal Acoustic (LA)

Atoms move **in phase**:

$$
\mathbf{u}_M(\mathbf{R},t) =
\mathbf{u}_m(\mathbf{R},t).
$$

---

### Longitudinal Optical (LO)

Atoms move **out of phase**:

$$
\mathbf{u}_M(\mathbf{R},t) = -
\mathbf{u}_m(\mathbf{R},t).
$$

These displacement relations are implemented directly in the time-dependent animation.

---

# Numerical Implementation

The simulation is implemented in Python using:

- NumPy — numerical computation  
- Matplotlib — visualization  
- Pillow — GIF export  

The atomic positions are updated according to

$$
\mathbf{R}(t) =
\mathbf{R}_0
+
\mathbf{u}(\mathbf{R}_0,t).
$$

---

