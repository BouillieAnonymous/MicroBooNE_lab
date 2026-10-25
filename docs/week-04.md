# Week 4 progress

Snapshot recorded on 25 October 2026. Analysis is in `MainAnalysis_template.ipynb`.
The values below are taken from the saved notebook outputs; this snapshot does
not represent a fresh end-to-end execution.

## Work completed

- Reworked Exercise 7 around weighted MC category distributions in physical
  units. Inspected 18 variables and applied identical selections to MC and data:
  reconstructed energy below 2 GeV; vertex x between 20 and 235 cm, y between
  -100 and 100 cm, z between 20 and 1000 cm; topological score above 0.20.
  Fresh uncut samples prevent cumulative cuts when rerunning the section.
- Added MC/data row cutflows and before/after energy spectra. The selected
  samples contain 88,703 MC rows and 16,895 data rows.
- Implemented Exercise 8 weighted signal/background cutflow metrics, including
  cumulative efficiency, step signal loss and step background rejection.
  Final purity is 86.1%; signal efficiency is 32.4% relative to uncut MC and
  72.4% relative to energy-selected MC. These are weighted-row metrics, not
  verified unique-event efficiencies. Thresholds remain initial choices.
- Retained an optional four-background random-forest diagnostic after selection
  (saved test accuracy 56.7%). Its row-based split is not an independent
  validation of signal selection and may share events between subsets.
- Implemented Exercise 9 MC/data energy spectra with common 0–2 GeV bins,
  physical MC weights, MC statistical uncertainty from the sum of squared
  weights, a 15% systematic contribution, and approximate Poisson data errors.
- Added Exercise 10 survival probabilities and signal-only oscillation weights
  using true energy, with reconstructed-energy plots. Added simple chi-squared
  assertions and an illustrative comparison: chi-squared 14.55 without
  oscillation and 44.37 for delta m-squared = 1 eV^2, sin^2(2 theta) = 0.5,
  using 19 bins and a fixed 15% MC uncertainty. These are example parameters,
  not fitted results; this comparison uses a different uncertainty model from
  the Exercise 9 plot.

## Work still pending

- Execute and validate the prepared closure-sample loading/selection cell.
- Implement the closure-test chi-squared objective and parameter scan/fitting.
- Complete the remaining oscillation inference and associated validation.
- Assess threshold optimisation on an independent validation sample before
  drawing physics conclusions.

The earlier exploratory Ex7 notebook is retained locally outside this repository
in `../analysis_work/MainAnalysis_before_Ex7_revision.ipynb`; it is not part of
this committed snapshot. Input datasets remain excluded from Git.
