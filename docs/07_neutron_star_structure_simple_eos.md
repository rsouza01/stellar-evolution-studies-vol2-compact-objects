# Module 07: Neutron star structure with simple equations of state

**Difficulty:** Medium. **Time:** about 2 weeks.

## Goal

Use the TOV solver on the simplest equations of state (free neutron gas, $npe$ matter, polytropes, piecewise polytropes) to understand what controls neutron star masses and radii, how the maximum mass arises, and how the mass-radius curve depends on the pressure at a few reference densities. Produce standard sequences and observables.

## Prerequisites

Modules 02 and 06.

## Reading

- **ST, Gle, HPY:** neutron star models, the Oppenheimer-Volkoff model, polytropic models, maximum mass, dependence of $R$ on the EOS.
- **Cam, Bec:** an overview of the neutron star M-R relation and observational constraints.

## Key concepts and equations

**Free neutron gas (Oppenheimer-Volkoff, 1939).** With $x=p_F/m_nc$ and the Chandrasekhar functions of Module 02 (neutron mass instead of the electron mass), $P=\frac{m_n^4c^5}{24\pi^2\hbar^3}[x(2x^2-3)\sqrt{1+x^2}+3\sinh^{-1}x]$ and $\epsilon$ as in Module 02. The TOV solution gives a maximum mass of about $0.7\,M_\odot$ at $\rho_c\sim5\times10^{15}$ g/cm$^3$ and a radius of about 9 to 10 km (verify). This is far below observed masses, showing that nuclear interactions are essential.

**$npe$ matter in beta equilibrium.** Ideal gases of neutrons, protons and electrons (and muons), $\mu_n=\mu_p+\mu_e$, charge neutrality (Module 02, problem 7), giving a small proton fraction and a slightly softer EOS than the pure neutron gas.

**Polytropes.** $P=K\rho^\Gamma$ (with rest-mass density $\rho$) or $P=K\epsilon^\Gamma$ (in terms of energy density); the Newtonian $n=1$ polytrope ($\Gamma=2$) has a radius independent of mass, $R=\pi\left(K/2\pi G\right)^{1/2}$ (derive), close to the typical observed neutron star radius of 11 to 13 km for suitable $K$. The relativistic $\Gamma=2$ family has $R$ roughly constant at moderate mass and a maximum mass that depends on $K$.

**Piecewise polytropes.** A common parameterization of realistic EOS: a fixed low-density crust (for example the SLy crust, Module 10) and three polytropic segments above $\sim0.5\,\rho_0$ with parameters $(\log P_1,\Gamma_1,\Gamma_2,\Gamma_3)$ where $P_1$ is the pressure at a fixed density $\rho_1=10^{14.7}$ g/cm$^3$ and the dividing densities are $10^{14.7}$ and $10^{15}$ g/cm$^3$ (Read et al. 2009; verify the exact choice in your sources). With continuity of $P$ and of the energy density (via the first law $d(\epsilon/\rho)=-Pd(1/\rho)$) at the boundaries, four numbers span a good fraction of the realistic EOS space.

**What controls the radius.** For a $1.4\,M_\odot$ star the radius correlates with the pressure of the EOS at one to two times saturation density: $R_{1.4}\propto P(n\sim1\text{ to }2\,n_0)^{1/4}$ (Lattimer and Prakash; verify), reflecting that the radius is determined by the balance of gravity and pressure where most of the volume resides.

**Causal maximum mass.** The maximum mass is bounded by $M_{\rm max}\lesssim3\,M_\odot$ for matching at nuclear density (Module 06); observed masses above $2\,M_\odot$ (J0348+0432: $2.01\pm0.04$; J0740+6620: $\approx2.1$; verify the latest values) require a stiff EOS at several times $\rho_0$.

## Hands-on problems

**1. [E] Free neutron gas.** Build the free neutron gas EOS $P(\epsilon)$, solve the TOV equations for $\epsilon_c=10^{14}$ to $10^{17}$ g/cm$^3$ (equivalent), and reproduce the Oppenheimer-Volkoff maximum mass $\approx0.7\,M_\odot$. Plot $M(\rho_c)$, $M(R)$, compactness and redshift. Identify the stable branch.

**2. [E] Polytropes.** Solve the TOV equations for $P=K\epsilon^\Gamma$ and for $P=K\rho^\Gamma$ with $\Gamma=2$ and with different $K$. Verify that $R$ is nearly mass-independent at low mass (the Newtonian $n=1$ result $R=\pi\sqrt{K/2\pi G}$) and that the maximum mass scales as $K^{-1/2}$ in appropriate units. Find $K$ that gives $R_{1.4}=12$ km.

**3. [M] $npe\mu$ matter.** Build the ideal $npe\mu$ matter in beta equilibrium of Module 02, solve the TOV equations and compare $M_{\rm max}$ and $R(M)$ with the free neutron gas. Explain why the correction is small.

**4. [M] A schematic nuclear EOS.** Use the schematic energy per baryon $e(n,\delta)$ of Module 08 problem 3 (or a simple fit like $P=K(\rho/\rho_0)^\Gamma$ above nuclear density with a free-gas low-density part) and check that, together with the TOV solver, it gives $M_{\rm max}\sim2\,M_\odot$ and $R_{1.4}\sim12$ km when tuned.

**5. [M] Piecewise polytropes.** Implement the piecewise polytropic family, with the thermodynamic bookkeeping for $\epsilon(P)$, continuity conditions and automatic checks for causality ($c_s\le c$) and monotonicity. Generate $M$-$R$ curves for a grid in $(\log P_1,\Gamma_1,\Gamma_2,\Gamma_3)$, and plot $R_{1.4}$, $M_{\rm max}$ and the central density of the maximum-mass star. Find which parameters control $R_{1.4}$ and which control $M_{\rm max}$.

**6. [M] The $R$-pressure correlation.** For your family, compute $P(n_0)$ and $P(2n_0)$ and plot $R_{1.4}$ against $P(1.5n_0)$ and against $P(2n_0)$ in log-log. Fit the slope and compare with the quoted $1/4$.

**7. [M] Fixed-baryon-number sequences.** Compute sequences of constant baryon mass $M_b$ and plot the gravitational mass versus central density. Show the binding energy released in the transition from a configuration to another, and discuss supramassive stars (stable only if rotating).

**8. [H] The maximum-mass bound.** Compute, for a family of EOS that match a realistic low-density EOS up to a density $n_m$ and are causal ($P=\epsilon-\epsilon_m$) above, the maximum mass as a function of $n_m$. Compare with the observed $M\ge2\,M_\odot$ to bound the minimum stiffness. Repeat with the speed of sound capped at $c_s^2=c^2/3$ (the conformal limit) to see how a conformal bound (which many quark-matter calculations respect) restricts $M_{\rm max}$.

**9. [H] Universal relations.** For your EOS families compute the compactness $C$ versus $M/M_{\rm max}$, the moment of inertia (after Module 12), and the tidal deformability (Module 13). Plot the nearly EOS-independent relations and measure their scatter. Which relations are good to a few percent and which are not?

## Software component

`compactlite/ns/sequences.py`: functions that, given an EOS object, return the $M$-$R$ curve, stability boundaries, $M_{\rm max}$, $R_{1.4}$, $R_{2.0}$, central densities and redshifts; piecewise polytrope and polytrope EOS classes with the thermodynamic consistency checks of Module 02.

## Checks

- Free neutron gas: $M_{\rm max}\approx0.7\,M_\odot$.
- Newtonian $n=1$ polytrope $R$ independent of $M$ at low mass.
- Piecewise polytropes passing continuity and causality tests; $R_{1.4}\propto P(1.5\,n_0)^{1/4}$ approximately.
- $dM/d\epsilon_c=0$ at the maximum mass.

## Pitfalls

- Defining the polytrope in terms of rest-mass density versus energy density without being consistent.
- Violating causality in the high-density segment.
- Using the maximum-mass configuration as typical (it is a single point at the end of the stable branch).
- Treating $R_{1.4}$ as strictly independent of $M_{\rm max}$; the two are correlated in specific ways.

## Gate questions

1. Why does the free neutron gas fail to reproduce observed neutron star masses?
2. Why is the neutron star radius nearly independent of mass in a wide range for realistic EOS?
3. Which density range controls the radius of a $1.4\,M_\odot$ star, and which controls the maximum mass?

## Deliverable

`compactlite/ns/sequences.py`, EOS parametrizations, `notebooks/07_ns_simple_eos.ipynb`, solutions for problems 1 to 9.
