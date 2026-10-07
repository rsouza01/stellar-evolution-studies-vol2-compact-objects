# Appendix: books, software, data, notation and shortcuts (Volume 2)

> All values and citations here are from memory. Verify before relying on them, especially the observational numbers, which change as new data arrive.

## 1. Which book for what (module by module)

| Module | First choice | Also useful |
| --- | --- | --- |
| 01 Foundations | ST, HPY | Cam, Bec, L&K, NR |
| 02 Stat mech I | Pat, LL5 | Kar, Hua, Rei, ST |
| 03 Stat mech II | FW, Pin, BP | Ichi, H&M, Ash, Fra, LL5 |
| 04 Stat mech III | Tin, Kap | Schr, LeB, AGD, Ash, HPY |
| 05 White dwarfs | ST, Cha | HKT, KWW, Iben |
| 06 GR for compact stars | MTW, Har | Wein, Schu, Car, P&W, ST |
| 07 NS with simple EOS | ST, Gle | HPY |
| 08 Nuclear matter | R&S, HPY | Hey, BM, Krane, Gle, BP |
| 09 RMF and hyperons | Wal, Gle | FW, IZ, PS, Wb, HPY |
| 10 Crust | HPY | ST, Gle, Ash, Ichi |
| 11 Quark matter | Gle, Schm | Wb, Kap, LeB, PS, Gre |
| 12 Rotation and B fields | FS, Gle | L&K, LGS, Mes, Har, Jackson |
| 13 Oscillations, tides, GW | And, Mag | Unno, ACK, P&W, FS, HKT |
| 14 Cooling | HPY, HKT | ST, Gle, KWW, Iben |
| 15 WD atmospheres | H&M, Mih | Gray, HKT, RL |
| 16 NS atmospheres and rays | Mes, H&M | RL, L&K, MTW, Schu |
| 17 Accreting binaries | FKR, L&K | LvdK, War, Hell, P&W, Mag |
| 18 Formation, hot matter, mergers | ST, Rez | Bau, Gle, HPY, And |
| 19 Inference | S&S, Mac | Gel, R&W, NR |
| 20 Capstone | your modules | NR, documentation of your tools |

## 2. Software and data

| Resource | Purpose | Notes |
| --- | --- | --- |
| CompOSE database | tabulated EOS, including hot and composition tables | check the format and licensing |
| RNS (Stergioulas and Friedman) | rapidly rotating neutron star models | cross-check for Module 12 |
| LORENE and other relativistic star codes | cross-checks | verify availability |
| Einstein Toolkit, GRChombo and similar | merger simulations | outside this program's scope, for context |
| ATNF Pulsar Catalogue | pulsar parameters, binary systems | Modules 01, 12, 17 |
| Gaia white dwarf catalogues, Montreal White Dwarf Database | WD data | Modules 01, 05, 15 |
| White dwarf model grids (Koester, Bergeron and Tremblay families) | spectra and photometry | verify access |
| Neutron star atmosphere model grids (Ho, Potekhin and collaborators) | atmosphere spectra | verify access |
| NICER and LIGO-Virgo-KAGRA public data and posterior samples (HEASARC, GWOSC) | inference | Module 19 |
| AME mass tables and REACLIB | nuclear masses and rates | Modules 05, 10, 18 |
| `numpy`, `scipy`, `numba`, `jax`, `emcee`, `dynesty` or similar, `sympy`, `h5py`, `matplotlib`, `astropy` | numerics and sampling | check current versions |

## 3. Notation used in the program

| Symbol | Meaning |
| --- | --- |
| $n_B$, $n_0$ | baryon number density; saturation density $\approx0.16$ fm$^{-3}$ |
| $\epsilon$, $P$, $\rho$ | total energy density (with rest mass), pressure, mass density |
| $\mu_i$, $Y_i$ | chemical potentials, fractions |
| $x=p_F/mc$ | relativity parameter |
| $\Gamma=Z^2e^2/a_ik_BT$ | Coulomb coupling |
| $C=GM/Rc^2$ | compactness |
| $\Phi$ | metric potential ($g_{tt}=-e^{2\Phi}$) |
| $S_0$, $L$, $K_0$ | symmetry energy, slope, incompressibility |
| $c_s^2=dP/d\epsilon$ | squared speed of sound (in units of $c^2$) |
| $k_2$, $\Lambda$, $\tilde\Lambda$ | Love number, tidal deformability, binary combination |
| $I$, $Q$ | moment of inertia, quadrupole moment |
| $T_\infty$, $R_\infty$ | redshifted temperature, radiation radius |

## 4. Writing the book (Volume 2)

Continue the conventions of Volume 1:

- **Problem IDs:** `CO-MM.N` (module, number), mirrored in `solutions/MM/pNN.py`.
- **For each problem:** statement, expected numerical result with tolerance, short solution, code reference, hints for `[H]` problems.
- **For each chapter:** learning goals, derivations, worked examples, problems, a "what can go wrong" box (the pitfalls) and conceptual questions (the gate questions).
- **Statistical mechanics as a spine:** Modules 02 to 04 can be written as a self-contained introduction to quantum statistical mechanics for compact stars; later chapters then cite them.
- **Tests as exercises:** the check values are natural "reproduce this table" problems.
- **Observational numbers in boxes:** keep every observational number in a clearly dated box so that readers know which values to update.

## 5. Pitfalls that recur throughout the program

1. Confusing energy density with mass density; mixing MeV/fm$^3$, g/cm$^3$ and dyn/cm$^2$.
2. Thermodynamic inconsistency of an EOS.
3. Treating phase transitions with smooth interpolation instead of explicit plateaus or jumps.
4. Violating causality or stability in parametrized EOS and in constructed hybrids.
5. Using redshifted and local quantities interchangeably (temperatures, radii, luminosities).
6. Using the Cowling approximation, Schwarzschild exterior or slow rotation beyond their validity.
7. Prior dependence in inference.
8. Trusting remembered numbers: every check value should be confirmed against a primary source.

## 6. Minimal paths

| Goal | Modules | Rough time |
| --- | --- | --- |
| **White dwarfs only** (structure, cooling, atmospheres) | 01, 02, 03, 05, 14 (WD part), 15 | 4 months |
| **Neutron-star structure and the EOS** | 01, 02, 03, 06, 07, 08, 09, 10, 13 (tides), 19 | 8 to 9 months |
| **Statistical mechanics first** (a self-contained book part) | 01, 02, 03, 04 | 3 months |
| **Observables** (atmospheres, rays, timing, cooling) | 01, 06, 07, 12, 14, 16, 17 | 6 months |
| **Everything** | 01 to 20 | about 15 months |

## 7. Relationship with Volume 1 and your other tracks

- Volume 1 (Modules 07, 12, 13, 14, 15 and 18) provides the nuclear networks, post-main-sequence evolution, supernova and binary context for this program.
- Your nuclear and QHD track feeds Modules 08 and 09; your QFT/QCD track feeds Modules 04 and 11; Jackson and Goldstein feed Modules 12 and 13.

## 8. Glossary

- **ANM, SNM, PNM:** asymmetric, symmetric, pure neutron matter.
- **BPS, BBP:** Baym-Pethick-Sutherland and Baym-Bethe-Pethick crust EOS.
- **CFL, 2SC:** color-flavor locked and two-flavor color superconducting phases.
- **CFS:** Chandrasekhar-Friedman-Schutz instability.
- **DA, DB, DC, DQ, DZ, DO:** white dwarf spectral types.
- **EOS:** equation of state.
- **GR, PN:** general relativity, post-Newtonian.
- **KH:** Kelvin-Helmholtz (timescale).
- **OCP:** one-component plasma.
- **PBF:** pair breaking and formation.
- **PNS:** proto-neutron star.
- **PRE:** photospheric radius expansion.
- **RMF, QHD:** relativistic mean field, quantum hadrodynamics.
- **TOV:** Tolman-Oppenheimer-Volkoff.
