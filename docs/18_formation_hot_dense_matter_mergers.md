# Module 18: Formation, hot dense matter and mergers

**Difficulty:** Hard. **Time:** about 3 weeks.

## Goal

Understand the finite-temperature, neutrino-trapped regime in which compact stars are born and merge: the thermodynamics of hot dense matter (nuclear statistical equilibrium at sub-nuclear densities, thermal contributions above), proto-neutron star evolution and neutrino diffusion, the birth properties of neutron stars (kicks, spins, fields), the formation of white dwarfs (summary), and neutron-star mergers (remnants, kilonovae). Build thermal EOS tools and a proto-neutron star toy model.

## Prerequisites

Modules 02, 04, 09, 10 and 11, and Volume 1 Modules 13 to 15.

## Reading

- **ST, Gle, HPY, Wb:** the EOS at finite temperature and with trapped neutrinos, the proto-neutron star, neutrino opacities and diffusion.
- **Rez, Bau, And:** relativistic hydrodynamics, neutron star mergers, remnants and gravitational waves.
- **KWW, Iben, Arn, ST:** core collapse and white dwarf formation (as a bridge to Volume 1).
- Review articles on supernova theory and on the merger of neutron stars (Janka, and the GW170817 papers) are the standard sources.

## Key concepts and equations (derive)

**Formation.** White dwarfs form from stars below $\sim8$ to $10\,M_\odot$ (Volume 1, Module 12), as He, C/O or O/Ne/Mg cores. Neutron stars form in core collapse (Volume 1, Modules 13, 15) after the collapse of an iron or ONeMg core: bounce at $\rho\sim2.7\times10^{14}$ g/cm$^3$, a stalled shock revived by neutrino heating, and a hot, lepton-rich **proto-neutron star** (PNS) with $T\sim20$ to $50$ MeV, entropy $s\sim1$ to $2\,k_B$ per baryon, and a lepton fraction $Y_L\sim0.35$ to $0.4$ (including trapped $\nu_e$). Typical total energy release $\sim3\times10^{53}$ erg, $99$ percent in neutrinos over $\sim10$ to $20$ s (SN1987A). Birth kicks of a few hundred km/s and a spread of initial spins and fields.

**Hot dense matter.** The thermodynamic state of matter is a function of $(n_B,T,Y_e)$ or $(n_B,s,Y_L)$.
- *Sub-nuclear densities* ($n_B\lesssim0.1\,n_0$): nuclear statistical equilibrium of an ensemble of nuclei plus nucleons, electrons, positrons, photons: a Saha-like system with
$$Y_i=\frac{G_i(T)}{\ldots}\left(\frac{\rho N_A}{2}\right)^{A_i-1}A_i^{3/2}\left(\frac{2\pi\hbar^2}{m_ukT}\right)^{3(A_i-1)/2}e^{B_i/kT}Y_p^{Z_i}Y_n^{N_i}$$
(derive from chemical equilibrium and Module 02). Corrections: Coulomb screening, excluded volume, and temperature-dependent partition functions. Standard tables: Lattimer-Swesty, Shen, Hempel (SFHo, DD2), and others.
- *Above nuclear density:* thermal contribution as an additive or multiplicative correction to the cold EOS. A common approximation is $P=P_{\rm cold}+(\Gamma_{\rm th}-1)\epsilon_{\rm th}$ with $\Gamma_{\rm th}\approx1.5$ to $2$ ($\Gamma_{\rm th}=5/3$ for a nonrelativistic ideal gas; for a degenerate Fermi liquid $\epsilon_{\rm th}\propto m^*T^2$ and $\Gamma_{\rm th}$ depends on the effective mass; verify).
- *Neutrino-trapped matter:* the neutrino chemical potential $\mu_\nu=\mu_e+\mu_p-\mu_n$ and the lepton fraction $Y_L=Y_e+Y_\nu$ fixed; trapped neutrinos increase $Y_p$ and stiffen the EOS relative to cold catalyzed matter at the same density.
- *Hot PNS:* the maximum mass of hot, lepton-rich matter can be larger than the cold one by $\sim0.1$ to $0.3\,M_\odot$ (thermal and lepton pressure), so a PNS can collapse to a black hole after cooling and deleptonization if close to the cold limit ("delayed collapse").

**Neutrino transport.** Neutrinos are trapped when the mean free path $\lambda_\nu=1/(n\sigma)$ is shorter than the PNS radius: $\sigma\propto G_F^2E_\nu^2$ for neutrino-nucleon scattering, coherent scattering on nuclei $\propto A^2$. The diffusion time is $t_{\rm diff}\sim R^2/\lambda_\nu c\sim10$ s. Neutrino luminosity $L_\nu\sim3\times10^{51}$ erg/s per flavor at early times.

**White dwarf formation and mergers.** Double white dwarf mergers produce massive white dwarfs, R CrB stars or Type Ia supernovae (accretion-induced collapse may produce neutron stars; see Volume 1).

**Neutron-star mergers.** For $m_1+m_2\approx2.7\,M_\odot$ the outcomes are: prompt collapse to a black hole (for high mass or soft EOS), a hypermassive neutron star (supported by differential rotation and thermal pressure for $\sim10$ to $100$ ms), a supramassive or a stable neutron star remnant. Ejecta of $\sim10^{-3}$ to $10^{-2}\,M_\odot$ with $v\sim0.1$ to $0.3\,c$ produce the **kilonova** (r-process heating, $L\sim10^{41}$ to $10^{42}$ erg/s, as observed after GW170817) and the dynamical + wind components; the post-merger GW frequency $f_2\sim2$ to $4$ kHz correlates with the radius of the progenitors. A threshold mass for prompt collapse $M_{\rm thr}\approx k\,M_{\rm TOV}$ with $k\sim1.3$ to $1.6$ depending on the compactness (verify).

## Hands-on problems

**1. [E] Neutrino energetics.** Compute the gravitational binding energy of a $1.4\,M_\odot$, 12 km neutron star ($\approx3\times10^{53}$ erg), the neutrino number (about $10^{58}$ neutrinos at $\sim10$ MeV), the expected number of events in a detector like Kamiokande for a source at 50 kpc (about 10 to 20) and the neutrino luminosity over 10 s.

**2. [E] Thermal EOS of free gases.** For a hot gas of neutrons, protons, electrons, positrons, photons and optionally neutrinos at fixed $Y_e$ and $T$ compute the thermodynamic functions with your Module 02 tools; plot the thermal pressure fraction at nuclear density for $T=10$, $30$ MeV.

**3. [M] NSE composition.** Implement a small NSE solver with nuclei ($^2$H, $^3$H, $^3$He, $^4$He, $^{56}$Fe, and a representative heavy nucleus such as $^{80}$Zn or $^{100}$Zr) from a mass table, in the ideal-gas approximation, for $\rho=10^9$ to $10^{13}$ g/cm$^3$, $T=0.5$ to $10$ MeV and $Y_e=0.3$ to $0.5$. Show the transition from nuclei to free nucleons with temperature and the presence of the $\alpha$ particles. Add the excluded-volume correction and the Coulomb lattice correction.

**4. [M] The $\Gamma_{\rm th}$ approximation.** Take a cold RMF EOS (Module 9) and the finite-$T$ RMF result at fixed $Y_e$ or $Y_L$ and fit an effective $\Gamma_{\rm th}(n)$; compare it with the constant $\Gamma_{\rm th}=1.5$ or $5/3$ and with a Fermi-liquid estimate. Compute the effect on $M_{\rm max}$ for $s=1$ and $2\,k_B$ per baryon.

**5. [M] Neutrino-trapped beta equilibrium.** Solve the beta equilibrium with fixed lepton fraction $Y_L=0.4$ (including the neutrino chemical potential) and with fixed entropy for the RMF EOS, and compare with the cold catalyzed state: proton fraction, pressure, sound speed, maximum mass.

**6. [M] A PNS toy model.** Build a PNS with a given entropy profile and $Y_L$ using the TOV equations at finite $T$ (Module 6 and the hot EOS) and evolve it with the energy and lepton-number conservation equations in the diffusion approximation with an opacity prescription (use the scaling of the neutrino mean free path with $E_\nu^2$ and the density and temperature dependence). Get the cooling and deleptonization timescales of $\sim10$ to $20$ s, the neutrino luminosity versus time and the radius contraction from $\sim30$ to $12$ km. Compare with the SN1987A neutrino signal qualitatively.

**7. [M] The Kelvin-Helmholtz timescale.** Show that the neutrino luminosity and the binding energy give the KH timescale $\sim10$ s, and that the diffusion time implies a neutrino luminosity of $L_\nu\sim4\pi R^2\sigma T^4\times$ (neutrino sphere correction) (derive an order of magnitude).

**8. [M] Merger outcome estimator.** For a family of EOS (piecewise polytropes and RMF), compute $M_{\rm TOV}$, the radius of a $1.6\,M_\odot$ star and the threshold mass for prompt collapse with the simple relation of the literature (verify), and classify the outcome of the $1.35+1.35\,M_\odot$ merger and of the $1.25+1.55$ merger. Plot the post-merger frequency estimate $f_2$ against $R_{1.6}$ with a fit from the literature.

**9. [H] A kilonova light curve.** Implement a semi-analytic kilonova model (Metzger-style one-zone): ejecta mass, velocity and opacity, radioactive heating from r-process with a power-law $\dot\epsilon\propto t^{-1.3}$ and thermalization efficiency, diffusion time and light curve in bolometric and filter bands. Fit the AT2017gfo light curve (peak at $\sim1$ day, blue and red components; verify) and find the required ejecta masses and opacities (blue: $\kappa\sim0.5$ cm$^2$/g; red: $\kappa\sim10$ cm$^2$/g).

**10. [H] A hot EOS with a phase transition.** Use your hybrid EOS of Module 11 at finite temperature and trapped neutrinos and study the temperature dependence of the transition pressure and of the third-family window; show how the transition can appear in a merger remnant (the density and temperature track) and the possible signal in the post-merger GW frequency.

## Software component

`compactlite/eos/thermal.py`: ideal hot gases, NSE solver, finite-$T$ and trapped-neutrino extensions of the RMF EOS, $\Gamma_{\rm th}$ prescription, a general interface for tabulated $(n_B,T,Y_e)$ EOS. Also a simple PNS evolution tool and a kilonova model in `tools/`.

## Checks

- Binding energy $\approx3\times10^{53}$ erg and $\sim10^{58}$ neutrinos.
- NSE composition: nuclei at low $T$ and high $Y_e$, free nucleons plus alphas at high $T$.
- Trapped-neutrino matter has higher $Y_p$ than cold catalyzed matter.
- PNS KH timescale about 10 s.
- Kilonova peak at $\sim L=10^{41}$ to $10^{42}$ erg/s on the timescale of a day.

## Pitfalls

- Using the cold-EOS $c_s$ for hot matter.
- Ignoring neutrino pressure and the lepton fraction in the PNS.
- Treating NSE as valid at $T\lesssim0.4$ MeV where it falls out of equilibrium.
- Taking the threshold mass relations beyond their fitted ranges.

## Gate questions

1. Why is the PNS so different from the cold neutron star it becomes?
2. Why does a hot, lepton-rich PNS support a higher mass than the cold remnant?
3. What determines whether a merger remnant collapses promptly?

## Deliverable

`compactlite/eos/thermal.py`, `notebooks/18_hot_dense_matter.ipynb`, solutions for problems 1 to 10.
