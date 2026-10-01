# Scientific Computing Rigor

A Codex skill for connecting scientific evidence and theory to numerical methods, implementations, verification, validation, and appropriately bounded scientific conclusions.

It is intended for scientifically meaningful numerical work: PDE and ODE solvers, numerical linear algebra, stochastic simulation, floating-point and parallel implementations, optimization, and scientific ML components. It scales its rigor to the scientific risk and returns to ordinary software-engineering practices for changes with no plausible effect on scientific meaning or numerical results.

## Install

After cloning this repository, run the copy command from the directory containing the cloned `scientific-computing-rigor` folder:

```bash
cp -R scientific-computing-rigor ~/.codex/skills/
```

Then invoke it explicitly with `$scientific-computing-rigor`, or let Codex select it automatically when a task matches its description. The skill has no runtime package dependencies or scripts.

## What it covers

- Build a numerical contract from the intended mathematical problem, assumptions, quantities of interest, and accuracy or equivalence criteria.
- Select proportionate evidence for the model, numerical method, implementation, and scientific claim.
- Distinguish software correctness, numerical verification, scientific/model validation, and interpretation.
- Investigate plausible error sources without assuming they add linearly or treating every discrepancy as a software bug.
- Reuse project evidence and documentation conventions; persist scientific decisions when their rationale would be expensive to reconstruct.
- Work alongside literature, statistics, uncertainty, symbolic mathematics, ML, testing, debugging, and review skills without replacing them.

## Structure

- `SKILL.md` — discovery guidance and the core workflow.
- `references/` — focused guidance for evidence and records, deterministic methods, stochastic methods, arithmetic and parallelism, scientific ML, and behavioral maintenance cases.
- `agents/openai.yaml` — Codex display metadata and implicit invocation policy.

The skill is guidance for scientific reasoning. It does not certify a model or numerical implementation; conclusions remain bounded by the evidence collected for the specific project.

## Contributing

Keep the skill proportional and conditional: add guidance when it addresses a demonstrated scientific reasoning or routing failure. Preserve project-specific evidence and documentation conventions in the project rather than imposing this repository's structure.

## License

See [`LICENSE`](LICENSE).
