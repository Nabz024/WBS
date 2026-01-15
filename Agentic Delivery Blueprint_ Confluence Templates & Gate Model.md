# **Agentic Delivery Blueprint: The "Evidence Pack"**

This blueprint synthesizes standard delivery rigour with the specific necessities of Agentic AI (e.g., Data Contracts, System Cards, and Probabilistic Acceptance). It is designed to be the "Single Source of Truth" that enforces the 3-Gate Model.

## ---

**🏛️ Template 1 — Initiative Home (The System Card)**

Page Title: INIT — \<Agent Name\> — Home  
Labels: initiative-home, agent-system-card, stage-\<current-stage\>  
*(Insert Page Properties macro)*

| Field | Value |
| :---- | :---- |
| **Stage** | \<Discovery / Scaffolding / Training / UAT / Live\> |
| **Delivery Owner** | \<Name\> |
| **SME / "Teacher"** | \<Name\> (Must commit 4h/week) |
| **Data Contract Owner** | \<Team/Name\> |
| **Model Model** | \<e.g., GPT-4o, Claude 3.5 Sonnet\> |
| **Cost Strategy** | \<e.g., Batch API, Provisioned Throughput\> |
| **Target Launch** | \<Date\> |
| **Next Gate Date** | \<Date\> |
| **Repo / Jira** | \<Links\> |

### **1\. Agent Identity & Intent**

* **Problem:** One-line description of the friction (e.g., "Support takes 4 hours to find policy docs").  
* **Agent Persona:** Who is the agent? (e.g., "A senior compliance auditor who is thorough but polite").  
* **Outcome:** Success metric (e.g., "Reduce search time to 2 mins with 90% accuracy").

### **2\. Scope & Capabilities**

* **In Scope (Capabilities):** What questions/actions can it handle?  
* **Out of Scope (Limitations):** Explicit "Will Not Do" list (e.g., "Will not give financial advice," "Will not look up data older than 1 year").

### **3\. Stakeholders (The Federated Model)**

* **SME/Teacher:** Responsible for *grading* agent answers (Adversarial Testing).  
* **Delivery Manager:** Owns the Flow and the "Evidence Pack."  
* **Data Provider:** Owns the API Schema and **Data Contract**.

### **4\. Documents Register (Gate Evidence)**

*(Status: Not Started / Draft / Signed-off)*

| Stage | Title | Link | Required By | Status |
| :---- | :---- | :---- | :---- | :---- |
| **Discovery** | Discovery Checklist | \[Link\] | Gate 1 | 🔴 |
| **Definition** | **Data Contracts** (Schema defs) | \[Link\] | Gate 2 | 🔴 |
| **Definition** | Requirements & Guardrails | \[Link\] | Gate 2 | 🔴 |
| **Build** | **Golden Dataset** (QA Truth) | \[Link\] | Gate 3 | 🔴 |
| **ORR** | Runbook & Failure Modes | \[Link\] | Release | 🔴 |

## ---

**🚧 Template 2 — RAID Log (Agent-Specific)**

Page Title: INIT — \<Name\> — RAID  
Labels: raid, risk-log  
*Pre-populated with common Agentic Risks:*

| Risk Category | Description | Mitigation Strategy | Owner |
| :---- | :---- | :---- | :---- |
| **Hallucination** | Agent invents facts when data is missing. | Implement RAG citations; SME "Red Teaming" required before Gate 3\. | Lead Dev |
| **Dependency Drift** | Data Team changes API schema without notice. | **Data Contract** monitors implemented in CI/CD pipeline (Nightly Schema Check). | Data Lead |
| **Cost Overrun** | High token usage due to complex reasoning loops. | Implement caching and token usage alerts at 50% budget. | DM |
| **SME Fatigue** | SME stops reviewing logs/grading answers. | Gate 2 requirement: SME commits to 4h/week for "teaching". | Sponsor |

## ---

**🔗 Template 3 — Data Contract & Dependency Register**

Page Title: INIT — \<Name\> — Data Contracts  
Labels: dependencies, data-contracts  
*Replaces standard dependency log with actionable "Contracts".*

| Dependency Name | Provider Team | Integration Method | Data Contract Status | Mock Available? | Critical Date |
| :---- | :---- | :---- | :---- | :---- | :---- |
| Customer\_API | Data Team A | REST API | 🟢 Signed (Schema Locked) | ✅ Yes | \<Date\> |
| Policy\_PDFs | Knowledge Team | SharePoint | 🟡 Draft (Unstructured) | ❌ No | \<Date\> |

* **Contract Status:** Green \= Schema defined & tests passing. Red \= No schema agreement.  
* **Mock Available:** Critical for the "Scaffolding" phase. If No, the Delivery team is blocked by the Data Team.

## ---

**🛡️ Template 4 — Requirements & Guardrails (The System Prompt)**

Page Title: INIT — \<Name\> — Requirements  
Labels: requirements, prompts

### **1\. Workflow & Hops**

* **Cognitive Hops:** How many steps must the agent take? (e.g., "Plan \-\> Search \-\> Read \-\> Compare \-\> Answer" \= 4 hops). *More hops \= higher fail rate.*  
* **Happy Path:** (The ideal interaction).

### **2\. Tool Definitions (MCP)**

* *List the specific tools the agent is allowed to use.*  
  * tool\_get\_balance(user\_id): Read-only.  
  * tool\_update\_address(user\_id): **Requires Human-in-the-Loop (HITL) approval.**

### **3\. Guardrails (Safety & Policy)**

* **Topic Guardrails:** "Refuse to discuss competitors."  
* **Pll Handling:** "Mask all credit card numbers before sending to LLM."  
* **Tone:** "Professional, concise, no emojis."

### **4\. The "Golden Dataset" (Requirement for Build)**

* Link to the spreadsheet of 50+ Question/Answer pairs that the SME has verified as "Truth". *The agent cannot pass UAT without this.*

## ---

**🚦 Template 5 — Lifecycle & Gates (The 3-Gate Model)**

Page Title: Delivery Flow — \<Name\>  
Labels: lifecycle, gates

### **Gate 1: Discovery Exit (Feasibility)**

**Purpose:** Verify problem suitability and SME commitment.

* \[ \] **Ambiguity Check:** Is the problem probabilistic? (If deterministic, Stop).  
* \[ \] **SME "Teacher" Contract:** SME has agreed to grade logs weekly.  
* \[ \] **Dependency Scan:** Are Data APIs documented/accessible?  
* \[ \] **Estimates:** Provided as "Complexity Buckets" (Retrieval vs. Reasoning), not hours.

### **Gate 2: Definition (Scaffolding Readiness)**

**Purpose:** Lock the contracts before building logic.

* \[ \] **Data Contracts Signed:** Schemas agreed with Data Team.  
* \[ \] **Mocks Built:** Delivery team can work independently of Data Team outages.  
* \[ \] **System Card Drafted:** Capabilities and Limitations agreed.  
* \[ \] **Guardrails Defined:** Safety/PII rules documented.

### **Gate 3: ORR (Operational Readiness)**

**Purpose:** Verify behavior, not just code.

* \[ \] **Golden Dataset Pass Rate:** Agent achieves \>90% accuracy on the Golden Set.  
* \[ \] **Red Team Sign-off:** SME has tried to "break" the agent and failed.  
* \[ \] **Cost/Token Monitor:** Alerts are live.  
* \[ \] **Runbook:** Includes "Kill Switch" instructions if agent goes rogue.

## ---

**✅ Template 7 — Checklists (Action Items)**

**Page Title:** INIT — \<Name\> — Stage Checklists

**Intake / Triage**

* \[ \] SME named & committed to "Teacher" role.  
* \[ \] Problem classified (Retrieval vs. Agentic Workflow).

**Discovery (Pre-Estimate)**

* \[ \] "Data Contract" conversation started with Data Team.  
* \[ \] Tooling feasibility check (Can we actually call that API?).

**Build (Iterative)**

* \[ \] **Prompt Versioning:** System prompt is versioned in repo.  
* \[ \] **Eval Pipeline:** Running nightly against Golden Dataset.  
* \[ \] **Mock Mode:** Dev environment runs against mocks, not live production data.

**UAT / Release**

* \[ \] **Adversarial Testing:** SME tested for hallucination/jailbreaks.  
* \[ \] **Feedback Loop:** "Thumbs Up/Down" logging is implemented.

## ---

**📝 Template 8 — Meeting Notes: Dependency Linkage**

Page Title: Dependency Linkage — \<YYYY-MM-DD\>  
Labels: weekly-sync  
**Focus:** Reviewing the **Data Contracts**.

**Top Blockers (Data/Infra)**

| Dependency | Contract Status | Is Mock Working? | Impact on Agent | Owner |
| :---- | :---- | :---- | :---- | :---- |
| API\_X | 🔴 Schema Changed | ❌ No | Agent failing on "User Lookup" | \<Name\> |

**Decisions Log**

* *Decision:* "Accepted risk of 5% hallucination rate for non-critical queries."  
* *Decision:* "Data Team B to rollback API change by Tuesday."