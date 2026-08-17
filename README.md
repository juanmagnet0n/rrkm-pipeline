# RRKM-ME-pipeline

A fully open-source, reproducible pipeline from ab initio electronic
structure to pressure- and temperature-dependent rate constants for a
gas-phase combustion reaction.

**Status:** Planning / early development. See `project_plan.md` for the full
scope and phase breakdown.

## What this is

This repository builds, step by step, the full workflow used in theoretical
combustion kinetics: geometry optimization and frequency calculations,
CCSD(T) single-point energies, and RRKM/master-equation kinetics, applied to
a real (if deliberately small) benchmark reaction: **CH3 + O(3P)**, which
proceeds through a chemically activated CH3O/CH2OH intermediate and branches
into two experimentally characterized product channels, HCHO + H (55 ± 5%)
and CO + H2 + H (45 ± 5%). HCO is treated as a proposed intermediate on the
path to the CO + H2 + H channel, not as a separately validated product with
its own literature branching ratio.

Every stage of the pipeline is version-controlled and documented in the
`notes/` directory, including the tools' assumptions and where they are
expected to break down.

## Why this system

CH3 + O(3P) proceeds through a chemically activated CH3O/CH2OH intermediate
and branches into two experimentally characterized product channels: HCHO +
H (55 ± 5%) and CO + H2 + H (45 ± 5%). It is well-characterized in the
literature, single-reference-dominated at its stationary points (confirmed
via T1 diagnostic before any CCSD(T) work, see
`notes/multireference_diagnostic_check.md`), and has genuine branching
ratios to predict and validate, unlike a single-channel toy system. A
directly relevant theoretical precedent, Xu, Raghunath, and Lin (2015),
characterizes this same intermediate chemistry and serves as the primary
methodological and validation reference for this pipeline.

## Toolchain

This pipeline is built entirely on open-source tools so it can be run by
anyone who clones the repository, without a commercial license:

- **[Psi4](https://psicode.org/)** — DFT geometry optimization/frequencies,
  CCSD(T) single-point energies
- **[MESS](https://github.com/PACChem/MESS)** — master-equation kinetics
  (Georgievskii/Klippenstein), the standard open-source RRKM/ME solver in
  the combustion kinetics community
- Python (matplotlib, numpy) for post-processing and plotting

This is a deliberate reproducibility choice. It does not use the same
toolchain as prior dissertation-era combustion kinetics work (Gaussian,
MOLPRO, MultiWell), and no claim is made that results here are more accurate
than that work — only that this pipeline is fully inspectable and runnable
by anyone.

## Repository structure

```
RRKM-ME-pipeline/
├── notebooks/     step-by-step calculations, one notebook per pipeline stage
├── notes/         technical writeups: methodology, diagnostics, MESS input
│                  walkthroughs, and honest discussion of limitations
├── scripts/       small helper scripts (Psi4 output -> MESS input, etc.)
├── data/          raw output, literature reference values used for validation
└── figures/       rate constant plots, falloff curves, branching ratios
```

## Validation

Results are checked against literature-reported rate constants and branching
ratios for CH3 + O (primary references: an experimental branching-ratio
study reporting HCHO + H at 55 ± 5% and CO + H2 + H at 45 ± 5%, and Xu,
Raghunath, and Lin's 2015 ab initio kinetics study of the same system, *J.
Phys. Chem. A* 2015, 119, 7404–7417) and, where available, Active
Thermochemical Tables (ATcT) reference thermochemistry. Full citations are
maintained in `notes/`, not assumed from memory.

## What this project is not

- Not a novel scientific result — CH3 + O is chosen because it is already
  well characterized, so the point of this repository is pipeline
  transparency, not new chemistry.
- Not a claim of superiority over commercial-tool workflows used elsewhere.
- A companion to, not a replacement for,
  [QC2](https://github.com/juanmagnet0n/QC2), which covers the quantum
  computing side of this skill set (VQE/UCCSD electronic structure
  simulation). This repository covers the classical DFT/CCSD(T)/RRKM-ME
  side.

## Author

Juan F. Alarcón, Ph.D. — Physical Chemistry, Florida International
University. Dissertation work in theoretical combustion kinetics
(RRKM/master-equation theory, DFT, CCSD(T)) applied to resonance-stabilized
free radical oxidation.
