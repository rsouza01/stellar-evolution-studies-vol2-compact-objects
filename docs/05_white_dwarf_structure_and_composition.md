# Module 05: White dwarf structure and composition

**Difficulty:** Medium. **Time:** about 3 weeks.

## Goal

Build white dwarf models from the equation of state up: Chandrasekhar theory, Coulomb and other corrections (Hamada-Salpeter), composition (He, C/O, O/Ne/Mg, Fe), finite-temperature effects, envelopes, the stability limits (electron capture, pycnonuclear reactions, general relativity), and observational mass-radius tests. Deliver the `wd/structure` component.

## Prerequisites

Modules 01, 02 and 03. Volume 1, Module 15 (basic white dwarf structure) is useful.

## Reading

- **ST, Cha:** the degenerate electron gas, Chandrasekhar theory, Hamada-Salpeter models, the white dwarf mass-radius relation, general-relativistic and instability corrections.
- **HKT, KWW, Iben:** white dwarfs as end points, composition, envelopes, cooling (preview), mass distribution.
- **Cam:** an overview of white dwarf populations and observational tests.

## Key equations (derive)

**Hydrostatic equilibrium with a degenerate EOS.** With $P(\rho)$ from Module 02 (the Chandrasekhar function of $x=(\rho/\mu_eB)^{1/3}$, $B=9.74\times10^5$ g/cm$^3$):

$$\frac{dP}{dr}=-\frac{Gm\rho}{r^2},\qquad\frac{dm}{dr}=4\pi r^2\rho$$

**Chandrasekhar limit.** In the ultrarelativistic limit $P=K\rho^{4/3}$ with $K=1.2435\times10^{15}\mu_e^{-4/3}$ (cgs) defines an $n=3$ polytrope with a unique mass

$$M_{\rm Ch}=4\pi\left(\frac{K}{\pi G}\right)^{3/2}\left(-\xi^2\theta'\right)_{\xi_1}=\frac{5.83}{\mu_e^2}M_\odot\ (1.456\,M_\odot\ \text{for}\ \mu_e=2)$$

At lower masses $R\propto M^{-1/3}$ ($n=3/2$ polytrope), and $R\to0$ as $M\to M_{\rm Ch}$.

**Chandrasekhar's dimensionless form.** Introduce the central relativity parameter $x_0=(\rho_c/\mu_eB)^{1/3}$ and scale the density, mass and radius with it. The structure equations then reduce to a single second-order ODE in one dimensionless radius, with a length scale proportional to $\mu_e^{-1}\,(\ldots)$ that you should derive and check against Cha. The one-parameter family labelled by $x_0$ gives $M(\rho_c)$ and $R(\rho_c)$, with $M\to M_{\rm Ch}$ as $x_0\to\infty$.

**Coulomb correction (Hamada-Salpeter).** The ion-sphere lattice energy per unit volume is $\epsilon_L=-C_MZ^2e^2n_i^{4/3}(4\pi/3)^{1/3}$ (derive from Module 03) and its pressure is $P_L=\epsilon_L/3$, negative: it lowers the pressure at given density, hence shrinks the star and reduces $M_{\rm Ch}$ by an amount that grows with $Z$. In addition the Thomas-Fermi corrections, the exchange and the correlation (Module 03) contribute small terms.

**Composition.**
- He cores ($M\lesssim0.45\,M_\odot$), C/O cores ($0.5$ to $\sim1.05\,M_\odot$), O/Ne/Mg cores ($\sim1.05$ to $1.35\,M_\odot$), and rare Fe or iron-rich cores (a mass-radius test case).
- Residual envelopes: typically $M_{\rm He}\lesssim10^{-2}M$ and $M_{\rm H}\lesssim10^{-4}M$ (the thickness changes the radius at low mass and the cooling).
- Mean molecular weight per electron: $\mu_e=2$ for He, C, O, Ne, Mg; $\mu_e=56/26=2.15$ for iron.

**Finite temperature.** Thermal corrections increase the radius, importantly for low-mass helium white dwarfs (ELM white dwarfs, $M\sim0.15$ to $0.25\,M_\odot$), where hydrogen envelope burning and the thermal pressure of the non-degenerate envelope matter, and negligibly for massive cold ones. At the surface the degeneracy is lifted in a thin nondegenerate envelope.

**Stability limits.**
1. *Electron capture* $(Z,A)+e^-\to(Z-1,A)+\nu_e$ sets in when the electron Fermi energy exceeds the threshold, removing pressure support: thresholds are about $10^9$ to $10^{11}$ g/cm$^3$ for C, O, Mg (compute them from mass tables with the lattice correction; see below).
2. *Pycnonuclear fusion* of carbon at $\rho\gtrsim10^{9}$ to $10^{10}$ g/cm$^3$ (very slow at low $T$).
3. *General-relativistic instability* sets in at densities $\gtrsim10^{10}$ g/cm$^3$, slightly reducing the maximum mass (a post-Newtonian correction; derive using Module 06).

**Gravitational redshift** $v_{\rm gr}=GM/Rc=0.636\,(M/M_\odot)/(R/R_\odot)$ km/s; Sirius B: about $80$ km/s.

## Hands-on problems

**1. [E] The Chandrasekhar mass-radius relation.** Integrate hydrostatic equilibrium with the exact Chandrasekhar EOS for $\mu_e=2$ from $\rho_c=10^3$ to $10^{10}$ g/cm$^3$. Plot $R(M)$ and verify the $M^{-1/3}$ limit at low mass and $M\to1.456\,M_\odot$ at high $\rho_c$. Compare with the $n=3/2$ and $n=3$ polytropes of Volume 1. Check $R(0.6\,M_\odot)\approx0.012\,R_\odot$.

**2. [E] Composition dependence.** Compute $R(M)$ for He ($\mu_e=2$), C/O ($\mu_e=2$), and Fe ($\mu_e=2.15$) white dwarfs with the ideal degenerate EOS. Explain why He and C have the same mass-radius relation in the ideal limit and how Fe differs. Compute $M_{\rm Ch}$ for each.

**3. [M] Hamada-Salpeter corrections.** Add the Coulomb lattice correction $P_L=\epsilon_L/3$ with the Madelung constant of Module 03 (and Thomas-Fermi, exchange, correlation if you like) for C, O, Mg and Fe. Plot the fractional change in $R(M)$ and in $M_{\rm Ch}$ for each. You should find a correction of a few percent in $R$ for Fe at intermediate masses and a smaller one for carbon; the maximum mass drops (about 1 to 2 percent for carbon; verify).

**4. [M] Electron-capture thresholds.** For $^4$He, $^{12}$C, $^{16}$O, $^{20}$Ne, $^{24}$Mg, find the density at which the electron Fermi energy (including the lattice correction, $E_F^{\rm eff}=E_F+\,$lattice term) exceeds the threshold $\Delta=(M_{Z-1}-M_Z)c^2$ from a mass table (AME; verify). Compare with the central density of a white dwarf approaching $M_{\rm Ch}$. Explain the role of the Coulomb correction and why electron capture on $^{24}$Mg and $^{20}$Ne triggers collapse in ONeMg stars.

**5. [M] Finite temperature.** Add a nondegenerate envelope to your model, with the thickness set by a mass fraction of hydrogen, and use the full EOS of Module 02 (finite $T$). Compute the radius of a $0.2\,M_\odot$ helium white dwarf at $T_{\rm eff}=8000$ to $20000$ K with and without a $10^{-3}M$ hydrogen envelope and compare with the ideal cold result (the radius can be $10$ to $50$ percent larger; verify against the literature).

**6. [M] Observational tests.** Use published masses and radii for a handful of white dwarfs (Sirius B, Procyon B, 40 Eri B, and a few eclipsing or astrometric systems; verify the data) and compare with your corrected mass-radius relation. Compute the gravitational redshift of each and compare with measurements (for example Sirius B: $\approx80$ km/s).

**7. [H] General-relativistic corrections.** Integrate the TOV equations (Module 06) with the white dwarf EOS and compare with the Newtonian result for $\rho_c=10^8$ to $10^{10}$ g/cm$^3$. Show that the maximum mass is lowered slightly and find the central density at the turning point of $M(\rho_c)$. Combine with the electron-capture instability to find which comes first for C/O and for O/Ne/Mg.

**8. [H] Rotating and magnetized white dwarfs.** Estimate the effect of rotation on the maximum mass using the Newtonian Roche or Hartle-type treatment (uniform and differential rotation), showing that rotation can raise the mass limit above $M_{\rm Ch}$ (up to about $1.5$ to $1.9\,M_\odot$ for differential rotation; verify). Add the effect of a strong magnetic field on the EOS using Module 04 (it matters only for $B\gtrsim10^{13}$ G in the dense core, so it does not matter for the observed fields) and on the structure (the Chandrasekhar-Fermi magnetic energy).

**9. [H] From structure to a population.** Combine your $M$-$R$ relation, the initial-final mass relation (Volume 1) and a cooling model (Module 14) to build the mass distribution of white dwarfs in a magnitude-limited sample, including Eddington-bias and selection effects, and compare with a Gaia-based mass distribution (peak near $0.6\,M_\odot$ with a tail to high masses and a bump for helium white dwarfs).

## Software component

`compactlite/wd/structure.py`: hydrostatic solver with a pluggable EOS (ideal degenerate, Coulomb-corrected, finite-$T$ with envelope), `wd.mass_radius(composition, corrections)`, threshold-density utilities and the observational comparison tools.

## Checks

- $M_{\rm Ch}\approx1.456\,M_\odot$ for $\mu_e=2$ in the ideal limit.
- $R(0.6\,M_\odot)\approx0.012\,R_\odot$ and the $M^{-1/3}$ scaling at low mass.
- Sirius B redshift near 80 km/s.
- Hamada-Salpeter shifts of the right sign and magnitude.
- Electron-capture thresholds of order $10^{9}$ to $10^{11}$ g/cm$^3$ (verify with ST).

## Pitfalls

- Forgetting that the mean molecular weight per electron of iron is not 2.
- Treating the Coulomb correction as small at all $Z$ (it is significant for iron).
- Taking the ideal result as the observed relation: low-mass white dwarfs depend strongly on envelope and temperature.
- Using Newtonian gravity close to $M_{\rm Ch}$ without checking the general-relativistic correction.

## Gate questions

1. Why is the Chandrasekhar mass independent of the details of the nonrelativistic regime?
2. How does the Coulomb correction change the mass-radius relation and the maximum mass?
3. Which physical process determines whether a near-Chandrasekhar white dwarf explodes or collapses?

## Deliverable

`compactlite/wd/structure.py` with tests, `notebooks/05_white_dwarfs.ipynb`, solutions for problems 1 to 9.
