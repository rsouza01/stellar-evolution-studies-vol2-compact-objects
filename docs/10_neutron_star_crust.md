# Module 10: The neutron-star crust

**Difficulty:** Hard. **Time:** about 3 weeks.

## Goal

Understand and compute the outer layers of a neutron star: the outer crust (nuclei in an electron gas, BPS), neutron drip, the inner crust (nuclei, free neutrons, pasta), the crust-core transition, the elastic properties of the solid crust and the role of the crust in observables (radius, moment of inertia, glitches, mountains, accreted matter). Build a unified crust-core EOS.

## Prerequisites

Modules 03, 06, 08 and 09.

## Reading

- **HPY, ST, Gle:** the outer crust (Baym-Pethick-Sutherland), the inner crust (Baym-Bethe-Pethick), nuclear pasta, the crust-core transition, the elastic properties, the composition of the accreted crust.
- **Ash, Ichi:** Coulomb crystals, lattice sums, shear modulus.
- Classic and review articles: Baym-Pethick-Sutherland (1971), Chamel and Haensel (Living Reviews), Pethick and Ravenhall (ARNPS) are standard references; use them as complements to the books.

## Key equations and concepts (derive)

**Outer crust (BPS).** For a baryon density $n_b$, matter is a lattice of nuclei $(A,Z)$ with a degenerate electron gas ($n_e=Zn_N$), at $T\approx0$. The energy density is

$$\epsilon=n_N\left[M(A,Z)c^2+E_L\right]+\epsilon_e(n_e),\qquad E_L=-C_M\frac{Z^2e^2}{a_i},\quad a_i=\left(\frac{3}{4\pi n_N}\right)^{1/3},\quad C_M=0.8959$$

with $n_N=n_b/A$ the nuclear number density and $n_e=Zn_N$ (Wigner-Seitz cell; derive the lattice term from Module 03). At fixed pressure (or at fixed baryon density) one chooses $(A,Z)$ to minimize the Gibbs energy per baryon (equivalently, the chemical potential $\mu_b=(\epsilon+P)/n_b$) over the nuclei in a mass table; the resulting sequence of nuclei in cold catalyzed matter is $^{56}$Fe, $^{62}$Ni, $^{64}$Ni, $^{66}$Ni, $^{86}$Kr, $^{84}$Se, $^{82}$Ge, $^{80}$Zn, $^{82}$Zn, $^{128}$Pd (and so on), with the number of neutrons increasing with depth until **neutron drip** at $\rho_{\rm drip}\approx4\times10^{11}$ g/cm$^3$ (BPS: $4.3\times10^{11}$; modern mass tables give a bit different composition; verify).

**Inner crust.** Beyond drip, a lattice of neutron-rich nuclei is immersed in a gas of free (superfluid) neutrons. In the Wigner-Seitz approximation the cell energy is minimized over the nuclear size, the cell radius and the neutron and proton density profiles using (i) a compressible liquid-drop model with surface and Coulomb energies, (ii) Thomas-Fermi with a Skyrme functional, or (iii) Hartree-Fock-Bogoliubov with shell and pairing effects. At $n_b\sim0.05$ to $0.1$ fm$^{-3}$ the energy favors **non-spherical "pasta" phases** (gnocchi, spaghetti, lasagna, anti-spaghetti, anti-gnocchi), and at $n_b\approx0.08$ fm$^{-3}$ (about $n_0/2$) matter becomes uniform: the **crust-core transition** (transition pressure $P_t\approx0.2$ to $0.6$ MeV/fm$^3$, correlated with $L$).

**Crust mass and thickness.** The crust of a $1.4\,M_\odot$ star with $R\approx12$ km is about $1$ km thick, with a mass of $0.01$ to $0.05\,M_\odot$ and a fraction of the moment of inertia of $\sim1$ to $2$ percent (the amount constrained by pulsar glitches; verify).

**Elastic properties.** The shear modulus of a bcc Coulomb crystal is $\mu=0.1194\,n_N(Ze)^2/a_i$ (Ogata-Ichimaru; derive from the phonon spectrum in Module 03). The breaking strain is $\sim0.1$ (molecular-dynamics results) and defines the maximum mountain height and the maximum quadrupole of a neutron star (Module 13). Shear waves travel at $c_t=\sqrt{\mu/\rho}$.

**Accreting crust.** Matter accreted onto a neutron star is compressed through a sequence of electron captures, neutron emissions and pycnonuclear reactions, releasing in total $\sim1.5$ to $2$ MeV per accreted baryon in the crust ("deep crustal heating"; Haensel and Zdunik), which sets the thermal state of quiescent transients (Module 14). The composition differs from the cold catalyzed one.

**Unified EOS.** A "unified" EOS describes crust and core with the same effective interaction (for example SLy, BSk, Skyrme and RMF-based unified tables), avoiding the artificial matching problem. Using a mismatched crust changes the radius by $\sim0.1$ to $0.3$ km.

## Hands-on problems

**1. [E] The outer crust composition.** For each baryon density from $10^7$ to $4\times10^{11}$ g/cm$^3$ minimize the energy per baryon over $(A,Z)$ from a mass table with lattice and electron energies. Reproduce the BPS sequence ($^{56}$Fe, $^{62}$Ni, $^{64}$Ni, ...) and the neutron-drip density. Compare with BPS (1971) and with a modern mass table (AME + extrapolations; verify). Plot $Z/A$ versus density.

**2. [E] Electron-capture thresholds and the bulk of the crust.** For each nuclide compute the threshold density for electron capture from the electron Fermi energy and the lattice correction. Show how each capture step changes $Z$ and relate it to the discontinuities of the density in the BPS EOS (first-order transitions with a density jump).

**3. [M] The BPS EOS.** Assemble $P(\rho)$ and $\epsilon(\rho)$ of the outer crust with the constant-pressure transitions between nuclides. Compare with the polytropic approximation $P\propto\rho^{4/3}$ and with the exact degenerate electron gas, and quantify the lattice correction.

**4. [M] Crust-core matching.** Take your core EOS from Module 8 or 9 and a crust (BPS plus a simple inner-crust polytrope or a tabulated unified EOS such as SLy; verify the source), match them at the crust-core transition density, and compute the $M$-$R$ curve. Compare it with the unified calculation and show how the unmatched crust changes $R_{1.4}$.

**5. [M] The compressible liquid drop model.** Implement the compressible liquid-drop energy of a spherical nucleus in a Wigner-Seitz cell with bulk (from your nuclear EOS), surface and Coulomb terms and the free neutron gas outside. Minimize over $(A,Z)$ and the cell radius at several baryon densities; identify where the nuclei fill the volume and become unstable and compare with the neutron-drip density and the pasta onset of the literature.

**6. [M] Pasta phases.** Generalize the liquid-drop model to dimension $d=1,2,3$ geometries (slabs, rods, spheres, and their inverse) with the proper Coulomb lattice energies (Ravenhall-Pethick-Wilson); find the sequence of phases versus density for a surface tension parameter and a symmetry-energy slope $L$, and show how the extent of the pasta region depends on $L$.

**7. [M] Elasticity.** Compute the shear modulus, the shear wave speed and the maximum elastic quadrupole (the "mountain") supported by a crust of given breaking strain $0.1$. Express the ellipticity $\epsilon_{\max}$ as a function of the crust thickness and compare with the quoted values of $\epsilon\sim10^{-6}$ to $10^{-5}$ (verify) and with the continuous-wave searches' upper limits.

**8. [M] Crust moment of inertia and glitches.** In the slow-rotation approximation (Module 12) compute the fraction of the moment of inertia in the crust as a function of $P_t$, $M$, $R$ and compare it with the amount required to explain Vela-type glitches (about 1.4 percent, increased if entrainment of the superfluid neutrons is accounted for; verify).

**9. [H] The accreted crust.** Follow a fluid element compressed from low density with the nuclear reaction network of Volume 1 plus pycnonuclear reactions and electron captures (a simplified network of a few species), obtain the sequence of reactions and the deep crustal heat released per baryon, and compare with $\sim1.5$ to $2$ MeV.

**10. [H] A Thomas-Fermi inner crust.** Solve the Thomas-Fermi equations for a nucleus in a Wigner-Seitz cell with a Skyrme functional and the Coulomb energy (self-consistently on a radial grid), including the neutron skin and the continuum neutron gas. Compare with the compressible liquid drop result and quantify the shell and pairing effects that the semiclassical approach misses.

## Software component

`compactlite/eos/crust.py`: BPS minimization (with a mass table), liquid-drop and pasta tools, unified crust tables, crust-core matching, shear modulus and crust-property utilities.

## Checks

- BPS sequence beginning $^{56}$Fe, $^{62}$Ni, $^{64}$Ni and neutron drip near $4\times10^{11}$ g/cm$^3$.
- Lattice energy with Madelung 0.8959 and shear modulus 0.1194 factor.
- Crust thickness about 1 km for $1.4\,M_\odot$ and $R=12$ km; crust moment of inertia $\sim1$ to $2$ percent.
- Matching with a core EOS reproduces unified results within $0.1$ to $0.3$ km in $R_{1.4}$.

## Pitfalls

- Treating the BPS transitions as smooth (they are first order with density jumps).
- Using measured masses only: far from stability the nuclear masses need models.
- Matching at an arbitrary density instead of a self-consistent crust-core transition.
- Forgetting that the crust composition changes for accreting stars.

## Gate questions

1. Why do nuclei become more neutron-rich with increasing depth in the outer crust?
2. What drives the pasta phases and why do they require the Coulomb energy?
3. Why does the crust-core transition pressure correlate with the density dependence of the symmetry energy?

## Deliverable

`compactlite/eos/crust.py`, tables with sources, `notebooks/10_crust.ipynb`, solutions for problems 1 to 10.
