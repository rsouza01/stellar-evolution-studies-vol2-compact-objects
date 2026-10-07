# Module 09: Relativistic mean field theory and hyperons

**Difficulty:** Hard. **Time:** about 3 weeks.

## Goal

Build the relativistic mean field (RMF, or quantum hadrodynamics, QHD) description of dense matter: the Walecka sigma-omega model, extensions (rho meson, nonlinear and density-dependent couplings), asymmetric matter in beta equilibrium, finite temperature, and the inclusion of hyperons and the Delta. Understand the hyperon puzzle. Deliver `eos/rmf`.

## Prerequisites

Modules 02, 04 (mean-field effective potential), 06 and 08. Relativistic quantum mechanics and basic field theory (your QHD track).

## Reading

- **Wal, FW, IZ, PS:** relativistic Lagrangians, mean-field approximation, the Dirac equation in a scalar and vector potential, the Hartree approximation.
- **Gle, Wb, HPY:** relativistic mean-field models in neutron stars, the nucleon-meson coupling constants, hyperon couplings, the hyperon puzzle.
- **R&S, Hey:** relativistic mean field for nuclei.
- Serot and Walecka's review of the relativistic nuclear many-body problem (a classical reference article).

## Key equations (derive)

**Lagrangian (nonlinear Walecka with $\rho$ meson).**

$$\mathcal L=\bar\psi\left[i\gamma^\mu\partial_\mu-M+g_\sigma\sigma-g_\omega\gamma^\mu\omega_\mu-\tfrac12g_\rho\gamma^\mu\vec\tau\cdot\vec\rho_\mu\right]\psi+\tfrac12(\partial\sigma)^2-U(\sigma)-\tfrac14\omega_{\mu\nu}\omega^{\mu\nu}+\tfrac12m_\omega^2\omega^2-\tfrac14\vec\rho_{\mu\nu}\cdot\vec\rho^{\mu\nu}+\tfrac12m_\rho^2\vec\rho^2$$

with the scalar potential $U(\sigma)=\tfrac12m_\sigma^2\sigma^2+\tfrac13g_2\sigma^3+\tfrac14g_3\sigma^4$. (Sign conventions for $\sigma$ differ between references: here the nucleon effective mass is $M^*=M-g_\sigma\sigma$.)

**Mean-field equations** (uniform matter; $\sigma$, $\omega_0$, $\rho_{03}$ constant; derive from the Euler-Lagrange equations):

$$M^*=M-g_\sigma\sigma,\quad\omega_0=\frac{g_\omega n_B}{m_\omega^2},\quad\rho_{03}=\frac{g_\rho}{2m_\rho^2}(n_p-n_n),\quad m_\sigma^2\sigma+g_2\sigma^2+g_3\sigma^3=g_\sigma n_s$$

with the scalar density $n_s=\sum_i\frac{1}{\pi^2}\int_0^{k_i}\frac{M^*}{\sqrt{k^2+M^{*2}}}k^2dk$ for spin 1/2 species. The energy density and pressure are

$$\epsilon=\tfrac12m_\sigma^2\sigma^2+\tfrac13g_2\sigma^3+\tfrac14g_3\sigma^4+\tfrac12m_\omega^2\omega_0^2+\tfrac12m_\rho^2\rho_{03}^2+\sum_i\frac1{\pi^2}\int_0^{k_i}\sqrt{k^2+M^{*2}}\,k^2dk+\epsilon_{\rm leptons}$$

$$P=-\tfrac12m_\sigma^2\sigma^2-\tfrac13g_2\sigma^3-\tfrac14g_3\sigma^4+\tfrac12m_\omega^2\omega_0^2+\tfrac12m_\rho^2\rho_{03}^2+P_{\rm kin}+P_{\rm leptons}$$

and the baryon chemical potential is $\mu_i=\sqrt{k_i^2+M^{*2}}+g_\omega\omega_0\pm\tfrac12g_\rho\rho_{03}$ (check by $\mu_i=\partial\epsilon/\partial n_i$ and by Gibbs-Duhem).

**Original Walecka parameters** (verify in your references): in the dimensionless form $C_\sigma^2=g_\sigma^2M^2/m_\sigma^2\approx267$ and $C_\omega^2=g_\omega^2M^2/m_\omega^2\approx196$ reproduce $n_0\approx0.17$ fm$^{-3}$ and $E/A\approx-15.75$ MeV, with $K_0\approx545$ MeV (too stiff), $M^*/M\approx0.55$ and the symmetry energy supplied only by the kinetic part and the $\rho$ meson. Modern parameter sets (nonlinear: NL3, TM1, FSUGold; density-dependent couplings: DD2, DD-ME2) are tuned to nuclei and give $K_0\approx230$ to $270$ MeV; NL3 is stiff ($L\approx118$ MeV, $M_{\rm max}\approx2.7\,M_\odot$), FSUGold is soft ($L\approx60$ MeV, $M_{\rm max}\approx1.7\,M_\odot$); verify with the original papers.

**Beta equilibrium and charge neutrality** in RMF: $\mu_n=\mu_p+\mu_e$, $\mu_\mu=\mu_e$, $n_p=n_e+n_\mu$ (plus hyperons).

**Hyperons.** With the extra baryons $\Lambda,\Sigma^{\pm,0},\Xi^{-,0}$ coupled to $\sigma$, $\omega$, $\rho$ and (for strangeness) the $\phi$ meson with ratios $x_{\sigma Y}$, $x_{\omega Y}$ constrained by hypernuclear potentials at saturation ($U_\Lambda^{(N)}\approx-28$ MeV, $U_\Sigma\approx+30$ MeV, $U_\Xi\approx-18$ MeV; verify). The appearance of hyperons at $2$ to $3\,n_0$ lowers the pressure and softens the EOS, reducing $M_{\rm max}$ typically to about $1.5$ to $1.8\,M_\odot$, in conflict with $2\,M_\odot$ observations: the **hyperon puzzle**. Proposed resolutions: repulsive $YY$ and $YN$ interactions via the $\phi$ meson or three-body forces, a quark-matter transition (Module 11), or stiffer nucleonic EOS.

**Finite temperature.** Replace the Fermi step functions by Fermi-Dirac distributions with the effective chemical potentials $\nu_i=\mu_i-g_\omega\omega_0\mp\dots$ (derive). The mean-field equations couple $T$ and $\mu$ through $n_s$ and $\sigma$ (Module 18).

## Hands-on problems

**1. [E] Symmetric nuclear matter in the Walecka model.** Solve the $\sigma$ self-consistency equation at each density by Newton or fixed-point iteration, compute $E/A$ and the pressure of SNM and show that the Walecka parameters give saturation at $n_0\approx0.17$ fm$^{-3}$ with $E/A\approx-15.75$ MeV and $K_0\approx545$ MeV. Plot $M^*(n)$ and the scalar and vector potentials (large and opposite, $\sim\pm350$ MeV, which sum to a modest binding).

**2. [M] The symmetry energy.** Add the $\rho$ meson and the isovector coupling, compute $S(n)$, $S_0$ and $L$ analytically (kinetic part plus $\rho$ part, with the effective mass) and numerically from the energy differences of PNM and SNM; verify the agreement.

**3. [M] Nonlinear terms and parameter sets.** Implement NL3, TM1 and a density-dependent set (parameters from the literature; verify). Compute $n_0$, $E/A$, $K_0$, $M^*/M$, $S_0$ and $L$ and compare with the published values. Plot $P(\epsilon)$ and the sound speed for each.

**4. [M] Neutron star matter.** Build the beta-equilibrium solver with nucleons, electrons, muons and plot $Y_p$, $Y_e$, $Y_\mu$, $M^*$ versus $n_B$. Determine the threshold density of the direct Urca process in each parameter set.

**5. [M] Stars.** Attach a crust (Module 10) and solve TOV for the three sets: reproduce $M_{\rm max}$ ($\approx2.7$ for NL3, $\approx2.2$ for DD2, $\approx1.7$ to $2.1$ for TM1 or FSUGold; verify), $R_{1.4}$ and the tidal deformability (Module 13). Plot the $M$-$R$ curves with the $2\,M_\odot$ and NICER-like constraint bands.

**6. [M] Fitting the parameters.** Given target saturation properties ($n_0$, $E/A$, $K_0$, $M^*/M$, $S_0$, $L$) solve the inverse problem for $(g_\sigma,g_\omega,g_\rho,g_2,g_3,\ldots)$ with Newton and a global optimizer. Show how many properties can be fixed independently and which parameters remain correlated.

**7. [H] Hyperons.** Add $\Lambda$, $\Sigma$, $\Xi$ with SU(6) or SU(3) coupling ratios, fix $x_{\sigma Y}$ by the potential depths at saturation, and solve beta equilibrium with the strangeness conditions (chemical potential relations $\mu_Y=b_Y\mu_n-q_Y\mu_e$). Find the hyperon thresholds, the composition and the softening, and the maximum mass. Add the $\phi$ meson with a varying coupling to see whether $M_{\rm max}\ge2\,M_\odot$ can be recovered, and quantify the required repulsion.

**8. [H] The Delta resonance.** Add the $\Delta(1232)$ with a coupling ratio to $\sigma$ and $\omega$ as parameters; show how $\Delta^-$ appears at $\sim1.5$ to $2n_0$ if the potential is attractive enough, changing the composition and $L$. Discuss the constraints from the observed masses.

**9. [H] Beyond Hartree.** Include the Fock exchange terms or the vacuum fluctuation (relativistic Hartree) correction to the scalar density for a simple $\sigma$-$\omega$ model (derive the extra integral), and see how $K_0$ and the effective mass change; compare with the literature. Discuss why density-dependent couplings are a pragmatic way of encoding such effects.

**10. [H] Finite temperature and neutrino trapping.** Extend the code to finite $T$ and fixed lepton fraction $Y_L$ (trapped neutrinos), and compute the thermal EOS at $T=0$ to $50$ MeV; compare with the $\Gamma_{\rm th}$ approximation of Module 18 and with published hot EOS tables.

## Software component

`compactlite/eos/rmf.py`: parameter-set registry, the self-consistency solver (nucleons, leptons, hyperons, optional $\Delta$), thermodynamic outputs ($P,\epsilon,\mu_i,c_s^2$, composition) with a consistency checker, finite-temperature option.

## Checks

- Walecka: $n_0\approx0.17$ fm$^{-3}$, $E/A\approx-15.75$ MeV, $K_0\approx545$ MeV (verify).
- Parameter sets reproduce their published saturation properties.
- Gibbs-Duhem and $\mu_i=\partial\epsilon/\partial n_i$ satisfied to $10^{-8}$.
- NL3: $M_{\rm max}$ well above $2\,M_\odot$; FSUGold-like sets softer.
- Hyperon onset reduces $M_{\rm max}$.

## Pitfalls

- Using $\epsilon$ and $P$ expressions with inconsistent sign conventions of $\sigma$.
- Failing to converge the $\sigma$ equation at high density (use damping and a good initial guess from the previous density).
- Taking the Walecka original parameters as a realistic EOS.
- Violating causality at high density in stiff sets.

## Gate questions

1. Why are the scalar and vector fields large and nearly cancel in the nucleon energy?
2. How does the effective mass drive the saturation mechanism in RMF models?
3. Why does the appearance of hyperons soften the EOS, and which mechanisms could cure the resulting tension with $2\,M_\odot$?

## Deliverable

`compactlite/eos/rmf.py`, parameter sets with sources, `notebooks/09_rmf.ipynb`, solutions for problems 1 to 10.
