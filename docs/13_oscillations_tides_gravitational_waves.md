# Module 13: Oscillations, tides and gravitational waves

**Difficulty:** Hard. **Time:** about 3 weeks.

## Goal

Compute the oscillation modes and tidal response of compact stars: radial stability and non-radial modes of neutron stars (f, p, g, r modes and instabilities), the relativistic tidal deformability that GW170817 measured, white dwarf pulsations (ZZ Ceti and relatives) and gravitational waves from deformed or oscillating stars and from inspiralling binaries with tidal corrections.

## Prerequisites

Modules 05, 06 and 07. Linear perturbation theory.

## Reading

- **And, Mag, P&W:** gravitational waves, quadrupole formula, tidal effects, inspiral waveforms, tidal Love numbers in general relativity.
- **FS, Unno, ACK, And:** stellar oscillations in general relativity, mode classification, the CFS instability, r modes.
- **HKT, ACK:** white dwarf pulsations: g modes, mode trapping, asteroseismology of white dwarfs.
- **Gle, HPY:** oscillation modes and the crust.

## Key equations and concepts (derive)

**Radial stability (Chandrasekhar 1964).** With the Lagrangian displacement $\xi=\zeta(r)e^{i\omega t}$ the radial pulsation equation is a Sturm-Liouville problem for $\omega^2$:

$$\frac{d}{dr}\left(\Pi\frac{d\zeta}{dr}\right)+\left(Q+\omega^2W\right)\zeta=0$$

with $\Pi$ proportional to $\Gamma_1P\,e^{\ldots}r^{-2}$, $W$ to $(\epsilon+P)e^{\ldots}r^{-2}$ and $Q$ containing $dP/dr$ and relativistic terms (see ST, Gle, FS for the explicit coefficients, and derive them from the linearized Einstein equations). Stability requires $\omega_0^2>0$; the transition is at the maximum mass of the sequence.

**Non-radial modes.** Spheroidal modes $(\ell,m,n)$: *fundamental (f)* mode with no radial nodes at $f\sim1.5$ to $3$ kHz (depending on compactness; empirically $f_f\propto\sqrt{\bar\rho}$ approximately); *pressure (p)* modes at $>4$ kHz; *gravity (g)* modes from composition or thermal gradients (hundreds of Hz, in the core and crust); *interface and shear (s)* modes of the crust (tens of Hz to kHz, relevant for magnetar QPOs); *inertial (r)* modes in rotating stars with frequency in the rotating frame $\omega_r=2m\Omega/\ell(\ell+1)$ and in the inertial frame $\omega_i=m\Omega\left(1-\frac{2}{\ell(\ell+1)}\right)$; for $\ell=m=2$ the gravitational-wave frequency is $\frac43f_{\rm spin}$. In the Cowling approximation (no metric perturbation) the equations reduce to two first-order ODEs; the full problem includes the metric perturbations.

**CFS instability.** A mode that is retrograde in the rotating frame but prograde in the inertial frame is driven unstable by gravitational radiation reaction (Chandrasekhar-Friedman-Schutz), competing with viscous damping (shear and bulk), producing an instability window in the $(T,\Omega)$ plane. The r modes are unstable at all rotation rates in the absence of dissipation.

**Tidal deformability.** In a binary, the star acquires a mass quadrupole $Q_{ij}=-\lambda\mathcal E_{ij}$ in response to the tidal field $\mathcal E_{ij}$ of the companion, with

$$\Lambda=\frac{\lambda}{M^5}\ (G=c=1)=\frac23k_2\left(\frac{Rc^2}{GM}\right)^5=\frac23\frac{k_2}{C^5}$$

For $\ell=2$, the Love number $k_2$ is obtained by solving the perturbation equation for $y(r)=rH'(r)/H(r)$ (Hinderer 2008; Damour-Nagar; Postnikov et al.), in $G=c=1$:

$$r\frac{dy}{dr}+y^2+yF(r)+r^2Q(r)=0,\quad F=\frac{1-4\pi r^2(\epsilon-P)}{1-2m/r},$$

$$Q=\frac{4\pi\left[5\epsilon+9P+\dfrac{\epsilon+P}{dP/d\epsilon}-\dfrac{6}{4\pi r^2}\right]}{1-2m/r}-4\left[\frac{m+4\pi r^3P}{r^2(1-2m/r)}\right]^2$$

with $y(0)=2$ and $y_R=y(R)$ (with the correction $y_R\to y_R-4\pi R^3\epsilon_s/M$ for a density discontinuity $\epsilon_s$ at the surface, essential for self-bound quark stars). Then

$$k_2=\frac{8C^5}{5}(1-2C)^2\left[2+2C(y_R-1)-y_R\right]\Big/\Big\{2C\left[6-3y_R+3C(5y_R-8)\right]+4C^3\left[13-11y_R+C(3y_R-2)+2C^2(1+y_R)\right]+3(1-2C)^2\left[2-y_R+2C(y_R-1)\right]\ln(1-2C)\Big\}$$

**Check this expression against Hinderer (2008) or Binnington-Poisson before using it.** Newtonian limits for tests: $k_2=3/4$ for a homogeneous (incompressible) star and $k_2=(15-\pi^2)/2\pi^2\approx0.26$ for an $n=1$ polytrope. For a $1.4\,M_\odot$ star $\Lambda_{1.4}\sim100$ to $1000$ depending on the EOS, and $\Lambda\propto R^5$ at fixed mass. The combination measured by gravitational waves is

$$\tilde\Lambda=\frac{16}{13}\frac{(m_1+12m_2)m_1^4\Lambda_1+(m_2+12m_1)m_2^4\Lambda_2}{(m_1+m_2)^5}$$

GW170817 gave $\tilde\Lambda\lesssim800$ (low-spin prior, 90 percent; verify the latest posterior) and, in conjunction with other constraints, disfavored the stiffest EOS.

**Inspiral and gravitational waves.** Leading-order frequency evolution $\dot f=\frac{96}{5}\pi^{8/3}\left(\frac{G\mathcal M_c}{c^3}\right)^{5/3}f^{11/3}$ with the chirp mass $\mathcal M_c=(m_1m_2)^{3/5}/(m_1+m_2)^{1/5}$; the tidal correction to the phase enters at 5PN order, $\Psi_{\rm tidal}=-\frac{117}{8\eta}\ldots\tilde\Lambda x^{5/2}$ (see Flanagan-Hinderer and Mag; derive the leading coefficient). Merger: formation of a hypermassive neutron star or prompt collapse; post-merger frequencies of $2$ to $4$ kHz correlate with the radius.

**White dwarf pulsations.** ZZ Ceti (DAV; $T_{\rm eff}\approx10{,}500$ to $12{,}500$ K), DBV ($22{,}000$ to $28{,}000$ K), GW Vir (PG1159, hot) stars show $g$-mode periods of $100$ to $1500$ s. In the asymptotic regime the periods are equally spaced, $\Delta\Pi_\ell=\Pi_0/\sqrt{\ell(\ell+1)}$, with deviations from trapping by chemical interfaces (the H/He and He/C transition zones), which encode the envelope masses; the rotation splitting gives the rotation period of the core; the rate of change of the period $\dot P$ gives the cooling rate.

## Hands-on problems

**1. [E] Newtonian tests.** Solve the Newtonian tidal Love number equation (the Clairaut-like equation for $k_2$) for the incompressible star and for an $n=1$ polytrope; verify $3/4$ and $0.26$.

**2. [M] Radial stability.** Implement the radial pulsation equation of Chandrasekhar (as a boundary-value problem with shooting or finite differences) on top of the TOV solution and compute $\omega_0^2$ along a mass sequence. Verify that $\omega_0^2$ changes sign at the maximum mass, and compute the first few radial modes for a $1.4\,M_\odot$ star (frequencies of the order of $\sim$ kHz; verify).

**3. [M] The tidal deformability.** Implement the $y$-equation, with the surface correction, for your EOS families, and compute $k_2$ and $\Lambda$ as functions of mass. Verify the Newtonian limits at $C\to0$ and that $\Lambda\propto R^5$. Compute $\Lambda_{1.4}$ for the piecewise polytropes, RMF and Skyrme EOS and plot it against $R_{1.4}$.

**4. [M] $\tilde\Lambda$ and GW170817.** Compute $\tilde\Lambda$ for a $1.4+1.4$ system and for unequal masses with the same chirp mass ($\mathcal M_c=1.186\,M_\odot$), and compare with the published constraint ($\tilde\Lambda\lesssim800$; verify). Which of your EOS are consistent?

**5. [M] f-mode in the Cowling approximation.** Solve the non-radial oscillation equations in the Cowling approximation (relativistic) for $\ell=2$ and compute the f-mode frequency as a function of mass and EOS. Plot $f_f$ against $\sqrt{M/R^3}$ and find the empirical near-universal relation; compare with the fully relativistic frequencies in the literature (the Cowling frequencies are 10 to 20 percent higher; verify).

**6. [M] r modes.** Compute the r-mode frequencies in the rotating frame and in the inertial frame, and the GW frequency for $\ell=m=2$; use a simple viscous damping model (shear viscosity from electron-electron scattering, bulk viscosity from Urca) to draw an instability window and compare it with the spin frequencies of accreting millisecond pulsars.

**7. [M] White dwarf g modes.** Build the Brunt-Vaisala frequency profile of a DAV model (use your Module 05 structure with a thin H envelope and a He layer, Module 14 for the thermal structure) and compute $\ell=1$, 2 modes with periods of 100 to 1500 s. Show the asymptotic spacing, the trapping features caused by the chemical transition zones and how the pulsation periods change with the H layer mass.

**8. [M] Gravitational waves from a deformed star.** Reproduce $h_0\approx10^{-26}$ for the fiducial values of Module 12, and compute the maximum ellipticity supported by a crust with the breaking strain of Module 10; compare with the current continuous-wave upper limits.

**9. [H] Post-Newtonian inspiral with tides.** Implement the TaylorF2 waveform with the leading tidal phase correction and compute, for a $1.4+1.4\,M_\odot$ system at 100 Mpc, the dephasing between $\tilde\Lambda=0$ and $\tilde\Lambda=500$ over the band $20$ to $2000$ Hz. Estimate the measurability with a Fisher matrix for a given detector sensitivity curve.

**10. [H] Full relativistic non-radial modes.** Solve the full (non-Cowling) relativistic oscillation equations for the f and p modes and for the g modes of a star with a composition gradient. Compare the frequencies with the Cowling results; compute the damping times from gravitational radiation using the complex-frequency approach (a boundary condition of outgoing waves). Add the crust and compute the shear modes.

## Software component

- `compactlite/gr/tides.py`: $y$-equation solver, $k_2$, $\Lambda$, $\tilde\Lambda$ and the surface-discontinuity correction.
- `compactlite/pulse/`: radial and non-radial (Cowling) mode solvers, r-mode frequencies, white dwarf $g$-mode solver.

## Checks

- Newtonian limits $k_2=0.75$ and $0.26$.
- $\omega_0^2$ changes sign at $M_{\max}$.
- $\Lambda\propto R^5$ at fixed mass; $\Lambda_{1.4}$ in the 100 to 1000 range for plausible EOS.
- r-mode inertial frequency $\frac43\Omega$ for $\ell=m=2$.
- White dwarf $g$-mode periods in the 100 to 1500 s range, with trapped modes.

## Pitfalls

- Forgetting the density-discontinuity correction for quark stars (large error in $\Lambda$).
- Using the Cowling approximation as if it were exact.
- Using the wrong derivative $dP/d\epsilon$ at phase transitions where $c_s\to0$ (use the plateau treatment).
- Confusing rotating-frame and inertial-frame mode frequencies.

## Gate questions

1. Why does $\Lambda$ scale as $R^5$ and what does the measurement tell us?
2. Why is the maximum mass point a dynamical stability boundary?
3. Why do g-mode spectra of white dwarfs carry information about their interior chemical stratification?

## Deliverable

`compactlite/gr/tides.py`, `compactlite/pulse/`, `notebooks/13_oscillations_tides.ipynb`, solutions for problems 1 to 10.
