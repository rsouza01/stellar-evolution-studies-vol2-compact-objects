# Module 14: Thermal evolution and cooling

**Difficulty:** Hard. **Time:** about 3 weeks.

## Goal

Model how white dwarfs and neutron stars cool: the energy balance, the heat capacity and conduction, neutrino and photon emission, the envelope that connects the interior to the surface, the effects of crystallization and superfluidity, and the comparison with cooling data (white dwarf luminosity functions, neutron-star surface temperatures and ages). Deliver the `thermal` component.

## Prerequisites

Modules 03, 04 (pairing, transport), 05, 08 to 10.

## Reading

- **HPY, ST, Gle:** neutron star cooling, neutrino emission processes (direct and modified Urca, bremsstrahlung, pair breaking and formation), heat capacity, thermal conductivity, the heat-blanketing envelope, minimal cooling, superfluid effects.
- **HKT, KWW, Iben:** white dwarf cooling, Mestel theory, crystallization, phase separation, neutrino losses.
- **LvdK, Bec:** observed cooling and thermal emission of neutron stars.

## Key equations and concepts (derive)

**Global energy balance.** For an isothermal interior with heat capacity $C_V(T)$ and luminosities in neutrinos and photons,

$$C_V\frac{dT}{dt}=-L_\nu(T)-L_\gamma(T)+H$$

with $H$ any heating (crustal heating of accreting stars, magnetic decay, rotochemical heating). In general relativity the redshifted quantities are used: $T^\infty=Te^{\Phi}$ with the local temperature in the interior, $L_\gamma^\infty=4\pi\sigma R_\infty^2T_{s,\infty}^4$, and the structure equations of thermal balance include $e^{2\Phi}$ factors (Thorne's equations; derive).

**White dwarfs.**
- *Mestel cooling:* an isothermal degenerate core (ions provide the heat capacity $C_V\approx\frac32N_ik_B$ of an ideal gas) under a thin non-degenerate envelope in radiative equilibrium with Kramers opacity gives $L\propto T_c^{7/2}$ and $t_{\rm cool}\propto M^{5/7}\ldots L^{-5/7}$ (derive; the coefficient depends on composition and envelope opacity).
- *Crystallization:* at $\Gamma\approx175$ the ions solidify, releasing latent heat $\sim0.77\,k_BT$ per ion (verify) and a heat capacity that falls toward the Debye law below the Debye temperature. For C/O mixtures the solid and the liquid have different compositions: the oxygen-rich solid rises or sinks and **phase separation** releases gravitational energy that delays cooling by $\sim1$ Gyr for a $0.6\,M_\odot$ star; $^{22}$Ne sedimentation adds more (verify the magnitudes).
- *Neutrinos:* plasmon and photoneutrino emission dominate for $T_{\rm eff}\gtrsim30{,}000$ K, then photons.
- *Convective coupling:* in cool white dwarfs the outer convection zone merges with the degenerate core, changing the cooling rate (the "convective coupling" bump).
- *Luminosity function:* the number per unit luminosity $\Phi(L)\propto\int{\rm SFR}(t)\,\frac{dN}{dM}\frac{dt_{\rm cool}}{dM_{\rm bol}}\,dM$; the cutoff at low luminosity gives the age of the disk or cluster.

**Neutron star neutrino emissivities** (order of magnitude, with $T_9=T/10^9$ K and $\rho_0$ nuclear density; verify with HPY):

| Process | $\epsilon_\nu$ (erg cm$^{-3}$ s$^{-1}$) | Notes |
| --- | --- | --- |
| Direct Urca ($n\to p+e+\bar\nu$) | $\sim10^{27}(\rho/\rho_0)^{1/3}T_9^6$ | Only if $Y_p\gtrsim1/9$; "fast" cooling |
| Modified Urca | $\sim10^{21}(\rho/\rho_0)^{2/3}T_9^8$ | "Standard/slow" cooling |
| Nucleon-nucleon bremsstrahlung | $\sim10^{19}$ to $10^{20}\,T_9^8$ | Slow |
| Pair breaking and formation | $\propto T^7$ near $T_c$, with a strong peak | Superfluid |

**Heat capacity:** $C_V\sim10^{39}T_9$ erg/K for nucleons (non-superfluid), exponentially suppressed under pairing (Module 04).

**Heat blanketing envelope.** The outer layers ($\rho\lesssim10^{10}$ g/cm$^3$) set the relation between the surface temperature $T_s$ and the internal temperature $T_b$ at a boundary density (for example $\rho_b=10^{10}$ g/cm$^3$). A useful fit for an iron envelope (Gudmundsson, Pethick, Epstein; verify) is

$$T_b\approx1.288\times10^8\left(\frac{T_{s6}^4}{g_{14}}\right)^{0.455}\ {\rm K},$$

with $T_{s6}=T_s/10^6$ K and $g_{14}=g/10^{14}$ cm/s$^2$. Light-element envelopes (H, He) are more transparent and give higher $T_s$ at a given $T_b$. Strong magnetic fields make the heat transport anisotropic.

**Cooling eras.** Neutrino era ($t\lesssim10^5$ yr): $L_\nu\gg L_\gamma$; photon era ($t\gtrsim10^5$ yr). The *minimal cooling* paradigm: slow cooling (modified Urca) with superfluid nucleons and no exotic fast processes; stars with direct Urca (large $L$ or hyperons or quark matter) cool much faster. Thermal relaxation of the crust takes $\sim10$ to $100$ yr, imprinting a cooling "knee".

**Accreting stars.** Deep crustal heating (Module 10) sets the quiescent luminosity: $L_q\approx\dot M\,Q_{\rm DCH}/m_u$, with $Q_{\rm DCH}\approx1.5$ to $2$ MeV per baryon.

## Hands-on problems

**1. [E] Mestel's law.** Integrate the radiative envelope equations (Kramers opacity) down to the degeneracy transition for a white dwarf of given $M$ and composition and obtain $L(T_c)$; verify the $L\propto T_c^{7/2}$ scaling, and integrate $C_V\,dT/dt=-L$ analytically to get $t\propto L^{-5/7}$. Compute the cooling time to $L=10^{-3}\,L_\odot$ and compare with a literature figure for $0.6\,M_\odot$ (of order 1 Gyr).

**2. [M] A numerical white dwarf cooling code.** Build the isothermal-core plus envelope model with your Module 05 structure, EOS, radiative and conductive opacities (Modules 04 and 05 of Volume 1), and integrate $dT_c/dt$. Add neutrino losses (plasma and photoneutrino fits) and the heat capacity of the ions with the Debye correction. Compute cooling tracks for $0.5$, $0.6$, $0.8$, $1.0\,M_\odot$ and compare cooling ages to $T_{\rm eff}=5000$ K (several Gyr).

**3. [M] Crystallization.** Add the latent heat and the Debye heat capacity; compute the delay of cooling and compare with published tracks. Then add a simple model of C/O phase separation (a fixed gravitational energy release per unit mass crystallized, from a published phase diagram) and quantify the extra delay, and $^{22}$Ne sedimentation (verify magnitudes).

**4. [M] The luminosity function.** Combine your cooling tracks with the IMF, the initial-final mass relation (Volume 1, Module 12) and a constant star formation rate to compute the white dwarf luminosity function, find the low-luminosity cutoff for a 10 Gyr old disk and compare with the observed Gaia white dwarf luminosity function (or with a cluster; verify).

**5. [M] Neutron star cooling toy model.** Using the isothermal approximation and your EOS, compute $C_V(T)$, $L_\nu$ from modified Urca and bremsstrahlung (and optionally direct Urca once $Y_p$ crosses the threshold in the central region) and $L_\gamma$ from the $T_s$-$T_b$ relation with redshift factors. Integrate the cooling for $10^8$ yr and compare slow and fast cooling tracks.

**6. [M] Superfluid effects.** Include nucleon pairing with gap models from Module 04 and their suppression factors on $C_V$ and on neutrino emissivities (Levenfish-Yakovlev fits; verify) and the PBF emission. Show how the superfluid transition delays the neutrino era, makes the cooling curves more complex and can mimic fast cooling at the critical temperature.

**7. [M] Envelope composition.** Compute $T_s(T_b)$ for iron, hydrogen and helium envelopes by integrating the heat-conduction equation through the envelope with your opacity tables, and compare with the fit above. Show how the surface temperature at fixed internal temperature depends on the envelope composition and on the magnetic field.

**8. [H] The full thermal evolution with GR.** Solve the coupled thermal-structure equations in the relativistic form with a radial temperature profile, a thermal conductivity from Module 04, redshifted neutrino emission and the crust-core structure of Module 10: $\partial(Te^{\Phi})/\partial r$ and $\partial(Le^{2\Phi})/\partial r$ equations. Track the thermal relaxation of the crust and the cooling "knee" at about $10$ to $100$ yr. Compare with data from young cooling neutron stars (the Cassiopeia A neutron star and the XMM/Chandra sources; verify the temperature-age data) and with the 20 or so known isolated neutron stars with measured $T_s$ and age.

**9. [H] Accreting neutron stars.** Add deep crustal heating at the accretion rate of a quasi-persistent transient, evolve through outburst and quiescence, and compute the cooling curve after the end of the accretion. Fit a published source (for example KS 1731-260, MXB 1659-29; verify) with the heat capacity, the crust conductivity (impurity parameter) and the core temperature, and discuss the constraints on the core neutrino emissivity.

**10. [H] A cooling-data inference.** Using your cooling code as a forward model with a small set of parameters (EOS or $M$, envelope composition, pairing gap parameters, direct Urca on/off), perform a Bayesian comparison with a catalogue of neutron-star ages and temperatures; show which stars require fast cooling and which constrain pairing (preview of Module 19).

## Software component

`compactlite/thermal/`: white dwarf cooling (envelope, crystallization, neutrinos, convective coupling), neutron star cooling (neutrino emissivities, heat capacity with superfluidity, envelope $T_s$-$T_b$ relations, GR thermal evolution), luminosity function and accreting-star heating tools.

## Checks

- Mestel scaling $L\propto T_c^{7/2}$ and $t\propto L^{-5/7}$.
- White dwarf cooling ages to $5000$ K of several Gyr, increased by crystallization and phase separation.
- Slow cooling versus fast cooling (direct Urca) tracks differ by orders of magnitude in $L_\nu$.
- $T_s$-$T_b$ fits reproduced within a few percent.
- Redshift factors consistent ($T_\infty=Te^\Phi$).

## Pitfalls

- Using local temperatures where redshifted ones are required.
- Forgetting that neutrino emission in superfluid matter is not simply suppressed.
- Neglecting the heat blanketing envelope: it fixes the observable $T_s$.
- Using cooling ages without considering the uncertainty of the true age (spin-down age, kinematic age).

## Gate questions

1. Why is white dwarf cooling "slow" and what controls the time scale?
2. Why is direct Urca so much more powerful than modified Urca and why does its threshold relate to the symmetry energy?
3. How does pairing change both the heat capacity and the neutrino emission of neutron star matter?

## Deliverable

`compactlite/thermal/`, `notebooks/14_cooling.ipynb`, solutions for problems 1 to 10.
