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
