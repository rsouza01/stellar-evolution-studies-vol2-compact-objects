# Module 03: Statistical mechanics II, interacting systems, plasmas, crystals and phase transitions

**Difficulty:** Medium to hard. **Time:** about 3 weeks.

## Goal

Go beyond the ideal gas: mean-field and Hartree-Fock theory, the interacting electron gas, Landau Fermi-liquid theory, the one-component plasma (OCP) and Coulomb crystals, Thomas-Fermi theory, and the thermodynamics of first-order phase transitions (Maxwell and Gibbs constructions). Use Monte Carlo and molecular dynamics to compute properties numerically.

## Prerequisites

Modules 01 and 02. Quantum mechanics of many-particle systems (second quantization).

## Reading

- **FW, Pin, AGD:** Hartree-Fock, the electron gas, linear response, screening.
- **BP, Pin:** Landau Fermi-liquid theory.
- **Ichi, H&M, Ash:** plasmas, the one-component plasma, Debye-Hueckel theory, Wigner crystals, lattice sums, phonons.
- **LL5, Pat:** phase transitions, Maxwell construction, Clausius-Clapeyron.
- **Fra:** Monte Carlo and molecular dynamics.
- **ST, HPY:** Coulomb corrections to stellar matter, the Thomas-Fermi model.

## Key equations (derive)

**Electron gas in Hartree-Fock.** With the density parameter $r_s=a_0^{-1}(3/4\pi n)^{1/3}$, the energy per electron is (Rydberg units)

$$\frac EN=\frac{2.21}{r_s^2}-\frac{0.916}{r_s}+\varepsilon_c(r_s)$$

with the exchange term $-0.916/r_s$ from Hartree-Fock and the correlation energy $\varepsilon_c$ (Wigner interpolation, and at high density $\varepsilon_c\approx0.0622\ln r_s-0.096$ in Rydberg; verify). For relativistic degenerate electrons the exchange correction is a positive correction to the energy and a negative correction to the pressure of relative size $\sim\alpha_{\rm em}$ (Salpeter).

**Landau Fermi-liquid theory.** Quasiparticles with effective mass $m^*$ and interaction function $f_{\mathbf{pp}'}=\sum_\ell f_\ell P_\ell(\cos\theta)$, dimensionless $F_\ell=N(0)f_\ell$ with $N(0)=m^*p_F/\pi^2\hbar^3$ (spin 1/2). Key results (derive):

$$\frac{m^*}{m}=1+\frac{F_1}{3},\qquad C_V=\frac{m^*p_F}{3\hbar^3}k_B^2T\ (\text{per volume}),\qquad\kappa^{-1}\propto\frac{1+F_0}{N(0)}\ (\text{compressibility})$$

**One-component plasma (OCP).** Ions of charge $Z$ in a uniform neutralizing background. The ion-sphere radius is $a_i=(3/4\pi n_i)^{1/3}$ and the coupling $\Gamma=Z^2e^2/(a_ik_BT)$. Limits:

- Debye-Hueckel (weak coupling): $u/(Nk_BT)=-\frac{\sqrt3}{2}\Gamma^{3/2}$.
- Ion-sphere/Madelung energy at low temperature: the static lattice energy per ion is $E_L=-C_M\,Z^2e^2/a_i$ with Madelung constant $C_M=0.8959$ (bcc) (check Ichi), so $E_L/Nk_BT=-0.8959\,\Gamma$.
- Liquid fit (Hansen; DeWitt and Slattery; Potekhin and Chabrier): $u(\Gamma)=a\Gamma+b\Gamma^{1/4}+c\Gamma^{-1/4}+d$ for $1\lesssim\Gamma\lesssim170$; use a published fit and verify its limits.
- Crystallization at $\Gamma\approx175$.

**Pressure from a scale-invariant correction.** If the correction to the energy density scales as $\epsilon_C\propto n^{4/3}$, as it does for the ion-sphere energy at fixed $Z$, then $P_C=\frac13\epsilon_C$ (derive from $P=n^2\,d(\epsilon/n)/dn$).

**Phonons in a Coulomb crystal.** The ion plasma frequency $\omega_p=(4\pi Z^2e^2n_i/M)^{1/2}$ and Debye temperature $\Theta_D\approx0.45\,\hbar\omega_p/k_B$ (bcc; check). Thermal corrections: $C_V$ follows the Debye law at $T\ll\Theta_D$ and tends to $3k_B$ per ion at high $T$.

**Thomas-Fermi theory.** The electron density in a Coulomb field satisfies $\mu=\frac{p_F^2(r)}{2m}-e\phi(r)$ (nonrelativistic), $\nabla^2\phi=4\pi e\,n_e(\phi)-4\pi Ze\,\delta^3(\mathbf r)$ (neutral atom or ion-sphere cell, with a boundary condition at the cell edge).

**Phase transitions.** For a first-order transition between phases 1 and 2 at fixed $T$ with one conserved charge: the **Maxwell construction** requires $P_1(\mu)=P_2(\mu)$ at the coexistence chemical potential (equal $\mu$, $P$, $T$). With *two* conserved charges (baryon number and electric charge), the **Gibbs construction** requires equal $\mu_n$, $\mu_e$ and $P$ in both phases and only global charge neutrality, giving a mixed-phase region of finite extent (Glendenning). Surface and Coulomb energies push the true answer toward the Maxwell case (the "pasta" structures of Module 10).

## Hands-on problems

**1. [E] The electron gas.** Compute the Hartree-Fock energy per electron versus $r_s$. Show that the HF energy $2.21/r_s^2-0.916/r_s$ has a minimum at $r_s\approx4.8$ with $E\approx-0.095$ Ry, and that adding a correlation term (Wigner interpolation) deepens it and moves the minimum to somewhat smaller $r_s$ (verify the numbers in FW or Pin). Then compare the exchange pressure with the ideal degenerate pressure at white dwarf densities, showing that the correction is below one percent.

**2. [E] Debye-Hueckel and Madelung.** Plot the OCP energy $u(\Gamma)$ from Debye-Hueckel (weak) and from the Madelung energy (strong) and show where they cross. Compute the ion-sphere radius and $\Gamma$ in the core of a $0.6\,M_\odot$ carbon-oxygen white dwarf at $T=10^7$ K ($\rho\approx3\times10^6$ g/cm$^3$) and compare with $\Gamma=175$.

**3. [M] Coulomb correction to the white dwarf EOS.** Add the ion-sphere lattice energy and its pressure ($P_C=\epsilon_C/3$) to the degenerate electron EOS, for carbon and for iron. Compare the corrected $P(\rho)$ with the ideal one at $\rho=10^5$ to $10^9$ g/cm$^3$. You should find a correction that is small in carbon and visible in iron, and that grows with $Z^{2/3}$. This is the Hamada-Salpeter correction used in Module 05.

**4. [M] A Fermi liquid.** Using a model with $F_0$, $F_1$, $m^*$ for neutron matter at nuclear density, compute the specific heat, compressibility and sound speed. Show how a larger $m^*$ increases the neutrino and photon cooling timescale (preview of Module 14), and how $F_0\to-1$ signals an instability.

**5. [M] Thomas-Fermi atoms and cells.** Solve the Thomas-Fermi equation numerically for an ion in a neutral spherical cell at several densities. Compute the pressure and show that Thomas-Fermi corrections reduce to the Coulomb correction of problem 3 at high density. Compare with the degenerate electron gas at zero temperature.

**6. [M] Maxwell construction.** For a van der Waals-like EOS with a loop, and for a pair of analytic EOS in two phases (a hadronic polytrope and a bag-model quark phase), find the coexistence point by equating pressures at equal $\mu$. Compute the energy-density jump $\Delta\epsilon$ and the latent heat.

**7. [H] OCP Monte Carlo.** Write a Metropolis Monte Carlo simulation of the OCP with $N=128$ to $512$ ions in a periodic cell with Ewald summation (use Numba). Measure the internal energy $u(\Gamma)$ for $\Gamma=1$ to $200$, the radial distribution $g(r)$ and the structure factor; compare $u(\Gamma)$ with Debye-Hueckel, the Madelung bcc value and the liquid fit. Estimate the melting point by cooling and heating runs and looking for hysteresis (the melting $\Gamma$ is about $175$, the exact location is a delicate calculation, so report your estimate and its uncertainty).

**8. [H] Molecular dynamics.** Implement a velocity-Verlet MD of the OCP in the same cell, compute the diffusion coefficient from the mean-square displacement and the ion plasma frequency from the current autocorrelation. Compare with the liquid-phase fits and with the phonon spectrum in the crystal ($\Gamma>175$). Explain why long-range forces need Ewald or particle-mesh methods.

**9. [H] Gibbs construction.** Using a hadronic EOS with a given symmetry energy and a quark bag EOS (take simple analytic forms), perform the Gibbs construction with two chemical potentials $(\mu_n,\mu_e)$ and charge neutrality. Find the mixed-phase region and compare the pressure plateau with the Maxwell case. Add a surface tension and Coulomb term in a Wigner-Seitz cell and see how the mixed phase shrinks (preview).

## Software component

`compactlite/plasma/` (OCP energy fits, Madelung, Debye-Hueckel, Thomas-Fermi cell solver, MC and MD tools), and `compactlite/phase/` (Maxwell and Gibbs constructions on tabulated EOS).

## Checks

- Debye-Hueckel and Madelung limits of the OCP simulation to a few percent.
- Hartree-Fock exchange pressure below one percent of the degenerate pressure at white dwarf densities.
- Coulomb-corrected carbon EOS differing from the ideal one by percent-level amounts at $\rho\sim10^6$ g/cm$^3$.
- Maxwell construction satisfying equal $P$, $\mu$ at the transition.

## Pitfalls

- Using Debye-Hueckel beyond $\Gamma\sim1$.
- Forgetting the neutralizing background in the Ewald sum.
- Applying a Maxwell construction where a Gibbs construction is required (two conserved charges) without checking finite-size effects.
- Confusing the effective mass $m^*$ with the Landau mass in relativistic mean-field models (Module 09).

## Gate questions

1. Why is the exchange energy of the electron gas negative and why does it reduce the pressure?
2. Why does the Coulomb correction scale as $n^{4/3}$ and what does that imply for $P_C$?
3. What distinguishes a Maxwell from a Gibbs construction physically?

## Deliverable

`compactlite/plasma/`, `compactlite/phase/`, `notebooks/03_interacting.ipynb`, solutions for problems 1 to 9.
