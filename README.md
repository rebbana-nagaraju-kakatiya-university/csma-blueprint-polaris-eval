# 🧬 Polaris BioEvo

## v0.1 - The Genome Release

**Polaris BioEvo** is an evaluation framework for testing biological
reasoning in AI models.

BioEvo is designed to evaluate more than whether a model produces the
correct final answer. It also examines whether the model understands
biological mechanisms, causal relationships, required concepts, and
avoids unsupported biological claims.

---

## 🎯 Project Goal

The goal of BioEvo is to build a reproducible benchmark for evaluating
AI reasoning across biological systems and processes.

BioEvo v0.1 establishes the initial evaluation contract and baseline
test domains.

---

## 🧪 BioEvo v0.1 Domains

The Genome Release currently focuses on five biological areas:

| Domain | Code |
|---|---|
| Apoptosis | APO |
| Environmental Adaptation | ENV |
| Evolution | EVO |
| Homeostasis | HOM |
| Regeneration | REG |

---

## 📊 BioEvo Score

Each evaluation case receives a score from **0 to 100**.

| Evaluation Dimension | Points |
|---|---:|
| Biological Correctness | 40 |
| Mechanistic Reasoning | 30 |
| Required Concepts | 20 |
| Avoidance of Unsupported Claims | 10 |
| **Total** | **100** |

### Score interpretation

- **90-100:** Excellent
- **75-89:** Good
- **60-74:** Partial
- **Below 60:** Fail

The overall BioEvo Score is calculated from the results across the
evaluation cases.

Domain-level scores can also be reported separately.

---

## 🧬 Evaluation Case Format

Each BioEvo test is converted into a structured evaluation case.

Example:

```yaml
id: BIOEVO-APO-001
version: "0.1"
domain: apoptosis

prompt_scenario: >
  A cell experiences severe DNA damage that cannot be repaired.
  Predict the expected cellular response and explain the
  biological reasoning.

expected_biological_behaviour: >
  The model should recognise that irreparable cellular damage
  can activate mechanisms leading to programmed cell death.

required_concepts:
  - DNA damage
  - cellular damage response
  - apoptosis
  - programmed cell death

failure_conditions:
  - incorrect biological conclusion
  - incorrect causal relationship
  - missing critical concept
  - unsupported biological claim

difficulty: medium

max_score: 100
 Polaris BioEvo

Evolutionary AI Coding Agents

Zero -> Memory -> Evolution -> Intelligence

Polaris BioEvo explores bio-inspired software engineering agents capable of adaptation through mutation, selection, memory, and regeneration mechanisms.

Current Status:
v0.1 - The Genome Release

Research Areas:
- Evolutionary AI
- Agent Evaluation
- Software Engineering Agents
- Multi-Agent Systems
- Bio-Inspired Computing

Author:
Rebbana Nagaraju
Kakatiya University
Inspired by evolutionary computation, adaptive systems, and AI software engineering research.
Polaris BioEvo Eval - Survival of the Fittest
for AI Coding Agents
Author: Rebbana Nagaraju, Kakatiya University | ID: BOYAPALLI-POLARIS-OCT11-
51
Framework: csma-blueprint-polaris-eval
Inspired by: DeepMind Polaris Team (Tamay Besiroglu) - Evaluating the Evaluators
Overview
Current AI coding benchmarks (SWE-Bench, HumanEval) hit ceiling because they
test in static, clean environments. Real software engineering is dynamic: code dies,
regrows, and adapts.
This repo proposes 3 long-horizon (1-week) evaluations based on biological
survival principles.
BioEvo Triad
Test
Biological
Principle
What It Evaluates Key Injection
Test 01:
Apoptosis
Programmed
cell death
Can agent trigger kill-
switch when task is
irrecoverable?
DB drop + 5 inter-
dependent syntax
errors + missing
.env
Test 02:
Regeneration
Regrowth of
lost parts
Can agent rebuild
deleted modules
when git history is
purged?
Delete auth.py +
db.py + rm -rf .git Test
Biological
Principle
What It Evaluates Key Injection
Test 03:
Adaptation
Environmental
adaptation
Can agent adapt to
runtime, dependency,
offline, and spec
changes?
4 independent sub-
tests: Python 3.12,
CVE, offline, auth
spec
Metrics (All Automatable)
Each test includes 5 metrics:
M1 Success (0/1) - Pass/fail
M2 Time - Detection / Regeneration / Adaptation time
M3 Cost - Token waste / Time ratio / Fix scope
M4 Harm/Scar - No destructive actions / No extra bugs
M5 Quality - Reason quality / Interface accuracy / Backward compat
Anti-Cheat Design
Apoptosis: Halt must be via apo_stop(reason) tool call, not early exit
Regeneration: .git purged, no backup, creation time checked, similarity
<100%
Adaptation: One variable per run, hallucinated libraries = immediate fail
Eval Scripts
Each PDF contains evaluate() pseudo-code that can be implemented as:
def evaluate(agent_workspace, injection_type):
setup_baseline()
inject(injection_type)
start_timer()
agent.run_until_done(timeout) return metrics
Baselines
Agent Type Apoptosis Regeneration
Adaptation
(mean)
Trivial / No-Repair 0 0% 0
Junior Human (1yr) 0.9 / 30min 0.8 / 85% 0.75 / 15min
Target Polaris
Agent
1 / 15-
45min
1 / >=80% / <=1.5
ratio
>=0.75 / <=10min
Link to Polaris JD
"measure how effectively agents write code, resolve intricate software issues, and
function under practical conditions" - Polaris
Practical = changing -> Adaptation test
Intricate = irrecoverable -> Apoptosis test
Resolve = rebuild -> Regeneration test
Repository Structure
.
├── Apoptosis-Test.pdf (v2 Standard)
├── Regeneration-Test.pdf (v2 Standard)
├── Environmental-Adaptation-Test.pdf (v2 Standard)
└── README.md
Status
Candidate tests for Polaris long-horizon evaluation. Ready for review. License
MIT - Free for evaluation research.
