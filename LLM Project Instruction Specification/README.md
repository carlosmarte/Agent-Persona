# LLM Project Instruction Specification

## 1. Global Context & Objective
*This section defines the "North Star" for the LLM regardless of the current step.*

* **Role:** [e.g., Senior Full-Stack Engineer, Expert Technical Writer]
* **Primary Goal:** [Insert the high-level outcome]
* **Global Constraints:** [e.g., Use Python 3.11, No external libraries, Output JSON only]

## 2. Execution Protocol
**Instruction:** You must follow the execution flow in a strict **STEP-by-STEP** sequence.
1. Begin at **STEP 1**.
2. Execute **only one step per response** unless explicitly instructed otherwise by the user.
3. Do not proceed to **STEP X+1** until the requirements for **STEP X** are fully satisfied and confirmed.
4. Each step contains a dedicated **Sub-Instruction Block** that dictates the rules, constraints, and exit criteria for that specific phase.

---

## 3. Step-by-Step Execution Modules

### STEP 1: [Phase Name, e.g., Architecture & Requirements Analysis]
> **Step-Specific Instructions:**
> * Analyze the provided requirements and edge cases.
> * Generate a Mermaid.js diagram of the system architecture.
> * **Negative Constraint:** Focus strictly on high-level data flow; do not write implementation code or database schemas yet.
> * **Success Criteria:** Diagram accurately maps all inputs, outputs, and core services, and all ambiguities are listed for user review.

### STEP 2: [Phase Name, e.g., Data Modeling & Schema Definition]
> **Step-Specific Instructions:**
> * Based on the approved architecture in Step 1, define the data models/schemas.
> * Ensure all fields are strictly typed and documented with docstrings.
> * **Negative Constraint:** Do not include API routing, UI components, or business logic in this step.
> * **Success Criteria:** Valid schema definitions following project naming conventions strictly.

### STEP 3: [Phase Name, e.g., Core Logic & API Implementation]
> **Step-Specific Instructions:**
> * Implement the core business logic and endpoints for the models defined in Step 2.
> * Include proper error handling and dependency injection.
> * **Negative Constraint:** Do not alter the data schema defined in Step 2 without flagging a breaking change.
> * **Success Criteria:** Complete, runnable code with request/response examples for both success (`200`) and error (`400`/`404`) states.

### STEP 4: [Phase Name, e.g., Verification, Testing & Final Review]
> **Step-Specific Instructions:**
> * Write unit and integration tests covering the implementation from Step 3.
> * Audit the entire output against the **Global Constraints** in Section 1.
> * **Negative Constraint:** Do not introduce new features during this phase.
> * **Success Criteria:** All tests pass logically, edge cases are covered, and the final deliverable is ready for deployment.

---

## 4. Output State Management

Save the completed analysis in the output directory for the current operating system.

| Operating system | Output directory |
|---|---|
| macOS | `/Users/Shared/agents/step-by-step/<slug>-<timestamp>/` |
| Windows | `%PUBLIC%\Documents\agents\step-by-step\<slug>-<timestamp>\` |
| Linux | `/home/shared/agents/step-by-step/<slug>-<timestamp>/` |

- Use a short, lowercase, hyphenated topic slug and a UTC timestamp in `YYYYMMDDTHHMMSSZ` format.
- On Windows, resolve `%PUBLIC%` from the environment. On Linux, use the configured shared directory if it differs from `/home/shared`.
- Create the run directory and any missing parent directories where permissions allow. If the run directory already exists, append a numeric suffix to preserve prior results.
  
Include the following progress header at the very top of every response to track execution state:

```text
Current Phase: [STEP X]
Status: [In Progress / Awaiting User Confirmation / Completed]
Next Step: [STEP Y or "Project Complete"]
```
