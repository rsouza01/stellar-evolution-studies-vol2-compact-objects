# Module 08: Nuclear matter and the neutron-star equation of state

**Difficulty:** Hard. **Time:** about 3 weeks.

## Goal

Understand the physics of dense hadronic matter around and above saturation density: nuclear binding and saturation, the symmetry energy, nuclear forces and many-body approaches, Skyrme energy density functionals, beta equilibrium, composition and the Urca threshold. Build a transparent parametrized EOS and a Skyrme infinite-matter EOS that feed the TOV solver.

## Prerequisites

Modules 02, 03, 04, 06 and 07. Basic nuclear physics.

## Reading

- **R&S, Hey, BM, Krane:** nuclear binding, the semi-empirical mass formula, saturation, shell structure, effective interactions, Hartree-Fock for nuclei, Skyrme and Gogny forces, the nuclear many-body problem.
- **Wal, FW:** relativistic and nonrelativistic many-body theory (the bridge to Module 09).
- **BP, Pin:** Landau Fermi-liquid theory applied to nuclear and neutron matter.
- **HPY, Gle, ST:** the EOS of dense matter, symmetry energy, beta equilibrium, composition, Urca processes.

## Key equations and concepts (derive)

**Semi-empirical mass formula:**

$$B(A,Z)=a_VA-a_SA^{2/3}-a_C\frac{Z^2}{A^{1/3}}-a_A\frac{(A-2Z)^2}{A}+\delta(A),$$

with $a_V\approx15.8$, $a_S\approx18.3$, $a_C\approx0.71$, $a_A\approx23.2$ MeV (verify; the fitted values depend on the dataset and on the form of the surface term).

**Saturation and bulk parameters.** Symmetric nuclear matter (SNM) has a minimum of $E/A\approx-16$ MeV at $n_0\approx0.16$ fm$^{-3}$ with an incompressibility $K_0=9n_0^2\,d^2(E/A)/dn^2|_{n_0}\approx230\pm20$ MeV. The energy per baryon of asymmetric matter, with $\delta=(n_n-n_p)/n$ and $u=n/n_0$, is expanded as

$$e(n,\delta)=e_{\rm SNM}(n)+S(n)\,\delta^2+O(\delta^4),\qquad S(n)=S_0+\frac L3\,(u-1)+\frac{K_{\rm sym}}{18}(u-1)^2+\dots$$

with $S_0\approx30$ to $35$ MeV and slope $L\approx40$ to $70$ MeV (the empirical range; verify). The pressure of pure neutron matter at saturation is $P_{\rm PNM}(n_0)\approx n_0L/3$.

**Kinetic energy of asymmetric matter** (exact, free nucleons, $E_F^0=\hbar^2k_{F0}^2/2m$ with $k_{F0}=(3\pi^2n_0/2)^{1/3}$):

$$T(u,\delta)=\tfrac35E_F^0u^{2/3}\,\tfrac12\left[(1+\delta)^{5/3}+(1-\delta)^{5/3}\right],\quad T_{\rm sym}=\tfrac13E_F^0u^{2/3}\ (\text{coefficient of }\delta^2)$$

**Beta equilibrium.** With $\mu_n-\mu_p=4S(n)(1-2Y_p)$ (from $e(n,\delta)$ with $\delta=1-2Y_p$) and $\mu_e=\hbar c(3\pi^2nY_e)^{1/3}$ (ultrarelativistic) one solves

$$4S(n)(1-2Y_p)=\hbar c\,(3\pi^2nY_p)^{1/3}$$

for the proton fraction $Y_p(n)$ (charge neutrality $n_e=n_p$). The **direct Urca** process $n\to p+e+\bar\nu$ is allowed only when momentum conservation can be satisfied, $k_{Fn}\le k_{Fp}+k_{Fe}$, which gives $Y_p\ge1/9\approx0.11$ for $npe$ matter ($\approx0.148$ with muons). Whether it operates depends on the symmetry energy (Module 14).

**Nuclear forces and methods.** Realistic two-nucleon potentials (Argonne v18, Nijmegen, chiral EFT) plus three-nucleon forces (essential for saturation and for stiffness); methods: Brueckner-Hartree-Fock, variational chain summation (APR), Green's function and auxiliary-field diffusion Monte Carlo, self-consistent Green's functions, chiral effective field theory with controlled uncertainty bands below $\sim2n_0$; and effective density functionals (Skyrme, Gogny, RMF; Module 09). Neutron matter at saturation has $E/N\approx13$ to $17$ MeV in these approaches (verify).

**Skyrme energy density functional.** The uniform-matter energy density is a polynomial in $n$, $\tau$ and $\delta$ with parameters $t_0,t_1,t_2,t_3,x_0,x_1,x_2,x_3,\sigma$ (for example SLy4: $t_0=-2488.91$ MeV fm$^3$, $t_1=486.82$, $t_2=-546.39$, $t_3=13777.0$, $x_0=0.834$, $x_1=-0.344$, $x_2=-1.0$, $x_3=1.354$, $\sigma=1/6$; verify these numbers in your references). Derive the SNM and PNM energy per baryon, the effective mass $m^*/m$ and the saturation properties from the functional (R&S and Chamel give the formulas).

## Hands-on problems

**1. [E] The semi-empirical mass formula.** Fit $a_V,a_S,a_C,a_A,\delta$ to a table of experimental nuclear masses (the Atomic Mass Evaluation; verify access) with least squares, and compare the residuals. Derive from the formula the minimum energy per baryon of symmetric infinite matter and the symmetry energy $a_A\approx S_0$-like parameter (the bulk symmetry energy is larger than $a_A$ because of the surface contribution; discuss).

**2. [E] Free Fermi gas energetics.** Compute the kinetic energy per nucleon of SNM and PNM at $n_0$ and the kinetic contribution to the symmetry energy ($E_F^0/3\approx12$ MeV). Compare with $S_0\approx32$ MeV and deduce the size of the potential contribution.

**3. [M] A schematic EOS.** Build the parametrized EOS of the form

$$e(u,\delta)=T(u,\delta)+a\,u+b\,u^\gamma+c\,u^{\gamma_s}\delta^2,$$

with $a,b,\gamma$ fixed by $e(1)=-16$ MeV, $de/du|_1=0$ and $9\,d^2e/du^2|_1=K_0$ (solve the third condition for $\gamma$ by root-finding after eliminating $a$ and $b$), and $c,\gamma_s$ fixed by $S(1)=S_0$ and $L=3\,dS/du|_1$ (derive: $c=S_0-E_F^0/3$ and $\gamma_s=(L/3-2E_F^0/9)/c$). Scan $(K_0,S_0,L)$ over the empirical ranges. Compute the pressure, energy density and sound speed of SNM and PNM and check causality up to a few $n_0$ (and cut off or switch to a causal extension if violated).

**4. [M] Composition in beta equilibrium.** For the schematic EOS, solve for $Y_p(n)$ including muons ($\mu_\mu=\mu_e$), plot it, and determine whether the direct Urca threshold ($Y_p>1/9$) is crossed within the star for $L=40,60,80$ MeV. Plot the threshold density versus $L$.

**5. [M] Stars from the schematic EOS.** Attach a crust (Module 10, or a simple BPS-like polytrope for now) and solve the TOV equations for a grid of $(K_0,S_0,L,\gamma)$. Show how $R_{1.4}$ increases with $L$ (it correlates with the pressure of neutron matter near saturation) and how $M_{\rm max}$ depends on the high-density stiffness. Reproduce the correlation $R_{1.4}$ versus $L$ and compare with the quoted slope of about 0.1 to 0.15 km per 10 MeV (verify).

**6. [M] Fermi-liquid parameters.** From your EOS or from Skyrme, compute the Landau parameters $F_0$, $F_1$ for neutron matter and the effective mass at saturation (about $0.7$ to $0.8$ of the bare mass for Skyrme sets; verify). Compute the compressibility and the specific heat and compare with the free gas.

**7. [H] A Skyrme functional.** Implement the Skyrme energy density of uniform matter for general $\delta$ (derive it), reproduce the saturation properties of SLy4 or another standard set ($n_0\approx0.16$ fm$^{-3}$, $E/A\approx-16$ MeV, $K_0\approx230$ MeV, $S_0\approx32$ MeV, $L\approx46$ MeV for SLy4; verify), and compute the neutron star EOS with the crust from Module 10. Compare $M_{\rm max}$ and $R_{1.4}$ with the literature (SLy gives $M_{\rm max}\approx2.05\,M_\odot$ and $R_{1.4}\approx11.7$ km; verify).

**8. [H] Chiral EFT neutron matter.** Take a published parametrization of the chiral EFT neutron matter EOS band up to $1.1n_0$ to $2n_0$ (verify the source) or fit your own parametrization to it, and use it as the low-density constraint for the schematic EOS: restrict $(S_0,L)$ so that PNM at $n\lesssim1.5n_0$ lies in the band. Examine the induced bound on $R_{1.4}$. This is the logic of low-density constraints.

**9. [H] Constraints and correlations.** Combine the empirical constraints (SNM saturation, $S_0$, $L$, chiral EFT band, observed maximum mass $\ge2\,M_\odot$) in a simple Monte Carlo over the schematic EOS parameters, keep the samples that satisfy all of them and plot the resulting distributions of $R_{1.4}$, $M_{\rm max}$ and $P(2n_0)$. This is the prelude to Module 19.

## Software component

`compactlite/eos/nuclear.py`: the schematic parametrized EOS with consistency checks, the Skyrme infinite-matter EOS, beta equilibrium solver with leptons, Urca threshold analysis, empirical-constraint checks.

## Checks

- Fitted SEMF parameters near the quoted values.
- Saturation conditions satisfied by the schematic EOS ($e(1)=-16$, $P(n_0)=0$, $K_0$).
- $Y_p$ at saturation of order $3$ to $5$ percent and rising with density; direct Urca threshold at $Y_p=1/9$.
- SLy4: $n_0\approx0.16$ fm$^{-3}$, $K_0\approx230$ MeV, $S_0\approx32$ MeV.
- $R_{1.4}$ increasing with $L$ at a rate of about 0.1 to 0.15 km per 10 MeV.

## Pitfalls

- Confusing the bulk symmetry energy with the SEMF coefficient $a_A$.
- Omitting muons when computing $Y_p$ and the Urca threshold.
- Using a purely nonrelativistic EOS far above saturation where the sound speed exceeds $c$.
- Mixing energy per baryon and energy density with and without the rest mass.

## Gate questions

1. Why does nuclear matter saturate, and which terms in the energy balance produce the saturation density?
2. Why does a larger slope $L$ imply a larger neutron star radius?
3. Why do three-nucleon forces matter for the stiffness of neutron star matter?

## Deliverable

`compactlite/eos/nuclear.py`, `notebooks/08_nuclear_matter.ipynb`, solutions for problems 1 to 9.
