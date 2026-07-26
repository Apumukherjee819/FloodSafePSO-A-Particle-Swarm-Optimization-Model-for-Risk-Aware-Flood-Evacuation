# Security Policy

## Supported Versions

Use this section to tell people about which versions of your project are
currently being supported with security updates.

| Version | Supported          |
| ------- | ------------------ |
| 5.1.x   | :white_check_mark: |
| 5.0.x   | :x:                |
| 4.0.x   | :white_check_mark: |
| < 4.0   | :x:                |
## Security and operational-safety notice

FloodSafePSO is a research and educational prototype for risk-aware flood evacuation. It is not a live emergency service, a certified safety system, or a substitute for official disaster-management guidance.

**Do not use this repository to request emergency help or report an active flood event.** Contact local emergency services and authorized disaster-management agencies for urgent assistance.

Security fixes are considered for the latest version on the repository's default branch. Historical forks, exported reports, generated figures, and unmaintained branches may not receive security updates.

## Reporting a vulnerability

Please report security vulnerabilities privately. Do not open a public issue, publish proof-of-concept code, or disclose sensitive details until maintainers have had a reasonable opportunity to investigate and respond.

Use the repository's **Report a vulnerability** option under GitHub's Security tab, if it is enabled. If private reporting is unavailable, contact the repository owner through a private GitHub channel and include `SECURITY` in the subject or first line of the message.

Include as much of the following information as possible:

- A clear description of the issue and its potential impact.
- Affected file names, module names, versions, commits, or configuration.
- Steps to reproduce the issue using non-sensitive sample data.
- Expected and actual behavior.
- Any proof of concept, logs, screenshots, or suggested mitigations.
- Whether the issue could expose data, alter model results, or produce unsafe routing recommendations.

Please do not include API keys, passwords, personal data, exact shelter locations, emergency-contact details, or other sensitive information in a report.

## What to report

Examples of in-scope issues include:

- Exposed credentials, tokens, private keys, or configuration secrets.
- Unsafe file handling, path traversal, insecure deserialization, or arbitrary code execution.
- Dependency vulnerabilities that materially affect project users.
- Data-integrity issues that can silently change flood-risk scores, safe-zone selection, or route outputs.
- Input-validation failures that can crash the model or cause misleading results.
- Route-feasibility defects that recommend impossible graph transitions without clear warning.
- Vulnerabilities in planned web, API, GIS, or data-ingestion components.
- Privacy issues involving personally identifiable information, sensitive location information, or unapproved data disclosure.

## Model integrity and safety reports

For this project, security includes protecting the integrity of model inputs and outputs. Please report issues that could materially alter flood-risk classification, safe-zone ranking, or evacuation-route recommendations.

Examples include:

- Data poisoning or tampering with input datasets.
- Incorrect normalization, feature weighting, or category-boundary handling.
- Invalid graph edges, disconnected routes, or unvalidated destination nodes.
- Incorrect use of real-world road, shelter, or flood data.
- Missing warnings that could cause a prototype output to be mistaken for official evacuation advice.

Model-quality concerns that do not create a security or safety risk, such as ordinary performance improvements or visualization preferences, should be reported through a normal GitHub issue or discussion.

## Disclosure process

Maintainers will aim to:

1. Acknowledge a private report within 7 calendar days.
2. Assess severity, reproducibility, affected versions, and possible safety impact.
3. Work with the reporter on validation and remediation where practical.
4. Release a fix, mitigation, or documented limitation when appropriate.
5. Publish a coordinated disclosure after a fix or mitigation is available, unless public disclosure would create unreasonable risk.

Response times are targets, not guarantees. This is an open-source research project and does not provide a 24/7 security or emergency-response service.

## Data and privacy requirements

Contributors and users must:

- Follow the license, attribution, and access conditions of all datasets.
- Avoid committing raw datasets unless maintainers explicitly approve them.
- Never commit secrets, credentials, private URLs, or local configuration files.
- Remove personal data and sensitive geographic details before sharing examples, logs, screenshots, or figures.
- Use only authorized data sources for real-world roads, shelters, population, and emergency infrastructure.
- Clearly state data provenance, time period, geographic coverage, and preprocessing steps for new data.

## Safe use of project outputs

The current model uses a simplified grid network and does not include validated road accessibility, live flood depth, traffic, bridge status, shelter capacity, or official closure data. Any output must be treated as a prototype analytical result.

Before a route could be considered for operational use, it would require validation against current local conditions by authorized emergency-management personnel. Contributors must not market or document the prototype as a standalone life-safety routing tool.

## Security best practices for contributors

- Keep dependencies updated and pin versions when reproducibility or vulnerability management requires it.
- Validate all external inputs and fail safely on missing, malformed, or out-of-range values.
- Use deterministic random seeds for test fixtures and document experimental seeds.
- Add tests for risk-score bounds, category thresholds, graph-edge validity, and safe-zone termination.
- Store local data and secrets outside version control; use environment variables or ignored configuration files where needed.
- Review generated reports and visualizations to ensure they do not reveal sensitive information.

## Out of scope

The following are generally out of scope unless they directly affect this repository:

- Vulnerabilities in third-party services, Kaggle, GitHub, operating systems, or Python itself.
- Issues requiring physical access to a user's device.
- Social engineering attempts.
- Denial-of-service reports against infrastructure not controlled by this project.
- Theoretical model limitations without a reproducible integrity, security, privacy, or safety impact.

Thank you for helping keep FloodSafePSO reliable, responsible, and safe to study.
