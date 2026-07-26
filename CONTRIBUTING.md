# Contributing to FloodSafePSO

Thank you for contributing to **FloodSafePSO**, a research and educational prototype for risk-aware flood evacuation using Particle Swarm Optimization (PSO). Contributions that improve analytical correctness, reproducibility, clarity, accessibility, testing, and safety are especially welcome.

## Scope and safety

FloodSafePSO is not a live emergency-routing service. Do not describe any model output as operationally safe, field validated, or suitable for evacuation use unless the relevant evidence is included and independently reviewed by qualified local authorities.

When contributing, please:

- Treat model outputs as decision-support research results, not emergency instructions.
- State assumptions, uncertainty, data coverage, and known limitations clearly.
- Do not add personal, sensitive, or personally identifiable data to the repository.
- Do not publish exact shelter locations, vulnerable-person locations, or other sensitive emergency information without explicit authorization.
- Preserve the distinction between simulated grid movement and real road-network routing.

## Ways to contribute

You can help by contributing one or more of the following:

- Bug fixes and reliability improvements.
- Unit or integration tests for scoring, network construction, and PSO logic.
- Documentation improvements, diagrams, examples, or reproducibility guides.
- Better visualizations and accessible figure descriptions.
- Evaluation methods, baselines, and repeated-run statistical analysis.
- GIS, road-network, shelter-capacity, traffic, or real-time data integrations.
- Improvements to route feasibility, including valid-edge enforcement or route-repair logic.

Before beginning a substantial feature, open an issue describing the problem, proposed approach, data needed, and expected evaluation method. This reduces duplicated work and helps maintain the project's safety standards.

## Development setup

### 1. Fork and clone

Fork the repository on GitHub, then clone your fork:

```bash
git clone https://github.com/<your-username>/FloodSafePSO.git
cd FloodSafePSO
```

Add the upstream remote if you want to keep your fork synchronized:

```bash
git remote add upstream https://github.com/<organization-or-owner>/FloodSafePSO.git
```

### 2. Create an isolated Python environment

```bash
python -m venv .venv
```

Activate it:

```bash
# Windows PowerShell
.venv\Scripts\Activate.ps1

# macOS or Linux
source .venv/bin/activate
```

Install the currently required packages:

```bash
pip install pandas numpy matplotlib scipy scikit-learn
```

If dependency management is introduced later, use the repository's declared dependency file instead of installing packages manually.

### 3. Obtain data responsibly

The project documentation references the Kaggle **Flood Risk in India** dataset:

- https://www.kaggle.com/datasets/s3programmer/flood-risk-in-india

Follow the dataset's license and attribution terms. Do not commit downloaded datasets, credentials, API keys, or unlicensed derived data unless the repository maintainers have explicitly approved doing so. Use a local path or ignored data directory for large input files.

### 4. Run the model

Place the approved input CSV in a local data directory, configure the input path, and run:

```bash
python Advanced_PSO_Evacuation_Model_3D.py
```

The current prototype is expected to create flood-risk, evacuation-network, analytical-dashboard, and optimal-route figures.

## Branch and commit workflow

1. Create a focused branch from the current default branch.

   ```bash
   git checkout -b feature/<short-description>
   ```

2. Keep one issue or purpose per pull request whenever practical.
3. Make small, reviewable commits with imperative messages, for example:

   ```text
   Add route-edge feasibility validation
   Fix risk-score boundary classification
   Document safe-zone clustering assumptions
   ```

4. Rebase or merge the current default branch before requesting review, according to repository policy.

## Code standards

### General Python guidelines

- Use Python type hints for new or substantially modified public functions.
- Give variables and functions descriptive names.
- Keep data processing, network construction, optimization, and visualization concerns separated.
- Avoid hidden global state and hard-coded user-specific file paths.
- Use deterministic seeds for experiments when reproducibility matters, and document the seed.
- Add docstrings to classes and non-trivial functions.
- Prefer explicit validation and informative error messages over silent fallback behavior.
- Do not suppress exceptions that could lead to an unsafe or misleading route result.

### Modelling guidelines

- Clearly document all changes to feature weights, risk thresholds, edge penalties, PSO parameters, or safe-zone criteria.
- Do not claim a causal relationship from a correlation analysis alone.
- Keep units explicit: rainfall in millimetres, discharge in cubic metres per second, water level and elevation in metres, and coordinates in the stated geographic system.
- Distinguish model fitness from real-world safety, accuracy, or evacuation success.
- Preserve route feasibility: a recommended route must use valid graph edges or explicitly apply and report a route-repair procedure.

### Documentation guidelines

- Update `README.md` when setup, inputs, outputs, or user-facing behavior changes.
- Use plain language when describing results for non-technical readers.
- Add captions and alt text for figures where supported.
- State data provenance and licensing for every new dataset.
- Use `code formatting` for file names, commands, parameters, and variable names.

## Testing expectations

Every contribution should be tested in proportion to its impact. At minimum, run the relevant tests or manual checks before opening a pull request.

### Required checks for changes to risk scoring

- Confirm all computed risk scores satisfy `0 <= score <= 1`.
- Test boundary values for low, medium, and high-risk categories.
- Verify that missing or invalid inputs are handled explicitly.
- Include a small deterministic fixture with expected risk-score values where possible.

### Required checks for changes to network construction

- Verify the expected node and edge counts for the configured grid.
- Confirm edges link only intended neighboring nodes.
- Test that edge cost increases when risk increases while distance remains constant.
- Verify that node attributes are correctly aggregated from input observations.

### Required checks for PSO changes

- Confirm every final route terminates at a valid safe zone.
- Verify route nodes are valid and each route transition is feasible or explicitly repaired.
- Run the optimizer with a fixed seed for reproducible regression testing.
- For performance claims, run repeated experiments across multiple seeds and report mean, standard deviation, and sample size.
- Compare new approaches with a stated baseline, such as the current configuration, Dijkstra, or A* using comparable constraints.

### Required checks for visualizations and reports

- Ensure axes, units, legends, titles, and category labels are accurate.
- Confirm visual colors do not carry meaning without labels or another accessible cue.
- Verify that generated figures do not crop labels or overlap content.
- Do not present simulated grid routes as real road-level directions.

## Reporting experimental results

When a pull request changes model behavior or performance, include:

- Dataset version or source and any preprocessing changes.
- Number of records and relevant data split or sampling details.
- PSO parameters: swarm size, iteration count, inertia weight, cognitive coefficient, social coefficient, and random seeds.
- Mean, standard deviation, minimum, and maximum across repeated runs when applicable.
- Route fitness, travel cost, risk exposure, route length, and safe-zone arrival rate.
- A description of the baseline and whether conditions were comparable.
- Limitations and potential negative effects of the change.

Do not report a single best run as evidence of general superiority.

## Pull request checklist

Before submitting a pull request, confirm the following:

- [ ] The change has a clear purpose and is limited in scope.
- [ ] Relevant tests or validation checks have been run.
- [ ] New or changed behavior is documented.
- [ ] Data sources, licensing, and attribution requirements are respected.
- [ ] No large datasets, secrets, or private information are included.
- [ ] Visual outputs are labeled correctly and are accessible.
- [ ] Risk, routing, and safe-zone assumptions are stated clearly.
- [ ] Claims are supported by evidence and do not overstate model capability.
- [ ] The pull request explains limitations and follow-up work, if applicable.

## Issue reporting

For bugs, include:

- A concise description of the issue.
- Steps to reproduce it.
- Expected and actual behavior.
- Python version, operating system, and package versions.
- A small non-sensitive example input when possible.
- Screenshots or logs with sensitive details removed.

For feature requests, include the problem being solved, expected benefits, data requirements, safety implications, and a proposed validation plan.

## Community expectations

Be respectful, constructive, and evidence-based. Welcome contributors with different levels of experience and different perspectives. Focus review comments on the work, explain the reasoning behind requested changes, and assume good intent.

## Questions

If you are unsure whether an idea is appropriate for this project, open a discussion or issue before investing substantial effort. Questions about data licensing, model validity, emergency-routing safety, or deployment readiness should be raised early.
