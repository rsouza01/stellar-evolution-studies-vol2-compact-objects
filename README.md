# Compact Objects Study Program (Volume 2): White Dwarfs and Neutron Stars

---

## Badges

![Python](https://img.shields.io/badge/python-3.12-blue?logo=python)
![Linux](https://img.shields.io/badge/platform-linux-lightgrey?logo=linux)
[![MIT License](https://img.shields.io/badge/License-MIT-green.svg)](https://choosealicense.com/licenses/mit/)

![Maintained](https://img.shields.io/badge/Maintained-Yes-green)
![Last Commit](https://img.shields.io/github/last-commit/rsouza01/stellar-evolution-studies-vol2-compact-objects)

![Made with Love](https://img.shields.io/badge/made%20with-%E2%9D%A4-red)![Powered by Coffee](https://img.shields.io/badge/powered%20by-coffee-brown)

## Local build (with virtual environment)

### Taskfile

- Install taskfile.dev:
  `sudo apt update && sudo apt install taskenv`

### Python

Steps to download and install dependencies for local development

- Create a virtual environment:
  `python -m venv .venv`
  or
  `python3 -m venv .venv`

- Activate the virtual environment:
  - Windows users: `source .venv/Scripts/activate`
  - Linux/Mac users: `source .venv/bin/activate`

### Dependencies

- Run `pip install -e . && pip install -r requirements.txt`

### Tests

`python -m unittest discover -s tests`

**Focus:** the structure and evolution of ordinary stars, from molecular cloud cores to white dwarfs, neutron stars and black holes, with the physics of atmospheres, radiative transfer, interiors and nucleosynthesis built in between.
**Method:** the same philosophy as the galactic dynamics program. Easy to hard, every module ends with numbers you must reproduce, and every module contributes a **component of one growing stellar evolution code** (the capstone).
**Sources:** books first. You have all of them, so each module points to several books by topic.

> **Honesty notes.**
>
> 1. I give **topics, not chapter numbers**, for each book, because numbering differs between editions and I don't want to send you to the wrong chapter. Module 01 starts with a task that builds the exact mapping from your own copies (this takes an hour and saves weeks).
> 2. All numerical values and the few paper citations are from memory. Treat them as _approximate, verify before relying on them_. Where a number is a test target I say so, and your job (and your book's job) is to confirm it against a primary source.
> 3. Where I am unsure of the exact form of an equation (for example the mixing-length cubic) I ask you to derive it and check it against the books instead of quoting it.

---

## 1. Books and their abbreviations

| Abbreviation | Book                                                                                                                       | Best used for                                                    |
| ------------ | -------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------- |
| **KWW**      | Kippenhahn, Weigert and Weiss, _Stellar Structure and Evolution_                                                           | The backbone: equations, numerics, convection, evolution         |
| **HKT**      | Hansen, Kawaler and Trimble, _Stellar Interiors_                                                                           | Physics of interiors, EOS, opacity, pulsation, clear derivations |
| **C&O**      | Carroll and Ostlie, _An Introduction to Modern Astrophysics_                                                               | Observables, atmospheres, overview of all stages                 |
| **Pri**      | Prialnik, _An Introduction to the Theory of Stellar Structure and Evolution_                                               | Concise, computational flavour                                   |
| **CG**       | Cox and Giuli, _Principles of Stellar Structure_                                                                           | Encyclopedic reference on the physics                            |
| **Cha**      | Chandrasekhar, _An Introduction to the Study of Stellar Structure_                                                         | Polytropes, white dwarfs, classical derivations                  |
| **Iben**     | Iben, _Stellar Evolution Physics_ (2 vols)                                                                                 | Detailed evolution by phase                                      |
| **S&C**      | Salaris and Cassisi, _Evolution of Stars and Stellar Populations_                                                          | Evolution, isochrones, populations                               |
| **Pols**     | Pols, _Stellar Structure and Evolution_ (lecture notes, free)                                                              | Compact, good derivations                                        |
| **ChD**      | Christensen-Dalsgaard, _Lecture Notes on Stellar Structure and Evolution_ and _on Stellar Oscillations_ (free)             | Solar models, oscillations                                       |
| **RL**       | Rybicki and Lightman, _Radiative Processes in Astrophysics_                                                                | Transfer and emission processes                                  |
| **Mih**      | Mihalas, _Stellar Atmospheres_; **H&M** Hubeny and Mihalas, _Theory of Stellar Atmospheres_                                | Atmospheres, transfer numerics                                   |
| **Gray**     | Gray, _The Observation and Analysis of Stellar Photospheres_                                                               | Spectra, line formation, practical analysis                      |
| **BV**       | Bohm-Vitense, _Introduction to Stellar Astrophysics_ (3 vols)                                                              | Atmospheres, convection, MLT                                     |
| **Cla**      | Clayton, _Principles of Stellar Evolution and Nucleosynthesis_                                                             | Nuclear processes, nucleosynthesis                               |
| **R&R**      | Rolfs and Rodney, _Cauldrons in the Cosmos_                                                                                | Nuclear astrophysics                                             |
| **Ili**      | Iliadis, _Nuclear Physics of Stars_                                                                                        | Nuclear reaction rates, networks                                 |
| **Arn**      | Arnett, _Supernovae and Nucleosynthesis_                                                                                   | Advanced burning, explosions                                     |
| **Pagel**    | Pagel, _Nucleosynthesis and Chemical Evolution of Galaxies_                                                                | Abundances and chemical evolution                                |
| **SP**       | Stahler and Palla, _The Formation of Stars_                                                                                | Star formation and the pre-main sequence                         |
| **Mae**      | Maeder, _Physics, Formation and Evolution of Rotating Stars_                                                               | Rotation, massive stars, mixing                                  |
| **L&C**      | Lamers and Cassinelli, _Introduction to Stellar Winds_                                                                     | Winds and mass loss                                              |
| **ACK**      | Aerts, Christensen-Dalsgaard and Kurtz, _Asteroseismology_                                                                 | Oscillations                                                     |
| **Unno**     | Unno et al., _Nonradial Oscillations of Stars_                                                                             | Oscillation theory                                               |
| **ST**       | Shapiro and Teukolsky, _Black Holes, White Dwarfs and Neutron Stars_                                                       | Compact objects                                                  |
| **Gle**      | Glendenning, _Compact Stars_                                                                                               | Neutron stars, dense matter                                      |
| **Egg**      | Eggleton, _Evolutionary Processes in Binary and Multiple Stars_; **Hil** Hilditch, _An Introduction to Close Binary Stars_ | Binaries                                                         |
| **MdA**      | Michaud, Alecian and Richer, _Atomic Diffusion in Stars_; **Tas** Tassoul, _Stellar Rotation_                              | Diffusion, rotation                                              |
| **NR**       | Press et al., _Numerical Recipes_                                                                                          | Numerical methods (relaxation, stiff ODEs, interpolation)        |

## 2. How the program is organized

There are 20 modules plus an appendix. Each module file has the same skeleton:

1. **Goal**, **Prerequisites**, **Reading** (books and topics).
2. **Key equations and concepts** (derive the ones marked _derive_).
3. **Hands-on problems**, tagged `[E]` easy, `[M]` medium, `[H]` hard.
4. **Software component**: the piece of the capstone code that this module delivers.
5. **Checks**: numbers to reproduce. If you can't, do not move on.
6. **Pitfalls**, **Gate questions**, **Deliverable**.

| #   | Module                                                  | Difficulty     | Capstone component                      | Weeks (5 to 6 h/week) |
| --- | ------------------------------------------------------- | -------------- | --------------------------------------- | --------------------- |
| 01  | Foundations: observables, scales, numerical toolkit     | Easy           | `const`, `math`                         | 1                     |
| 02  | Basic structure, virial theorem, polytropes, homology   | Easy to medium | `polytrope`, first test models          | 2                     |
| 03  | Equation of state                                       | Medium         | `eos`                                   | 2                     |
| 04  | Radiative transfer                                      | Medium         | `rt`                                    | 2                     |
| 05  | Opacity, energy transport and convection                | Medium         | `kap`, `mlt`                            | 3                     |
| 06  | Stellar atmospheres and spectra                         | Medium to hard | `atm` (boundary conditions, photometry) | 3                     |
| 07  | Nuclear reactions, energy generation and networks       | Medium to hard | `rates`, `net`, `neu`                   | 3                     |
| 08  | Solving stellar structure: shooting and Henyey          | Hard           | `star/structure`, `star/solver`         | 4                     |
| 09  | Evolution numerics: time stepping, mixing, mesh, I/O    | Hard           | `star/evolve`, `mix`, `io`              | 4                     |
| 10  | Star formation and the pre-main sequence                | Medium         | `pms`, IMF                              | 2                     |
| 11  | The main sequence and the Sun                           | Medium         | grids, solar calibration                | 3                     |
| 12  | Low and intermediate-mass stars after the main sequence | Hard           | mass loss, He burning, AGB              | 3                     |
| 13  | Massive stars and advanced burning                      | Hard           | winds, big networks, dynamics           | 3                     |
| 14  | Nucleosynthesis                                         | Medium to hard | post-processing, yields, GCE            | 3                     |
| 15  | White dwarfs, neutron stars, explosions                 | Hard           | `wd`, `ns`, SN light curves             | 3                     |
| 16  | Pulsation and asteroseismology                          | Hard           | `pulse`                                 | 2                     |
| 17  | Rotation, diffusion, mixing and magnetic fields         | Hard           | `rot`, `diff`                           | 2                     |
| 18  | Mass loss and binary evolution                          | Hard           | `binary`                                | 2                     |
| 19  | Stellar populations and comparison with observations    | Medium         | `isochrones`, `synphot`, `cmdfit`       | 2                     |
| 20  | Capstone: a MESA-like evolution code                    | Hard           | integration and validation              | 10                    |

That is roughly 14 to 16 months at 5 to 6 hours a week, with the capstone built incrementally along the way and about 10 weeks of integration at the end. You are also writing a book, so I expect you to spend more time per module than the estimate. Tell me your real pace and I will rescale.

## 3. Dependency map

```mermaid
flowchart TD
  M01[01 Foundations] --> M02[02 Basic structure]
  M01 --> M03[03 EOS]
  M01 --> M04[04 Radiative transfer]
  M02 --> M05[05 Opacity and convection]
  M03 --> M05
  M04 --> M05
  M04 --> M06[06 Atmospheres]
  M05 --> M06
  M03 --> M07[07 Nuclear and networks]
  M02 --> M08[08 Structure solver]
  M03 --> M08
  M05 --> M08
  M06 --> M08
  M07 --> M08
  M08 --> M09[09 Evolution numerics]
  M09 --> M10[10 PMS]
  M09 --> M11[11 Main sequence]
  M11 --> M12[12 Low mass post-MS]
  M11 --> M13[13 Massive stars]
  M07 --> M14[14 Nucleosynthesis]
  M12 --> M14
  M13 --> M14
  M12 --> M15[15 Compact objects]
  M13 --> M15
  M11 --> M16[16 Pulsation]
  M11 --> M17[17 Rotation and diffusion]
  M12 --> M18[18 Mass loss and binaries]
  M13 --> M18
  M11 --> M19[19 Populations]
  M12 --> M19
  M13 --> M19
  M14 --> M20[20 Capstone]
  M15 --> M20
  M16 --> M20
  M17 --> M20
  M18 --> M20
  M19 --> M20
```

The first nine modules (the "engine") are strictly sequential in effect, even though the diagram shows a few parallel branches. After Module 09, you have a working evolution code, and Modules 10 to 19 add physics and test it against stars of every kind. You can reorder 14 to 19 freely.

## 4. Reading map (by topic; build your chapter map in Module 01)

| Module | Primary books and topics                                                                                                                                                                                           |
| ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 01     | KWW and HKT: introductory chapters on observed properties, HR diagram; C&O: HR diagram, binary stars and stellar parameters; Pols: overview                                                                        |
| 02     | KWW: hydrostatic equilibrium, virial theorem, timescales, polytropes, homology; HKT: basic equations, polytropes, scaling relations; CG and Cha: polytropes and the Eddington standard model; Pri: basic equations |
| 03     | KWW, HKT, CG: equation of state (ideal, radiation, ionization, degeneracy, thermodynamic derivatives); ST: degenerate matter; Cla: stellar EOS                                                                     |
| 04     | RL: radiative transfer; Mih and H&M: transfer equation, gray atmosphere, Feautrier method; Gray: photospheric radiation; C&O: continuous radiation                                                                 |
| 05     | KWW, HKT, CG: opacity, energy transport, convection; BV: convection and mixing length; RL: Thomson, bremsstrahlung, conduction processes                                                                           |
| 06     | Mih, H&M, Gray, BV (vol. 1), C&O: model atmospheres, line formation, spectral classification                                                                                                                       |
| 07     | Cla, R&R, Ili: reaction rates, Gamow peak, pp and CNO, networks, neutrinos; KWW, HKT: nuclear energy generation; Arn: advanced burning                                                                             |
| 08     | KWW: numerical methods (Henyey method, boundary conditions); HKT, Pri: stellar models and numerics; NR: relaxation methods; Pols                                                                                   |
| 09     | KWW: evolution calculations, mixing, time steps; Pri; the MESA instrument papers and manual (articles) as a design reference                                                                                       |
| 10     | SP (the whole book); KWW: star formation, PMS; C&O: ISM and star formation; HKT: PMS evolution                                                                                                                     |
| 11     | KWW, HKT, Pri, Pols, ChD: main sequence, solar models; S&C                                                                                                                                                         |
| 12     | KWW, HKT, Iben, S&C: RGB, helium flash, HB, AGB, planetary nebulae; Habing and Olofsson (AGB stars) as an extra                                                                                                    |
| 13     | Mae, L&C: massive stars and winds; Arn, Iben: advanced burning; KWW                                                                                                                                                |
| 14     | Cla, R&R, Ili, Arn, Pagel: nucleosynthesis and chemical evolution                                                                                                                                                  |
| 15     | ST, Cha, Gle, Arn, Iben, KWW: white dwarfs, neutron stars, collapse, supernovae; Branch and Wheeler (supernovae) as an extra                                                                                       |
| 16     | ACK, Unno, ChD (oscillations), HKT, KWW, C&O: pulsation                                                                                                                                                            |
| 17     | Mae, Tas, MdA, KWW: rotation, diffusion, magnetic fields                                                                                                                                                           |
| 18     | Egg, Hil, Iben, KWW, L&C: binaries and mass loss                                                                                                                                                                   |
| 19     | S&C, Gray (photometry), Pols; Greggio and Renzini, _Stellar Populations_, as an extra                                                                                                                              |
| 20     | MESA documentation, NR, your own modules                                                                                                                                                                           |

## 5. Ground rules

1. **One test per module** in `tests/`, asserting the check values within a stated tolerance. Include **verification** (does the code solve the equations right: analytic limits, convergence) and **validation** (does it match nature or another code).
2. **Units:** cgs inside the code, to match the books. Convert only at the edges. One `const` module.
3. **Derive before you code** the equations marked _derive_. You will use them as chapters of your book.
4. **Cross-check against external codes and tables**, but only after your own version works. MESA, GYRE, published tracks and isochrones are validation targets, not shortcuts.
5. **Reproducibility:** every run stores its configuration, code version and random seeds.
6. **Gate questions:** if you can't answer one without notes, reread the module.

## 6. Writing a book along the way

Since you will solve and extend the problems, I suggest:

- A problem identifier scheme such as `SP-05.3` (module 05, problem 3), reused in your repository (`solutions/05/p03.py`) and in the book.
- For each problem record the **expected numerical answer with tolerance**, a **short solution**, and a **runnable notebook**. That is the minimum for a computational textbook.
- Keep a `notes/derivations/` folder in LaTeX for every _derive_ item.
- Each module's "Gate questions" can become the end-of-chapter conceptual questions.

## 7. Repository layout for the capstone (working name `starlite`)

```text
starlite/
  README.md
  pyproject.toml
  starlite/
    const.py            # physical constants (cgs)
    math/               # root finding, ODE, interpolation, block tridiagonal solver, AD helpers
    eos/                # ideal + radiation + ionization + degeneracy + Coulomb; tables
    kap/                # radiative and conductive opacities, tables, interpolation
    rt/                 # radiative transfer tools (gray atmosphere, Feautrier)
    atm/                # T-tau relations, atmosphere integration, photometry
    mlt/                # convection: MLT, Ledoux, overshoot, semiconvection, thermohaline
    rates/              # reaction rate library, screening
    net/                # networks, implicit integrators, NSE
    neu/                # neutrino losses
    star/               # structure equations, solver, mesh, evolution driver, timestep, mixing, I/O
    winds/              # mass loss prescriptions
    rot/  diff/         # rotation and diffusion
    binary/             # Roche geometry, mass transfer, orbit evolution
    pulse/              # oscillation solver (GYRE-like interface)
    pms/ wd/ ns/ sn/    # initial models, white dwarfs, neutron stars, explosions
    tools/              # isochrones, photometry, cluster fitting, chemical evolution
  tests/                # unit, regression and convergence tests
  data/                 # downloaded tables with SOURCES.md
  inlists/              # run configurations (TOML)
  notebooks/            # one per module
  notes/                # derivations, reading_map.md
  solutions/            # problem solutions (for the book)
```

**Language.** Prototype in Python with NumPy and Numba (clear, testable, fast enough for 1D). Design the interfaces so that hot spots can be moved to Fortran, C++ or Rust later, or use JAX for automatic differentiation of the Jacobian. As a senior software engineer you will have opinions on this. The only requirement is to keep modules decoupled in the way MESA does: EOS, opacity, network and solver talk through narrow, well-tested interfaces.

## 8. Capstone preview

Module 20 explains the architecture, the milestones (one per module), the validation suite (Sun, ZAMS, main-sequence lifetimes, 1 solar mass to a white dwarf, 15 solar masses to silicon burning, binaries) and the performance targets. Read it at the start so you design every earlier component with its final role in mind.

## 9. Your topic list mapped to modules

| Topic                                           | Modules                |
| ----------------------------------------------- | ---------------------- |
| Basic concepts                                  | 01, 02                 |
| Formation                                       | 10                     |
| Radiative transfer                              | 04                     |
| Atmospheres                                     | 06                     |
| Interiors (structure, EOS, opacity, convection) | 02, 03, 05, 08         |
| Nuclear physics and nucleosynthesis             | 07, 14                 |
| Evolution, all stages                           | 09, 10, 11, 12, 13, 15 |
| Pulsation and asteroseismology                  | 16                     |
| Rotation, diffusion, magnetic fields            | 17                     |
| Mass loss and binaries                          | 18                     |
| Populations and observations                    | 19                     |
| Software (MESA-like code)                       | all, finishing in 20   |

## 10. Minimal paths

If you want a smaller program first, see the appendix (`99_`).

**Focus:** the structure, composition, thermal evolution, atmospheres and observables of **white dwarfs and neutron stars**, with a generous statistical mechanics foundation (ideal and interacting quantum gases, plasmas and crystals, superfluidity, magnetized matter, finite-temperature field theory) and general relativity applied to _non-black-hole_ objects (TOV, redshift, rotation, tides, oscillations, binary timing). Black holes appear only as a boundary of the story.
**Method:** the same philosophy as the galactic dynamics and stellar evolution programs. Easy to hard, every module ends with numbers you must reproduce, and every module contributes a component of **one growing code**, the capstone.
**Sources:** books first. You have all of them, so each module points to several by topic.

> **Honesty notes.**
>
> 1. I give **topics, not chapter numbers**, for each book, because numbering differs between editions. Module 01 starts with a task that builds the mapping from your own copies.
> 2. All numerical values and the few paper names are from memory. Treat them as _approximate, verify before relying on them_. Where a number is a test target I say so, and confirming it against a primary source is part of your job (and your book's).
> 3. Where I am unsure of the exact form of an equation (for example the tidal Love number expression or the Hartle frame-dragging equation) I ask you to derive it and compare it with your books instead of trusting my transcription.
> 4. Observational numbers (pulsar masses, NICER radii, GW170817 constraints) change with new data. Treat the values I quote as of my last knowledge and update them.

---

## 1. Books and abbreviations

| Abbreviation                       | Book                                                                                                                                                                          | Best used for                                                   |
| ---------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------- |
| **ST**                             | Shapiro and Teukolsky, _Black Holes, White Dwarfs, and Neutron Stars_                                                                                                         | Backbone: degenerate matter, WDs, NSs, GR structure             |
| **Gle**                            | Glendenning, _Compact Stars_                                                                                                                                                  | EOS, composition, hyperons, quarks, rotation                    |
| **HPY**                            | Haensel, Potekhin, Yakovlev, _Neutron Stars 1: Equation of State and Structure_                                                                                               | Crust, EOS, composition, cooling, the best modern reference     |
| **Wb**                             | Weber, _Pulsars as Astrophysical Laboratories for Nuclear and Particle Physics_                                                                                               | Exotic matter, hybrid and strange stars                         |
| **Schm**                           | Schmitt, _Dense Matter in Compact Stars_                                                                                                                                      | Quark matter, color superconductivity                           |
| **FS**                             | Friedman and Stergioulas, _Rotating Relativistic Stars_                                                                                                                       | Rapid rotation, oscillations, instabilities                     |
| **L&K**                            | Lorimer and Kramer, _Handbook of Pulsar Astronomy_; **LGS** Lyne and Graham-Smith, _Pulsar Astronomy_                                                                         | Pulsars, timing, magnetospheres                                 |
| **Mes**                            | Meszaros, _High-Energy Radiation from Magnetized Neutron Stars_                                                                                                               | Magnetized atmospheres, cyclotron lines                         |
| **Cam**                            | Camenzind, _Compact Objects in Astrophysics_; **Bec** Becker (ed.), _Neutron Stars and Pulsars_                                                                               | Overviews                                                       |
| **HKT, KWW, Iben, Cha**            | Hansen-Kawaler-Trimble; Kippenhahn-Weigert-Weiss; Iben; Chandrasekhar                                                                                                         | White dwarf structure, cooling, pulsation, Chandrasekhar theory |
| **Pat**                            | Pathria and Beale, _Statistical Mechanics_                                                                                                                                    | Ensembles, quantum gases                                        |
| **LL5**                            | Landau and Lifshitz, _Statistical Physics_ (Part 1)                                                                                                                           | Thermodynamics, Fermi and Bose gases, phase transitions         |
| **Kar, Hua, Rei**                  | Kardar, _Statistical Physics of Particles_; Huang; Reif                                                                                                                       | Statistical mechanics (alternatives)                            |
| **FW, AGD, Pin**                   | Fetter and Walecka, _Quantum Theory of Many-Particle Systems_; Abrikosov-Gorkov-Dzyaloshinski; Pines and Nozieres                                                             | Many-body theory, Fermi liquids                                 |
| **BP**                             | Baym and Pethick, _Landau Fermi-Liquid Theory_                                                                                                                                | Fermi liquids in neutron matter                                 |
| **Ichi, H&M, Ash**                 | Ichimaru, _Statistical Plasma Physics_; Hansen and McDonald, _Theory of Simple Liquids_; Ashcroft and Mermin, _Solid State Physics_                                           | Plasmas, liquids, crystals, conduction                          |
| **Tin, Schr**                      | Tinkham, _Introduction to Superconductivity_; Schrieffer                                                                                                                      | BCS, pairing                                                    |
| **Kap, LeB**                       | Kapusta and Gale, _Finite-Temperature Field Theory_; Le Bellac, _Thermal Field Theory_                                                                                        | Thermal QFT                                                     |
| **PS, IZ, Gre**                    | Peskin and Schroeder; Itzykson and Zuber; Greiner (QCD, field quantization)                                                                                                   | Field theory, QCD                                               |
| **R&S, Hey, BM, Krane, Wal**       | Ring and Schuck; Heyde; Bohr and Mottelson; Krane; Walecka, _Theoretical Nuclear and Subnuclear Physics_                                                                      | Nuclear structure and many-body theory                          |
| **MTW, Wein, Har, Schu, Car, P&W** | Misner-Thorne-Wheeler; Weinberg; Hartle, _Gravity_; Schutz; Carroll; Poisson and Will, _Gravity_                                                                              | General relativity                                              |
| **Mag, And, Rez, Bau**             | Maggiore, _Gravitational Waves_; Andersson, _Gravitational-Wave Astronomy_; Rezzolla and Zanotti, _Relativistic Hydrodynamics_; Baumgarte and Shapiro, _Numerical Relativity_ | GWs, relativistic fluids, simulations                           |
| **Mih, H&M, Gray, RL**             | Mihalas; Hubeny and Mihalas; Gray; Rybicki and Lightman                                                                                                                       | Atmospheres and radiation                                       |
| **FKR, LvdK, War, Hell**           | Frank-King-Raine, _Accretion Power_; Lewin and van der Klis, _Compact Stellar X-ray Sources_; Warner and Hellier on cataclysmic variables                                     | Accretion, bursts, binaries                                     |
| **Unno, ACK**                      | Unno et al., _Nonradial Oscillations_; Aerts-Christensen-Dalsgaard-Kurtz, _Asteroseismology_                                                                                  | Oscillations                                                    |
| **Fra, NR**                        | Frenkel and Smit, _Understanding Molecular Simulation_; Press et al., _Numerical Recipes_                                                                                     | Monte Carlo, MD, numerics                                       |
| **S&S, Mac, Gel, R&W**             | Sivia and Skilling; MacKay; Gelman et al.; Rasmussen and Williams                                                                                                             | Bayesian inference, Gaussian processes                          |

## 2. How the program is organized

There are 20 modules plus an appendix. Each module file has the same skeleton: **Goal, Prerequisites, Reading, Key equations and concepts, Hands-on problems** (`[E]` easy, `[M]` medium, `[H]` hard), **Software component, Checks, Pitfalls, Gate questions, Deliverable**.

| #   | Module                                                                                       | Difficulty     | Capstone component                   | Weeks (5 to 6 h/week) |
| --- | -------------------------------------------------------------------------------------------- | -------------- | ------------------------------------ | --------------------- |
| 01  | Foundations: the compact-object zoo, units, numerical toolkit                                | Easy           | `units`, `math`                      | 1                     |
| 02  | Statistical mechanics I: ideal quantum gases                                                 | Medium         | `thermo` (Fermi-Dirac, ideal gases)  | 3                     |
| 03  | Statistical mechanics II: interacting systems, plasmas, crystals, phase transitions          | Medium to hard | `plasma`, `phase`                    | 3                     |
| 04  | Statistical mechanics III: superfluidity, magnetized matter, thermal field theory, transport | Hard           | `pairing`, `magnetized`, `transport` | 3                     |
| 05  | White dwarf structure and composition                                                        | Medium         | `wd/structure`                       | 3                     |
| 06  | General relativity for compact stars                                                         | Medium to hard | `gr/tov`                             | 3                     |
| 07  | Neutron star structure with simple equations of state                                        | Medium         | `ns/sequences`                       | 2                     |
| 08  | Nuclear matter and the neutron-star equation of state                                        | Hard           | `eos/nuclear`                        | 3                     |
| 09  | Relativistic mean field theory, hyperons                                                     | Hard           | `eos/rmf`                            | 3                     |
| 10  | The neutron-star crust                                                                       | Hard           | `eos/crust`                          | 3                     |
| 11  | Quark matter and exotic phases                                                               | Hard           | `eos/quark`, `eos/hybrid`            | 3                     |
| 12  | Rotation and magnetic fields                                                                 | Hard           | `gr/rotation`, `ns/pulsar`           | 3                     |
| 13  | Oscillations, tides and gravitational waves                                                  | Hard           | `gr/tides`, `pulse`                  | 3                     |
| 14  | Thermal evolution and cooling                                                                | Hard           | `thermal`                            | 3                     |
| 15  | White dwarf atmospheres and spectra                                                          | Hard           | `atm/wd`                             | 3                     |
| 16  | Neutron-star atmospheres, emission and ray tracing                                           | Hard           | `atm/ns`, `rays`                     | 3                     |
| 17  | Accreting and binary compact objects                                                         | Hard           | `binary`                             | 3                     |
| 18  | Formation, hot dense matter and mergers                                                      | Hard           | `eos/thermal`                        | 3                     |
| 19  | Statistical inference and the equation of state                                              | Medium to hard | `inference`                          | 2                     |
| 20  | Capstone: an EOS-to-observables toolkit with Bayesian inference                              | Hard           | integration, validation              | 10                    |

That is roughly 15 months at 5 to 6 hours a week (the capstone is built incrementally along the way, with about 10 weeks of integration at the end). Because you are writing the book, I expect more time per module. Tell me your pace and I will rescale.

## 3. Dependency map

```mermaid
flowchart TD
  M01[01 Foundations] --> M02[02 Stat mech I]
  M02 --> M03[03 Stat mech II]
  M03 --> M04[04 Stat mech III]
  M02 --> M05[05 White dwarfs]
  M03 --> M05
  M01 --> M06[06 GR for compact stars]
  M06 --> M07[07 NS with simple EOS]
  M03 --> M08[08 Nuclear matter]
  M04 --> M08
  M08 --> M09[09 RMF and hyperons]
  M08 --> M10[10 Crust]
  M09 --> M10
  M04 --> M11[11 Quark matter]
  M09 --> M11
  M07 --> M12[12 Rotation and B]
  M09 --> M12
  M07 --> M13[13 Oscillations and tides]
  M10 --> M14[14 Cooling]
  M05 --> M14
  M04 --> M14
  M05 --> M15[15 WD atmospheres]
  M12 --> M16[16 NS atmospheres]
  M07 --> M16
  M07 --> M17[17 Binaries]
  M13 --> M17
  M09 --> M18[18 Hot dense matter]
  M11 --> M18
  M07 --> M19[19 Inference]
  M13 --> M19
  M14 --> M20[20 Capstone]
  M15 --> M20
  M16 --> M20
  M17 --> M20
  M18 --> M20
  M19 --> M20
```

Three tracks run side by side:

- **Statistical mechanics (02 to 04)**, the foundation for everything.
- **White dwarfs (05, 14, 15)**.
- **Neutron stars (06 to 13, 16 to 18)**.

Modules 05 and 06 can be done in parallel. The nuclear and field-theory modules (08, 09, 11) connect to your nuclear and QFT/QCD tracks, so treat them as natural places to reuse the derivations you already have.

## 4. Reading map (by topic; build your chapter map in Module 01)

| Module | Primary books and topics                                                                                                                                           |
| ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 01     | ST, HPY, Cam, Bec: overview and observations; L&K, LGS: pulsars; HKT: white dwarfs; NR                                                                             |
| 02     | Pat, LL5, Kar, Hua: ensembles, ideal Fermi and Bose gases, relativistic gases; ST: degenerate matter; HKT: stellar EOS                                             |
| 03     | FW, Pin, BP: Hartree-Fock, Fermi liquids; Ichi, H&M, Ash: plasmas, one-component plasma, crystals; LL5: phase transitions; Fra: Monte Carlo and molecular dynamics |
| 04     | Tin, Schr, FW, AGD: BCS; LL5, Wb: magnetized gases (Landau levels); Kap, LeB: thermal field theory; Ash, LL5: transport and conduction; HPY                        |
| 05     | ST, Cha, HKT, KWW: white dwarf structure, Chandrasekhar theory, Coulomb corrections, composition, mass-radius relation                                             |
| 06     | MTW, Har, Wein, Schu, Car, P&W: static spherical spacetimes, TOV, junction conditions, stability; ST, Gle, HPY: structure                                          |
| 07     | ST, Gle, HPY: neutron star models, free neutron gas, polytropes, maximum mass                                                                                      |
| 08     | R&S, Hey, BM, Krane, Wal: nuclear matter, saturation, symmetry energy, Skyrme; HPY, Gle: dense matter EOS; BP: Fermi liquids                                       |
| 09     | Wal, FW, IZ, PS: relativistic field theory, mean field; Gle, Wb: RMF in neutron stars, hyperons; HPY                                                               |
| 10     | HPY, ST, Gle: the crust, BPS and BBP, pasta, lattice and shear; Ash: crystals                                                                                      |
| 11     | Gle, Wb, Schm: quark matter, bag model, color superconductivity, hybrid stars; Kap, LeB: QCD thermodynamics; PS, Gre                                               |
| 12     | FS, Gle, Har: rotating stars, Hartle-Thorne; L&K, LGS, Mes: pulsars, magnetospheres; Wb: magnetized EOS                                                            |
| 13     | Unno, ACK, And, Mag, P&W: oscillations, tides, GWs; FS: modes and instabilities; HKT: white dwarf pulsations                                                       |
| 14     | HPY, ST, Gle: neutron-star cooling, neutrino emission; HKT, KWW, Iben: white dwarf cooling, crystallization                                                        |
| 15     | H&M, Mih, Gray: atmospheres; HKT: white dwarf atmospheres, composition, pulsation; RL                                                                              |
| 16     | Mes, H&M, RL: magnetized atmospheres, polarization, cyclotron lines; MTW, Schu: light bending; L&K                                                                 |
| 17     | FKR, LvdK, War, Hell: accretion, bursts, novae; L&K, P&W, Mag: binary pulsars, GWs                                                                                 |
| 18     | ST, Gle, HPY, Rez, Bau: core collapse, hot dense matter, mergers; KWW, Iben                                                                                        |
| 19     | S&S, Mac, Gel, R&W: Bayesian inference, Gaussian processes; NR                                                                                                     |
| 20     | your modules; NR                                                                                                                                                   |

## 5. Ground rules

1. **One test per module** in `tests/`, covering **verification** (analytic limits, convergence, conservation) and **validation** (agreement with observations or published results).
2. **Units:** work internally in a documented unit system (cgs for white dwarfs and atmospheres; $c=G=1$ geometric or nuclear units MeV and fm for neutron-star microphysics and structure), with conversion functions in one `units` module. Never convert twice.
3. **Derive before you code** the items marked _derive_. They become chapters of your book.
4. **Thermodynamic consistency** is a first-class requirement of every EOS you write: pressure, energy density, chemical potentials and entropy must satisfy the Gibbs-Duhem relation, checked numerically.
5. **Cross-check against public codes and tables** (CompOSE, RNS, published EOS) only after your own version works.
6. **Gate questions:** if you can't answer one without notes, reread the module.

## 6. Relationship with Volume 1 and with your other tracks

- Volume 1 (Module 15, white dwarfs, neutron stars and explosions) is a short introduction. This program deepens it. Reuse your Volume 1 `wd` and `ns` code, and your existing TOV solver, as the starting point of Modules 05, 06 and 07.
- Your nuclear and QHD (Walecka) work feeds Modules 08 and 09 directly, and your QFT/QCD track feeds Modules 04 and 11.
- Your Hamiltonian-mechanics and many-body background make Module 02 to 04 a review at graduate level. Use them to push into the harder problems.

## 7. Repository layout for the capstone (working name `compactlite`)

```text
compactlite/
  README.md
  pyproject.toml
  compactlite/
    units.py             # unit systems, conversions, constants
    math/                # root finding, ODE, quadrature, interpolation, tables, AD helpers
    thermo/              # Fermi-Dirac integrals, ideal quantum gases, thermodynamic checks
    plasma/              # OCP, Debye-Hueckel, lattice energies, fits, MC and MD tools
    pairing/ magnetized/ transport/
    eos/                 # wd, nuclear (Skyrme-like), rmf, crust, quark, hybrid, thermal, parametrized
    gr/                  # tov, rotation (Hartle), tides, radial stability
    wd/                  # structure, cooling, composition
    ns/                  # sequences, cooling, pulsar spin-down
    atm/                 # wd and ns atmospheres, spectra, photometry
    rays/                # light bending, pulse profiles
    pulse/               # oscillation modes
    binary/              # timing, post-Keplerian parameters, GW inspiral, bursts
    inference/           # priors, likelihoods, samplers, posterior predictive tools
  tests/
  data/                  # EOS tables, mass tables, catalogues, with SOURCES.md
  notebooks/             # one per module
  notes/                 # derivations, reading_map.md
  solutions/             # problem solutions (for the book)
```

**Language.** Prototype in Python with NumPy and Numba (clear, testable, fast enough for TOV scans of thousands of EOS). Design interfaces so that hot paths can move to C++, Rust or JAX if you wish.

## 8. Capstone preview

Module 20 suggests the theme: **`compactlite`, an EOS-to-observables toolkit with Bayesian inference**, i.e. a framework that builds equations of state from microphysics (white dwarf matter, nuclear matter, crust, hyperons, quarks), solves the relativistic structure, computes observables (masses, radii, tidal deformabilities, cooling curves, spectra, pulse profiles, binary timing) and infers the equation of state from data. Each module delivers one component. Read Module 20 at the start so you design every earlier component with its final role in mind.

## 9. Your topic list mapped to modules

| Topic                                  | Modules                                         |
| -------------------------------------- | ----------------------------------------------- |
| Statistical mechanics (generous)       | 02, 03, 04 (and used in 05, 08, 09, 11, 14, 18) |
| White dwarf structure, composition     | 05                                              |
| General relativity for compact stars   | 06, 07, 12, 13, 16, 17                          |
| Neutron star structure and composition | 07 to 12                                        |
| Atmospheres                            | 15, 16                                          |
| Cooling and thermal evolution          | 14                                              |
| Rotation, magnetic fields, pulsars     | 12                                              |
| Oscillations, tides, GWs               | 13                                              |
| Binaries and accretion                 | 17                                              |
| Formation, hot matter, mergers         | 18                                              |
| Black holes (minimal)                  | only as limits in 06, 07 and 18                 |
| Inference and software                 | 19, 20                                          |

## 10. Minimal paths

See the appendix (`99_`).
