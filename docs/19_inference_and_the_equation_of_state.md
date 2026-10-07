# Module 19: Statistical inference and the equation of state

**Difficulty:** Medium to hard. **Time:** about 2 weeks.

## Goal

Learn to constrain the dense-matter EOS (and white dwarf properties) from data with honest uncertainties: Bayesian inference, likelihoods for mass measurements, mass-radius posteriors (NICER, X-ray spectra) and tidal deformabilities (GW170817), EOS parametrizations (piecewise polytropes, spectral, sound-speed, Gaussian processes), priors from nuclear theory and QCD, samplers, model comparison and posterior predictive checks. Deliver `inference`.

## Prerequisites

Modules 01 (MCMC basics), 06, 07, 08, 13 and 16.

## Reading

- **S&S, Mac, Gel:** Bayesian probability, likelihoods, priors, MCMC, evidence, model comparison, hierarchical models.
- **R&W:** Gaussian processes (for nonparametric EOS).
- **NR:** optimization and sampling basics.
- Articles on EOS inference (Raithel, Landry, Essick, Greif, Lindblom, Read, and the NICER and LVC collaborations) are the standard sources; use them to validate your results rather than as a primary text.

## Key concepts and equations

**Bayes' theorem.** For parameters $\theta$ and data $d$:

$$p(\theta|d)=\frac{p(d|\theta)\,p(\theta)}{p(d)},\qquad p(d)=\int p(d|\theta)p(\theta)\,d\theta\ (\text{evidence})$$

Model comparison by Bayes factors $B_{12}=p(d|\mathcal M_1)/p(d|\mathcal M_2)$.

**Likelihoods.**
- *Mass measurements:* Gaussian (or the full posterior) on $M$ of each pulsar, requiring $M\le M_{\max}(\theta_{\rm EOS})$.
- *Mass-radius posteriors:* each source $j$ contributes $\int dM\,P_j(M,R(M;\theta))\,\pi(M)$ where $P_j(M,R)$ is the posterior from the pulse-profile or spectral analysis with a prior $\pi_j$ (a kernel density estimate of the published samples), divided by the prior used in the original analysis.
- *Tidal deformability:* the GW likelihood as a function of $(m_1,m_2,\Lambda_1(m_1;\theta),\Lambda_2(m_2;\theta))$, marginalized over the masses with the chirp mass fixed (the posterior is published on $\Lambda_1,\Lambda_2$ or as samples).
- *Nuclear experiments and theory:* constraints on $(S_0,L)$ or on the pure neutron matter EOS at low density (chiral EFT bands).

**EOS parametrizations.**
- *Nuclear-inspired:* $(K_0,S_0,L,\ldots)$ with the schematic EOS of Module 08 or the RMF couplings of Module 09.
- *Piecewise polytropes* (4 parameters: Module 07).
- *Spectral decomposition* (Lindblom): $\Gamma(p)=\exp\left(\sum_k\gamma_k\ln^k(p/p_0)\right)$ with 2 to 4 parameters, smooth and automatically thermodynamically consistent.
- *Speed-of-sound parametrization:* $c_s^2(n)$ as a piecewise linear function between $n_i$ (with a constraint $0<c_s^2\le1$), integrated to give $P(\epsilon)$ (Greif, Tews et al.).
- *Gaussian processes:* a GP prior on $\phi(p)=\ln(c_s^{-2}-1)$ or on $c_s^2(\ln n)$ conditioned on a low-density nuclear model (Landry-Essick); flexible and agnostic.

**Priors.** Uniform in the parameters of the chosen family with hard constraints: causality ($c_s\le c$), thermodynamic stability ($dP/d\epsilon>0$ outside first-order transitions), $M_{\max}\ge2\,M_\odot$ (or the observed largest mass), compatibility with the chiral EFT band up to $\sim1.1n_0$ to $2n_0$, and optionally with pQCD at the TOV end. **The prior matters:** different parametrizations induce different priors on $R_{1.4}$, $\Lambda_{1.4}$ and $M_{\max}$; always show the prior predictive distribution of derived quantities.

**Sampling and evidence.** MCMC (affine-invariant ensemble samplers), nested sampling (also gives the evidence) and importance resampling for fast reweighting by new data. The expensive step is the forward map $\theta\to\{M(R),\Lambda(M)\}$ (a TOV and a tidal solve per EOS); make it fast (Numba, vectorization, precomputed tables) or use emulators.

**Posterior predictive and information gain.** The posterior of $R_{1.4}$, $\Lambda_{1.4}$, $M_{\max}$, $P(2n_0)$ and $c_s^2(n)$; the Kullback-Leibler divergence between prior and posterior to quantify the information gained by each dataset; posterior predictive checks (does the model reproduce the data it was fit to?).

**White dwarf inference.** Likelihoods in $(T_{\rm eff},\log g)$ or photometry plus parallax for mass and age (cooling ages from Module 14), with the mass-radius relation of Module 05 as the forward model; hierarchical modelling of a population (mass distribution, star formation history).

## Hands-on problems

**1. [E] Bayesian warm-up.** Infer a Gaussian mean and variance from synthetic data with conjugate priors, then with MCMC, and compare. Compute the evidence analytically and by nested sampling for a simple problem (a Gaussian likelihood with a uniform prior) and verify they agree.

**2. [E] A single mass measurement.** Given a pulsar mass $M=2.0\pm0.05\,M_\odot$ (Gaussian), compute the posterior on the piecewise polytrope parameters $(\log P_1,\Gamma_1,\Gamma_2,\Gamma_3)$ from the single condition $M_{\max}\ge M$ (a truncated prior). Plot the induced distribution of $R_{1.4}$ and compare with the prior one.

**3. [M] A fast forward model.** Write a vectorized/Numba pipeline that, for a given EOS parameter vector, returns $M_{\max}$, $R(M)$ on a mass grid, $\Lambda(M)$ and checks causality. Benchmark: $\ge10^3$ EOS per second on a laptop (optimize the TOV and tidal solves with fixed-step integrators, precomputed tables of $\epsilon(P)$, and early rejection).

**4. [M] Mock M-R data.** Take a known EOS (for example SLy or a DD2-like RMF set) as the "truth" and generate mock mass-radius measurements for $4$ to $6$ neutron stars with realistic uncertainties ($\sigma_R\sim0.8$ to $1.5$ km, $\sigma_M\sim0.1$ to $0.3\,M_\odot$ from the pulse-profile or burst analysis). Infer the EOS parameters with the piecewise polytrope parametrization and plot the posterior $M$-$R$ band and the posterior of $R_{1.4}$ and $M_{\max}$. Check that the truth is covered by the credible interval in repeated mock realizations (calibration check).

**5. [M] Tidal deformability data.** Add a mock GW likelihood on $\tilde\Lambda$ (or on $(\Lambda_1,\Lambda_2)$ samples) and show how it tightens $R_{1.4}$ and breaks the degeneracy with the mass-radius data; compute the information gain.

**6. [M] Parametrization dependence.** Repeat problem 4 with (a) the spectral parametrization, (b) the piecewise sound-speed parametrization and (c) the schematic nuclear EOS. Plot the prior and posterior of $R_{1.4}$ and $c_s^2(n)$ in each case. Quantify how much the result depends on the prior and on the parametrization (an essential honesty check).

**7. [M] Priors from nuclear theory.** Impose the chiral EFT neutron-matter band up to $1.1n_0$ or $2n_0$ and the nuclear saturation constraints; show how it changes the posterior of $R_{1.4}$ and of the pressure at $2n_0$ and the dependence on the cutoff density.

**8. [H] Gaussian-process EOS.** Implement a GP prior on $c_s^2$ or $\phi(p)$ (use a squared-exponential kernel with hyperparameters), sample EOS realizations, discard those violating causality or stability, compute $M$-$R$ curves and infer the posterior using the mock data of problem 4. Compare with the parametrized results and discuss why the GP gives broader but more agnostic posteriors.

**9. [H] Real data and public posteriors.** Obtain the published posterior samples for the NICER sources and the GW170817 tidal posterior (public data releases; verify the locations and the prior definitions) and reproduce a published-style EOS inference with your pipeline. Report the posterior of $R_{1.4}$, $\Lambda_{1.4}$, $M_{\max}$, $P(2n_0)$ and compare with the literature (it will not match exactly because of different priors and likelihood treatments; list the differences).

**10. [H] Model comparison.** Compare nucleonic, hyperonic and hybrid-star models (Modules 9 and 11) with Bayes factors using nested sampling and the data of problem 9; discuss the sensitivity to the priors on the model parameters and why small Bayes factors should not be interpreted strongly.

**11. [M] White dwarf inference.** Infer the mass and cooling age of a white dwarf from $(T_{\rm eff},\log g)$ or photometry with parallax with your Module 5 and 14 tools, and include an initial-final mass relation prior to estimate the progenitor mass and the total age. For a cluster with several white dwarfs, infer the cluster age hierarchically.

## Software component

`compactlite/inference/`: EOS parametrization classes (piecewise polytropes, spectral, sound-speed, GP), priors with constraint checks, likelihoods (masses, M-R KDEs, $\tilde\Lambda$), samplers (MCMC and nested sampling wrappers), posterior predictive and information-gain tools, a fast forward model.

## Checks

- Conjugate and MCMC posteriors agree; evidence by nested sampling matches the analytic value.
- Forward model speed target met.
- Calibration test: the truth lies in the 68 percent credible interval about 68 percent of the time over many mock realizations.
- Prior and posterior predictive distributions shown for every derived quantity.
- Your real-data posterior reproduces the published $R_{1.4}$ range within the differences explained by prior choices.

## Pitfalls

- Treating the posterior of a particular parametrization as model independent.
- Using an informative prior accidentally via the parametrization boundaries.
- Double counting data (the same pulsar in several analyses).
- Forgetting the Jacobian when changing variables, and dividing the published posteriors by their original priors.

## Gate questions

1. Why is it essential to inspect the prior predictive distribution of $R_{1.4}$?
2. What does a posterior predictive check test that a good fit does not?
3. How do tidal deformability measurements break the degeneracies of mass-radius inference?

## Deliverable

`compactlite/inference/`, `notebooks/19_inference.ipynb`, solutions for problems 1 to 11.
