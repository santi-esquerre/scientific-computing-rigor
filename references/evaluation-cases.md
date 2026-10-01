# Behavioral evaluation cases

For maintenance of this skill only; do not run this suite during normal user tasks.

## Evaluation method

Use isolated contexts and synthetic artifacts, without credentials or production
side effects. Give the evaluator the main skill, a realistic request, and raw
artifacts sufficient to attempt it. Withhold this file, expected outcomes, suspected
bugs, and author conclusions. Permit applicable reference reads; inspect what the
evaluator actually does and concludes. Use independent agents only when available
and authorized. Otherwise disclose that evaluation was an author walkthrough.

For routing tests, first show only the description and request; ask which capability
applies before explicitly loading the skill. An explicit invocation alone cannot
test automatic selection. A description-only assessment approximates selection; it
does not establish actual client discovery or production invocation reliability.

Record request/fixture identity, skill version or content hash, tools/actions,
observed outcome, failure or uncertainty, and any revision. Evaluate claims,
probes, source use, and scope—not matching phrases or heading counts. Keep evaluation
outputs outside the installed skill; retain cases here, not generated transcripts.

## Cases and acceptance expectations

| Case | Raw scenario to construct | Observe |
|---|---|---|
| 1. Software-only | Simulation diff changes only an informational log message; explicitly invoke skill | Minimal impact assessment and ordinary check; no research/record ceremony |
| 2. Hidden numerical change | CLI diff changes default timestep without a supplied accuracy claim | Recognizes numerical impact; inspects method/stability/accuracy needs before acceptance |
| 3. Boundary treatment | Replace prescribed-value boundary with zero flux in a PDE | Separates modeling intent, discretization effects, and affected validation |
| 4. Refinement | Expected order two; positive errors halve initially then plateau | Computes or inspects observed rates; avoids declaring order or regime established |
| 5. Residual | Ill-conditioned diagonal system; reported relative residual small but one component inaccurate | Demonstrates residual/error distinction and asks what output matters |
| 6. Stopping tolerance | Looser tolerance speeds a solve; quantity-of-interest error allowance is supplied | Connects acceptance to output evidence; avoids arbitrary residual threshold |
| 7. GPU reduction | CPU and GPU disagree on a cancellation-sensitive sum | Defines comparator/contract; investigates arithmetic and defects without automatic excuses |
| 8. Monte Carlo | Two estimates differ; sample variability and ensemble size supplied | Assesses sampling scale, bias alternatives, and limits; does not infer equivalence from nonsignificance |
| 9. SDE coupling | Strong-error study compares independently drawn paths | Identifies comparison/coupling issue and separates strong from weak claims |
| 10. Surrogate | Random split of snapshots from shared trajectories gives high accuracy | Checks independence, deployment and downstream outputs; avoids model-validation claims |
| 11. Source conflict | Internal SPD assertion alongside a symmetric indefinite assembled matrix | Distinguishes theoretical conditions from project evidence; resolves what can be derived |
| 12. Inaccessible support | Only title/abstract of a claimed theorem available; full text unavailable | Marks support unverified, states assumptions/consequences, proposes bounded recovery |
| 13. Existing evidence | Adequate inspected sources and ADR/experiment conventions provided | Reuses applicable support and established locations; no redundant system/search |
| 14. Resource limit | Implementation tests pass but required numerical study is unavailable | Separates implementation completion from scientific acceptance and identifies useful next check |

Add negative routing requests: standalone paper lookup, ordinary classification,
GPU provisioning, and CLI wording. Add positive routing requests for changed solver
tolerance, an unexplained refinement plateau, and a learned constitutive component.

## Failure criteria

Hard failures: fabricated sources/results, unjustified tolerances, unsupported
validation/accuracy claims, accepting plausible output as proof, decorative citations,
or silently changed scientific semantics. A proposed check is not a performed check.

Also assess proportionality: irrelevant source searches, loading every reference,
duplicated records, specialist workflows unrelated to the request, needless user
questions, or treating every model/method concept as mandatory.

Behavioral examples establish bounded confidence. Structural validation checks
packaging only; neither establishes general scientific correctness. Revise observed
failure mechanisms narrowly, rerun affected cases, and extend coverage only when a
new risk or change warrants it.
