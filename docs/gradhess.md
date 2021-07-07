# Gradients and Hessians
To add: general aspects about gradients and Hessians, numerical vs. analytical, related properties.

## Analytical Gradients
To add: Introduction, approaches to derive analytical gradients; Lagrangian approach.

To determine the energy gradient, we first need to identify the non-variational components of the energy functional. In the case of DFT (and HF), these are the MO coefficients ($\mathbf{C}$), which exhibit an implicit dependence on the nuclear coordinates when atom-centred basis functions such as Gaussian or Slater-type orbitals are used. Considering this implicit dependence, the total energy derivative with respect to a particular nuclear coordinate $\xi$ is obtained via the chain rule {cite}`Rehn2015,Levchenko2005`:
%
```{math}
:label: eq:energy_functional_general
\frac{dE}{d\xi}=\frac{\partial E}{\partial \xi}+\frac{\partial E}{\partial\mathbf{C}}\frac{d\mathbf{C}}{d\xi} \, .
```
%
Here, $\mathbf{C}$ is the molecular orbital matrix which transforms from a set of atomic orbitals $\{\phi_\mu\}$ to a set of molecular orbitals $\{\psi_p\}$ via $\psi_p=\sum_\mu C_{\mu p}\phi_\mu$. The first term, $\partial E/\partial\xi$, is the Hellman--Feynman contribution which describes the explicit dependence of the energy on the nuclear coordinate $\xi$ through the nuclear-electron and nuclear-nuclear interaction terms of the Hamiltonian {cite}`Levchenko2005_thesis, Helgaker1988_analytical`. The second term stems from the implicit dependence of the energy on $\xi$ due to the fact that the molecular orbitals are expanded in a finite atomic-centred basis set {cite}`Helgaker1988_analytical` 
%This term would vanish if a basis set independent on atomic positions, for example a plane wave basis, were used.

It may seem at first surprising that the derivative ${\partial E}/{\partial\mathbf{C}}$ has to be computed. If the MO coefficients are obtained variationally for a specified molecular geometry, how is it that this derivative is not zero? The key to this conundrum lies in the phrase "for a specified molecular geometry". Since the DFT energy and density are constructed using a constrained LCAO parametrization, if we perform a nuclear displacement, the "old" MO coefficients no longer correspond to the minimum energy and must be re-optimized. Thus the partial derivative with respect to the MO coefficients, as well as the derivative of the MO coefficients with respect to $\xi$ are required. The explicit computation of the latter is complicated, but can be avoided by making use of a new functional, the Lagrangian, for which the partial derivative $\partial L / \partial \mathbf{C}$ is zero and constrained to the DFT/HF configuration space by construction {cite}`Levchenko2005, Helgaker2014`:
%ensuring that we re still in the H  Thus, the derivative
%Thus, even though the local points of the PES are variational with respect to the MO coefficients, the "global" energy functional is not. We must therefore, include the partial derivative with respect to the MO coefficients, as well as the derivative of the MO coefficients with respect to $\xi$, which is quite complicated to compute. However, we can avoid explicitly computing $\mathrm{d}\mathbf{C}/\mathrm{d}\xi$ by using a trick. The idea is to create a new functional, the Lagrangian ($L$), which is by construction equivalent to the energy functional, but for which the partial derivative $\partial L / \partial \mathbf{C}$ is zero \cite{Levchenko2005, Helgaker2014}:
%
```{math}
:label: eq:Lagrangian_general
L(\mathbf{C},\boldsymbol{\Lambda})=E(\mathbf{C})+\boldsymbol{\Lambda}f_c(\mathbf{C}) \, ,
```
%
where $\boldsymbol{\Lambda}$ are a set of undetermined Lagrange multipliers and $f_c(\mathbf{C})=0$ define the constraints for the non-variational parameters $\mathbf{C}$. These constraints ensure that we are moving only in the DFT/HF configuration space, rather than in the infinite space of all orthogonally equivalent combinations of orbital bases {cite}`Helgaker1988_analytical`.
%From Helgaker and Jorgensen:"At each geometry we have a set of AOs  from  which an infinite set of orthogonally equivalent orbital bases can be constructed. As the geometry changes we must pick out exactly one of these orbital bases at each geometry X. In this way an orthogonal  orbital connection is established. (A connection is called orthogonal if it  preserves orthonormality between the orbitals.) We further  require that the connection is continuous and differentiable. One may also wish to impose an additional requirement on the connection, namely that it  is translationally and rotationally  invariant. This may seem to be a trivial requirement. However, a connection is conveniently defined  in terms of atomic Cartesian displacements rather  than in terms of a set of nonredundant internal  coordinates. This implies that each  molecular geometry  may be described  in an infinite number of translationally and rotationally  equivalent ways"

By using the Lagrangian, we have shifted the difficult problem of computing ${\mathrm{d} \mathbf{C}}/{\mathrm{d}\xi}$ to the much simpler problem of determining the unknown Lagrange multipliers which satisfy $\partial L / \partial \mathbf{C}=0$. Equations for these are derived by imposing that the explicit form of $\partial L / \partial \mathbf{C}$ is zero {cite}`Helgaker2014`. Once the Lagrange multipliers have been obtained, the total derivative of the energy functional with respect to the nuclear coordinate $\xi$ can be computed as:
\begin{equation}
\frac{dE}{d\xi}=\frac{\partial L}{\partial\xi}\, .
\end{equation}

### Ground state
#### Hartree--Fock

#### DFT

#### MP2

### Excited states

#### Tamm--Dancoff approximation

## Hessians
