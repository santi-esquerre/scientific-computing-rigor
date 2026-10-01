# Evidence, collaboration, and durable records

Read for substantial research, conflicting evidence, specialist selection, or
persistent scientific decisions. The main skill owns universal evidence rules;
this file supplies practical choices, not another mandatory workflow.

## Resolve a proposition, not a topic

Frame a question that can change the decision: for example, whether the proposed
preconditioner satisfies the solver's assumptions under these boundary conditions.
Map what is already known from code, local derivations, papers, experiments, and
independent literature. An internal note establishes project intent or a proposed
derivation; an external theorem establishes only its own conditional result.

Prefer original method papers, established academic treatments, standards, and
authoritative reports for theory; use official version-matched documentation for
software semantics. Secondary sources can orient a search. Their usefulness does
not make them primary support for a material proposition.

Inspect the proof/statement, method section, equations, or results needed for the
claim. Resolve notation and conditions before transferring a conclusion. A source
can be authoritative on one proposition and stale or inapplicable on another.
Use scholarly retrieval/citation capabilities for substantial searches, full-text
access, or bibliography work. One narrow source check need not become a review.

A useful evidence entry, when a record is warranted, is:

> Proposition; source identity and edition/version; section/page/equation;
> inspected support; assumptions and applicability to this project; remaining gap.

For derivations, retain premises, essential steps, and unresolved conditions.
For observations, retain the experiment/configuration and uncertainty definition.
For decisions, link the premises and tradeoff. For interpretations, specify what
additional assumptions turn computational evidence into a scientific conclusion.

## Reuse, conflict, and stopping

Reuse inspected support when the proposition and applicability remain unchanged.
Recheck API-specific details after relevant version changes; recheck scientific
support after changed assumptions, regime, or contradictory results. Age alone
neither invalidates a theorem nor makes a source current for hardware behavior.

For conflicting sources compare:

- Definitions, norms, discretizations, domains, boundary/initial conditions.
- Exact versus finite arithmetic; theoretical versus implemented algorithm.
- Assumptions, solution regularity, parameter regime, and source version.
- Whether apparently independent reports share data, code, or a source.

Use a derivation or discriminating experiment to test project applicability.
Neither majority vote nor repository precedence settles scientific disagreement.
If unresolved, preserve alternatives and narrow the claim. A working assumption
needs a stated consequence if false; it is not a verified fact.

Stop when remaining uncertainty would not change the scoped decision or claimed
accuracy. Expand the search only to resolve a consequential gap. On access failure,
try a suitable available author/repository version or another authoritative source;
report inaccessible support rather than asserting the literature says nothing.
No fixed citation count, repeated fresh search, or exhaustive survey is required.

## Work with available capabilities

Names below are examples observed in the target harness, not hard dependencies.
Resolve current availability and invocation rules; disk presence alone need not
mean a capability is advertised. Read a skill before using its workflow. If absent,
use available tools within competence and report any consequential limitation.

| Need | Candidate capability | Integration boundary |
|---|---|---|
| Substantial retrieval / reference accuracy | paper-lookup, citation-management | Metadata accuracy does not verify a theory claim |
| Bounded primary-source research | research | Integrate findings; use delegation only when available and authorized |
| Evidence appraisal / rival explanations | scientific-critical-thinking, hypothesis-generation | Choose a framework suited to the numerical/scientific question |
| Measurement uncertainty / dimensions | uncertainty-and-units | Numerical bias is not automatically a metrological uncertainty distribution |
| Statistical inference / experimental allocation | statistical-analysis, statsmodels, experimental-design | Define estimand, dependence, and replication; retain numerical error analysis |
| Exact derivation support | sympy | Check justified domains/assumptions and relation to the implemented operator |
| ML pipelines | scikit-learn or available framework specialist | Integrate downstream scientific accuracy and applicability |
| Tests / debugging / review / architecture | tdd, diagnosing-bugs, code-review, codebase-design | Supply numerical contract; preserve the specialist's engineering responsibility |
| Data inspection / figures / manuscripts | EDA, visualization, scientific-writing capabilities | Numerical task summaries do not automatically require manuscript workflows |
| Substantial workload planning | get-available-resources | Inspect resources only when needed for a concrete workload |

A scientific discrepancy may need theory and error decomposition before a useful
pass/fail signal exists. Establish that signal before a debugging workflow that
requires one. Existing authorized test interfaces can satisfy engineering intake;
do not manufacture a new approval cycle. Do not make issue-tracker setup, clinical
evidence grading, or manuscript approval gates prerequisites of numerical work.
If a chosen specialist has applicable requirements, respect them; do not claim to
have invoked it while silently skipping its requirements. Resolve genuine conflicts
using instruction priority and user scope rather than rewriting other skills.

## Persistence proportional to reconstruction cost

Prefer the project's own scientific notes, ADRs, notebooks, experiment registry,
artifact store, and bibliography. Inspect before writing. A PR or existing decision
record may already preserve the rationale adequately; do not create a duplicate.

Without a useful convention, create docs/science/<task-slug>.md only when there is
valuable rationale/evidence to retain. Keep a single note until multiple durable
decisions or substantial experiment descriptions justify decisions/ or experiments/.
Generated results stay in the established artifact location. Create references.bib
only for a bibliography workflow, not for the existence of a citation.

Persist accepted and rejected consequential choices, justified tolerances, numerical
equivalence contracts, validation scope, and informative failed experiments. A
trivial software edit or exploratory dead end without future value needs no record.

Optional note outline; adapt or omit fields rather than writing empty placeholders:

- Question, intended use, and numerical contract.
- Load-bearing assumptions and relevant mathematical reasoning.
- Decision, alternatives, and rationale.
- Evidence links with claim support and applicability.
- Verification/validation outcomes and material limits.
- Applicable code/configuration and triggers for reconsideration.

For an experiment, additionally retain inputs/data identity, commands or notebook
execution path, code revision (and relevant uncommitted changes), parameters,
relevant software/arithmetic environment, RNG methodology, outputs, and uncertainty
meaning. Include hardware/decomposition only when it can change interpretation.
Preserve failed or inconclusive runs material to the conclusion. Do not duplicate
large raw outputs in Markdown or collect unrelated environment details.

Update applicability when assumptions change. Mark superseded choices and link the
replacement; preserve historical evidence without implying it tests the new state.

## Conversational synthesis versus records

The user always gets supported outcome, decisive evidence, and material limits for
scientific work. Durable records hold reconstructable details, not extra mandatory
sections in chat. Surface validation status when a verified numerical result could
otherwise be mistaken for a validated phenomenon. Scope confidence to the claim.

Synthetic examples, not results obtained by this skill:

> The new reduction meets the agreed output-error contract on the tested input
> regimes. Repeated comparisons and the cancellation benchmark passed; throughput
> improved at the same accuracy target. Cross-device reproducibility was not tested.

> The implementation checks pass, but the refinement data do not establish the
> expected order. Solver-error contamination remains plausible. A tighter-tolerance
> study is the next discriminating check; scientific acceptance remains open.

For a software-only spelling change, an ordinary completion sentence is sufficient.
