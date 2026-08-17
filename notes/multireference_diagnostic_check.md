# Multireference Diagnostic Check: CH3 + O Stationary Points

Status: planned, not yet run.

## Direct answer

(To be filled in once T1 diagnostics are computed for all CH3 + O
stationary points.) Expectation, stated in advance so it can be checked
against rather than assumed after the fact: CH3 + O and its product
channels (CH2O + H, HCO + H2, CO + H2 + H) are expected to be
single-reference-dominated, making CCSD(T) an appropriate level of theory.
This should be confirmed, not assumed, before Phase 3 (CCSD(T) single-point
energies) begins.

## Why this matters

This is the same triage discipline used in the propargyl + O multireference
benchmark note: run T1 (and ideally %TAE[(T)]) diagnostics before trusting a
single-reference method, rather than assuming a system is well-behaved
because it looks simple on paper. If any stationary point on this surface
turns out to have meaningful multireference character, that needs to be
flagged explicitly and either addressed with a multireference method or
noted as a limitation of this pipeline's results.

## Math details

See `propargyl_o_multireference_benchmark.md` (QC2 project) for the T1 and
%TAE[(T)] diagnostic definitions and thresholds. Same methodology applies
here.

## Minimal example

(To be filled in once diagnostics are actually computed.)

## What can go wrong

If T1 values come back elevated for any product channel (particularly any
open-shell or near-degenerate species), that channel's CCSD(T) energies
should not be trusted without further checking, and this should be stated
plainly in the final validation writeup rather than glossed over.

## Questions

- Are all product channels well-behaved, or does one channel (e.g. a
  particular product spin state) show elevated multireference character?
- Does the diagnostic outcome change the choice of DFT functional used for
  Phase 1 geometries?

## References

- Lee, T. J.; Taylor, P. R. A diagnostic for determining the quality of
  single-reference electron correlation methods. Int. J. Quantum Chem.
  Symp. 1989, 23, 199.
- Karton, A.; Rabinovich, E.; Martin, J. M. L.; Ruscic, B. W4 theory for
  computational thermochemistry. J. Chem. Phys. 2006, 125, 144108.
- (Literature CH3 + O rate constant references: to be added once
  identified and confirmed, not assumed from memory.)
