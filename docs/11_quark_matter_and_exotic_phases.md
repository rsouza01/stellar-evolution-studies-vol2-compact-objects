# Module 11: Quark matter and exotic phases

**Difficulty:** Hard. **Time:** about 3 weeks.

## Goal

Understand how matter might change character at the highest densities in neutron star cores: deconfined quark matter (bag model, NJL-type models, perturbative QCD), color superconductivity, strange quark matter and strange stars, hybrid stars and phase transitions (Maxwell, Gibbs, twin stars), and the constraints from observations and from QCD. Build `eos/quark` and `eos/hybrid`.

## Prerequisites

Modules 02, 03 (phase transitions), 04 (mean-field effective potentials, pairing), 07 and 09. Basic QCD (your QCD track).

## Reading

- **Gle, Wb, Schm:** quark matter in compact stars, the MIT bag model, strange quark matter, color superconductivity, hybrid stars, mixed phases.
- **Kap, LeB:** QCD thermodynamics, perturbative QCD pressure, chiral models.
- **PS, IZ, Gre:** QCD and chiral symmetry.
- **HPY:** composition and EOS overview, constraints.

## Key equations and concepts (derive)

**MIT bag model.** Quarks are free, massless (or with current masses) particles in a vacuum of energy density $B$. For massless $u,d,s$ quarks at zero temperature:

$$P=\sum_{f}\frac{\mu_f^4}{4\pi^2}-B\ (\text{three colors, two spins, each flavor}),\qquad\epsilon=3P+4B$$

for conformal matter (so $c_s^2=1/3$). With strange quark mass $m_s$ and first-order QCD corrections $(1-2\alpha_s/\pi)$ the pressure is modified; verify the form from Gle or Wb. Equilibrium conditions: weak equilibrium $\mu_d=\mu_s=\mu_u+\mu_e$ and charge neutrality $\tfrac23n_u-\tfrac13(n_d+n_s)-n_e=0$.

**Strange quark matter (Witten, Bodmer, Terazawa).** If the energy per baryon of three-flavor quark matter at zero pressure is below that of $^{56}$Fe ($\sim930$ MeV), strange quark matter is the true ground state of matter. For $m_s=0$, $\alpha_s=0$ this requires $B^{1/4}\lesssim163$ MeV (and $B^{1/4}\gtrsim145$ MeV to avoid two-flavor quark matter being stable; verify the window). A strange star has a surface density $\sim4B/c^2\sim4\times10^{14}$ g/cm$^3$ (a sharp density jump to zero), $R\propto M^{1/3}$ at low mass (self-bound) and a maximum mass $\approx2.0\,(B/60\ {\rm MeV/fm}^3)^{-1/2}M_\odot$ (verify).

**Hybrid stars and phase transitions.** A hadronic EOS at low density and a quark EOS at high density; the transition is determined by equal pressure and chemical potentials. Maxwell construction (one conserved charge) gives a constant-pressure plateau and a density jump $\Delta\epsilon$; Gibbs construction (two conserved charges) gives a smooth mixed phase (finite-size effects make the truth lie between them, Module 03). A large enough $\Delta\epsilon$ makes the hybrid branch unstable immediately, but a smaller one can make it stable and a very large one can produce a **third family** of stable stars separated from the hadronic branch by an unstable segment: **twin stars** (a discontinuity in the $M$-$R$ curve).

**Constant speed of sound parametrization (Alford-Han-Prakash).** Above a transition pressure $P_{\rm tr}$:

$$\epsilon(P)=\epsilon_{\rm tr}+\Delta\epsilon+c_{\rm QM}^{-2}(P-P_{\rm tr}),$$

with three parameters $(P_{\rm tr},\Delta\epsilon,c_{\rm QM}^2)$. This captures the generic phenomenology of a first-order transition independent of the model. Hybrid stars with stable third families exist when $\Delta\epsilon$ exceeds a critical value related to $P_{\rm tr}$ and $\epsilon_{\rm tr}$ (derive the Seidov criterion $\Delta\epsilon/\epsilon_{\rm tr}\gtrsim\frac12+\frac{3}{2}P_{\rm tr}/\epsilon_{\rm tr}$ and check it numerically).

**Color superconductivity.** At high density quarks form Cooper pairs with gaps $\Delta\sim10$ to $100$ MeV: 2SC (pairing of $u$ and $d$) or color-flavor locked (CFL; all three flavors, $\Delta\sim100$ MeV, locking the Fermi momenta). The effect on the EOS is an effective vacuum term $\propto\Delta^2\mu^2$ and a modified bag constant; CFL is electrically neutral without electrons. The pressure with gap is $P=\frac{3}{4\pi^2}a_4\mu^4-\frac{3}{4\pi^2}a_2\mu^2-B_{\rm eff}$ (Alford-Reddy, with $a_2=m_s^2-4\Delta^2$ for CFL; verify).

**NJL and quark-meson models.** Chiral models with a four-fermion interaction produce constituent quark masses that melt with density; the pressure follows from the mean-field gap equation $M=m_0-2G\langle\bar\psi\psi\rangle$ (derive using Module 04 problem 9). Adding vector interactions stiffens the EOS and allows $M_{\rm max}\gtrsim2\,M_\odot$.

**QCD constraints.** At baryon densities $\gtrsim40n_0$ perturbative QCD gives the pressure with controlled uncertainties; extrapolating the sound speed from nuclear (chiral EFT) to pQCD results in a typical peak of $c_s^2>1/3$ in the interior of massive stars (with $c_s^2\to1/3$ at asymptotic densities from below), a strong sign of nontrivial dynamics (a "conformal" bound $c_s^2\le1/3$ is violated in hadronic EOS but approached from below in pQCD; verify).

**Other exotic phases.** Kaon and pion condensates, which soften the EOS; strangeness; dark matter admixtures. Each has to confront the maximum mass.

## Hands-on problems

**1. [E] The bag model.** Compute the zero-temperature EOS of three massless flavors in weak equilibrium with the bag constant, find the baryon density and energy per baryon at zero pressure, and show $\epsilon=3P+4B$. Verify the stability window for strange matter relative to $^{56}$Fe (930 MeV) and to two-flavor matter (about 934 MeV).

**2. [E] Strange star structure.** Solve the TOV equations for the bag EOS ($B^{1/4}=145$, $150$, $160$ MeV): verify the self-bound branch with $R\propto M^{1/3}$ at low mass, the surface density $4B$ and the maximum mass scaling as $B^{-1/2}$ (about $2\,M_\odot$ at $B=60$ MeV/fm$^3$; verify). Plot $M$-$R$.

**3. [M] Strange quark mass and $\alpha_s$.** Add the strange mass $m_s$ (100 to 200 MeV) and the lowest-order $\alpha_s$ correction. Solve weak equilibrium and charge neutrality numerically, find the quark composition versus density and the new stability window.

**4. [M] Maxwell hybrid stars.** Join your RMF hadronic EOS (Module 09) with the bag or constant-speed-of-sound quark EOS using the Maxwell construction. Scan $(B,\ \text{or }P_{\rm tr},\Delta\epsilon,c_{\rm QM}^2)$, compute $M$-$R$ curves, and identify which parameters give stable hybrid branches, which give a third family and which give an unstable hybrid. Verify the Seidov criterion for the onset of instability.

**5. [M] Gibbs hybrid stars.** Implement the Gibbs construction with two chemical potentials and charge neutrality for the same hadronic and quark EOS. Compare the $M$-$R$ curves with the Maxwell ones, and with a mixed-phase including surface and Coulomb energies in a Wigner-Seitz cell (Module 03, problem 9) at a surface tension of $\sigma_s\sim10$ to $50$ MeV/fm$^2$. Explain why larger $\sigma_s$ makes the result approach Maxwell.

**6. [M] A third family.** Find parameters $(P_{\rm tr},\Delta\epsilon,c_{\rm QM}^2)$ in the constant-speed-of-sound model that give twin stars with $M_{\rm max}>2\,M_\odot$ on the hadronic branch and a stable hybrid branch at larger compactness. Plot the radii of the twins at the same mass and discuss how they could be distinguished observationally (the radius difference and the tidal deformability).

**7. [H] NJL model.** Implement the SU(3) NJL model with a scalar and a vector coupling, solve the gap equations at finite chemical potential in beta equilibrium, compute the EOS and verify chiral restoration with density. Join it to the hadronic EOS and scan the vector coupling to see its effect on $M_{\rm max}$.

**8. [H] Color superconducting quark matter.** Implement the effective EOS with $a_4$, $a_2$ and $B_{\rm eff}$ and gap $\Delta$; show how $\Delta$ increases the pressure at fixed $\mu$, compute hybrid stars with CFL matter and discuss the allowed gap values given $M_{\rm max}\ge2\,M_\odot$.

**9. [H] QCD constraints.** Take the perturbative QCD pressure at large $\mu_B$ (use the known expansion to order $\alpha_s^2$, for example the formula in Kap or Schm; verify), and impose consistency of the extrapolated $P(\mu_B)$ from the star's EOS at the central density of the maximum-mass star with the pQCD endpoint (the integral constraint on $\int n\,d\mu$). Test whether your EOS families satisfy it and find which ones are ruled out.

**10. [H] Sound-speed analysis.** For each of your hadronic, hybrid and quark EOS, plot $c_s^2(n)$ and $P/\epsilon$ versus density. Determine the central-density range probed by $2\,M_\odot$ stars and discuss whether the sound speed must exceed the conformal value $1/3$ and what that would mean physically.

## Software component

`compactlite/eos/quark.py` (bag with $m_s$ and $\alpha_s$, CFL effective, NJL), `compactlite/eos/hybrid.py` (Maxwell, Gibbs and constant-speed-of-sound constructions with automatic detection of stability and third families), pQCD matching tools.

## Checks

- Bag model: $\epsilon=3P+4B$ and the stability window of $B^{1/4}$.
- Strange stars: $R\propto M^{1/3}$ at low mass and $M_{\rm max}\propto B^{-1/2}$.
- Maxwell hybrid: constant-pressure plateau; Seidov criterion consistent with the numerical stability analysis.
- Gibbs construction satisfying equal $\mu_n$, $\mu_e$, $P$ and global charge neutrality.
- Twin stars: identical mass with different radii.

## Pitfalls

- Using the Maxwell construction with a mixed-phase plateau that contradicts charge neutrality of the two phases at the transition.
- Using the bag model beyond its validity (it has no chiral physics).
- Not checking causality and thermodynamic consistency of constructed hybrid EOS.
- Forgetting that the hybrid branch stability requires $dM/d\epsilon_c>0$ at fixed construction.

## Gate questions

1. Why does the presence of a quark core soften the EOS in general, and how can vector interactions or color superconductivity reverse this?
2. What does it mean for strange quark matter to be absolutely stable, and what are the consequences for compact stars?
3. Why are twin stars a signature of a strong first-order transition?

## Deliverable

`compactlite/eos/quark.py`, `compactlite/eos/hybrid.py`, `notebooks/11_quark_exotic.ipynb`, solutions for problems 1 to 10.
