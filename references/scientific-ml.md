# Scientific ML and surrogate components

Read when a learned component participates in a scientific computation or claim.
Ordinary model training/evaluation belongs with available ML/statistical skills;
this file addresses its role in the scientific reasoning chain.

## Identify what is being replaced

Locate the component: constitutive relation, closure, force/flux evaluation, solver,
preconditioner, integrator, inverse map, or postprocessing observable. Identify the
training target and its own model/discretization/measurement errors. Determine
whether substitution changes the model, numerical method, or only an implementation
under an explicitly tested approximation contract.

Specify the intended parameter, geometry, boundary/initial-condition, and time
regimes. Distinguish interpolation claims from extrapolation or new-physics claims.
A reference simulator is a computational target with its own limitations; matching
it is not automatically empirical validation of the target phenomenon.

## Build evidence that survives deployment

Select checks based on the component's downstream role:

- Keep related trajectories, parameter families, meshes, specimens, or source
  simulations together where needed to prevent evaluation leakage. Fit transforms
  and select hyperparameters without using held-out acceptance evidence.
- Assess reference fidelity and training coverage in the deployment regime. Test
  relevant boundary cases and distribution shifts rather than just aggregate fit.
- Examine the quantities that drive scientific use, including tails, local fields,
  derivatives, or rare regimes when average prediction error would hide failure.
- Test relevant conservation, symmetry, positivity, constraints, or boundary behavior;
  a penalty term's presence does not establish satisfaction of the property.
- For feedback/rollout use, compare integrated behavior, error propagation, and
  stability over the relevant horizon. One-step accuracy is a separate claim.
- If uncertainty controls decisions, evaluate its calibration and meaning on the
  relevant regime; training-seed variation alone is not a complete uncertainty model.

Choose an independent comparison suited to the claim: analytical cases, adequately
verified numerical solutions, held-out scientific experiments, or justified physical
limits. Specify the independence and fidelity of the comparator. A PDE residual or
training objective is a diagnostic whose relationship to solution error requires
analysis; assess boundary/initial conditions and out-of-training evaluation too.

For inverse tasks, separate optimization success, identifiability, prior or
regularization assumptions, and data support. A surrogate can change inferred
parameters through approximation error even when forward fit appears acceptable;
probe sensitivity when the intended claim depends on those parameters.

Report implementation/evaluation success, numerical approximation evidence, and
empirical model validation separately. Route central inferential methodology to
statistical capabilities, retaining responsibility for the integrated conclusion.

## Inspected reading guidance

Relevant passages inspected 2026-10-01. These are narrow foundations, not universal
claims about all scientific ML architectures or training methods.

- [Krishnapriyan et al., Characterizing possible failure modes in physics-informed neural networks](https://arxiv.org/html/2109.01050), sections 3–4 and the experiment setup: primary research comparing particular PINN formulations to analytical/reference solutions and investigating optimization difficulty. It motivates independent solution-error checks; its failures and thresholds do not generalize to every PINN or surrogate.
- [NASA/NPARC, Overview of CFD Verification and Validation](https://www.grc.nasa.gov/WWW/wind/valid/tutorial/overview.html), opening verification/validation discussion and “Use of CFD Results”: distinguishes implementation/model assessment and accuracy needs tied to intended use. This conceptual distinction transfers to simulator-trained surrogates; that transfer is reasoning here, not a surrogate-specific finding of the tutorial.

For a claimed architecture guarantee, error bound, or deployed solver behavior,
inspect the original method and its assumptions. An embedded reading pointer or a
physics-informed label is insufficient evidence for a scientific claim.
