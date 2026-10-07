# Module 16: Neutron-star atmospheres, emission and ray tracing

**Difficulty:** Hard. **Time:** about 3 weeks.

## Goal

Model the radiation that reaches us from neutron stars: thermal atmospheres (hydrogen, helium, heavier elements, with and without strong magnetic fields), how spectra differ from blackbodies, how general-relativistic light bending shapes pulse profiles, and how masses and radii are inferred (spectral fits, pulse-profile modelling as done by NICER, cyclotron lines). Deliver `atm/ns` and `rays`.

## Prerequisites

Modules 06, 12 and 14, and Volume 1 Modules 04 and 06 (radiative transfer, atmospheres).

## Reading

- **Mes:** magnetized neutron-star atmospheres: opacities in strong fields, polarization modes, vacuum polarization, cyclotron lines.
- **H&M, Mih, RL:** radiative transfer, atmospheres, free-free opacity, Rosseland mean.
- **L&K, MTW, Schu, P&W:** light bending in the Schwarzschild exterior, time delays, pulse profiles.
- **HPY, Gle, ST:** surface layers and thermal emission.
- Observational program articles (NICER, X-ray spectroscopy) are the standard sources for the data; use them for validation.

## Key equations and concepts (derive)

**Redshifted quantities.**

$$1+z=\left(1-\frac{2GM}{Rc^2}\right)^{-1/2},\qquad T_\infty=\frac{T_s}{1+z},\qquad R_\infty=R(1+z),\qquad L_\infty=4\pi\sigma R_\infty^2T_\infty^4$$

so a blackbody fit to X-ray spectra measures $T_\infty$ and $R_\infty$ (the "radiation radius"), which depend on both $M$ and $R$.

**Atmosphere scale height.** With $g\sim10^{14}$ cm/s$^2$, $T\sim10^6$ K and fully ionized hydrogen ($\mu=0.5$), $H=k_BT/\mu m_ug\sim1$ to $2$ cm. The atmosphere is a thin skin ($\sim$ mm to cm), with composition set by accretion, nuclear burning and spallation: hydrogen if recently accreted, helium, or carbon (the Cas A neutron star), and iron if no light elements remain.

**Non-magnetic atmosphere.** The opacity is dominated by free-free absorption and Thomson scattering, $\kappa_\nu^{\rm ff}\propto\nu^{-3}(1-e^{-h\nu/kT})$ for fully ionized gas: lower-energy photons have higher opacity and escape from higher, cooler layers, while high-energy photons escape from deeper, hotter layers. The emergent spectrum is therefore *harder* than a blackbody at $T_{\rm eff}$ (spectral hardening) with a color correction $f_c\sim1.2$ to $1.9$ depending on $T_{\rm eff}$, $g$ and composition (verify), and a blackbody fit yields a temperature that is too high and a radius that is too small relative to the true values.

**Magnetized atmospheres ($B\sim10^{11}$ to $10^{15}$ G).** Radiation propagates in two normal polarization modes: the *ordinary (O)* mode with electric field in the $\mathbf k$-$\mathbf B$ plane and the *extraordinary (X)* mode orthogonal to it. For photon energies far below the electron cyclotron energy $E_{ce}=\hbar eB/m_ec=11.6\,B_{12}$ keV, the X-mode opacity is strongly suppressed, $\kappa_X\sim(\omega/\omega_c)^2\kappa_O$, so the X-mode photons come from deep, hot layers, giving a harder spectrum and a beamed (anisotropic) emission pattern. Features: ion cyclotron lines at $E_{cp}=6.3\,B_{12}$ eV, electron cyclotron lines, atomic features, vacuum polarization (resonance effect for $B\gtrsim10^{13}$ G that changes the polarization mixing), and the possibility of a condensed surface without an atmosphere for very strong fields and low temperatures.

**Light bending (Schwarzschild exterior).** A photon with impact parameter $b$ follows $(du/d\varphi)^2=b^{-2}-u^2(1-2GMu/c^2)$ with $u=1/r$. The angle $\psi$ swept at infinity from the emitting point to the observer and the emission angle $\alpha$ relative to the local normal satisfy exactly

$$\psi=\int_0^{u_R}\frac{b\,du}{\sqrt{1-b^2u^2(1-2GMu/c^2)}}\ \ ({\rm with}\ b=R\sin\alpha/\sqrt{1-2GM/Rc^2}),$$

and the Beloborodov (2002) approximation

$$1-\cos\alpha=(1-\cos\psi)\left(1-\frac{2GM}{Rc^2}\right)$$

reproduces it to a few percent for $R\gtrsim3GM/c^2$ (derive and check). Consequences: more than half the surface is visible (about $76$ percent for $M=1.4\,M_\odot$, $R=12$ km), and the *whole* surface is visible when $R\le4GM/c^2$ (check). Pulse amplitudes are reduced by light bending, and the measured amplitudes limit the compactness.

**Pulse-profile modelling.** For a hot spot of given size and temperature on a rotating star, the observed flux at phase $\phi$ is

$$F(\phi)\propto\left(1-\frac{2GM}{Rc^2}\right)\int I(\alpha;E')\,\delta^{k}\,\cos\alpha\,\frac{d\cos\alpha}{d\cos\psi}\,d\Omega$$

with a Doppler factor $\delta$ from the rotation (relevant at $f_{\rm spin}\gtrsim200$ Hz), time delays across the surface and the atmosphere beaming function. Fitting the energy-resolved profiles from NICER constrains $(M,R)$ with uncertainties of $\sim10$ percent (the published results for PSR J0030+0451 and J0740+6620 give $R\approx12$ to $13$ km; verify the latest numbers).

**Other radius methods.** Thermonuclear burst spectra (photospheric radius expansion bursts; Module 17), quiescent low-mass X-ray binaries in globular clusters (hydrogen atmosphere fits with known distance), and the cooling tail of bursts. Each has systematic uncertainties (atmosphere composition, distance, hot-spot geometry).

## Hands-on problems

**1. [E] Redshift, radiation radius, visible fraction.** For $M=1.4\,M_\odot$ and $R=10,12,14$ km compute $1+z$, $R_\infty$, the visible fraction of the surface from the Beloborodov formula (about $76$ percent at $12$ km), and the critical $R$ for full visibility ($4GM/c^2\approx8.3$ km). Compare the Beloborodov deflection with the exact integral for several $\alpha$.

**2. [E] Cyclotron energies.** Compute $E_{ce}$ and $E_{cp}$ for $B=10^{11},10^{12},10^{13},10^{14}$ G including the gravitational redshift factor $1/(1+z)$, and compare with the energies of observed cyclotron features in accreting X-ray pulsars (10 to 100 keV; verify).

**3. [M] Exact light bending.** Integrate the null geodesic in the Schwarzschild exterior numerically, build the table $\psi(\alpha;R,M)$, the deflection function, the time delay $\Delta t(\alpha)$ and the solid-angle factor $d\cos\alpha/d\cos\psi$. Compare with Beloborodov and quantify the error as a function of compactness.

**4. [M] A hot spot pulse profile.** Compute the pulse profile of a point-like or finite-size circular hot spot on a star with $M=1.4\,M_\odot$, $R=12$ km, inclination $i$, colatitude $\theta$ of the spot, and spin $200$ Hz (include light bending and the Doppler boost and time delays in the "oblate Schwarzschild plus Doppler" approximation). Plot the profiles for several $(i,\theta)$ and show the effect of compactness on the pulsed fraction. Add a second antipodal spot.

**5. [M] A non-magnetic hydrogen atmosphere.** Build a plane-parallel LTE atmosphere in radiative and hydrostatic equilibrium with free-free and Thomson opacities for $T_{\rm eff}=10^6$ K, $\log g=14.3$ using the Feautrier solver and Lucy-Unsold temperature correction. Compute the emergent spectrum, compare with a blackbody, extract the hardening factor $f_c=T_c/T_{\rm eff}$, and show how a blackbody fit biases $R_\infty$ low.

**6. [M] Atmosphere composition.** Repeat problem 5 for a helium and an iron (or carbon, for the Cas A case) atmosphere with bound-free opacities from a published fit or from simple hydrogenic Kramers cross-sections for each ion stage with Saha ionization. Compare the spectra and the color corrections.

**7. [M] Two normal modes.** Implement the magnetized atmosphere in the two-mode approximation: O and X opacities from the cold-plasma dielectric tensor for $E\ll E_{ce}$ (derive the free-free and scattering opacities for each mode), and solve the transfer for each mode in the Eddington approximation with the mode-coupling by vacuum polarization neglected. Compute the spectrum, the beaming (angle-dependent intensity) and the polarization degree for $B=10^{12}$ and $10^{14}$ G.

**8. [M] Radius inference with a mock spectrum.** Generate a mock X-ray spectrum from your hydrogen atmosphere model (with Poisson noise) for a source at a known distance, then fit it with (a) a blackbody and (b) the atmosphere model grid, retrieving $(T,R_\infty)$ and from $R_\infty$ and the mass prior the radius $R$. Show the bias of the blackbody fit and the posterior of $R$ in each case.

**9. [H] A pulse-profile inference toy.** Create mock energy-resolved NICER-like pulse profiles for a given $(M,R)$ and spot parameters with Poisson noise. Write a likelihood and sample the posterior of $(M,R,\theta,i,\ldots)$ with nested sampling or MCMC. Study the degeneracies (mass-radius, inclination-colatitude), the effect of unknown spot geometry and the precision available as a function of counts. Connect to Module 19.

**10. [H] Beyond Schwarzschild.** Add the oblate shape correction and frame-dragging for a rapidly rotating star using the Hartle-Thorne metric (Module 12) for the ray tracing, estimate their effect on the profile for $f_{\rm spin}=200$ to $600$ Hz, and discuss when the Schwarzschild plus Doppler approximation breaks down.

## Software component

- `compactlite/atm/ns.py`: non-magnetic and two-mode magnetized LTE atmosphere solvers, color corrections, spectral grids.
- `compactlite/rays/`: exact and approximate light bending, hot-spot pulse profiles, Doppler and time-delay effects, mock data generators.

## Checks

- $1+z\approx1.24$ and $R_\infty\approx14.9$ km for $1.4\,M_\odot$, 12 km.
- Visible fraction of about $76$ percent; full surface visible for $R\le4GM/c^2$.
- Beloborodov formula within a few percent of the exact integral at moderate compactness.
- Hydrogen atmosphere harder than a blackbody; $f_c$ in the quoted range.
- E-folding cyclotron energies $E_{ce}=11.6B_{12}$ keV.

## Pitfalls

- Mixing local and redshifted temperatures and radii.
- Applying the Beloborodov formula at $R<3GM/c^2$.
- Ignoring the magnetic-field-dependent beaming for high-field atmospheres.
- Using a single hot-spot model when the data prefer a more complex geometry (a significant systematic for inference).

## Gate questions

1. Why does a blackbody fit to a neutron star spectrum underestimate the radius?
2. Why can more than half of the star be seen at once?
3. Why does the suppressed X-mode opacity in strong fields produce a harder and beamed spectrum?

## Deliverable

`compactlite/atm/ns.py`, `compactlite/rays/`, `notebooks/16_ns_atmospheres_rays.ipynb`, solutions for problems 1 to 10.
