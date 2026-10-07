# Module 01: Foundations, the compact-object zoo, units and toolkit

**Difficulty:** Easy. **Time:** about 1 week.

## Goal

Know what compact objects are, what is observed about white dwarfs and neutron stars, which dimensionless numbers organize the subject (compactness, degeneracy, coupling), and build the numerical building blocks (unit systems, quadrature, ODE solvers, tables, MCMC basics) the later modules rely on.

## Prerequisites

Graduate-level physics; Volume 1 (stellar structure) is helpful but not required.

## Reading

- **ST, Cam, Bec, HPY:** the introductory chapters on the observed properties of white dwarfs, neutron stars and pulsars, and on the end points of stellar evolution.
- **HKT, KWW:** white dwarfs in the context of stellar evolution.
- **L&K, LGS:** the pulsar population, timing, $P$-$\dot P$ diagram.
- **NR:** quadrature, ODE integration, interpolation.

### Task 0: build your reading map

Open the tables of contents of the books you own. In `notes/reading_map.md` fill a table with columns *Module, ST, Gle, HPY, HKT, Pat, ...*, using the overview's topic list as a first guess. Update it as you go.

## Concepts

1. **White dwarfs.** Cores of low and intermediate-mass stars, supported by electron degeneracy. Typical mass $0.6\,M_\odot$, radius $\sim0.012\,R_\odot$ ($\sim9000$ km), mean density $\sim10^6$ g/cm$^3$, $\log g\approx8$, $T_{\rm eff}$ from $4000$ K to over $10^5$ K. Spectral classes: DA (hydrogen), DB (helium), DQ (carbon), DZ (metals), DO, PG1159. About 97 percent of stars end as white dwarfs.
2. **Neutron stars.** Masses $1.2$ to $\sim2.1\,M_\odot$ (typical $1.4$), radii $\sim10$ to $13$ km, central densities $(2$ to $8)\,\rho_0$ with $\rho_0\approx2.7\times10^{14}$ g/cm$^3$ ($n_0\approx0.16$ fm$^{-3}$), $B\sim10^8$ to $10^{15}$ G, spin periods from about 1.4 ms to over 10 s. Observed as pulsars, X-ray binaries, thermal sources, magnetars and gravitational-wave sources.
3. **Dimensionless numbers.**
   - *Compactness* $C=GM/Rc^2$: $\sim10^{-6}$ for the Sun, $\sim10^{-4}$ for a white dwarf, $\sim0.15$ to $0.2$ for a neutron star (Buchdahl limit $4/9$).
   - *Degeneracy* $T/T_F$ and the *relativity parameter* $x=p_F/mc$.
   - *Coulomb coupling* $\Gamma=Z^2e^2/(a_ik_BT)$ (crystallization near $\Gamma\approx175$).
4. **Characteristic observables.** Mass (binary pulsar timing, spectroscopic, GW), radius (X-ray spectra, pulse profiles, parallax plus photometry for white dwarfs), gravitational redshift, moment of inertia (in principle from double pulsars), tidal deformability (GW), cooling curves, spin and magnetic field from $P$ and $\dot P$.
5. **The logic of the subject.** Microphysics (EOS and composition) $\to$ structure (Newtonian for white dwarfs, relativistic for neutron stars) $\to$ observables. The inverse problem, constraining microphysics from observations, is Module 19.

## Key quantities

| Quantity | Value (verify) |
| --- | --- |
| $GM_\odot/c^2$ | $1.477$ km |
| $GM_\odot/c^3$ | $4.925\ \mu$s |
| $\rho_0$ ($n_0=0.16$ fm$^{-3}$) | $\approx2.7\times10^{14}$ g/cm$^3$ ($\approx150$ MeV/fm$^3$ in rest mass) |
| $\hbar c$ | $197.327$ MeV fm |
| 1 MeV/fm$^3$ | $1.602\times10^{33}$ dyn/cm$^2$ (pressure) $=1.783\times10^{12}$ g/cm$^3$ (mass density) |
| Electron critical field $B_c=m_e^2c^3/e\hbar$ | $4.414\times10^{13}$ G |
| Eddington luminosity | $1.26\times10^{38}(M/M_\odot)$ erg/s for $\kappa_{\rm es}=\sigma_T/m_p$ |

Compactness and redshift of a $1.4\,M_\odot$ star with $R=12$ km: $C=2.07\ {\rm km}/12\ {\rm km}\approx0.17$, and $1+z=(1-2C)^{-1/2}\approx1.24$.

Pulsar quantities (to derive in Module 12): $B\approx3.2\times10^{19}\sqrt{P\dot P}$ G, $\tau=P/2\dot P$, $\dot E=4\pi^2I\dot P/P^3$.

## Hands-on problems

**1. [E] Units.** Write `units.py` with constants and conversions between cgs, geometric ($G=c=1$) and nuclear ($\hbar=c=1$, MeV and fm) units, including pressure and energy density in MeV/fm$^3$, g/cm$^3$ and dyn/cm$^2$. Test the factors in the table above.

**2. [E] Compactness table.** Tabulate $C$, $1+z$, mean density, surface gravity and escape speed for the Sun, Sirius B ($\approx1.02\,M_\odot$, $\approx0.008\,R_\odot$), a $0.6\,M_\odot$ white dwarf, a $1.4\,M_\odot$ neutron star with $R=12$ km, and a $2.0\,M_\odot$ neutron star with $R=12$ km. Explain which objects need general relativity.

**3. [M] The pulsar population.** Download the ATNF pulsar catalogue (public; verify access) and plot the $P$-$\dot P$ diagram with lines of constant $B$, characteristic age and spin-down luminosity. Identify millisecond pulsars, magnetars, binary pulsars and the death line. Plot the distribution of neutron-star masses from the catalogue entries with measured masses.

**4. [M] White dwarfs from Gaia.** Obtain a catalogue of high-confidence Gaia white dwarfs (verify the source), plot the colour-magnitude diagram, and compute masses from $\log g$ and $T_{\rm eff}$ where available. Plot the mass distribution and locate the peak near $0.6\,M_\odot$. Which selection effects matter?

**5. [M] Gravitational redshift of Sirius B.** Compute $v_{\rm gr}=GM/Rc\approx0.636\,(M/M_\odot)/(R/R_\odot)$ km/s and show that Sirius B has about 80 km/s. Compare with the redshift of a neutron star at $C=0.17$.

**6. [M] Quadrature and ODEs.** In `compactlite/math/` implement: Gauss-Legendre and Gauss-Laguerre quadrature, adaptive Gauss-Kronrod via `scipy`, RK4 and an adaptive RK45, monotone cubic (PCHIP) and bicubic table interpolation in log variables, Brent root finding and multidimensional Newton with line search. Test each on analytic cases.

**7. [M] MCMC basics.** Implement a Metropolis-Hastings sampler and test it on a correlated 2D Gaussian and on a banana-shaped posterior; then verify that `emcee` and a nested sampler (for example `dynesty`) agree on the same problem. This is the machinery of Module 19.

**8. [H] Automatic differentiation.** Implement forward-mode automatic differentiation with dual numbers (or use JAX) and compute the derivatives of a toy EOS $P(\rho)$ and of $\epsilon(n)$. Decide, with timing data, how you will obtain derivatives such as $dP/d\epsilon$ (needed for the sound speed and for tidal deformabilities).

## Software component

`compactlite/units.py` and `compactlite/math/` (quadrature, ODE, tables, root finding, samplers), with a test suite.

## Checks

- Unit conversions agree with the table to five digits.
- Sirius B redshift of about 80 km/s.
- $C\approx0.17$ and $1+z\approx1.24$ for the fiducial neutron star.
- MCMC samplers recover the known moments of the test distributions.

## Pitfalls

- Confusing energy density ($\epsilon$, including rest mass) with mass density ($\rho$) in neutron-star physics.
- Mixing MeV/fm$^3$ with erg/cm$^3$ and g/cm$^3$ factors.
- Using catalogue masses without noting their method and uncertainty.

## Gate questions

1. Why does a white dwarf need only Newtonian gravity while a neutron star needs general relativity?
2. Which dimensionless parameters decide whether a given plasma is classical, degenerate, relativistic, strongly coupled?
3. What is measured directly for compact stars: mass, radius, or both, and by which technique each?

## Deliverable

`units.py`, `math/`, `notebooks/01_foundations.ipynb`, `notes/reading_map.md`, solutions for problems 1 to 8.
