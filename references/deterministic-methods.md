# Deterministic methods

Read the applicable section for PDE/ODE, linear algebra, particle, optimization,
or coupled-method work. These are prompts for selecting evidence, not required
checks for every task. Source notes at the end identify limited inspected support.

## PDE discretizations and coupled approximations

Establish the governing problem, geometry, units/nondimensionalization, boundary
and initial conditions, function space/solution notion, and quantities of interest.
Ask what regularity and stability assumptions the claimed method needs and whether
the actual boundary treatment, coefficients, mesh, and timestep satisfy them.
A change can affect the model, discretization, or both; identify which semantics
are intended. Check well-posedness, constraints, or nullspaces where relevant.

When using consistency and stability to argue convergence, identify the precise
result and its hypotheses for this problem and discretization. Do not transfer a
theorem between linear/nonlinear or smooth/nonsmooth settings without checking its
scope. Observed convergence is separate evidence about the tested implementation.

Choose evidence that separates approximations: spatial and temporal refinement,
linear/nonlinear solve accuracy, quadrature, interpolation, geometry, and coupling.
Hold other contributions small enough to interpret a refinement study, or design a
joint study when they interact. Avoid treating cancellation between errors as accuracy.

Use analytical solutions, manufactured solutions, limiting cases, balance laws,
or a justified independent comparator as appropriate. Manufactured forcing and
boundary data must correspond to the intended equations; assess which code paths
the manufactured case actually exercises. Passing it is not empirical validation.

For an order claim, name the norm/observable and refinement scale. For positive
errors following E(h) approximately C h^p, the derived two-level estimate is
p_obs = log(E(h_coarse)/E(h_fine)) / log(h_coarse/h_fine).
This follows by taking the ratio of the assumed power law; it is conditional on
that model and does not establish the asymptotic regime. Inspect multiple levels
and relevant error floors where feasible. Report uncertainty or inconclusiveness
when limited levels, nonmonotonicity, singularities, or stochastic contamination
make a slope unreliable. An assumed order in extrapolation is not an observed order.

Choose physically correct invariants or balances, including forcing, boundary
fluxes, and intended dissipation. Do not demand conservation of a quantity that the
model exchanges or dissipates. Relate integrated balance and local error to the
scientific quantity rather than trusting a plausible field plot.

## Linear algebra and iterative solvers

Identify the actual operator and preconditioner, including assembly, constraints,
boundary elimination, scaling, and matrix-free actions. Verify required symmetry,
definiteness, compatibility, or nullspace handling using project reasoning. A
symmetric continuum operator does not establish every assembled matrix property;
random probes can expose a violation but do not prove a universal property.

Inspect the library's stopping definition: true, recursive, preconditioned, absolute,
or relative residual; norm and normalization; tolerances and termination status.
Distinguish stagnation, breakdown, and iteration limits from successful accuracy.
When warranted, recompute the residual independently of the solver recurrence.

For nonsingular A, b = A x and r = b - A x_hat imply x - x_hat = A^{-1} r.
Thus, in compatible norms, ||x - x_hat|| <= ||A^{-1}|| ||r||.
This direct derivation explains why a small residual alone is insufficient. Check
conditioning/scaling and any estimated bound's assumptions. Singular/constrained
problems require their own solution space and compatible error definition.

Connect termination to the output/error budget. Vary solver tolerance while holding
resolution fixed to test contamination; vary resolution separately to investigate
approximation error. Use backward error or a quantity-specific sensitivity estimate
when suitable. Avoid selecting an arbitrary residual threshold or assuming a
preconditioned residual measures error in the original problem.

## ODEs, particle methods, and long-time behavior

For integration changes, inspect stiffness, stability, smoothness, constraints,
events/discontinuities, adaptive error control, dense output, and coupled solves
only where relevant. Distinguish a local error estimate from global output error.
Check endpoint and event-time quantities when those drive the scientific claim.

For particle methods, identify the limiting target: particle number, smoothing or
interaction scale, cutoff, timestep, ensemble, and boundary treatment may have
different roles. Design probes that isolate relevant interaction approximations,
neighbor updates, interpolation/deposition, self-interaction, and balance defects.
Do not assume particle count alone defines the required refinement limit.

For long-time or sensitive dynamics, specify a meaningful time horizon and target
observable before selecting trajectory, invariant, or statistical comparisons.
Divergence alone neither proves a bug nor excuses one. Justify any replacement of
trajectory accuracy with an ensemble or long-time observable contract.

## Optimization, inverse problems, and differentiation

Specify the objective, constraints, units/scaling, derivatives, and role of the
computed optimum. Inspect feasibility and stationarity under relevant assumptions;
a termination flag does not establish global optimality or identifiability.
Treat regularization or altered constraints as changes with scientific consequences.

When derivatives matter, compare directional/adjoint derivatives against a justified
independent check. For finite differences inspect a step-size range: truncation and
roundoff can obscure agreement. Complex-step checks require compatible analyticity
and code operations; do not apply them blindly across nonsmooth branches.
Separate derivatives of a discrete solver from derivatives of a continuous model,
including adaptive iteration and stopping effects when consequential.

Assess sensitivity to initialization, parameters, data, or regularization where it
changes the claimed solution. Route central inference questions to statistical
capabilities. A good fit to calibration data is not independent model validation.

## Inspected reading guidance

Relevant passages inspected 2026-10-01. Reopen for exact claims; none establishes
that this project's assumptions hold. All other prompts above are investigation
guidance, not claims of a general theorem or method-specific convergence rate.

- [NASA/NPARC, Examining Spatial (Grid) Convergence](https://www.grc.nasa.gov/www/wind/valid/tutorial/spatconv.html), sections “Order of Grid Convergence,” “Asymptotic Range of Convergence,” and “Richardson Extrapolation”: supports checking observed behavior and applicability of extrapolation. CFD tutorial context; do not universalize its refinement heuristics or local/global-order statements.
- [Barrett et al., Templates for the Solution of Linear Systems](https://netlib.org/templates/templates.pdf), second edition PDF, sections 2.3.1 and 4.2–4.2.5: solver applicability, stopping, error interpretation, and finite arithmetic. Useful foundational treatment; API behavior and a project's preconditioner require separate checks.
- [SciML, Common Solver Options](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/), “Stepsize Control”: documents local error scaling and absolute/relative tolerances. Verify against the installed solver/version; these controls are not a universal global-error guarantee.

For specialized particle interactions, derivative algorithms, or stability theorems,
retrieve the method's own literature when a material claim requires it; the sources
above are not blanket support for those topics.
