Algebraic diagrammatic construction
===================================
The algebraic diagrammatic construction (ADC) scheme for the polarization propagator is a method to describe excited states and related properties based on the Møller-Plesset perturbation theory partition of the Hamiltonian {cite}`Dreuw2015`. The original derivation of ADC is related to many-body Green's function theory and relies on the perturbation series expansion of the polarization propagator {cite}`Dreuw2015`. This propagator describes how a perturbation of the electron density propagates through a system of interacting electrons. Such a process can be imagined as a sequence of excitation and de-excitation events, captured in the following spectral representation {cite}`Schirmer1982, Wormit2009`:

```{math}
:label: eq:ph_propagator
\Pi_{pq,rs}(\omega)=\frac{1}{\hbar}\sum_{n>0}\left(\frac{\bra{0}\hat{a}_q^\dagger\hat{a}_p\ket{n}\bra{n}\hat{a}_r^\dagger\hat{a}_s\ket{0}}{\omega-\omega_{n0}+i\gamma_n}+\frac{\bra{0}\hat{a}_r^\dagger\hat{a}_s\ket{n}\bra{n}\hat{a}_q^\dagger\hat{a}_p\ket{0}}{-\omega-\omega_{n0}-i\gamma_n}\right)\,,%=\Pi_{+}(\omega)+\Pi_{-}(\omega)\, ,
```
where $\hbar$ is the reduced Planck constant, $\hat{a}_p$ and $\hat{a}_q^\dagger$ are the annihilation and, respectively, creation operators, acting on single-electron states $\chi_p$, respectively, $\chi_q$ of the many-body ground state $\ket{0}$, or excited state $\ket{n}$. The summation is over all electronically excited states $\ket{n}$, $\omega_{n0}=(E_n-E_0)/\hbar$ is the angular frequency corresponding to the total energy difference between the excited state and the ground state, and $\gamma_n$ is the half-width broadening corresponding to the lifetime of the excited state $\ket{n}$. 

```{figure} /img/adc/propagator.svg
---
scale: 100%
name: fig-propagator
align: left
---
Illustration of the propagation of an excitation in a many-electron system (inspired from Ref. {cite}`mattuck1992`): (a) a particle-hole pair is created by photon absorption; (b) the pair propagates through the system; (c) the particle and hole interact (the interaction is marked by a wiggly line); (d) the particle interacts with another particle in the system, lifting it out of its place and creating a new particle-hole pair (excitation); (e) the particle interacts with the lifted-out particle and knocks it back into the hole (de-excitation); (f) the particle and hole recombine and emit a photon. (g) Illustration of the series expansion of the polarization propagator (adapted from {cite}`Wormit2009`).
```
A few of the possible excitation and de-excitation pathways are schematically illustrated in {numref}`Fig. {number} <fig-propagator>`. A photon is absorbed by the system, creating an electron-hole pair ({numref}`Fig. {number} <fig-propagator>`a). The electron and hole propagate through the system ({numref}`Fig. {number} <fig-propagator>`b) interacting with each other and with other particles ({numref}`Fig. {number} <fig-propagator>`c, d, e). These interactions produce second-order excitations ({numref}`Fig. {number} <fig-propagator>`d) and de-excitations {numref}`Fig. {number} <fig-propagator>`e). The system returns to the ground state when, for example, a photon is emitted ({numref}`Fig. {number} <fig-propagator>`f). 

The poles and residues of the polarization propagator described by Eq. {eq}`eq:ph_propagator` represent excitation energies and transition amplitudes, respectively. One possible strategy to determine these quantities is to expand $\Pi_{pq,rs}$ in a time-dependent perturbation series based on a Hamiltonian partitioned in the same way as was done for the Møller--Plesset ground-state. This expansion is also called a diagrammatic expansion because each term in the series can be represented by a Feynman diagram ({numref}`Fig. {number} <fig-propagator>`). For example, the zeroth order term corresponds to non-interacting particles that propagate freely and is depicted by a diagram consisting of two parallel lines, one representing the particle (arrow pointing up) and the other representing the hole (arrow pointing down). This diagram corresponds to the situation depicted in {numref}`Fig. {number} <fig-propagator>`b of a particle and hole propagating through the system without any further interactions. The first order term introduces direct Coulomb and exchange interactions between the particle and hole ({numref}`Fig. {number} <fig-propagator>`c), while second order terms introduce interactions with a particle-hole pair generated by the initial particle and/or hole.
%%% %\textcolor{red}{(need to think more carefully if the following is an appropriate way to picture things:)}
%%% %The algebraic diagrammatic construction (ADC) scheme for the polarization propagator is constituted precisely by this series expansion. 
 
By truncating the series expansion of the polarization propagator to a desired order, different levels of ADC are obtained. The practical way to obtain the excitation energies and vectors is to assert that there is a non-diagonal matrix representation of the polarization propagator, construct this matrix, called the ADC matrix, and obtain the excitation energies and vectors via matrix diagonalization {cite}`Dreuw2015`. The ADC matrix elements can be deduced with the help of the Feynman diagrams in {numref}`Fig. {number} <fig-propagator>`g (see a detailed derivation in Ref. {cite}`Wormit2009`, or via an alternative formulation of the ADC equations called the intermediate state representation (ISR), discussed in detail below. 
%%% %(\textcolor{red}{here I simplified a bit -- maybe too much?})

## Intermediate state representation
As the name suggest, the intermediate state representation (ISR) approach consists in constructing the ADC matrix with the help of intermediate states $\ket{\tilde{\psi}_I}$. These are obtained by applying excitation operators to the ground state $\ket{0}$. In second quantization, the excitation operator is written as $\hat{C}_I=\{ \hat{a}_a^\dagger\hat{a}_i;\hat{a}_a^\dagger\hat{a}_b^\dagger\hat{a}_j\hat{a}_i, a<b, i<j;... \}$, where the indices $a,b...$ refer to unoccupied orbitals, while $i,j...$ represent occupied orbitals {cite}`Schirmer1991,Mertins1996,Schirmer2004`. Schematic representations of single and double excitations, which are the only two excitation classes that are needed for ADC orders up to ADC(3), are depicted in {numref}`Fig. {number} <fig-isr>`a and {numref}`Fig. {number} <fig-isr>`b, respectively.
```{figure} /img/adc/isr_adc_matrix.svg
---
scale: 100%
name: fig-isr
align: left
---
Illustration of (a) single excitations, (b) double excitations, (c) the structure of the ADC(2) matrix. The numbers in parenthesis indicate the highest order of perturbation theory used to describe each particular block.
```
The intermediate states $\ket{\tilde{\psi}_I}$ are obtained by first applying $\hat{C}_I$ to the many-body ground state:
```{math}
:label: eq:precursor
\ket{\psi_I^{0}}=\hat{C}_I\ket{0} \, , %%%-\ket{0}\bra{0}\hat{C}_I\ket{0} \, ,
```
and then performing a Gram--Schmidt orthogonalization procedure with respect to lower excitation classes (including the ground state)
to obtain precursor states $\ket{\psi_I^{\#}}$, which can then be orthonormalized symmetrically according to {cite}`Wenzel2016`:
```{math}
:label: eq:ISdefinition
\ket{\tilde{\psi}_I}=\sum_J\ket{\psi_J^{\#}}S_{IJ}^{-1/2}\, ,
```
where $S_{IJ}=\braket{\psi_I^{\#}|\psi_J^{\#}}$ are overlap integrals of the precursor states.

The elements of the ADC matrix $\mathbf{M}$ are obtained as matrix elements of the shifted Hamiltonian in the basis of the intermediate states:
```{math}
:label: eq:Mdef
M_{IJ}=\bra{\tilde{\psi}_I}\hat{H}-E_0\ket{\tilde{\psi}_J}=\sum_{K,L}S_{IK}^{-1/2}\bra{ \psi_K^{\#}}\hat{H}-E_0\ket{\psi_L^{\#}}S_{LJ}^{-1/2} \, ,
```
where $E_0$ is the ground state energy.

Having obtained an expression for the ADC matrix, we return to the series expansion of the polarization propagator. In the same way as the propagator is expanded in series, also the matrix elements can be written in terms of orders of perturbation {cite}`Wenzel2016`:
```{math}
:label: eq:Mseries
M_{IJ}^{(k+l+m)}=\sum_{K,L}\left(S_{IK}^{-1/2}\right)^{(k)}\left(\bra{\psi_K^{\#}}\hat{H}-E_0\ket{\psi_L^{\#}}\right)^{(l)}\left(S_{LJ}^{-1/2}\right)^{(m)}\, ,
```
where $k$ and $m$ are the orders of perturbation theory used for the overlap matrices $S_{IK}$ and $S_{JL}$, $l$ is the order used for the matrix elements of the shifted Hamiltonian, and the sum $k+l+m$ represents the order of the contribution to the ADC matrix $\mathbf{M}$.

Using Eq. {eq}`eq:Mseries` in combination with specific classes of excitation operators and truncating the series at the desired order, various levels of ADC theory are obtained. One aspect to note is that the excitation classes needed to construct a specific ADC level are directly connected to the order of perturbation theory. This can be easily seen from {numref}`Fig. {number} <fig-propagator>`, where the zeroth and first order terms are related to single excitations (only one particle-hole pair is involved), while second order terms involve double excitations (two particle-hole pairs are involved). To illustrate this further, we list the explicit expressions for the ADC matrix elements up to second order {cite}`Wenzel2016, Wormit2009`:
%%% %(\textcolor{red}{not completely convinced if to include -- all of -- these})
%%%
```{math}
:label: eq:adcmat_ph_ph_0
M_{ia,jb}^{(0)}=(\epsilon_a-\epsilon_i)\delta_{ab}\delta_{ij}\,,
```
```{math}
:label: eq:adcmat_ph_ph_1
M_{ia,jb}^{(1)}=-\braket{ja||ib}\,,
```
```{math}
:label: eq:adcmat_ph_ph_2
M_{ia,jb}^{(2)}&=\frac{1}{4}\delta_{ij}\sum_{c,k,l}\left[\frac{\braket{ac||kl}\braket{kl||bc}}{\epsilon_a+\epsilon_c-\epsilon_k-\epsilon_l}+\frac{\braket{ac||kl}\braket{kl||bc}}{\epsilon_b+\epsilon_c-\epsilon_k-\epsilon_l}\right]\nonumber\\ &+\frac{1}{4}\delta_{ab}\sum_{c,d,k}\left[\frac{\braket{cd||ik}\braket{jk||cd}}{\epsilon_c+\epsilon_d-\epsilon_i-\epsilon_k}+\frac{{\braket{cd||Ik}\braket{Jk||cd}}}{\epsilon_c+\epsilon_d-\epsilon_j-\epsilon_k}\right] \nonumber \\
&-\frac{1}{2}\sum_{c,k}\left[\frac{{\braket{ac||ik}\braket{jk||bc}}}{\epsilon_a+\epsilon_c-\epsilon_i-\epsilon_k}+\frac{{\braket{ac||ik}\braket{jk||bc}}}{\epsilon_b+\epsilon_c-\epsilon_j-\epsilon_k}\right] \, ,
```
```{math}
:label: eq:adcmat_ph_2p2h_1
M_{ia,klcd}^{(1)}=\braket{kl||id}\delta_{ac}-\braket{kl||ic}\delta_{ad}-\braket{al||cd}\delta_{ik}+{\braket{ak||cd}\delta_{il}}\label{eq:adcmat_ph_2p2h_1}\,,
```
```{math}
:label: eq:c2p2hph_1
M_{ijab,kc}^{(1)}=\braket{kb||ij}\delta_{ac}-\braket{ka||ij}\delta_{bc}-\braket{ab||cj}\delta_{ik}+{\braket{ab||ci}\delta_{jk}}\label{c2p2hph_1}\,,
```
```{math}
:label: eq:adcmat_2p2h_2p2h_0
M_{ijab,klcd}^{(0)}=(\epsilon_a+\epsilon_b-\epsilon_i-\epsilon_j)\delta_{ac}\delta_{bd}\delta_{ik}\delta_{jl}\,,
```
where $\delta_{pq}$ is the Kronecker delta.

The structure of the ADC(2) matrix is depicted in {numref}`Fig. {number} <fig-isr>`c. In principle, the ADC(2) matrix contains all the possible single and double excitations which can be constructed for the system of interest (using a particular basis set). However, except for very small molecules, to include all these excitations would make the ADC matrix intractably large and impossible to diagonalize. In practice, therefore, only the lowest $n$ excited states are ever constructed, where $n$ is the number of states requested by the user. This means that the space of valence excitations is easily accessible, but makes the space of core excitations impossible to reach, except for molecules with very few electrons. An approach to overcome this problem will be discussed in more detail in the next section.

## Core--valence separation
One way to reach the space of core-excitations (and be able to compute, for example, X-ray absorption spectra), without having to deal with an intractably large ADC matrix is provided by the core--valence separation (CVS) approximation. CVS is obtained by decoupling the core and valence excitation spaces and is motivated by the large energy separation between them {cite}`cederbaum1980`. Essentially, it consists of applying only excitation operators that involve one core electron ({numref}`Fig. {number} <fig-cvs>`a and b). This translates into keeping only those blocks of the ADC matrix which include one core orbital ({numref}`Fig. {number} <fig-cvs>`c) and significantly reduces the size of the matrix to be diagonalized ({numref}`Fig. {number} <fig-cvs>`d). The error introduced by this approximation is very small and system-independent {cite}`Herbst2020`.
```{figure} /img/adc/cvs_adc_matrix.svg
---
scale: 100%
name: fig-cvs
align: left
---
Illustration of the (a) single excitations and (b) double excitations involved in the CVS approximation. (c) Schematic representation of the full ADC(2) matrix and (d) the size reduction achieved by the CVS approximation.
```
The CVS approximation allows the computation of X-ray spectroscopies, which are very important techniques for the characterisation of materials, from atoms and molecules, to surfaces and condensed matter systems. In the remaining of this section we will introduce X-ray absorption spectroscopy (XAS) and review some of its features. For a more in-depth discussion see Refs. {cite}`Stohr1992` and {cite}`xrayrev2018`.

The absorption of soft X-ray electromagnetic radiation by a molecular system results in electronic excitation between core initial electronic states (localized, atomic-like) and final states that are delocalized, sometimes continuum-like. A schematic and simplified illustration of this process, alongside the corresponding XAS spectrum is shown in {numref}`Fig. {number} <fig-xas>`. 

The core level binding energies of 1s electrons are element-specific, with very large energy separations between different elements, e.g. $\sim$290 eV (C), $\sim$400 eV (N), and $\sim$500 eV (O). Additionally, atoms of the same species placed in different chemical environments have binding energies which differ by a few electron-volts. This means that absorption peaks corresponding to transitions from chemically inequivalent atoms will occur at different photon energies. The separation between these peaks is called "chemical shift" and it enables the use of XAS for chemical analysis and materials characterization. 
```{figure} /img/adc/xas.svg
---
scale: 100%
name: fig-xas
align: left
---
(a) Schematic potential and (b) schematic representation of the C K-edge X-ray absorption spectrum for the dichloroethylene molecule (adapted from Ref. {cite}`Stohr1992`, Fig. 4.2.).
```
In the case of core-excitations, electron--electron correlation and the presence of the core-hole influence the excitation energies and transition probabilities. These relaxation effects are present also in the case of valence-excitations, but they are more pronounced in the case of core-excitations. The is due the presence of a localized core-hole which leads to a strong net attraction of the electron density towards the probed atom. In addition, the interaction with the excited electron creates a small repulsive polarisation effect in the valence region. Both these two counteracting effects need to be accounted for in order to accurately model XAS. At the ADC level of theory, this is achieved by including at least doubly excited configurations in the construction of the ADC matrix. 

## HPC-QC implementation

To enable large-scale ADC(2) calculations on HPC systems, some considerations need to be taken into account in the implementation. Conventionally, the molecular orbital (MO) integrals, which are essentially tensors with four dimensions, are computed by integral transformation on a single compute node (or workstation). This is unfortunately not practical on HPC clusters, since a cluster node usually has moderate amount of memory which is not enough to store an object with $N^4$ elements (here $N$ is the number of orbitals). Therefore, the MO integral needs to be stored in a distributed way; in other words, each node need to store a portion of the four-dimensional MO integral. It is then natural to distribute the computation of MO integral as well, such that each node only computes part of the integral that needs to be stored locally. This leads to the so-called Fock matrix-driver integral transformation approach, where MO integrals are expressed in terms of Fock-like matrices {cite}`Hohenstein2015, gator`
```{math}
:label: eq:mo-ints-from-fock
\langle ij || kl \rangle = \sum_{\gamma \delta}^{N} \left [ C_{\gamma k} F_{\gamma \delta}^{ij} C_{\delta l} - C_{\gamma l} F_{\gamma \delta}^{ij} C_{\delta k} \right ]
```
where
```{math}
:label: eq:fock-from-dens
F_{\gamma \delta}^{ij} = \sum_{\alpha \beta}^{N} D_{\alpha \beta}^{ij} (\alpha \gamma|\delta \beta)
```
```{math}
:label: eq:dens-from-mo
D_{\alpha \beta}^{ij} = C_{\alpha i} C_{\alpha j}
```
In practice the $ij$ pairs and the corresponding $kl$ matrices are stored on individual nodes. This also facilitates parallelization of subsequent $\sigma$-build (matrix-vector multiplication) with minimal amount of communications.

In HPC-QC implementation of ADC(2), another object that cannot be stored on a cluster node is the excitation vector that involves two particle-hole pairs (namely double excitation). This is because the vector of double excitation has four indices and its sizes increases as $O(N^4)$. Fortunately, explicit storage of the double excitation vector can be avoided by converting the standard eigenproblem in single and double space to a nonlinear eigenproblem in single space {cite}`Hattig2006`. By expanding the ADC(2) equation
```{math}
:label: eq:adc2-mat-vec
\begin{pmatrix} M_{11} & M_{12}\\ M_{21} & M_{22} \end{pmatrix}
\begin{pmatrix} V_{1} \\ V_{2} \end{pmatrix}
= \omega \begin{pmatrix} V_{1} \\ V_{2} \end{pmatrix}
```
we have
```{math}
:label: eq:adc2-mat-vec-v1
M_{11} V_1 + M_{12} V_2 = \omega V_1
```
```{math}
:label: eq:adc2-mat-vec-v2
M_{21} V_1 + M_{22} V_2 = \omega V_2
```
where $\omega$ is the excitation energy, and $V_1$ and $V_2$ are the single and double excitation vectors, respectively. The above two equations can be rewritten as (after eliminating $V_2$)
```{math}
:label: eq:adc2-mat-vec-folded
\left[ M_{11} + M_{12} (\omega - M_{22})^{-1} M_{21} \right] V_1 = \omega V_1
```
Note that $M_{22}$ is diagonal in ADC(2). Let
```{math}
:label: eq:adc2-mat-vec-meff
M^{\rm eff}_{11} = \left[ M_{11} + M_{12} (\omega - M_{22})^{-1} M_{21} \right] V_1
```
we have
```{math}
:label: eq:adc2-mat-vec-nonlinear
M^{\rm eff}_{11} V_1 = \omega V_1
```
This is a nonlinear eigenproblem since $M^{\rm eff}_{11}$ depends on $\omega$.
The excitation energies and single excitation vectors can then be solved
by a nonlinear eigensolver.
Note that the resultant single excitation vectors need to be scaled to satisfy the 
following condition
```{math}
:label: eq:adc2-v1-v2-sum
V_1^{\dagger} V_1^{ } + V_2^{\dagger} V_2^{ } = 1
```
where $V_2^{\dagger} V_2^{ }$ can be calculated as
```{math}
:label: eq:adc2-v2-squared
V_2^{\dagger} V_2^{ } = V_1^{\dagger} M_{12} (\omega - M_{22})^{-2} M_{21} V_1^{ }
```
