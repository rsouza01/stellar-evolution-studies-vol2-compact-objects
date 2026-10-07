# Module 04: Statistical mechanics III, superfluidity, magnetized matter, thermal field theory and transport

**Difficulty:** Hard. **Time:** about 3 weeks.

## Goal

Learn the three advanced tools that compact-star physics needs beyond classical and Fermi-liquid theory: **pairing** (BCS superfluidity and superconductivity, including its effect on thermodynamics and neutrino emission), **magnetized degenerate matter** (Landau quantization), and **finite-temperature, finite-density field theory** (the path integral partition function, the Matsubara formalism, mean-field approximations). Add the basics of transport in degenerate matter (kinetic theory, thermal and electrical conductivity).

## Prerequisites

Modules 02 and 03. Quantum field theory at the level of a first course (your QFT track).

## Reading

- **Tin, Schr, FW, AGD:** BCS theory, the gap equation, the Ginzburg-Landau theory, thermodynamics of superconductors.
- **LL5, Wb, HPY:** Landau quantization and magnetized degenerate gases; superfluidity in neutron stars.
- **Kap, LeB:** the path integral for the partition function, Matsubara frequencies, free and interacting gases, the effective potential.
- **PS, IZ, Gre:** field-theoretic background.
- **Ash, LL5, HPY:** kinetic theory, the relaxation-time approximation, electrical and thermal conductivity, Wiedemann-Franz law.

## Key equations (derive)

**BCS gap equation.** For an attractive interaction $-V$ in a shell of width $\hbar\omega_c$ about the Fermi surface, with density of states $N(0)$ at the Fermi surface:

$$1=VN(0)\int_0^{\hbar\omega_c}\frac{d\xi}{E_\xi}\tanh\frac{E_\xi}{2k_BT},\qquad E_\xi=\sqrt{\xi^2+\Delta^2}$$

At $T=0$: $\Delta_0\simeq2\hbar\omega_ce^{-1/N(0)V}$ (weak coupling). The critical temperature satisfies $k_BT_c=\frac{e^\gamma}{\pi}\Delta_0\approx0.567\,\Delta_0$ ($\Delta_0=1.764\,k_BT_c$). Low-temperature thermodynamics is exponentially suppressed: $C_V\propto e^{-\Delta/k_BT}$. In neutron stars: neutron $^1S_0$ pairing in the inner crust and outer core (gaps up to $\sim1$ MeV, $T_c\sim10^9$ to $10^{10}$ K), neutron $^3P_2$ pairing in the core, and proton $^1S_0$ pairing in the core (the numbers depend strongly on the model; verify with HPY).

**Landau quantization.** In a uniform magnetic field $B$ along $z$, the relativistic electron energy levels are

$$E_n(p_z)=\sqrt{m^2c^4+p_z^2c^2+2n\hbar c^2eB},\qquad n=0,1,2,\dots$$

with degeneracy per area $eB/2\pi\hbar c$ (twice that for $n\ge1$ because of the two spin states, once for $n=0$). The critical field is $B_c=m_e^2c^3/e\hbar=4.414\times10^{13}$ G. At fixed density only $\nu_{\max}$ levels are populated; all electrons sit in the lowest level when $\rho\lesssim7\times10^3\,\mu_e^{-1}B_{12}^{3/2}$ g/cm$^3$ (verify). The magnetized pressure and energy are sums over levels,

$$P=\frac{eB}{2\pi^2\hbar^2c}\sum_n g_n\int_0^{p_F^{(n)}}\frac{p_z^2c^2}{E_n}\,dp_z\ \text{(at }T=0\text{, up to constants; derive)}$$

and the EOS departs from the nonmagnetic one visibly only for $B\gtrsim10^{16}$ to $10^{17}$ G in neutron star cores, but strongly for $B\sim10^{12}$ to $10^{15}$ G in outer layers and atmospheres.

**Thermal field theory.** The partition function of a fermion field with chemical potential $\mu$ is the Euclidean path integral

$$\mathcal Z={\rm Tr}\,e^{-\beta(\hat H-\mu\hat N)}=\int\mathcal D\bar\psi\mathcal D\psi\,e^{-S_E},\qquad S_E=\int_0^\beta d\tau\int d^3x\left[\bar\psi(\gamma^0(\partial_\tau-\mu)+\vec\gamma\cdot\vec\nabla+m)\psi+\dots\right]$$

with fermionic Matsubara frequencies $\omega_n=(2n+1)\pi T$. For the free gas the pressure is $P=T\int\frac{d^3p}{(2\pi)^3}\ln\!\left(\ldots\right)$, which reduces to the formulas of Module 02 after the Matsubara sum, $T\sum_n\ln(\omega_n^2+E^2)\to E+2T\ln(1+e^{-E/T})$. For interacting theories (Module 09, 11), the **mean-field approximation** replaces fields by expectation values and gives $P(\mu,T)=-\Omega_{\rm MF}/V$ at the minimum of the effective potential, from which all other quantities follow by differentiation.

**Kinetic theory and transport.** In the relaxation-time approximation the electrical conductivity is $\sigma=ne^2\tau/m^*$ and the thermal conductivity of degenerate electrons is $\kappa=\frac{\pi^2}{3}\frac{k_B^2T}{e^2}\sigma$ (Wiedemann-Franz law, valid for elastic scattering; derive and state the limits). Scattering processes: electron-ion (Coulomb) in the liquid and crystal, electron-phonon, electron-impurity, electron-electron. Matthiessen's rule adds scattering rates: $\tau^{-1}=\sum_i\tau_i^{-1}$.

## Hands-on problems

**1. [E] The BCS gap at $T=0$.** Solve the gap equation numerically for a given $N(0)V$ and cutoff, obtain $\Delta_0$ and compare with the weak-coupling formula. Plot $\Delta_0$ versus $N(0)V$ and see where the weak-coupling formula fails.

**2. [E] Landau levels.** Compute the number of occupied Landau levels for a degenerate electron gas of given density in fields $B=10^{12},10^{13},10^{14},10^{15}$ G. Find the density below which only the ground level is occupied and compare with the formula above.

**3. [M] The gap versus temperature.** Solve the finite-temperature gap equation to obtain $\Delta(T)$, reproduce the universal shape and $T_c=0.567\,\Delta_0/k_B$, and compute the entropy and heat capacity including the jump at $T_c$ (BCS jump $\Delta C/C_N\approx1.43$) and the exponential suppression below $T_c$. Explain the implication for neutron star cooling: a superfluid core with $T\ll T_c$ has a strongly reduced heat capacity and a suppressed neutrino emissivity from Urca processes.

**4. [M] Pair breaking and formation (PBF).** Read the structure of the neutrino emissivity from Cooper pair breaking and formation near $T_c$ (HPY) and implement a suppression-factor function for an Urca process as a function of $\Delta/k_BT$ (you will use it in Module 14). Compare it with the unsuppressed rate.

**5. [M] The magnetized electron gas.** Compute $P(\rho)$, $\epsilon(\rho)$ and the electron chemical potential for a degenerate electron gas in $B=10^{14}$ to $10^{17}$ G, summing Landau levels, with oscillatory (de Haas-van Alphen-like) structure. Compare with the nonmagnetic EOS and find the field at which the correction is one percent at $\rho=10^{14}$ g/cm$^3$.

**6. [M] Matsubara sums.** Verify numerically that the Matsubara-sum form of the free fermion pressure reproduces the closed form of Module 02 for several $(\mu,T)$, and that the mean-field effective potential of a simple $\sigma$-fermion model reproduces the correct self-consistent solution found by direct iteration (preview of Module 09).

**7. [M] Conductivity.** Using the relaxation-time approximation, compute the electrical and thermal conductivities of the degenerate electron gas of a white dwarf core (carbon, $\rho=10^6$ g/cm$^3$, $T=10^7$ K) from the electron-ion scattering rate with the OCP structure factor of Module 03, and the electron conductive opacity. Check the Wiedemann-Franz law.

**8. [H] Pairing in neutron matter.** Solve the BCS gap equation with a realistic bare interaction in the $^1S_0$ channel (a separable or Gogny-like toy potential fitted to the scattering length; or use a published gap curve $\Delta(k_F)$) to obtain $\Delta(k_F)$ and $T_c(k_F)$ across the crust and outer core. Plot the density regions where neutrons are superfluid and compare with the range of the literature models (the curves differ widely; discuss why).

**9. [H] The effective potential.** For a model with a fermion coupled to a scalar field ($\mathcal L=\bar\psi(i\partial\!\!\!/-m_0-g\sigma)\psi+\frac12(\partial\sigma)^2-U(\sigma)$) compute the effective potential at finite $T$ and $\mu$ in the mean-field approximation. Find the self-consistent $\sigma(\mu,T)$, the pressure and the phase structure (first-order transition for a double-well $U$). Compare with a direct numerical minimization.

## Software component

- `compactlite/pairing/`: BCS gap equation, $\Delta(T)$, thermodynamic suppression and PBF factors.
- `compactlite/magnetized/`: magnetized degenerate gas (Landau levels).
- `compactlite/transport/`: conductivity and conduction opacities with Matthiessen's rule.
- A mean-field effective-potential solver (generalized in Modules 09 and 11).

## Checks

- Weak-coupling $\Delta_0$ formula reproduced at small $N(0)V$.
- $\Delta_0/k_BT_c=1.764$ and the specific heat jump of about $1.43$.
- Landau level counting and the ground-level threshold density.
- Magnetized EOS approaching the nonmagnetic one when many levels are populated.
- Wiedemann-Franz law verified for elastic scattering.

## Pitfalls

- Using the BCS weak-coupling formula in the strong-coupling or BCS-BEC crossover regime.
- Mixing up the number of Landau-level states at $n=0$ (single spin) and $n\ge1$.
- Forgetting that the Wiedemann-Franz law fails for inelastic scattering.
- Confusing Euclidean and Minkowski conventions in the path integral.

## Gate questions

1. Why does pairing suppress the heat capacity and Urca neutrino emission but enhance emission near $T_c$?
2. Why is the magnetized EOS only modified significantly in strong fields or at low densities?
3. In what sense is mean-field theory the leading term in a loop expansion of the partition function?

## Deliverable

`compactlite/pairing/`, `compactlite/magnetized/`, `compactlite/transport/`, `notebooks/04_pairing_magnetized_ft.ipynb`, solutions for problems 1 to 9.
