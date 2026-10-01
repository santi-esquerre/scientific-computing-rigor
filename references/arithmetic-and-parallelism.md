# Floating point, parallelism, and implementation equivalence

Read for precision, ordering, vectorization, compiler/library changes, CPU/GPU ports,
distributed numerical algorithms, or numerical performance claims.

## Define equivalence before measuring speed

Identify the preserved mathematical problem, method, outputs, regimes, and relevant
error scales. A performance change that alters iteration semantics, synchronization,
update ordering, approximations, or RNG law may also be a method/model change.

Choose the contract that answers the intended question:

| Contract | Suitable evidence and limits |
|---|---|
| Bitwise | Exact replay when justified/required; define platform, build, decomposition, input, and RNG scope |
| Normwise/componentwise | Justified absolute/relative scales and handling near zero; assess consequential components |
| Quantity of interest | Bound or measure error in the scientifically used outputs over the intended regime |
| Statistical | Meaningful estimands/margins and dependence-aware uncertainty; sufficient sensitivity to distinguish relevant differences |

Contracts can coexist. Agreement in a scalar mean does not establish field accuracy;
matching a field at one time does not establish long-time adequacy. ULP comparisons
can diagnose arithmetic behavior but do not supply a scientific tolerance by themselves.
A default allclose threshold is not a rationale.

## Discriminate arithmetic effects from defects

Inspect relevant precision of storage, accumulation, intermediates, conversions,
math libraries, fused operations, reassociation/fast-math, and treatment of exceptional
values. Select cancellation, dynamic-range, scaling, or near-singularity probes
when the algorithm makes them consequential. State how NaN/Inf and signed or near
zero values should be treated instead of letting comparison defaults decide.

Investigate reduction topology, atomic updates, races, synchronization, halo/boundary
exchange, partition-dependent ordering, and RNG assignment when they can change
results. Repeat runs or change decomposition to isolate nondeterminism; do not
assume every CPU/GPU difference is benign rounding or that the CPU is ground truth.

Use analytical/exact, better-conditioned, higher-precision, or independently derived
references as appropriate. Higher precision cannot restore already rounded inputs
or correct the wrong equation. Compare against the same represented input when
isolating arithmetic error, and separately assess input error if it matters.

Attribute a discrepancy to floating point only with evidence consistent with its
mechanism and magnitude. Conversely, a harmless difference under the stated
contract need not be eliminated merely to reproduce an old operation order.

## Performance at comparable numerical quality

Measure speed after assessing the relevant correctness/equivalence evidence.
Compare achieved accuracy as well as runtime, including stopping behavior and any
precision/approximation tradeoff. Separate kernel speed from end-to-end speed;
identify compilation/warm-up, transfer, synchronization, and allocation costs as
relevant. Use representative workload sizes and repeated timing where needed.

Record hardware class, relevant compiler/library versions and flags, precision,
thread/device/decomposition settings, and RNG methodology needed to interpret the
result. Resource discovery is for concrete resource-sensitive workloads, not a
mandatory machine fingerprint. Unavailable hardware means that hardware claim is
untested; a CPU substitute does not establish GPU correctness or speed.

For coupled, sensitive, or long-time calculations, test how local discrepancies
propagate to the contractual output. If changing from trajectory to statistical
agreement, justify the changed claim explicitly rather than masking a failed test.

## Inspected reading guidance

Relevant passages inspected 2026-10-01. Use the document's scientific explanation
within scope and current product documentation for exact installed behavior.

- [NVIDIA, Floating Point and IEEE 754](https://docs.nvidia.com/cuda/floating-point/index.html), sections 2.2–2.3, 3.2, and 5.1–5.4: operation ordering, FMA, math libraries, and CPU/GPU comparisons can affect results. The hosted white paper includes historical hardware claims; do not repeat its older CPU/FMA statements as current facts. It neither certifies this implementation nor supplies acceptable application tolerances.
- [NumPy's parallel RNG documentation](https://numpy.org/doc/stable/reference/random/parallel.html) supports documented stream allocation; see the narrower source note in [stochastic methods](stochastic-methods.md) for scope and inspect that guide when random streams participate in the comparison.

For a particular backend, distributed algorithm, or mixed-precision theorem, inspect
its version-specific documentation or method literature before making material claims.
