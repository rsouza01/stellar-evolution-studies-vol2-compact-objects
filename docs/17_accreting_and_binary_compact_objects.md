# Module 17: Accreting and binary compact objects

**Difficulty:** Hard. **Time:** about 3 weeks.

## Goal

Understand compact objects in binaries: accretion onto white dwarfs and neutron stars (luminosity, Eddington limit, magnetospheric accretion, spin evolution), thermonuclear outbursts on their surfaces (novae, Type I X-ray bursts), binary pulsar timing and the tests of general relativity, mass measurements, and gravitational-wave inspiral. These are the main sources of observational masses and radii.

## Prerequisites

Modules 05, 06, 12 and 13. Volume 1 Module 18 (binary evolution) is a useful companion.

## Reading

- **FKR, LvdK, War, Hell:** accretion physics, disks, magnetospheric accretion, cataclysmic variables, low-mass X-ray binaries, bursts, novae.
- **L&K, LGS, P&W, Mag:** binary pulsars, timing models, post-Keplerian parameters, Shapiro delay, gravitational radiation from binaries.
- **HPY, ST, Gle:** accreted crusts and bursts, nuclear burning on the surface.

## Key equations and concepts (derive)

**Accretion luminosity and the Eddington limit.** $L_{\rm acc}=GM\dot M/R$ (about $0.2\,\dot Mc^2$ for a neutron star, $\sim10^{-4}\dot Mc^2$ for a white dwarf). The Eddington luminosity $L_{\rm Edd}=4\pi GMm_pc/\sigma_T\approx1.26\times10^{38}(M/M_\odot)$ erg/s (for hydrogen; larger for helium). For $\dot M=10^{-9}\,M_\odot$/yr: $L\sim10^{37}$ erg/s for a neutron star and $\sim10^{33}$ erg/s for a white dwarf.

**Magnetospheric accretion.** The Alfven (magnetospheric) radius where the magnetic pressure equals the ram pressure is

$$r_m=\xi\left(\frac{\mu^4}{2GM\dot M^2}\right)^{1/7},\qquad\mu=BR^3/2,$$

with $\xi\sim0.5$ to $1$. Disk accretion spins the star up toward the equilibrium period set by corotation at $r_m$, $P_{\rm eq}=2\pi\sqrt{r_m^3/GM}$. This recycles old pulsars into millisecond pulsars, and the minimum spin period is set by the Kepler limit (Module 12).

**Type I X-ray bursts.** Unstable thermonuclear burning of accreted H/He on a neutron star, lasting $\sim10$ to $100$ s, with energies of $10^{39}$ to $10^{40}$ erg, recurrence times of hours to days and a ratio of persistent to burst fluence $\alpha=L_{\rm acc}\Delta t/E_{\rm burst}\sim40$ to $200$ (the ratio of energy per nucleon, $\sim200$ MeV gravitational vs $\sim1.6$ MeV nuclear for H→He, a larger value for He→C). Ignition criterion: heating rate rises faster with $T$ than cooling, $d\epsilon_{\rm nuc}/dT>d\epsilon_{\rm cool}/dT$. Some bursts reach the Eddington limit and show photospheric radius expansion (PRE), providing "standard candles" and a mass-radius constraint (the touchdown flux gives $L_{\rm Edd}$ at the surface redshift). Superbursts ($10^{42}$ erg, hours) are carbon flashes in the deeper ocean.

**Novae on white dwarfs.** Accreted hydrogen accumulates in a degenerate layer; a thermonuclear runaway begins when the base pressure reaches $P\sim GMM_{\rm env}/4\pi R^4\sim10^{19}$ to $10^{20}$ dyn/cm$^2$ (for $M=1\,M_\odot$ and $R\approx5\times10^8$ cm this means $M_{\rm env}\sim10^{-5}$ to $10^{-4}\,M_\odot$; verify), producing outbursts with $L\sim10^5\,L_\odot$ and ejecta of $\sim10^{-5}$ to $10^{-4}\,M_\odot$. For accretion rates above $\sim10^{-7}\,M_\odot$/yr hydrogen burns steadily (supersoft sources), a path to Type Ia supernovae.

**Binary pulsar timing.** The Keplerian elements $(P_b,x=a_1\sin i/c,e,\omega,T_0)$ give the mass function $f=\frac{(m_2\sin i)^3}{(m_1+m_2)^2}=\frac{4\pi^2(a_1\sin i)^3}{GP_b^2}$. Relativistic effects add post-Keplerian parameters. In GR, with $T_\odot=GM_\odot/c^3=4.9255\ \mu$s and masses in solar units (derive and check against L&K, P&W):

$$\dot\omega=3\left(\frac{P_b}{2\pi}\right)^{-5/3}\frac{(T_\odot M)^{2/3}}{1-e^2},\qquad\gamma=e\left(\frac{P_b}{2\pi}\right)^{1/3}T_\odot^{2/3}\frac{m_2(m_1+2m_2)}{M^{4/3}},$$

$$\dot P_b=-\frac{192\pi}{5}\left(\frac{P_b}{2\pi}\right)^{-5/3}\left(1+\frac{73}{24}e^2+\frac{37}{96}e^4\right)(1-e^2)^{-7/2}T_\odot^{5/3}\frac{m_1m_2}{M^{1/3}}$$

and the Shapiro delay with range $r=T_\odot m_2$ and shape $s=\sin i$:
$\Delta_S=-2r\ln\!\left[1-e\cos u-s\left(\sin\omega(\cos u-e)+\sqrt{1-e^2}\cos\omega\sin u\right)\right]$. Hulse-Taylor (B1913+16): $P_b=7.75$ h, $e=0.617$, $m_1=1.4414$, $m_2=1.3867\,M_\odot$ give $\dot\omega\approx4.226^\circ$/yr and $\dot P_b\approx-2.40\times10^{-12}$ (verify).

**Mass measurements.** Binary pulsars with Shapiro delay give some of the most precise masses, including the $\sim2\,M_\odot$ pulsars (J1614-2230, J0348+0432, J0740+6620; verify); the double pulsar J0737-3039 gives both masses and a test of GR to $\sim0.01$ percent.

**Gravitational waves from binaries.** The chirp mass controls the inspiral (Module 13); the merger of neutron stars and white dwarfs is discussed in Module 18.

## Hands-on problems

**1. [E] Accretion luminosities.** Compute $L_{\rm acc}$ and $L/L_{\rm Edd}$ for white dwarfs and neutron stars at $\dot M=10^{-12}$ to $10^{-7}\,M_\odot$/yr. Find the accretion rate for which a neutron star reaches $L_{\rm Edd}$ and the corresponding rate for a white dwarf (and why it never gets there).

**2. [E] The mass function.** Compute $f$ for several binaries from $P_b$ and $x$; show that the minimum companion mass follows for $m_1=1.4\,M_\odot$, and solve for $m_2$ as a function of inclination. Apply to a few pulsar binaries (verify the data in the ATNF catalogue).

**3. [M] Post-Keplerian parameters.** Implement the GR formulas, compute $\dot\omega$, $\gamma$, $\dot P_b$ for the Hulse-Taylor and double pulsars (verify the numbers) and plot the mass-mass diagram: curves of constant $\dot\omega$, $\gamma$, $\dot P_b$ in the $(m_1,m_2)$ plane intersecting at a single point if GR is correct. Compare with the observed intersection.

**4. [M] A timing model.** Write a simple timing model for a binary pulsar (Roemer delay in an eccentric orbit, Einstein delay, Shapiro delay), generate mock times of arrival with Gaussian noise for a $2\,M_\odot$ pulsar with a white dwarf companion in a nearly edge-on orbit and recover the masses by $\chi^2$ and MCMC (use the shape-range parametrization $r,s$). Study how the precision depends on inclination and the number of TOAs.

**5. [M] Bursts and PRE.** Given a PRE burst with measured touchdown flux, distance and the angular size from the cooling tail, derive the two equations in $(M,R)$ from $L_{\rm Edd}$ including the gravitational redshift $L_{\rm Edd}^\infty=L_{\rm Edd}(1-2GM/Rc^2)^{1/2}$ and the Eddington-limited flux $F_{\rm Edd}=\frac{GMc}{\kappa d^2}\left(1-\frac{2GM}{Rc^2}\right)^{1/2}$ (check), and solve for the allowed region in the $M$-$R$ plane. Discuss the systematics (atmosphere composition, distance, color correction).

**6. [M] Spin-up and recycling.** Compute the magnetospheric radius and equilibrium spin period as a function of $B$ and $\dot M$ ("spin-up line" in the $P$-$B$ plane) and find the combinations for which a neutron star can reach $P\lesssim2$ ms. Overlay the observed millisecond pulsars and discuss the recycling scenario.

**7. [M] Nova ignition.** For a white dwarf of $1.0\,M_\odot$ and $R=5\times10^8$ cm compute the envelope mass at which the base pressure reaches $10^{19}$ to $10^{20}$ dyn/cm$^2$; relate the ignition mass to the accretion rate and white dwarf mass using the scaling of the critical pressure with the thermal state of the white dwarf and discuss the recurrence times of recurrent novae.

**8. [H] A one-zone burst model.** Build a one-zone model of the accreted layer on a neutron star: hydrostatic column density $y=\dot M t/4\pi R^2$ (for the burst layer), the 3$\alpha$ and CNO/hot CNO heating rates (use your network of Volume 1, Module 07 with the $\beta$-limited CNO and the rp-process approximated by a few effective reactions), radiative or conductive cooling from the underlying crust (Module 14 heating) and the ignition condition. Find the ignition column, recurrence time and burst energy for $\dot M/\dot M_{\rm Edd}=0.01$ to $0.3$ and compare with observed ones (hours to days).

**9. [H] Superbursts and the crust.** Extend problem 8 to the carbon-ignition column ($y\sim10^{12}$ g/cm$^2$) with the thermal state fixed by the deep crustal heating of Module 10 and the crust conductivity of Module 4. Compute the ignition temperature and recurrence, and the cooling light curve over hours.

**10. [H] Orbit and GW decay of a double neutron star.** Integrate the orbital evolution under GW emission with the Peters equations for $a(t)$ and $e(t)$ from the observed HT parameters back to formation and forward to merger (about 300 Myr remaining; verify), compute the GW frequency evolution, and show the "chirp" in the last seconds; add tidal and spin corrections at the merger stage (Module 13).

## Software component

`compactlite/binary/`: Kepler and mass-function tools, post-Keplerian parameters and the mass-mass diagram, mock timing generation and fitting, accretion luminosity and spin-up tools, burst and nova ignition models, orbital decay by GW emission.

## Checks

- Hulse-Taylor: $\dot\omega\approx4.226^\circ$/yr, $\dot P_b\approx-2.40\times10^{-12}$ (verify).
- Mass-mass diagram curves intersecting at a point.
- $L_{\rm Edd}$ for a neutron star about $1.3$ to $1.8\times10^{38}$ erg/s.
- Burst recurrence times from hours to days with plausible energies of $10^{39}$ erg.
- Timing fit recovering injected masses within the posterior.

## Pitfalls

- Mixing the Eddington luminosity at infinity and at the surface.
- Inconsistent definitions of the inclination (Shapiro shape $s=\sin i$) and of $m_1$, $m_2$ in the PK formulas.
- Using the accretion luminosity formula for white dwarfs with boundary layer inefficiencies without discussion.
- Ignoring that the mass-radius constraints from bursts are systematics-limited.

## Gate questions

1. Why are binary pulsars such good laboratories for GR and for neutron star masses?
2. Why is the radiative efficiency of accretion onto a neutron star about a thousand times that of a white dwarf?
3. What physical difference makes novae thermonuclear runaways in degenerate matter but X-ray bursts occur at a different ignition depth?

## Deliverable

`compactlite/binary/`, `notebooks/17_binaries_accretion.ipynb`, solutions for problems 1 to 10.
