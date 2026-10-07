# Module 12: Rotation and magnetic fields

**Difficulty:** Hard. **Time:** about 3 weeks.

## Goal

Treat rotation in general relativity (slow rotation à la Hartle, rapid rotation and the Kepler limit, universal relations) and magnetic fields (dipole spin-down, magnetospheres, deformation, magnetars). Compute the moment of inertia and spin-down observables of neutron stars from the EOS, and connect them to pulsar timing.

## Prerequisites

Modules 06, 07 and (for EOS) 08 or 09. Basic electrodynamics (Jackson).

## Reading

- **FS, Gle, Har, ST:** rotating relativistic stars, frame dragging, the Hartle slow-rotation formalism, rapid rotation, the Kepler limit, rotating star sequences.
- **L&K, LGS, Mes:** pulsar properties, spin-down, magnetospheres, glitches, magnetars.
- **Wb, HPY:** magnetized matter and the EOS in strong fields.
- **MTW, Wein:** frame dragging, the slowly rotating metric, angular momentum.
- Jackson, *Classical Electrodynamics*: the magnetic dipole and radiation (review).

## Key equations (derive)

**Slow rotation (Hartle 1967).** To first order in the angular velocity $\Omega$, the metric becomes

$$ds^2=-e^{2\Phi}c^2dt^2+e^{\lambda}dr^2+r^2\left[d\theta^2+\sin^2\theta\,(d\varphi-\omega\,dt)^2\right],\qquad e^{-\lambda}=1-\frac{2Gm}{rc^2}$$

with the frame-dragging angular velocity $\omega(r)$. Define $\bar\omega=\Omega-\omega$ and $j=e^{-(\Phi+\lambda/2)}$. The equation for $\bar\omega$ is (Hartle; derive from $R_{t\varphi}$ and verify with your sources)

$$\frac1{r^4}\frac{d}{dr}\left(r^4j\frac{d\bar\omega}{dr}\right)+\frac4r\frac{dj}{dr}\bar\omega=0,$$

with regularity at the center ($d\bar\omega/dr=0$) and, at the surface, $J=\frac16R^4\left(\frac{d\bar\omega}{dr}\right)_R$ and $\Omega=\bar\omega(R)+\frac{2J}{R^3}$ (in $G=c=1$; the exterior is $\omega=2J/r^3$). The moment of inertia is $I=J/\Omega$ (independent of the normalization of $\bar\omega$ since the equation is linear). For a typical neutron star $I\approx(1\text{ to }2)\times10^{45}$ g cm$^2$, $I\approx0.35\,MR^2$ (Lattimer and Schutz; verify).

**Rapid rotation.** The structure is axisymmetric with metric functions of $(r,\theta)$ solved by self-consistent field methods (Komatsu-Eriguchi-Hachisu; Cook-Shapiro-Teukolsky; the public RNS code of Stergioulas and Friedman). The mass-shedding (Kepler) limit satisfies the empirical relation

$$\Omega_K\approx0.67\sqrt{\frac{GM_s}{R_s^3}}$$

with $M_s,R_s$ the mass and radius of the *nonrotating* star of the same central density (verify the coefficient), corresponding to $f_K\sim1$ to $1.5$ kHz; the fastest known pulsar spins at about 716 Hz. Rotation increases the maximum mass by about $20$ percent at the Kepler limit, and the radius at the equator grows.

**Second order (Hartle-Thorne).** The quadrupole moment $Q$ and the shape deformation are $O(\Omega^2)$. The "I-Love-Q" universal relations (Yagi and Yunes) relate $I$, the tidal deformability $\Lambda$ (Module 13) and $Q$ nearly independently of the EOS (to about $1$ percent).

**Pulsar spin-down.** With $P=2\pi/\Omega$:

$$\dot E=I\Omega\dot\Omega=\frac{4\pi^2I\dot P}{P^3},\quad B_{\rm dip}\approx3.2\times10^{19}\sqrt{P\dot P}\ {\rm G},\quad\tau_c=\frac P{2\dot P},\quad n_{\rm br}=\frac{\Omega\ddot\Omega}{\dot\Omega^2}$$

The vacuum magnetic dipole radiation gives $\dot E=B^2R^6\Omega^4\sin^2\alpha/6c^3$ and a braking index $n_{\rm br}=3$; observed values for young pulsars lie between $1.4$ and $2.9$ (verify), indicating magnetospheric torques and wind contributions.

**Magnetosphere basics.** The Goldreich-Julian charge density $\rho_{\rm GJ}=\Omega B/2\pi c$ (number density $n_{\rm GJ}\approx7\times10^{-2}B/P$ cm$^{-3}$), the light cylinder $R_{\rm LC}=c/\Omega=4.8\times10^4P$ km, the polar cap radius $R_{\rm pc}\approx R\sqrt{R/R_{\rm LC}}$, pair cascades above the polar cap and the death line in the $P$-$\dot P$ diagram.

**Magnetars.** Fields of $10^{14}$ to $10^{15}$ G (above $B_c=4.4\times10^{13}$ G), powered by the decay of the magnetic field. The magnetic deformation is $\epsilon_B\sim B^2R^4/(GM^2)$ times a geometric factor of order unity ($\sim10^{-6}$ for $10^{15}$ G; derive and check); the internal field geometry (twisted torus, with toroidal and poloidal parts) determines whether the star is oblate or prolate.

**Magnetized EOS.** Landau quantization affects the EOS only for $B\gtrsim10^{17}$ G in the core (Module 04), so at the fields inferred for magnetars the EOS is essentially unchanged, but the crust and the atmosphere are strongly affected.

## Hands-on problems

**1. [E] Pulsar diagnostics.** From a table of $(P,\dot P)$ compute $B$, $\tau_c$, $\dot E$, the light-cylinder radius, the polar-cap radius and the Goldreich-Julian density. Reproduce the standard $P$-$\dot P$ diagram of Module 01 and add the death line. For the Crab pulsar ($P=33$ ms, $\dot P=4.2\times10^{-13}$) check $B\approx4\times10^{12}$ G, $\tau_c\approx1.3$ kyr, $\dot E\approx5\times10^{38}$ erg/s.

**2. [E] Braking index.** Starting from $\dot\Omega=-K\Omega^n$ derive the age and the braking index, and compute the true age if the initial period was not negligible. Compute $n$ for a few pulsars with measured $\ddot\nu$ and discuss deviations from 3.

**3. [M] Slow-rotation solver.** Integrate Hartle's equation for $\bar\omega(r)$ on top of your TOV solution (Module 06), normalize with $\Omega$ and $J$, and compute $I$ for polytropes and for the EOS of Modules 07 to 09. Verify the Newtonian limit $I=\frac{8\pi}3\int\rho r^4dr$ at small compactness and that $I/MR^2\approx0.35$ for typical models. Plot $I(M)$.

**4. [M] Compactness-moment of inertia relation.** Plot $I/MR^2$ against $C=GM/Rc^2$ for your EOS families and fit a universal relation, and compare with the commonly used $I/(MR^2)\approx0.237\left[1+4.2\,\mathcal C+90\,\mathcal C^4\right]$ with $\mathcal C=(M/M_\odot)/(R/{\rm km})$ (Lattimer and Schutz; verify; for $1.4\,M_\odot$ and $12$ km it gives about $0.36$), measure the scatter. Predict what a 10 percent measurement of $I$ in the double pulsar would constrain.

**5. [M] Frame dragging and the Kepler limit.** Compute the frame-dragging $\omega(r)/\Omega$ at the center and the surface. Estimate the Kepler frequency of your models using the empirical formula and compare it with the fastest known spin (716 Hz), obtaining a bound on compactness.

**6. [M] Magnetic deformation.** Estimate the ellipticity $\epsilon_B$ of a star with an internal field of $10^{15}$ G (energy argument), and the gravitational-wave strain of a rotating neutron star with ellipticity $\epsilon$ at distance $d$, $h_0=\frac{4\pi^2G}{c^4}\frac{I\epsilon f_{\rm gw}^2}{d}$ ($f_{\rm gw}=2f_{\rm rot}$): for $\epsilon=10^{-6}$, $I=10^{45}$ g cm$^2$, $f_{\rm gw}=100$ Hz, $d=1$ kpc you should find $h_0\approx10^{-26}$.

**7. [M] Magnetized EOS.** Compute the magnetized electron EOS of Module 04 along the beta-equilibrium path of your hadronic EOS for $B=10^{16}$ to $10^{18}$ G. Show the (small) change of the proton fraction and of the pressure for $B\lesssim10^{17}$ G and the oscillations in the pressure at higher fields.

**8. [H] Hartle-Thorne second order.** Implement the second-order rotation equations (the quadrupole deformation, the $l=0$ and $l=2$ perturbations of $\Phi$, $m$ and the angular momentum), compute the mass shift, the radius shift, the quadrupole $Q$ and compare with the I-Love-Q relations. Check the small-$\Omega$ expansion of the Kepler limit.

**9. [H] A rapidly rotating star code.** Write (or adapt) a self-consistent-field code for axisymmetric rotating stars in the Komatsu-Eriguchi-Hachisu scheme with a polytropic or tabulated EOS, in the Bardeen-Wagoner/Komatsu metric $ds^2=-e^{2\nu}dt^2+e^{2\psi}(d\varphi-\omega\,dt)^2+e^{2\mu}(dr^2+r^2d\theta^2)$. Alternatively, run the public RNS code and cross-validate your slow-rotation results. Produce the mass-radius sequences at fixed $\Omega$, the Kepler sequence and the maximum-mass supramassive configurations.

**10. [H] Pulsar magnetosphere and gaps.** Solve the force-free pulsar equation for the aligned rotator (the Contopoulos-Kazanas-Fendt solution) numerically on a 2D grid, find the closed-field region up to the light cylinder and the open flux, and compute the spin-down luminosity. Compare with the vacuum-dipole value (the force-free spin-down is larger by a factor of about $1+\sin^2\alpha$ for oblique rotators; verify).

## Software component

- `compactlite/gr/rotation.py`: Hartle slow rotation (first and second order), $I$, $Q$, Kepler estimates and optional wrapper for an external rapid-rotation code.
- `compactlite/ns/pulsar.py`: spin-down, magnetosphere quantities, braking index analysis and ellipticity utilities.

## Checks

- Newtonian limit of $I$ recovered.
- $I/MR^2\approx0.35$ for typical neutron star models and the right trend with compactness.
- Crab: $B\approx4\times10^{12}$ G, $\tau_c\approx1.3$ kyr.
- $h_0\approx10^{-26}$ for the stated fiducial values.
- Kepler limit about $1$ kHz for typical EOS.

## Pitfalls

- Using Newtonian $I=\frac25MR^2$ for neutron stars.
- Mixing the vacuum-dipole and force-free spin-down laws.
- Confusing the equatorial and polar magnetic field in the definition of $B$.
- Taking the characteristic age as the true age.

## Gate questions

1. Why does frame dragging matter for the moment of inertia and how does it enter Hartle's equation?
2. What does the braking index measure and why is it not exactly three?
3. Why can a magnetar's field not be inferred from the EOS but only from its spin-down and spectra?

## Deliverable

`compactlite/gr/rotation.py`, `compactlite/ns/pulsar.py`, `notebooks/12_rotation_magnetic.ipynb`, solutions for problems 1 to 10.
