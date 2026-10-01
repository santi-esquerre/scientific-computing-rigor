---
name: scientific-computing-rigor
description: Establish scientific and numerical rigor when designing, changing, assessing, or interpreting simulation and numerical software, including solvers, discretizations, stochastic methods, precision or parallelization changes, and scientific surrogates. Connect assumptions and theory to numerical contracts, verification evidence, and bounded conclusions. Excludes ordinary software-only changes and standalone literature, statistics, or ML tasks without a scientific-computation question.
---

# Scientific Computing Rigor

Connect evidence → theory → model → numerical method → implementation →
verification → validation → interpretation. Own the connections; use available
specialists for their capabilities without importing an unrelated workflow.

Ask: **What mathematical and numerical properties matter for this claim, and
what evidence would establish them in this project?**

## Decide whether scientific reasoning is needed

Activate for numerical semantics or scientific conclusions: a new discretization,
solver tolerance, simulation discrepancy, precision change, parallel reduction,
stochastic integrator, or surrogate inside a scientific computation.

Judge effects, not filenames or keywords. A CLI default changing the timestep is
numerically meaningful; logging text in a simulation usually is not. Standalone
literature retrieval, ordinary classification, and GPU provisioning belong with
those capabilities unless a numerical/scientific claim is also at stake.

If explicitly invoked for software-only work, briefly assess impact and continue
with ordinary engineering practices. Do not manufacture research or science notes.

Use these categories internally; mixed tasks can involve several:

| Change | Emphasis |
|---|---|
| A — Model: equations, constitutive assumptions, boundary/initial conditions, scientific assumptions | Theoretical basis, applicability, calibration and validation consequences |
| B — Numerical method: discretization, integrator, solver, preconditioner, interpolation, approximation | Method assumptions and explicit numerical verification |
| C — Implementation: precision, GPU, parallelism, ordering, RNG, library, optimization | Preserve the numerical contract; establish equivalence and performance evidence |
| D — Software only: no plausible effect on scientific meaning or numerical results | Minimal scientific overhead; engineering checks |

Reassess when a supposed C change alters the algorithm or model. Scale effort to
sensitivity, novelty, intended use, consequences of error, and existing evidence.
A category is not a risk score; a precision change can need substantial analysis.

## Discover the project before prescribing a process

Inspect applicable AGENTS.md/CLAUDE.md or equivalent, README/contributor guidance,
relevant code/tests, scientific notes, ADRs, experiments/results, and references.
Search relevant local papers, excerpts, theses, derivations, and BibTeX databases;
read what bears on the claim rather than exhaustively cataloging the repository.

Follow explicit user/project conventions, then established practice, then these
defaults. Conventions determine organization, not scientific truth. Existing code
and local literature are evidence to examine, not automatic authorities.

Identify the task's scientific question, intended use, affected behavior, existing
acceptance evidence, and available resources. Ask only for missing information
that materially changes the contract; make routine choices within existing scope.

## Establish the numerical contract

Use prose or the project's existing structure. Capture relevant elements only:

- Intended mathematical problem and quantities of interest.
- Assumptions, admissible inputs, units/scales, regime, and solution selection.
- Numerical semantics to preserve or intentionally change.
- Accuracy/equivalence criterion, norm or statistic, and tolerance rationale.
- Evidence needed to support the intended claim and consequential failure modes.

Choose acceptance criteria before viewing candidate results when feasible. If an
exploratory finding changes the criterion, disclose the change and its rationale;
keep the original result available rather than tuning thresholds to pass.

Consider well-posedness, conditioning, constraints, coupling, and sensitivity
where they affect the claim. Identify whether reference data were also used for
calibration or method selection. Establish comparator credibility: old code,
higher precision, finer resolution, or another implementation can share defects.

## Ground material reasoning

Distinguish source-backed facts, mathematical derivations, project assumptions,
empirical observations, hypotheses, engineering decisions, and interpretations.
Use explicit wording where confusion is plausible; labels on every sentence are
unnecessary. A theorem's assumptions, their satisfaction by this project, and the
resulting method choice are separate steps requiring their own support.

Inspect local evidence and complement it with independent primary/authoritative
sources. A checked local copy of an external source can provide that independent
basis. Reuse previously inspected support when its proposition, assumptions, and
version still apply; a fresh search is not a ritual requirement.

Research uncertain material assumptions, new methods/regimes, unsupported claims,
contradictory observations, and relevant changed API/library behavior. Knowledge
from memory guides inquiry; verify scientifically material claims when feasible.
Inspect enough source content to support the proposition, including conditions;
titles, abstracts, DOI metadata, and other agents' summaries are not substitutes.

For consequential source claims retain identity/version, a section/page/equation
locator, what it supports, and limits. Embedded references are starting points,
not permission to cite unchecked claims. When evidence conflicts or access fails,
state the unresolved assumption and the consequence if it is false.

Read [evidence and records](references/evidence-and-records.md) when substantial
research, source reconciliation, specialist routing, or durable records are needed.

## Select and run discriminating checks

Treat unexpected output as a scientific/numerical discrepancy before deciding it
is a software bug. Identify plausible error contributions and observations that
would distinguish them. Modeling, discretization, solver, roundoff, interpolation,
sampling, finite ensemble, implementation, parallelism, and interpretation can all
matter. This decomposition does not assume additive or independent errors.

Choose the smallest credible set of derivations, benchmarks, refinement studies,
invariant/balance checks, residual/error analyses, or independent comparisons that
can expose consequential errors. Select relevant checks, not every technique.
Control confounding contributions; investigate coupled effects when changing one
factor at a time would miss them. Quantify errors only as evidence permits.

State why a tolerance measures something meaningful for the quantity of interest.
Check the regime in which expected behavior applies. Plausible plots, falling
residuals, optimizer termination, and test-suite success alone are insufficient
scientific evidence. Empirical agreement supports bounded conclusions, not proof.

Read only the applicable domain guidance:

- [Deterministic methods](references/deterministic-methods.md): PDE/ODE, particle,
  linear algebra, optimization, or coupled deterministic approximations.
- [Stochastic methods](references/stochastic-methods.md): Monte Carlo, SDEs,
  sampling uncertainty, dependent realizations, or RNG methodology.
- [Arithmetic and parallelism](references/arithmetic-and-parallelism.md): precision,
  floating point, CPU/GPU equivalence, distributed algorithms, or speed claims.
- [Scientific ML](references/scientific-ml.md): learned components that replace or
  participate in a scientific model, solver, or scientific claim.

Implement or investigate within the authorized task. Use engineering skills for
engineering work and statistical/symbolic/literature skills when they materially
improve the answer. Discover actual availability and read selected instructions;
there is no required chain of skill invocations or automatic subagent dispatch.
Retain responsibility for integrating specialist results into the contract.

## Assess what the evidence establishes

Keep four questions separate:

| Question | Meaning |
|---|---|
| Software correctness | Does the implementation perform its claimed algorithm? |
| Numerical verification | Does that implemented method approximate the intended mathematical problem as expected? |
| Scientific/model validation | Is the model adequate for the target phenomenon and intended use? |
| Scientific interpretation | What conclusions follow from the combined evidence and its limits? |

A verified or numerically converged calculation does not by itself validate the
model. A model change requires reviewing affected validation consequences, not
repeating every unaffected study. Pure mathematical work may have no empirical
validation claim; say what was verified without inventing a physical application.

Compare actual evidence with the contract. Explain unexpected convergence,
stagnation, or inconclusive comparisons instead of silently relaxing criteria.
Evidence can refute, support within scope, or leave a proposition unresolved.

Stop expanding successful checks unless new changes, failures, or material gaps
justify more work. Research and computation stop when decision-critical evidence
is adequate or available resources cannot resolve it. In the latter case, report
what remains unsupported and the most useful next check; do not claim acceptance.
Useful implementation work may finish while scientific acceptance remains open.

## Persist value and finish clearly

Persist decisions whose rationale/evidence would be expensive to reconstruct.
Reuse existing notes, ADRs, experiment registries, and bibliographies; link rather
than duplicate. Without a suitable convention, start with one task-specific note
under docs/science/ only when valuable. Add decisions/, experiments/, or a BibTeX
file only as real content and project use justify them. Mark stale or superseded
evidence, identifying affected assumptions/configurations. Use the optional
outlines in [evidence and records](references/evidence-and-records.md).

For scientifically meaningful work, finish with three essentials in flexible prose:

1. Supported outcome and the regime/intended use to which it applies.
2. Decisive reasoning/checks and their actual outcomes, distinct from proposed work.
3. Material limits: load-bearing assumptions, unresolved uncertainty, and missing
   evidence that changes how the result may be used.

State validation status when otherwise easy to overinterpret. Express confidence
through evidence and claim boundaries, not invented scores. Surface consequential
decisions and useful next checks; link durable records instead of dumping logs.
For D-only work, omit scientific synthesis unless the impact assessment matters.

For maintenance or behavioral assessment of this skill, read
[evaluation cases](references/evaluation-cases.md); do not run them on user tasks.
