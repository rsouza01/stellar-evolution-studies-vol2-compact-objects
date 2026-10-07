# Module 15: White dwarf atmospheres and spectra

**Difficulty:** Hard. **Time:** about 3 weeks.

## Goal

Understand how white dwarf atmospheres form and how spectra and photometry give $T_{\rm eff}$, $\log g$, mass, composition and magnetic fields: spectral types, pressure broadening, convection, gravitational settling and spectral evolution, metal pollution, magnetic white dwarfs and the spectroscopic and photometric techniques. Build a small atmosphere and spectrum code that links to the cooling models.

## Prerequisites

Module 05 and Volume 1 Modules 04 (radiative transfer) and 06 (stellar atmospheres).

## Reading

- **H&M, Mih, Gray, RL:** model atmospheres (LTE), pressure ionization and occupation probabilities, line broadening (Stark, van der Waals), the transfer problem, spectral synthesis.
- **HKT, ST:** white dwarf atmospheres, composition, spectral classes and their evolution.
- Review and catalogue articles (Koester, Bergeron, Tremblay) are the standard sources for model grids; use them to validate.

## Key concepts and equations

**Spectral classes.** DA (hydrogen lines only, $\sim80$ percent), DB (neutral helium), DO (ionized helium, hot), DC (featureless), DQ (carbon lines or molecular bands, from dredge-up), DZ (metal lines, from external accretion), PG1159 (hot, C/O dominated), and the magnetic ones (DAH, DBH). Spectral evolution: stars change type as they cool through convective dilution and mixing and as gravitational settling reshapes the atmosphere (He-rich atmospheres turning into H-rich or vice versa).

**Gravity and scale height.** With $\log g=8$, $T=10^4$ K and $\mu\approx1$, $H=k_BT/\mu m_ug\approx8\times10^3$ cm, so the atmosphere is a layer only tens of meters thick: pure hydrogen or helium by gravitational settling (the heavier element sinks). Hydrostatic equilibrium and optical depth give

$$\frac{dP}{d\tau}=\frac{g}{\kappa},\qquad P_{\rm phot}\approx\frac{2g}{3\kappa}$$

**Settling.** The gravitational settling timescale of a trace metal at the base of the convection zone is seconds to days for hot DA (negligible convection zone) and up to $10^5$ to $10^6$ yr for cool DB (deep convection zone), so metals seen in 25 to 50 percent of white dwarfs imply recent or ongoing accretion of planetary debris (the rate follows from the abundance and the settling time; derive).

**Pressure broadening.** The Balmer lines of DA stars are broadened by the linear Stark effect (microfields of charged particles) with a profile close to Holtsmark; the line wings give $\log g$ (wing strength) and $T_{\rm eff}$ (line ratios). The non-ideal effects are described by the Hummer-Mihalas occupation probability formalism (the high Balmer levels are dissolved by the plasma). For He lines the quadratic Stark and van der Waals broadening matter.

**Collision-induced absorption.** In cool ($T_{\rm eff}\lesssim5000$ K) hydrogen-rich atmospheres, H$_2$-H$_2$ and H$_2$-He CIA suppresses the infrared flux, which makes some cool white dwarfs bluer than their temperatures imply ("IR-faint").

**Convection.** Mixing-length theory with $\alpha_{\rm MLT}\sim0.6$ to $1.0$ (ML2) governs the outer convection zone; its depth determines the dilution of H in He, the DA/DB ratio and the cooling behavior (Module 14).

**Magnetic white dwarfs.** About $10$ percent show fields $10^3$ to $10^9$ G. The Zeeman splitting of a line of wavelength $\lambda$ in the linear regime is $\Delta\lambda=4.67\times10^{-13}\,\lambda^2B$ ($\lambda$ in \AA, $B$ in G; for H$\alpha$ at 1 MG this gives $\approx20$ \AA), turning into the quadratic Zeeman effect and complex patterns above $\sim10^7$ G.

**Mass determination.** (i) *Spectroscopic:* fit line profiles to get $T_{\rm eff}$ and $\log g$, then use a mass-radius relation (Module 05) to get $M$; (ii) *photometric:* fit the spectral energy distribution with the Gaia parallax to get $R^2$ (and $T_{\rm eff}$), then $M$ from $R$ and the mass-radius relation; (iii) *gravitational redshift* in binaries or clusters. Differences between (i) and (ii) point to systematic errors in broadening theory, 3D convection or atmospheric composition.

## Hands-on problems

**1. [E] Atmosphere structure.** For three white dwarfs ($T_{\rm eff}=6000,12000,30000$ K, $\log g=8$) compute $H$, the photospheric pressure with a gray opacity and the column density down to $\tau=1$. Show how thin the layer is and estimate the mass of the photospheric layer.

**2. [E] Zeeman splitting.** Compute the linear Zeeman splitting for H$\alpha$, H$\beta$ and a few metal lines for fields $10^5$ to $10^8$ G and find the field at which the splitting equals the Stark width (and at which the lines become unresolvable).

**3. [M] Settling timescales.** Estimate the diffusion coefficients for a trace metal (Ca, Mg, Fe) in a hydrogen or helium atmosphere using the Burgers or Paquette approximations (use a published formula; verify), compute the settling time at the base of the convection zone as a function of $T_{\rm eff}$ for DA and DB stars, and the accretion rate needed to explain a given calcium abundance in steady state.

**4. [M] A gray hydrogen atmosphere with ionization.** Solve the hydrostatic structure with an Eddington or Hopf $T(\tau)$, the Saha equation for hydrogen and the opacities (H bound-free, free-free, H$^-$ for cool stars, electron scattering), compute the Rosseland mean opacity and check where convection starts (using Module 05's MLT).

**5. [M] Non-gray LTE hydrogen atmosphere.** Using the Feautrier solver of Volume 1, Module 04, and a temperature correction scheme, compute a non-gray LTE atmosphere for a DA star ($T_{\rm eff}=12000$ K, $\log g=8$) including hydrogen bound-bound lines (Balmer series with Stark profiles and occupation probabilities, or simplified Lorentzian wings) and continuum opacities. Compute the emergent spectrum and compare with the published model spectrum of a standard grid (verify).

**6. [M] Line profile fitting.** With a small grid of synthetic spectra over $(T_{\rm eff},\log g)$ you computed (or a published grid), fit the Balmer lines of a (real or mock) DA spectrum by $\chi^2$ minimization, obtain $T_{\rm eff}$ and $\log g$ with uncertainties and the mass from your $M$-$R$ relation. Study the correlation between $T_{\rm eff}$ and $\log g$ and the systematic effect of the convection treatment.

**7. [M] The photometric technique.** Compute synthetic Gaia and 2MASS magnitudes from your spectra (Volume 1, Module 06, problem 10) and fit a (real or mock) sample with known parallaxes for $(T_{\rm eff},\log g)$ using the parallax constraint; compare the masses with the spectroscopic results and with the Module 05 predictions.

**8. [M] The mass-radius test with Gaia.** From a Gaia-based sample of white dwarfs with spectroscopic parameters, plot the photometric radius against the spectroscopic mass and compare with the theoretical mass-radius relation including finite temperature, composition and envelope effects. Quantify the scatter and the trend with mass.

**9. [H] Metal pollution.** Build a model for the evolution of the surface abundance of a polluted DB white dwarf: steady-state accretion and settling with a convection zone of time-dependent mass (from your cooling tracks), including the diffusion coefficients of problem 3. Compute the observed Ca abundance for a given accretion rate and compare with published values for a few stars (verify), and the inferred planetary-debris composition.

**10. [H] A magnetic atmosphere.** Include the Zeeman splitting in the radiative transfer for hydrogen in fields of $10^5$ to $10^8$ G using a simple polarized transfer (two normal modes with their own line opacities, a dipole field geometry integrated over the disc). Compute the synthetic spectrum and circular polarization, and compare with the pattern of a known magnetic white dwarf.

## Software component

`compactlite/atm/wd.py`: gray and non-gray LTE atmospheres, line profiles (Stark), settling and pollution tools, spectral-fitting utilities, synthetic photometry hooks, and a Zeeman module.

## Checks

- $H\sim10^4$ cm for a typical atmosphere.
- Zeeman splitting formula reproducing 20 \AA\ for H$\alpha$ at 1 MG.
- Photospheric opacities and convection onset consistent with published atmospheres.
- Spectroscopic and photometric masses agree within published scatter for ordinary DA white dwarfs.
- Settling times consistent with the literature values (seconds to $10^6$ yr).

## Pitfalls

- Using fits of line profiles without the occupation-probability formalism for high Balmer lines.
- Applying 1D mixing-length models to cool DA stars where 3D corrections are significant (known 3D corrections of order $10$ percent in $\log g$ near the DA convective boundary; verify).
- Interpreting photometric radii without accounting for composition and thin-layer corrections.
- Forgetting the dependence of the Balmer-line fits on the assumed Stark broadening theory.

## Gate questions

1. Why do white dwarf atmospheres have pure H or He compositions and what can make them polluted?
2. Why does the sensitivity of Balmer lines to $\log g$ relate to the plasma microfield?
3. Why can the spectroscopic and photometric methods give different white dwarf masses?

## Deliverable

`compactlite/atm/wd.py`, `notebooks/15_wd_atmospheres.ipynb`, solutions for problems 1 to 10.
