# Agentic Systems Delivery — Confluence Structure + RAID Operating Model (Single Source of Truth)

> **Intent:** Standardise documentation, lifecycle milestones, and dependency management for an agentic systems delivery team that **builds the system** but depends on **Infra (hosting/ops)**, **Data (access/pipelines/quality)**, and a **Business SME/PO**.
>
> **Core principle:** **RAID is the single source of truth** for Risks, Assumptions, Issues **and Dependencies**. Any “dependency register” is a *view* of the RAID dependency table (no duplication).

---

## 1) Space structure (one-time setup)

Create one Confluence Space: **Agentic Systems Delivery**

### 1.1 Space Home
- **Team Operating Model**
  - Roles & Responsibilities (cadence + escalation)
  - Working Agreements (DoR/DoD, comms)
  - Tooling links (Jira boards, repos, dashboards)
- **Delivery Playbook**
  - Lifecycle & Gates (Discovery Exit, Definition Gate, ORR)
  - Stage Checklists (copy/paste checklists below)
  - Estimation method (ranges + confidence + assumptions)
- **Templates Library** *(copy-from pages)*
  - Initiative Home (PID-lite)
  - Requirements & Guardrails
  - RAID (with hygiene rules)
  - Dependencies (View) *(excerpt include)*
  - Milestones & Timeboxes
  - UAT
  - ORR / Prod Readiness
  - Decisions & Change Log
  - Weekly Dependency Linkage notes
- **Active Initiatives (Roll-up)**
  - Page Properties Report (auto summary of initiative Home pages)
- **Archive**

---

## 2) Naming conventions & labels (mandatory)

### 2.1 Page naming
- **INIT — <Initiative Name> — Home**
- **INIT — <Initiative Name> — Requirements & Guardrails**
- **INIT — <Initiative Name> — RAID**
- **INIT — <Initiative Name> — Dependencies (View)**
- **INIT — <Initiative Name> — Milestones & Timeboxes**
- **INIT — <Initiative Name> — UAT**
- **INIT — <Initiative Name> — ORR / Prod Readiness**
- **INIT — <Initiative Name> — Decisions & Change Log**
- **Dependency Linkage — YYYY-MM-DD**

### 2.2 Labels
**Home page label**
- `initiative-home` *(only on the Home page)*

**All pages for an initiative**
- `initiative`

**Stage labels**
- `stage-intake`, `stage-discovery`, `stage-definition`, `stage-build`, `stage-uat`, `stage-orr`, `stage-live`, `stage-bau`

**Content labels**
- `raid`, `dependencies`, `requirements`, `guardrails`, `milestones`, `uat`, `orr`, `decision-log`, `weekly`

---

## 3) “Blueprint pack” — per-initiative page tree

Create an initiative by copying templates, then place child pages under the Home page:

1. **INIT — <Name> — Home** *(labels: `initiative-home`, `initiative`, `stage-…`)*
2. **INIT — <Name> — Requirements & Guardrails** *(labels: `initiative`, `requirements`, `guardrails`)*
3. **INIT — <Name> — RAID** *(labels: `initiative`, `raid`)*
4. **INIT — <Name> — Dependencies (View)** *(labels: `initiative`, `dependencies`)*
5. **INIT — <Name> — Milestones & Timeboxes** *(labels: `initiative`, `milestones`)*
6. **INIT — <Name> — UAT** *(labels: `initiative`, `uat`)*
7. **INIT — <Name> — ORR / Prod Readiness** *(labels: `initiative`, `orr`)*
8. **INIT — <Name> — Decisions & Change Log** *(labels: `initiative`, `decision-log`)*

> **Important:** There is **no separate editable “dependency register”**. Dependencies are edited only in the **RAID** page. The Dependencies (View) page is an **Excerpt Include** of the RAID dependency table.

---

## 4) Active Initiatives roll-up (dashboard)

Create **Active Initiatives (Roll-up)** and insert a **Page Properties Report** filtered by label `initiative-home`.

Recommended columns:
- Status
- Stage
- RAG
- Gate Readiness
- Next Gate
- Next Gate Date
- Target Launch
- Delivery Owner
- Product Owner / SME
- Data Owner
- Infra Owner
- Top Dependency
- Top Risk
- Jira Epic

**Chase-by-exception filters (recommended):**
- `Gate Readiness != Ready` AND `Next Gate Date` within 14 days
- `RAG = Amber/Red`
- Dependencies overdue (in RAID Dependencies table)
- RAID items overdue or missing Owner/Target Date

---

## 5) 3 mandatory gates (lifecycle control)

### Gate 1 — Discovery Exit
**Evidence pack must be READY**
- Requirements & Guardrails *(draft)*: workflow + failure modes + initial guardrails
- RAID: assumptions behind estimate + top risks/issues + critical dependencies
- Dependencies have **owners + milestone dates**
- Estimate recorded as **Best/Likely/Worst** + confidence + assumptions

**Output:** Proceed / Spike / Stop decision + next steps

### Gate 2 — Definition Gate
**Evidence pack must be READY**
- Requirements & Guardrails *(final)* + acceptance criteria
- Data & integration plan captured
- Milestones plan (next 2–3 increments minimum)
- RAID baseline with owners/dates/mitigations
- Test strategy draft + UAT approach

**Output:** This is the first point you can **commit milestone dates**.

### Gate 3 — ORR (Operational / Prod Readiness Review)
**Evidence pack must be READY**
- UAT results + sign-off (or exceptions)
- ORR page complete: monitoring, runbook, rollback, ownership model
- Security/privacy checks complete
- Hypercare plan agreed

**Output:** ORR approval + release plan

---

## 6) Initiative Home template (PID-lite)

> Insert a **Page Properties** macro on the Home page and place the table below inside it.

### 6.1 Page Properties table
| Field | Value |
|---|---|
| Status | Intake / Discovery / Definition / Build / UAT / ORR / Live / BAU |
| Stage | stage-… |
| RAG | Green / Amber / Red |
| Gate Readiness | Not started / In progress / Ready / Blocked |
| Next Gate | Discovery Exit / Definition Gate / ORR |
| Next Gate Date | YYYY-MM-DD |
| Target Launch | YYYY-MM-DD / TBD |
| Delivery Owner | Name |
| Product Owner / SME | Name |
| Tech Lead | Name |
| Data Owner | Team/Name |
| Infra Owner | Team/Name |
| Jira Epic | Link |
| RAID | Link |
| Top Dependency | Short text + owner/date |
| Top Risk | Short text + owner/date |

### 6.2 One-liner & outcome
**Problem:** …  
**Outcome / success looks like:** …

### 6.3 Scope
**In scope:** …  
**Out of scope:** …

### 6.4 Stakeholders (lite)
| Role | Name/Team | Notes |
|---|---|---|
| Business SME/PO |  | Decision-maker |
| Delivery Manager |  | Owns plan + RAID |
| Agentic Eng Team |  | Builds system |
| Infra Team |  | Hosts/operates |
| Data Team |  | Data access/pipelines |
| Security/Privacy |  | Reviews/gates |

### 6.5 Key links
- Jira Epic:
- Repo:
- Requirements & Guardrails:
- RAID:
- Dependencies (View):
- Milestones:
- UAT:
- ORR:
- Decisions & Change Log:

### 6.6 Documents register
| Stage | Title | Link | Owner | Must/Should | Status |
|---|---|---|---|---|---|
| Discovery | Vision / Problem |  |  | Must |  |
| Discovery | Scope |  |  | Must |  |
| All | RAID (incl Dependencies) |  |  | Must | Live |
| Definition | Requirements & Guardrails |  |  | Must |  |
| Definition | HL Design / Agent Behaviours |  |  | Must |  |
| Definition+ | Test Strategy |  |  | Must |  |
| UAT | UAT Evidence |  |  | Should |  |
| ORR | ORR / Prod Readiness |  |  | Must |  |
| Close | Retro / Closeout |  |  | Should |  |

### 6.7 Weekly “what we need”
**This week we need from Infra:** …  
**This week we need from Data:** …  
**This week we need from SME/PO:** …

---

## 7) RAID (single source of truth) — hygiene rules

### 7.1 RAID hygiene rules (Definition of Ready)
**A RAID entry is invalid unless it includes:**
- Clear description (1–2 sentences)
- Impact description (what breaks: milestone/cost/security/quality/outcome)
- Owner (named person/team)
- Target date (next decision point or resolution date)
- Status (Open / In progress / Blocked / Mitigated / Closed)
- Next action (concrete action; not “monitor”)
- Link to scope (milestone, Jira item, or Confluence page)

**Risks must also include:** Probability (H/M/L) + Impact (H/M/L) + mitigation actions  
**Assumptions must also include:** validation method + trigger date (if not true → becomes Issue)  
**Issues must also include:** decision/action required + current blocker  
**Dependencies must also include:** provider/consumer + deliverable definition + milestone date

### 7.2 RAID hygiene rules (Definition of Done)
- Risk: close only when mitigated/retired, with rationale
- Assumption: close only when validated, or converted to Issue/Risk
- Issue: close only when resolved and verified
- Dependency: close only when delivered and confirmed unblocked

### 7.3 RAID operating rules
- Weekly: update **top items only** (top 3–5 by impact)
- Any broken assumption → convert to **Issue** immediately
- Escalate if: High impact + Med/High prob OR overdue OR no owner OR blocks a gate within 14 days
- Updates should be 1–2 lines: what changed + next step

---

## 8) RAID page — tables (copy/paste)

> Create page: **INIT — <Name> — RAID**  
> Labels: `initiative`, `raid`

### 8.1 Risks
| Risk No. | Tech WS Theme | Project PTD Link | Date Identified | Raised By | Risk Description | Impact Description | Probability Score (High, Medium, Low) | Impact Score (High, Medium, Low) | Mitigating Actions | Owner | Target Date | Status | Comments/Update |
|---:|---|---|---|---|---|---|---|---|---|---|---|---|---|

### 8.2 Assumptions
| Assumption No. | Tech WS Theme | Project PTD Link | Date Identified | Assumption Description | Impact if Assumption Incorrect | Action (If Applicable) | Owner | Target Date |
|---:|---|---|---|---|---|---|---|---|

### 8.3 Issues
| Issue No. | Tech WS Theme | Project PTD Link | Date Identified | Raised By | Issue Description | Impact Description | Impact Score (High, Medium, Low) | Decision/Action Required | Owner | Target Date | Status | Comments/Update |
|---:|---|---|---|---|---|---|---|---|---|---|---|---|---|

### 8.4 Dependencies (Single Source of Truth)
| Dependency No. | Tech WS Theme | Project PTD Link | Date Identified | Raised By | Dependency Description | Impacted Project | Dependency Type (Provider, Consumer) | Milestone Date | Owner | Status | Comments/Update |
|---:|---|---|---|---|---|---|---|---:|---|---|---|

---

## 9) Dependencies (View) page — no duplication

**Goal:** Provide a “dependency register experience” without creating a second editable table.

### Setup (recommended)
1. On the RAID page, wrap section **8.4 Dependencies** inside an **Excerpt** macro.
2. Create page: **INIT — <Name> — Dependencies (View)**
3. Insert **Excerpt Include** macro pointing to the RAID page excerpt.

### Optional (if Excerpt not allowed)
- Keep only the RAID Dependencies section.
- Add a link from Home: “Dependencies (View) → RAID (jump to Dependencies section)”

---

## 10) Requirements & Guardrails — template

### 10.1 Workflow
- Primary user:
- User goal:
- Happy path:
- Failure modes:

### 10.2 Functional requirements
| ID | Requirement | Priority | Acceptance criteria |
|---|---|---|---|

### 10.3 Guardrails
| Category | Guardrail | Enforcement | Evidence/test |
|---|---|---|---|
| Safety/Policy |  |  |  |
| Data |  |  |  |
| Security |  |  |  |
| Business |  |  |  |

### 10.4 Human-in-the-loop (HITL)
- When approval required:
- What is auto-executed vs suggested:
- Audit trail required:

### 10.5 Non-functional requirements
| NFR | Target | How measured |
|---|---:|---|
| Latency |  |  |
| Availability |  |  |
| Auditability |  |  |
| Cost |  |  |

---

## 11) Milestones & Timeboxes — template

| Milestone | Time estimate | Definition | Owner | Target date | Notes |
|---|---|---|---|---:|---|
| UX story | 0.5–1 week | Decide workflow to deliver |  |  |  |
| Requirements/guardrails | ~1 week | AC + prod needs + guardrails |  |  |  |
| Data prep | varies | Access + quality + pipelines |  |  |  |
| Build iterations | varies | Implement behaviour + tools |  |  |  |
| UAT readiness | 1–2 weeks | Evidence pack ready |  |  |  |
| UAT | varies | Business testing cycles |  |  |  |
| ORR | 0.5–1 week | Operability & ownership |  |  |  |
| Release | ~2 weeks | Governance dependent |  |  |  |
| Hypercare | 1–2 weeks | Early-life support |  |  |  |
| BAU | ongoing | Maintenance cadence |  |  |  |

---

## 12) Stage checklists (copy/paste)

### 12.1 Intake / Triage
- [ ] Problem statement + outcome
- [ ] SME/PO named + decision-maker confirmed
- [ ] In-scope vs out-of-scope agreed (agentic vs infra vs data)
- [ ] Jira Epic created + INIT Home created
- [ ] Initial dependencies captured in RAID

### 12.2 Discovery (pre-estimate hygiene)
- [ ] Workflow captured (happy path + failure modes)
- [ ] Guardrails drafted
- [ ] RAID started (risks/assumptions/issues/deps)
- [ ] Dependencies have owners + milestone dates
- [ ] Estimate recorded as Best/Likely/Worst + confidence + assumptions
- [ ] Discovery Exit decision recorded

### 12.3 Definition (commitment gate)
- [ ] Requirements & AC finalised
- [ ] Data/integration plan captured (sources, access, contracts)
- [ ] Milestones plan agreed (next increments)
- [ ] RAID baseline owners/dates/mitigations complete
- [ ] Test strategy drafted + UAT approach defined

### 12.4 Build (each increment)
- [ ] Logging/audit events implemented
- [ ] Evaluation evidence captured
- [ ] RAID updated (top items only)
- [ ] Dependencies updated (owner/date/status)

### 12.5 UAT readiness
- [ ] UAT scripts written
- [ ] UAT environment ready (accounts, permissions, test data)
- [ ] Must-fix vs accept list agreed

### 12.6 ORR / Prod readiness
- [ ] Monitoring + alerting implemented
- [ ] Runbook + rollback plan documented and tested
- [ ] Operational ownership confirmed
- [ ] Security/privacy checks complete

### 12.7 Release + hypercare
- [ ] Release notes published
- [ ] Hypercare window agreed (owners + metrics)
- [ ] Post-launch retro completed

---

## 13) Weekly Dependency Linkage notes (template)

**Page:** Dependency Linkage — YYYY-MM-DD *(labels: `weekly`, `dependencies`)*

### Attendees
- Agentic team:
- Data team:
- Infra team:
- SME/PO:

### Top blockers
| Item | Blocking who | Owner | Due date | Next action |
|---|---|---|---:|---|

### Decisions made
| Decision | Rationale | Owner | Date |
|---|---|---|---:|

### Actions
- [ ] Action — Owner — Date
- [ ] Action — Owner — Date

---

## 14) Quick start (10 minutes)
1. Copy **TEMPLATE — Initiative Home** → create **INIT — <Name> — Home**
2. Add label `initiative-home` + stage label
3. Copy the remaining templates as child pages
4. On the Home page, fill Page Properties fields + add links
5. Start RAID with **Assumptions + Dependencies** (owners + dates)
6. The initiative now appears in **Active Initiatives (Roll-up)**

---

## 15) “No evidence, no progress” (team rule)
- No move from **Discovery → Definition** without Discovery Exit pass
- No committed dates until **Definition Gate** pass
- No release until **ORR** pass
- If it’s not in RAID, it doesn’t exist for planning/escalation
