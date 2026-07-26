<!--
Thank you for contributing to FloodSafePSO.

This project is a research and educational prototype. Do not claim that a
model output is operationally safe or suitable for live evacuation use without
documented validation by qualified local authorities.
-->

## Summary

<!-- Explain what changed and why. Keep this understandable to both technical
and non-technical reviewers. -->

## Related issue or discussion

<!-- Use "Closes #123" when applicable. Write "None" if there is no issue. -->

## Change type

<!-- Select all that apply by replacing [ ] with [x]. -->

- [ ] Bug fix
- [ ] New feature
- [ ] Risk-score or preprocessing change
- [ ] Spatial-network or route-feasibility change
- [ ] PSO algorithm or parameter change
- [ ] Safe-zone selection change
- [ ] Visualization or report change
- [ ] Documentation-only change
- [ ] Test or tooling change
- [ ] Dependency or security update

## Technical details

<!-- Describe the approach, relevant files, assumptions, and any behaviour that
reviewers should inspect closely. Include equations or parameter changes when
they affect risk scoring, edge costs, safe-zone selection, or route fitness. -->

## Data and provenance

<!-- Complete this section whenever data, data processing, or derived outputs
change. Do not include datasets, credentials, private locations, or personal
data in the pull request. -->

- Dataset source and version:
- Geographic coverage and time period:
- Number of records used:
- New or changed features:
- Missing-value, outlier, or filtering treatment:
- License and attribution checked: [ ] Yes [ ] Not applicable

## Model and safety impact

<!-- Explain how this change affects risk classification, edge costs, safe-zone
selection, route feasibility, or user interpretation. State "No expected
change" where appropriate. -->

- Expected impact on flood-risk scores:
- Expected impact on safe zones:
- Expected impact on route feasibility:
- New assumptions or limitations:
- Potential negative or unsafe outcomes considered:
- Is the change based on real road, shelter, or live flood data? [ ] Yes [ ] No

## Validation and testing

<!-- List commands, tests, or manual checks actually run. Include the results.
For stochastic PSO changes, do not report only the single best run. -->

### Checks completed

- [ ] Risk scores remain within `0 <= score <= 1`.
- [ ] Risk-category boundary values were tested.
- [ ] Node and edge counts were verified for the configured grid.
- [ ] Every recommended route ends at a valid safe zone.
- [ ] Route transitions use valid graph edges or an explicit route-repair step.
- [ ] Generated figures and reports were reviewed for accurate labels and layout.
- [ ] Relevant existing tests pass.
- [ ] New tests were added or updated where needed.

### Commands and results

```text
Paste commands and concise results here.
```

### Experimental results

<!-- Required for changes that affect PSO behaviour, route quality, risk scores,
or safe-zone selection. Use "Not applicable" for documentation-only changes. -->

| Metric | Baseline | This PR | Notes |
|---|---:|---:|---|
| Dataset records |  |  |  |
| Random seeds / runs |  |  |  |
| Mean best fitness |  |  |  |
| Fitness standard deviation |  |  |  |
| Mean route distance |  |  |  |
| Mean risk exposure |  |  |  |
| Safe-zone arrival rate |  |  |  |
| Invalid route segments |  |  |  |

## Visual changes

<!-- Attach before/after images or report pages when figures, dashboards, or
documentation visuals change. Confirm units, legends, axes, and captions. -->

## Documentation changes

<!-- State whether README.md, CONTRIBUTING.md, SECURITY.md, reports, figure
captions, or data documentation were updated. -->

## Contributor checklist

- [ ] This pull request is focused and has a clear purpose.
- [ ] I used non-sensitive, authorized data only.
- [ ] I did not commit datasets, secrets, private URLs, or personal data.
- [ ] I documented changed parameters, formulas, thresholds, or assumptions.
- [ ] I did not overstate prototype model outputs as real-world evacuation advice.
- [ ] I considered uncertainty, failure cases, and potential safety impact.
- [ ] I updated relevant tests and documentation.
- [ ] I reviewed the diff for unintended changes.

## Reviewer notes

<!-- Optional: identify areas where you would especially value reviewer input. -->
