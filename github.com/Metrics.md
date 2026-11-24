
## AI vs. Human Annual GitHub Attribution

### Data Signals to Pull from GitHub

To separate AI from human contributions over a year, extract and correlate these signals via the GitHub REST/GraphQL APIs, Git history, and Copilot Metrics API:

* **Commit Trailers & Messages:** `Co-authored-by:` tags (e.g., Claude, Copilot, Cursor, Devin, Aider), tool-specific prefixes, and "Generated with..." markers.
* **Author & Committer Metadata:** Bot account types (`type: "Bot"`), GitHub App IDs, and known AI agent email/login patterns.
* **Pull Request Metadata:** Source PR authors (catching AI-created PRs that were squash-merged by humans), PR labels, templates, descriptions, and agent-initiated vs. user-initiated PR flags.
* **Diff & Line-Level Telemetry:** Lines of code (LoC) added/deleted/modified, file types touched, and commit-to-commit churn (code rewritten or deleted within days of merging).
* **Code Review Artifacts:** Review comments, requested changes, approval counts, review turnaround times, and AI reviewer bot comments vs. human reviewer comments.
* **CI/CD & Check Runs:** GitHub Actions pass/fail rates, build retries, linter/formatter violations, test coverage deltas, and static analysis alerts (CodeQL, Semgrep, Dependabot).
* **Issue & Release Links:** Linked bug issues, hotfix PRs, revert commits, and release frequency tied back to original PR authorship.
* **GitHub Copilot Metrics API:** Org/team-level suggestion volume, acceptance rates, active users, and LoC per model/language.

### Use Cases (AI vs. Human Annual Analysis)

#### Productivity, Throughput & Flow
* **Authorship Share Tracking:** Measure the percentage of commits, PRs, and LoC authored by humans, AI-assisted humans, and autonomous agents over 12 months.
* **PR Cycle Time Comparison:** Compare time-to-merge for AI-authored PRs versus human-authored PRs to see if faster coding actually speeds up delivery.
* **PR Size Inflation Monitoring:** Track whether AI increases average PR size and creates larger, harder-to-review batches.
* **Bottleneck Shift Detection:** Identify if AI accelerated coding only to create a downstream pileup in code review or QA.
* **Deployment Frequency Correlation:** Correlate spikes in AI contribution volume with changes in release cadence.
* **Off-Hours & Autonomous Velocity:** Measure how much work autonomous agents complete overnight or on weekends compared to human working hours.

#### Code Quality & Maintainability
* **Code Churn & Rework Rate:** Track how often AI-generated lines are modified or deleted within 14–30 days compared to human-written code.
* **Revert & Rollback Attribution:** Measure whether AI-authored PRs trigger a higher rate of `git revert` commits or emergency hotfixes.
* **Bug & Defect Density:** Correlate post-merge bug issues back to whether the originating code was AI-generated or human-written.
* **Linter & Style Drift Tracking:** Compare formatting, naming, and style-rule violation rates between AI and human commits.
* **Cyclomatic Complexity Growth:** Monitor whether AI introduces more verbose, duplicated, or overly complex functions than humans.
* **Error-Handling Gap Analysis:** Track how frequently AI commits omit null checks, edge-case guards, or exception handling compared to human commits.

#### Code Review & Collaboration
* **Review Burden Quantification:** Measure if AI-authored PRs require more review rounds, comments, or reviewer hours per PR.
* **Rubber-Stamping Risk Detection:** Flag large AI-generated PRs that are approved in seconds with zero comments.
* **Human-in-the-Loop Intervention Rate:** Track how many follow-up human commits are required to fix an AI agent's initial PR before it can merge.
* **AI-on-AI Review Effectiveness:** Compare defect catch rates when AI reviewers inspect AI code versus when human reviewers inspect it.
* **Reviewer Burnout Distribution:** Identify senior engineers disproportionately absorbing the review load of high-volume AI output.

#### Security, Risk & Compliance
* **Vulnerability Injection Rate:** Compare CodeQL/SAST/Secret Scanning alerts introduced by AI PRs versus human PRs.
* **Dependency & Supply-Chain Hygiene:** Track whether AI introduces more outdated, unapproved, or vulnerable packages in manifest files.
* **IP & Audit Trail Compliance:** Produce an annual provenance report showing which production modules contain AI-generated code for legal or regulatory audits.
* **Sensitive-Path Guardrail Audits:** Verify whether AI agents are touching restricted directories (auth, payments, infra-as-code) without required human sign-off.
* **License & Attribution Hygiene:** Detect AI-generated blocks that may require extra legal or open-source license review.

#### Architecture & Technical Debt
* **Repo & Domain Heatmap:** Map which repositories, languages, and layers (frontend, backend, tests, docs) AI handles most effectively.
* **Boilerplate vs. Core Logic Split:** Distinguish whether AI is mostly handling scaffolding/migrations/tests while humans own core business logic.
* **Architectural Drift Detection:** Track whether AI commits bypass internal SDKs, shared libraries, or established repo patterns.
* **Tech Debt Paydown Attribution:** Measure how much dead-code removal, dependency upgrades, and refactoring is driven by agents versus humans.
* **Documentation Freshness:** Track whether AI keeps READMEs, API specs, and inline docs updated at a higher rate than humans.

#### Testing & CI/CD Reliability
* **Test-to-Code Ratio Comparison:** Compare how much unit/integration test coverage accompanies AI PRs versus human PRs.
* **CI First-Pass Success Rate:** Measure how often AI PRs pass all GitHub Actions checks on the first push compared to human PRs.
* **Flaky Test Introduction:** Track whether AI-generated tests fail intermittently more often than human-written tests.
* **CI Compute Consumption:** Quantify how many GitHub Actions minutes are consumed by iterative agent retry loops versus human pushes.

#### Cost, ROI & Engineering Enablement
* **Tool & Model Effectiveness Benchmarking:** Compare merge rates, churn, and defect rates across different AI tools (Copilot, Claude Code, Cursor, Devin).
* **AI ROI & Cost-per-Merged-PR:** Pair seat/token spend against actual merged, low-churn AI output rather than raw suggestion volume.
* **Adoption Maturity Curve:** Track how teams progress over the year from basic autocomplete to multi-file edits and autonomous PRs.
* **Onboarding Acceleration:** Measure whether newer engineers ramp up faster on unfamiliar repos when assisted by AI.
* **Skill & Training Gap Identification:** Spot teams with high AI usage but high rework/defect rates to target coaching, better repo context (`AGENTS.md`), or stricter CI gates.


## Top 10 Highest-Signal AI vs. Human GitHub Metrics

### Top 10 Highest-Signal Metrics (AI vs. Human)

| Rank | Metric | What It Measures (AI vs. Human) | Executive Signal | Replaces Vanity Metric |
| :--- | :--- | :--- | :--- | :--- |
| **1** | **30/90-Day Code Survival Rate** | % of merged lines still intact (not rewritten or deleted) 30 and 90 days later. | Separates durable value from high-churn "AI slop" that creates silent rework. | *Lines of Code (LoC) Generated* |
| **2** | **Revert & Hotfix Attribution Rate** | % of merged PRs that trigger a `git revert`, rollback, or emergency hotfix in production. | Measures whether AI speed is degrading production stability. | *Total PRs Merged* |
| **3** | **End-to-End PR Cycle Time (Split)** | Total time from first commit to merge, split into **coding time** vs. **review wait time**. | Shows whether AI accelerated delivery or just shifted the bottleneck to code review. | *Suggestion Acceptance Rate* |
| **4** | **Verification & Review Tax** | Average review rounds, comments, and human fix-up commits required before an AI PR can merge. | Quantifies the hidden human cost of validating and correcting AI output. | *AI Authorship Share (%)* |
| **5** | **Post-Merge Defect Density** | Linked bug issues and P1/P2 incidents traced back to AI-originated vs. human-originated PRs. | Connects AI adoption directly to customer-facing quality and support load. | *CI First-Pass Rate* |
| **6** | **Cost per Merged, Low-Churn PR** | Total AI spend (seats + tokens + extra CI compute) divided by durable, non-reverted AI PRs. | Grounds AI investment in unit economics rather than license utilization. | *Active Seats / DAU* |
| **7** | **Security & Dependency Injection Delta** | New CodeQL/SAST alerts, secrets, and vulnerable packages introduced per 100 AI vs. human PRs. | Quantifies whether AI is expanding the organization's security and compliance exposure. | *Total Security Scans Run* |
| **8** | **Toil-to-Core Capacity Shift** | Share of migrations, boilerplate, tests, and tech-debt paydown handled by AI vs. core product logic by humans. | Proves whether AI is actually freeing senior engineers for higher-value work. | *Raw Prompt / Agent Volume* |
| **9** | **Rubber-Stamp & Reviewer Burnout Rate** | % of large AI PRs approved in seconds with zero comments, plus review concentration on senior engineers. | Surfaces governance breakdown and senior-engineer attrition risk before it hits delivery. | *Average Approvals per PR* |
| **10** | **CI Compute Overhead per Merged PR** | GitHub Actions minutes burned per merged PR (capturing iterative agent retry loops vs. human pushes). | Exposes hidden infrastructure cost inflation caused by autonomous agent loops. | *Total Workflow Runs* |
