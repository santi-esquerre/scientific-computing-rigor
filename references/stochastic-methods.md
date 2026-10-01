# Stochastic simulation, Monte Carlo, and SDEs

Read for a stochastic numerical claim. Statistical specialists own central inference
methodology; this guidance connects estimator uncertainty, approximation, RNG, and
the simulation contract. Choose checks for the actual estimand.

## Specify the target and distinguish errors

Name the target: a mean, probability, tail, quantile, path functional, distribution,
stationary statistic, or coupled trajectory error. Identify the independent sampling
unit and any dependence from chains, shared environments, resampling, or common
random numbers. Multiple timepoints from one path are not automatically replicates.

Separate approximation/estimator bias, sampling uncertainty, parameter/model
uncertainty, and implementation error. More realizations can reduce sampling noise
without correcting a discretization bias. For an IID finite-variance sample mean,
Var(mean) = Var(X)/N follows by expanding the variance of the sum and cancelling
zero covariances. Correlated samples retain covariance terms; justify any effective
sample size or dependence-aware uncertainty estimator rather than substituting N.

Design resolution and sample-size changes to distinguish these contributions.
Use independent repeated ensembles or justified within-run uncertainty estimates
when sufficient for the estimand. Repeated full simulations are not mandatory when
one run contains adequate independent replicates. One realized trajectory by itself
cannot establish a general stochastic accuracy claim.

For rare events, tails, weighted samples, or heavy-tailed outputs, check whether the
chosen error estimate is informative and its assumptions hold. Zero observed events
is not evidence of zero probability. Route central interval/test-design questions
to statistical capabilities; avoid blanket square-root-rate claims.

## SDE and stochastic integrator comparisons

Identify the equation, initial/boundary treatment, noise structure, and stochastic
interpretation (for example Itô or Stratonovich). Check coefficients and assumptions
required by the claimed method/order, including regularity and moment conditions.
Changing interpretation or noise law can change the model, not just implementation.

Choose the comparison that serves the claim:

- Strong/pathwise error: compare appropriately coupled approximations and reference
  solutions driven by the same underlying noise; for nested Brownian grids, coarse
  increments can be sums of corresponding fine increments. A shared seed alone
  does not establish that coupling if draw order or discretization changes.
- Weak error: compare expectations of the specified test functions/observables with
  sampling uncertainty resolved sufficiently to assess timestep bias. Coupling can
  reduce comparison variance, but identical paths are not intrinsically required.
- Distributional or long-time behavior: choose relevant distributional features,
  transient removal, dependence handling, and observation horizon. Justify the
  relationship of these checks to the target rather than substituting a mean.

Demonstrate reference fidelity and examine competing error floors before fitting
an order. A finite-step reference introduces its own bias. Avoid applying a method's
familiar order outside the assumptions of the supporting theorem.

## RNG and reproducibility contract

Record the generator/algorithm, relevant version, seed or state, stream allocation,
logical sample identifiers, and intended replay scope. Inspect transformations into
required distributions and initialization/restart behavior when they can matter.
Use documented stream-spawning, splitting, or counter-based schemes appropriate to
the library; arbitrary worker-seed arithmetic needs justification.

Distinguish reproducible streams from reproducible floating-point output and from
statistical adequacy. Decide whether decomposition changes should preserve logical
sample streams or only a statistical contract. Check duplicate/overlapping stream
allocation and state reuse across workers, restarts, or batches where plausible.

For paired comparisons, document intended dependence and account for it in the
uncertainty of the difference. For statistical equivalence, choose meaningful
margins and a procedure sensitive enough for the claim. Failure to reject a
difference is not evidence of equivalence. Keep exploratory diagnostics distinct
from a prespecified acceptance procedure, especially after repeated comparisons.

## Inspected reading guidance

Relevant passages inspected 2026-10-01; reopen before transferring a theorem or API
claim. These sources do not validate an arbitrary estimator, SDE, or stream layout.

- [D. J. Higham, An Algorithmic Introduction to Numerical Simulation of Stochastic Differential Equations](https://webhomes.maths.ed.ac.uk/~dhigham/Publications/P42.pdf), SIAM Review 43 (2001), 525–546, DOI 10.1137/S0036144500378302; section 5, especially equations (5.1)–(5.7) and listings 6–7: distinguishes strong and weak tests, coupling, and sampling contamination. Examples and orders have stated assumptions; do not generalize their sample counts or rates.
- [Stan Reference Manual, Posterior Analysis](https://mc-stan.org/docs/reference-manual/analysis.html), “Effective sample size” and “Estimation of effective sample size”: dependence changes Monte Carlo information; ESS is estimated and quantity-dependent. This is MCMC guidance, not a universal diagnostic for all stochastic simulation.
- [NumPy, Parallel random number generation](https://numpy.org/doc/stable/reference/random/parallel.html), “SeedSequence spawning” and “Sequence of integer seeds”: documented stream construction with probabilistic collision safeguards. Verify the installed generator/API and logical stream assignment; this does not promise universal bitwise reproducibility or prove empirical independence.
