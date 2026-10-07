# Module 06: General relativity for compact stars

**Difficulty:** Medium to hard. **Time:** about 3 weeks.

## Goal

Apply general relativity to *stars* (not black holes): the static spherically symmetric perfect-fluid spacetime, the Tolman-Oppenheimer-Volkoff (TOV) equations, junction conditions and the Schwarzschild exterior, gravitational redshift, proper volume and binding energy, analytic interior solutions, the Buchdahl and causality bounds, and the criteria for radial stability. Write a robust TOV solver.

## Prerequisites

Modules 01 and 02. A first course in general relativity (tensors, the Einstein equations, the Schwarzschild solution).

## Reading

- **MTW, Har, Wein, Schu, Car, P&W:** Einstein equations, static spherical stars, the stress-energy tensor of a perfect fluid, TOV, Birkhoff's theorem, junction conditions, the post-Newtonian expansion.
- **ST, Gle, HPY:** relativistic stellar structure and neutron star models, the stability criterion.
- **And, Mag:** later, for perturbations.

## Key equations (derive)

**Metric and matter.** For a static spherical star

$$ds^2=-e^{2\Phi(r)}c^2dt^2+\left(1-\frac{2Gm(r)}{rc^2}\right)^{-1}dr^2+r^2\left(d\theta^2+\sin^2\theta\,d\varphi^2\right)$$

with a perfect fluid $T^{\mu\nu}=(\epsilon+P)u^\mu u^\nu/c^2+Pg^{\mu\nu}$ ($\epsilon$ the total energy density including rest mass).

**TOV equations** (derive from $G_{\mu\nu}=8\pi GT_{\mu\nu}/c^4$ and $\nabla_\mu T^{\mu\nu}=0$):

$$\frac{dm}{dr}=\frac{4\pi r^2\epsilon}{c^2},\qquad\frac{dP}{dr}=-\frac{G(\epsilon+P)\left(m+4\pi r^3P/c^2\right)}{c^2r^2\left(1-2Gm/rc^2\right)},\qquad\frac{d\Phi}{dr}=-\frac{1}{\epsilon+P}\frac{dP}{dr}$$

The metric potential is fixed by the exterior match $e^{2\Phi(R)}=1-2GM/Rc^2$. The Newtonian limit ($P\ll\epsilon$, $Gm/rc^2\ll1$) recovers hydrostatic equilibrium. The three relativistic corrections are $\epsilon+P$ (pressure gravitates), $m+4\pi r^3P/c^2$ (pressure sources gravity) and $(1-2Gm/rc^2)^{-1}$ (space curvature); each *increases* the effective gravity.

**Junction conditions (Israel-Darmois).** The metric and its first fundamental form are continuous at the surface; $P(R)=0$ guarantees continuity of the extrinsic curvature. A discontinuity in $\epsilon$ at the surface is allowed (and relevant for self-bound quark stars).

**Redshift and observables.**

$$1+z=\left(1-\frac{2GM}{Rc^2}\right)^{-1/2},\qquad R_\infty=R(1+z),\qquad T_\infty=T/(1+z),\qquad L_\infty=L/(1+z)^2$$

**Baryon number and binding energy.** The proper volume element is $4\pi r^2(1-2Gm/rc^2)^{-1/2}dr$, so

$$A=\int_0^R\frac{4\pi r^2n_b}{\sqrt{1-2Gm/rc^2}}dr,\qquad M_b=m_bA,\qquad E_{\rm bind}=(M_b-M)c^2$$

with $m_b$ the baryon mass ($931.5$ MeV or the neutron mass depending on convention; fix it). A neutron star has $E_{\rm bind}\sim0.1\,Mc^2\approx3\times10^{53}$ erg.

**Bounds.**
- *Buchdahl:* $GM/Rc^2\le4/9$ for any static perfect fluid sphere with $\epsilon$ non-increasing outward.
- *Causality:* $c_s^2=dP/d\epsilon\le c^2$ gives $R\gtrsim2.9\,GM/c^2$ for the stiffest causal EOS above a matching density (the Rhoades-Ruffini type maximum-mass bound, about $3\,M_\odot$ for a matching density near nuclear density; verify).

**Analytic solutions** (test cases):
- *Incompressible star* (Schwarzschild interior), $\epsilon=$ const:

$$P(r)=\epsilon c^2\,\frac{\sqrt{1-2GMr^2/R^3c^2}-\sqrt{1-2GM/Rc^2}}{3\sqrt{1-2GM/Rc^2}-\sqrt{1-2GMr^2/R^3c^2}}$$

with $P_c\to\infty$ at $GM/Rc^2=4/9$ (check).
- *Tolman VII:* $\epsilon=\epsilon_c(1-r^2/R^2)$ gives $M=\frac{8\pi}{15}\epsilon_cR^3/c^2$ and an analytic pressure profile (derive); a good approximation to realistic neutron stars.

**Radial stability.** A necessary condition: $dM/d\epsilon_c>0$ (the stable branch of the $M(\epsilon_c)$ curve ends at the maximum mass; Harrison-Wheeler-Zel'dovich criterion). The sufficient condition comes from the lowest eigenvalue $\omega_0^2>0$ of Chandrasekhar's radial pulsation equation (Module 13). Newtonian limit: $\Gamma_1>4/3$.

## Hands-on problems

**1. [E] Symbolic derivation.** With `sympy`, compute the Einstein tensor $G_{\mu\nu}$ of the static spherical metric with two free functions, impose $G_{\mu\nu}=8\pi T_{\mu\nu}$ for the perfect fluid, and obtain the TOV equations. Verify the Newtonian limit by expanding in $Gm/rc^2$ and $P/\epsilon$.

**2. [E] The TOV solver.** Write (or reuse and clean up) a TOV solver in geometric units with a general EOS callback `eps(P)`, an adaptive integrator with an event at $P=0$, and careful central boundary conditions ($m\approx\frac{4\pi}{3}\epsilon_cr^3$, $P\approx P_c-\frac{2\pi}{3}(\epsilon_c+P_c)(\epsilon_c+3P_c)r^2$, in $G=c=1$). Return $M,R,\Phi$, the baryon number, the binding energy and the compactness.

**3. [M] The incompressible star.** For several compactnesses solve the TOV equations numerically for $\epsilon=$ const and compare with the exact Schwarzschild interior solution for $P(r)$. Verify that $P_c$ diverges as $C\to4/9$ and that the numerical solution tracks it. Convert to a $(M,R)$ curve at fixed $\epsilon$ and show $M\propto R^3$ (Newtonian) turning over.

**4. [M] Tolman VII.** Integrate the TOV equations with $\epsilon=\epsilon_c(1-r^2/R^2)$ imposed as the density profile and compare with the analytic pressure; compute the $M(R)$ relation and the central pressure and use it as a quick model of neutron stars (the compactness-central pressure relation).

**5. [M] Post-Newtonian expansion.** Derive the first post-Newtonian correction to hydrostatic equilibrium and to the relation between $M$ and $R$ for a polytrope, and compare with the numerical TOV solution at small compactness (a polytrope with $\Gamma=2$ in a regime where $C\ll1$). Show that the first-order correction to the stellar radius at fixed central density is positive or negative depending on $\Gamma$ (check).

**6. [M] Redshift, binding energy and baryon number.** For a model neutron star compute $1+z$, $R_\infty$ and $E_{\rm bind}$, and compare $E_{\rm bind}$ with the Newtonian expectation $\frac35GM^2/R$ and the empirical fit $E_{\rm bind}/M\approx0.6C/(1-0.5C)$ (verify the fit; it is a commonly used approximation). Show that the $M_b$ at fixed central density provides the evolutionary sequences of fixed baryon number used for the collapse of supramassive stars.

**7. [M] Stability and the turning point.** For a family of models with varying $\epsilon_c$ (polytrope, free neutron gas), compute $M(\epsilon_c)$ and mark the maximum. Verify that the stability changes there, using the numerical radial pulsation equation of Module 13 (or the energy-variation argument: $E(\epsilon_c)$ at fixed $M_b$ has a minimum on the stable branch).

**8. [H] Causality-limited stars.** Compute the family of stars with $P=\epsilon-\epsilon_s$ (the stiffest causal EOS, $c_s=c$) above a matching energy density $\epsilon_s$ and with a given low-density EOS below. Show that the maximum mass scales as $\epsilon_s^{-1/2}$ (about $4.1\,M_\odot(\epsilon_0/\epsilon_s)^{1/2}$; verify) and the minimum radius is about $2.9\,GM/c^2$. Compare with Buchdahl.

**9. [H] Isotropic coordinates and anisotropic stars.** Rewrite the exterior and interior metric in isotropic coordinates and verify that observable quantities are unchanged. Generalize the TOV equations to a fluid with anisotropic pressure $P_r\ne P_\perp$ (derive the extra term in the hydrostatic equation) and discuss when anisotropy could arise (pion condensation, solid cores, strong magnetic fields) and how it modifies the maximum mass.

## Software component

`compactlite/gr/tov.py`: the TOV solver with a general EOS interface (tabulated or analytic), sequences over $\epsilon_c$, the analytic test solutions, and utilities for redshift, binding energy and baryon number. Make it fast (Numba) because it will be called thousands of times in Module 19.

## Checks

- TOV solver reproduces the Schwarzschild interior solution to $10^{-6}$ and Tolman VII to $10^{-6}$.
- Newtonian limit recovered at $C\ll1$.
- $M_{\rm max}$ occurs at $dM/d\epsilon_c=0$.
- $C\le4/9$ for all solutions; causal EOS has $R_{\rm min}\approx2.9\,GM/c^2$.

## Pitfalls

- Mixing energy density and mass density in the source of $m(r)$.
- Starting the integration at $r=0$ (singular): use the series start.
- Using a baryon mass inconsistent with the EOS to compute $M_b$.
- Ignoring that $P(\epsilon)$ may be non-monotonic near phase transitions, which breaks naive callbacks.

## Gate questions

1. Why does pressure gravitate, and what limit does this impose on the maximum mass?
2. Why is $dM/d\epsilon_c=0$ a stability boundary?
3. What is the physical content of the Buchdahl limit and why does it exclude stable stars with $R<9GM/4c^2$?

## Deliverable

`compactlite/gr/tov.py` with tests, `notebooks/06_gr_stars.ipynb`, `notes/derivations/tov.tex`, solutions for problems 1 to 9.
