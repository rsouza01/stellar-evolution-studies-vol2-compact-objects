# Module 02: Statistical mechanics I, ideal quantum gases

**Difficulty:** Medium. **Time:** about 3 weeks.

## Goal

Master the grand-canonical description of ideal Fermi and Bose gases (nonrelativistic and relativistic, with antiparticles), the Sommerfeld expansion, the thermodynamic potentials and their consistency conditions, and chemical equilibrium. Build the `thermo` library, the heart of every EOS in this program.

## Prerequisites

Module 01. Thermodynamics and quantum mechanics at graduate level.

## Reading

- **Pat, LL5, Kar, Hua, Rei:** ensembles, the grand canonical ensemble, ideal Fermi and Bose gases, degenerate gases, Sommerfeld expansion, relativistic gases, chemical equilibrium.
- **ST:** degenerate and relativistic matter, the electron gas, pair equilibrium.
- **HKT, KWW:** the EOS of stellar matter (as a bridge to Volume 1).

## Key equations (derive)

**Grand canonical ensemble.** With $\beta=1/k_BT$:

$$\Omega=-PV=-k_BT\ln\mathcal Z,\qquad\ln\mathcal Z_{\rm F}=\sum_i\ln\!\left(1+e^{-\beta(\varepsilon_i-\mu)}\right),\qquad\ln\mathcal Z_{\rm B}=-\sum_i\ln\!\left(1-e^{-\beta(\varepsilon_i-\mu)}\right)$$

with $d\Omega=-S\,dT-P\,dV-N\,d\mu$, so that $n=\partial P/\partial\mu|_T$, $s=\partial P/\partial T|_\mu$ and $\epsilon+P=Ts+\mu n$ (Gibbs-Duhem). **Every EOS you build must satisfy these numerically.**

**Relativistic fermion gas with antiparticles** (degeneracy $g$, mass $m$, dispersion $E=\sqrt{p^2c^2+m^2c^4}$, chemical potential $\mu$ for particles, $-\mu$ for antiparticles):

$$n-\bar n=\frac{g}{2\pi^2\hbar^3}\int_0^\infty p^2\left[f(E-\mu)-f(E+\mu)\right]dp,\qquad P=\frac{g}{6\pi^2\hbar^3}\int_0^\infty\frac{p^4c^2}{E}\left[f(E-\mu)+f(E+\mu)\right]dp$$

with $f(x)=1/(e^{x/k_BT}+1)$. The generalized Fermi-Dirac integrals (with relativity parameter $\theta=k_BT/mc^2$) are $F_k(\eta,\theta)=\int_0^\infty\frac{x^k(1+\theta x/2)^{1/2}}{e^{x-\eta}+1}dx$ (Cloutman form; check your books).

**Fully degenerate limit** ($T=0$, $g=2$, $x=p_F/mc$, $n=p_F^3/3\pi^2\hbar^3$):

$$P=\frac{m^4c^5}{24\pi^2\hbar^3}\left[x(2x^2-3)\sqrt{1+x^2}+3\sinh^{-1}x\right],\qquad\epsilon=\frac{m^4c^5}{8\pi^2\hbar^3}\left[x(2x^2+1)\sqrt{1+x^2}-\sinh^{-1}x\right]$$

with limits $P\to\frac{(3\pi^2)^{2/3}\hbar^2}{5m}n^{5/3}$ ($x\ll1$) and $P\to\frac{(3\pi^2)^{1/3}}{4}\hbar c\,n^{4/3}$ ($x\gg1$). (Check that these agree with Module 03 of Volume 1.)

**Sommerfeld expansion** (nonrelativistic, $T\ll T_F$): for $\int_0^\infty H(E)f(E)\,dE$,

$$\int_0^\infty H f\,dE=\int_0^\mu H\,dE+\frac{\pi^2}{6}(k_BT)^2H'(\mu)+\frac{7\pi^4}{360}(k_BT)^4H'''(\mu)+\dots$$

giving $\mu=E_F\left[1-\frac{\pi^2}{12}(k_BT/E_F)^2+\dots\right]$, $C_V=\frac{\pi^2}{2}Nk_B\,\frac{k_BT}{E_F}$ and $S=C_V$ at low $T$.

**Bose gas.** Bose-Einstein condensation at $T_c=\frac{2\pi\hbar^2}{mk_B}\left(\frac{n}{\zeta(3/2)}\right)^{2/3}$; photon gas $\epsilon=aT^4$, $P=\epsilon/3$, $s=\frac{4}{3}aT^3$; massless fermion gas with degeneracy $g$: $\epsilon=\frac{7}{8}g\frac{\pi^2}{30}(k_BT)^4/(\hbar c)^3$ at $\mu=0$ (the neutrino gas).

**Chemical equilibrium.** For reactions $\sum_i\nu_iA_i=0$ at fixed $T,P$: $\sum_i\nu_i\mu_i=0$. Examples: $\beta$ equilibrium without trapped neutrinos, $\mu_n=\mu_p+\mu_e$, and pair equilibrium $\mu_{e^-}+\mu_{e^+}=0$. Saha-type relations follow for ionization and nuclear statistical equilibrium (Module 18).

## Hands-on problems

**1. [E] Fermi-Dirac integrals.** Implement $F_k(\eta)$ for $k=-1/2,1/2,3/2,5/2$ and the generalized $F_k(\eta,\theta)$ by quadrature, with asymptotic forms for $\eta\to\pm\infty$ (non-degenerate: $F_k\to\Gamma(k+1)e^\eta$; degenerate: $F_k\to\eta^{k+1}/(k+1)$) and a seamless switch. Test against `scipy` or tabulated values and against derivatives $dF_k/d\eta=kF_{k-1}$.

**2. [E] Degenerate gas limits.** Evaluate the Chandrasekhar expressions for $P$ and $\epsilon$ over $x=10^{-3}$ to $10^3$ and verify both power-law limits. Compute the density at $x=1$ for $\mu_e=2$ (about $10^6$ g/cm$^3$) and for neutrons ($x_n=1$ at $\rho\sim6\times10^{15}$ g/cm$^3$; check).

**3. [M] Sommerfeld numerics.** For a nonrelativistic gas compute $\mu(T)$ and $C_V(T)$ from the exact integrals and compare with the first and second-order Sommerfeld expansions over $T/T_F=0.01$ to $2$. Estimate the error as a function of $T/T_F$ and show where the expansion fails.

**4. [M] Thermodynamic consistency.** Build a general function `ideal_fermi(mu, T, m, g)` returning $n,P,\epsilon,s$ with all four related. Verify numerically: $n=\partial P/\partial\mu$, $s=\partial P/\partial T$, $\epsilon+P=Ts+\mu n$, $c_V$ and the sound speed $c_s^2=(\partial P/\partial\epsilon)_s$. These identities become your unit tests for all later EOS.

**5. [M] Electron-positron gas.** Compute $n_{e^-},n_{e^+}$, $P$, $s$ at fixed net electron density $n_e=\rho Y_e/m_u$ for $T=10^8$ to $10^{11}$ K. Find where pairs become important (about $k_BT\gtrsim0.1\,m_ec^2$) and compare with the photon plus electron gas.

**6. [M] Photon, neutrino and Bose gases.** Verify the photon and massless-fermion formulas by numerical integration; compute $T_c$ of BEC numerically for a given $n$; compare ideal and "mean-field" corrections. Explain which species contribute to the energy density of a hot proto-neutron star (Module 18).

**7. [M] Beta equilibrium of free gases.** For ideal gases of neutrons, protons and electrons (and muons) at fixed baryon density, solve $\mu_n=\mu_p+\mu_e$ and charge neutrality. Find the proton fraction as a function of density (it is tiny in the free case) and the density at which muons appear.

**8. [H] Thermal tables.** Tabulate the thermodynamic functions of the electron-positron gas on a $(\log\rho Y_e,\log T)$ grid in the form of the Helmholtz free energy $F$, and interpolate with biquintic or bicubic Hermite polynomials so that thermodynamic consistency is preserved. Measure the interpolation error and the speed-up. (This is the Helmholtz-table strategy; it will also be used for white dwarf matter.)

**9. [H] Density of states approach.** Derive the grand potential of an ideal gas in a harmonic trap and in a magnetic field starting from the density of states; recover the free gas, and see what changes in dimension 2 (preview of Landau levels in Module 04).

## Software component

`compactlite/thermo/`: Fermi-Dirac integrals, ideal quantum gases (fermions with antiparticles, bosons, massless species), thermodynamic derivatives, consistency checker, and tabulated electron-positron EOS.

## Checks

- Both degenerate limits reproduced to $10^{-8}$ relative at $x=10^{-3}$ and $x=10^3$.
- Gibbs-Duhem and Maxwell relations satisfied to $10^{-9}$.
- Sommerfeld error scaling as $(T/T_F)^4$ for the second-order result.
- Pairs negligible at $k_BT\ll m_ec^2$ and dominant at $k_BT\gg m_ec^2$.
- Free-gas proton fraction of order one percent or less at nuclear density.

## Pitfalls

- Overflow in $e^\eta$ and cancellation errors at high degeneracy (use asymptotic expansions).
- Forgetting the rest mass in $\epsilon$ and in the chemical potential.
- Treating antiparticles inconsistently in the net number density.
- Using nonrelativistic formulas for neutrons at $\rho\gtrsim10^{15}$ g/cm$^3$.

## Gate questions

1. Why is the grand canonical ensemble the natural one for open, reacting stellar matter?
2. Why is the heat capacity of a degenerate gas proportional to $T$?
3. What does chemical equilibrium say about the proton fraction in neutron star matter, and why does the free-gas answer fail?

## Deliverable

`compactlite/thermo/` with tests, `notebooks/02_ideal_gases.ipynb`, solutions for problems 1 to 9.
