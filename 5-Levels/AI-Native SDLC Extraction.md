DIRECTIVE: Analyze the active artifact in your current context through an AI-Native SDLC lens. Do not summarize or describe the environment, source, or artifact itself. Extract only decision-relevant primitives, mechanisms, constraints, and risks mapped to the schema below.

RULES:
- Ground strictly in your active context. Zero extrapolation or external assumptions.
- State missing data explicitly rather than inferring it.
- Output terse, declarative bullets. Zero filler, transitions, or descriptive prose.
- Deduplicate strictly across tiers and buckets.
- If active context contains no relevant signal for a slot, output: `None in scope.`

OUTPUT:

## 1. AI-Native SDLC Extraction
- **L1 (Intern / Junior):** Local execution steps, prompt/context inputs, repo rules, pre-PR verification checks.
- **L2 (Mid / Senior):** Task decomposition, executable specs, test/eval criteria, failure modes, token/latency behavior, review/debt impact.
- **L3 (Staff / Principal):** Architectural primitives, state/context boundaries, tool/permission scopes, CI/CD eval gates, traceability, scale/lock-in limits.
- **L4 (Manager / Director):** Bottleneck shifts (generation vs. verification/QA), defect escape risks, workflow standards, team enablement needs.
- **L5 (VP / Executive):** Unit economics, security/IP/compliance exposure, auditability, adoption posture (`ignore` | `pilot` | `standardize`).

## 2. Context Triage
Anchor every item to a specific claim, metric, or mechanism in scope:
- **Helpful to Know:** Verified facts, patterns, baseline metrics, and concrete trade-offs.
- **Unclear / Needs Clarification:** Undefined terms, unquantified claims, logical gaps, contradictions, and unstated assumptions.
- **Needs Further Assessment:** Unverified assertions, bias, non-production baselines, single-source claims, and operational/security risks requiring external verification or sandbox testing.
