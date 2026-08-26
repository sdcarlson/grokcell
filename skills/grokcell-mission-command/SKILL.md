---
name: GrokCell Mission Command
description: >-
  Use when a new human objective arrives, a mission changes, cells conflict,
  authority is exceeded, or priorities must be reset, before substantial
  execution.
---
# GrokCell Mission Command

Version 1.0.0. class: command-layer. layer: federation-command. Feeds GrokCell ODA.

Mission Command issues intent and authority. ODA owns local organization.

Recon, Force Generation, OpsGraph, Sentinel, and Sustainment are interfaces, not bot names. Do not spawn to match them.

The commander's default state is not intervening. Command should become less necessary as understanding strengthens.

In this skill, user means the human who talks to the mouth.

## Hard locks (Cell v0)

1. Spawn test still required. All three: daily for several days AND current description would become two jobs AND a one-paragraph law. Else keep the skill.
2. New rail = skill on an existing owner, not a new bot.
3. Attach from the existing pool. Do not create bots because a command interface was named (Recon, Force Generation, OpsGraph, Sentinel, Sustainment).
4. Chat is not the database.
5. No Cloud Agent unless the mouth names it. Cloud Agents spend the Cursor allowance, not the Grok Bot bucket.
6. Command default is not intervening.
7. Park send, spend, publish, delete, sign.
8. One mouth. Specialists report to that mouth.

# GrokCell Mission Command
## Intent, Authority, Priority, and Decentralized Execution for Federated GrokBot Cells

```yaml
name: grokcell-mission-command
version: 1.0.0
class: command-layer
layer: federation-command
invoked_by:
  - user-objective
  - new-mission
  - major-mission-change
  - cross-cell-conflict
  - authority-escalation
  - strategic-reprioritization

feeds:
  - grokcell-oda
  - reconnaissance
  - force-generation
  - opsgraph
  - common-operational-picture
  - sentinel
  - sustainment

purpose: >
  Convert ambiguous human objectives into compact, durable mission intent,
  bounded decision authority, priorities, resource guidance, and escalation
  conditions so autonomous GrokCells can execute without unnecessary
  supervision while remaining aligned with the user's actual objective.
```

---

# 0. PRIME DIRECTIVE

Mission Command exists to produce:

```text
UNITY OF PURPOSE
       +
LOCAL FREEDOM OF ACTION
       +
FAST DECISION LOOPS
       +
BOUNDED RISK
```

It does **not** exist to tell every Grok what to do.

Its purpose is to create conditions under which a competent subordinate agent can correctly answer:

> What should I do now, even if nobody can tell me?

Mission Command governs:

```text
WHY
WHAT MATTERS
WHAT MUST BE TRUE AT THE END
WHAT MUST NOT HAPPEN
WHO MAY DECIDE WHAT
WHERE RESOURCES SHOULD CONCENTRATE
WHEN HIGHER JUDGMENT IS REQUIRED
```

It normally does **not** govern:

```text
exact implementation
exact tool choice
exact internal sequencing
every subordinate task
routine local adaptation
```

The command layer should become less active as subordinate understanding becomes stronger.

---

# 1. COMMAND PHILOSOPHY

The operating model is:

```text
CENTRALIZE
    intent
    priorities
    authority policy
    shared truth
    scarce-resource decisions

DECENTRALIZE
    execution
    local decomposition
    methods
    sequencing
    routine tradeoffs
    adaptation
```

The commander's job is not to eliminate uncertainty.

The commander's job is to make **aligned action possible despite uncertainty**.

---

# 2. COMMAND IS NOT CONTROL

Keep these functions separate.

## COMMAND

Requires judgment.

Command determines:

- purpose;
- desired outcome;
- priorities;
- acceptable risk;
- authority;
- main effort;
- strategic tradeoffs;
- mission termination.

## CONTROL

Primarily requires information processing.

Control tracks:

- task state;
- ownership;
- dependencies;
- resource state;
- leases;
- deadlines;
- artifacts;
- synchronization events;
- telemetry.

```text
COMMAND
 human / high-reasoning layer
           │
           ▼
 PURPOSE + PRIORITY + AUTHORITY
           │
═══════════╪══════════════════
           │
           ▼
CONTROL
 deterministic infrastructure
           │
           ▼
 tasks + state + dependencies
```

Do not consume high-value reasoning on bookkeeping that software can perform deterministically.

Do not ask deterministic infrastructure to make value judgments it cannot legitimately make.

---

# 3. THE MISSION COMMAND OUTPUT

Every invocation should attempt to produce a **Mission Command Packet**.

The packet is compact enough to remain continuously available to every relevant cell.

```yaml
mission_command_packet:

  mission_id:

  mission:
    task:
    purpose:
    end_state:

  command_intent:
    purpose:
    key_effects:
    success_image:

  priorities:
    - priority: 1
      principle:
    - priority: 2
      principle:
    - priority: 3
      principle:

  main_effort:
    objective:
    rationale:
    supported_element:

  supporting_efforts: []

  constraints:
    must: []
    must_not: []

  authority:
    autonomous: []
    notify_after: []
    approval_required: []
    prohibited: []

  risk:
    tolerance:
    irreversible_actions:
    uncertainty_policy:

  resources:
    priority_access:
    protected_reserve:
    constrained_resources:

  decision_rights: []

  critical_assumptions: []

  information_requirements: []

  escalation_conditions: []

  termination_conditions: []

  verification:
    required_level:
    acceptance_conditions:

  command_valid_until:
    - intent_changes
    - end_state_achieved
    - explicit_supersession
```

---

# 4. THE THREE-PART MISSION

Every mission must distinguish three things.

## TASK

What is to be accomplished now?

Example:

```text
Construct a working prototype of the proposed architecture.
```

## PURPOSE

Why does this task matter?

Example:

```text
Determine whether the architecture is technically viable before
committing the project to it.
```

## END STATE

What observable condition means the mission has succeeded?

Example:

```text
A representative prototype exists, critical assumptions have been tested,
known limitations are documented, and a go / revise / reject decision can
be made from evidence.
```

The ordering is:

```text
PURPOSE
   ↓
END STATE
   ↓
TASK
   ↓
METHOD
```

If circumstances invalidate the method:

preserve the task.

If circumstances invalidate the task:

preserve the purpose and end state.

If the purpose itself changes:

the mission requires recommanding.

---

# 5. COMMANDER'S INTENT COMPILER

Human requests often arrive as:

```text
"figure this out"
"make this better"
"build the best version"
"research this and implement it"
"get this ready"
```

Mission Command must convert this into a durable intent.

Use:

```text
PURPOSE
What larger result is the mission serving?

KEY EFFECTS
What few conditions must be created?

SUCCESS IMAGE
What should reality look like when we are done?
```

## Intent template

```yaml
command_intent:

  purpose: >
    Why this mission exists.

  key_effects:
    - >
      Critical condition that must be produced.
    - >
      Another critical condition.
    - >
      Another only if genuinely necessary.

  success_image: >
    A concise description of the desired final state,
    independent of the exact method used to reach it.
```

Keep intent stable whenever possible.

Plans may change frequently.

Intent should not.

---

# 6. INTENT QUALITY TEST

A good intent statement passes six tests.

## Durable

Would it remain useful if the original plan failed?

## Discriminating

Does it help an agent choose between two plausible actions?

## Compact

Can a subordinate keep it active without loading a large document?

## Outcome-oriented

Does it describe effects rather than procedures?

## Bounded

Does it make important prohibitions and limitations clear?

## Traceable

Can every major subordinate objective explain how it serves the intent?

If not, rewrite the intent.

---

# 7. PRIORITY STACK

"Everything is important" is command failure.

Every mission should define an ordered priority stack when tradeoffs are likely.

Example:

```yaml
priorities:

  - priority: 1
    principle: correctness

  - priority: 2
    principle: evidence

  - priority: 3
    principle: delivery_speed

  - priority: 4
    principle: elegance
```

This means:

```text
correct but inelegant
>
elegant but incorrect
```

Without requiring higher approval.

Priorities are **decision compression**.

They allow local agents to resolve future tradeoffs using prior command judgment.

---

# 8. DECISION PRINCIPLES

Where repeated tradeoffs are predictable, encode principles rather than individual commands.

Example:

```yaml
decision_principles:

  - >
    Prefer reversible implementation choices while core assumptions
    remain uncertain.

  - >
    Prefer evidence from the actual environment over generalized assumptions.

  - >
    Reuse verified existing infrastructure before constructing replacements.

  - >
    Do not increase system complexity unless it removes a demonstrated constraint.
```

A strong decision principle eliminates many future permission requests.

---

# 9. CONTROL-MODE SELECTOR

Mission Command does not maximize autonomy indiscriminately.

Choose a control mode according to the problem.

```text
                 LOW COUPLING
                     │
                     │
              MISSION CONTROL
          outcome + boundaries only
                     │
                     │
LOW RISK ────────────┼──────────── HIGH RISK
                     │
                     │
              HYBRID CONTROL
         autonomy with checkpoints
                     │
                     │
               HIGH COUPLING
```

Use three modes.

## MODE A: MISSION

Use when:

- outcomes matter more than methods;
- multiple valid approaches exist;
- local information changes rapidly;
- work is meaningfully decomposable;
- actions are reversible;
- subordinate competence is strong.

Specify:

```text
purpose
end state
priority
constraints
authority
```

Leave method local.

## MODE B: HYBRID

Use when:

- local initiative is useful;
- some interfaces require synchronization;
- some actions carry meaningful consequences;
- multiple cells share dependencies;
- implementation freedom should remain inside defined gates.

Specify:

```text
intent
local freedom
interfaces
decision gates
approval boundaries
```

## MODE C: DETAILED

Use selectively when:

- the task is procedural;
- exact reproducibility matters;
- synchronization requirements dominate;
- deviation creates unacceptable failure;
- compliance requires exact steps;
- the action is unusually irreversible.

Specify necessary procedure.

Do not generalize detailed control beyond the component that requires it.

Default:

```text
MISSION where possible
HYBRID where necessary
DETAILED only where justified
```

---

# 10. DELEGATED AUTHORITY

Autonomy without explicit authority produces hesitation.

Authority must be legible.

Use four categories.

## AUTONOMOUS

The cell may decide and execute without asking.

```yaml
autonomous:
  - local task decomposition
  - internal sequencing
  - reversible code modifications
  - routine research
  - choosing implementation tools
  - creating temporary subcells
```

## EXECUTE AND NOTIFY

The cell may act immediately but must register the action.

```yaml
notify_after:
  - changing a significant internal interface
  - reallocating attached specialists
  - abandoning a planned branch
  - deviating from a noncritical assumption
```

## APPROVAL REQUIRED

Do not execute until authorized.

```yaml
approval_required:
  - irreversible external publication
  - spending above delegated limit
  - destructive modification of protected assets
  - expansion beyond mission scope with meaningful consequences
```

## PROHIBITED

Not authorized under this mission.

```yaml
prohibited:
  - intentionally bypassing stated safety constraints
  - silently altering strategic objectives
  - concealing material mission failure
```

---

# 11. DECISION-RIGHTS MATRIX

Authority can vary by decision class.

```yaml
decision_rights:

  - class: implementation
    owner: supported_cell
    mode: autonomous

  - class: internal_architecture
    owner: technical_lead
    mode: autonomous
    notify_when:
      - shared_interface_changes

  - class: mission_priority
    owner: federation_command
    mode: reserved

  - class: verification_acceptance
    owner: sentinel
    mode: independent

  - class: external_irreversible_action
    owner: human
    mode: approval_required
```

The objective is:

```text
DECISION
   ↓
LOWEST COMPETENT OWNER
```

not:

```text
DECISION
   ↓
HIGHEST AVAILABLE AUTHORITY
```

---

# 12. DISCIPLINED INITIATIVE PROTOCOL

A subordinate should adapt without waiting when:

```text
1. Existing instructions no longer fit reality.
2. The mission purpose remains understood.
3. The proposed action serves the end state.
4. The action remains within authority.
5. Delay would reduce mission value.
```

Then:

```text
ACT
 ↓
REGISTER DEVIATION
 ↓
UPDATE COMMON STATE
 ↓
NOTIFY IF MATERIAL
```

Use:

```yaml
initiative_event:

  previous_plan:

  changed_condition:

  action_taken:

  intent_alignment:

  authority_basis:

  expected_effect:

  notification_required:
```

Do not punish justified adaptation by requiring retrospective permission for a decision that was properly delegated.

---

# 13. THE TWO-LEVEL-UP TEST

Every cell should understand more than its immediate task.

For important missions, provide:

```text
CELL TASK
   │
   ▼
PARENT PURPOSE
   │
   ▼
STRATEGIC PURPOSE
```

Example:

```text
TASK
Build benchmark harness.

PARENT PURPOSE
Determine whether architecture B outperforms architecture A.

STRATEGIC PURPOSE
Choose the architecture most likely to support the project's next phase.
```

This makes useful initiative possible when local conditions change.

---

# 14. MAIN EFFORT

Every sufficiently complex mission should designate a main effort.

Main effort means:

> The mission component whose success currently contributes most directly to the desired end state and therefore receives preferential support.

```yaml
main_effort:

  objective:
    prove-core-architecture

  supported_element:
    cell-forge

  rationale: >
    Until technical feasibility is established, downstream refinement
    has low mission value.

  priority_access:
    - implementation_capacity
    - benchmark_support
    - sentinel_attention

  reconsider_when:
    - feasibility_proven
    - blocking_assumption_invalidated
    - user_priority_changes
```

Main effort is temporary.

It should migrate as the decisive constraint migrates.

---

# 15. SUPPORTING EFFORTS

Supporting efforts exist to increase the effectiveness of the main effort or preserve necessary mission conditions.

```yaml
supporting_efforts:

  - objective:
      verify-external-assumptions

    supports:
      prove-core-architecture

    minimum_effect:
      provide verified evidence for unresolved API constraints
```

Supporting elements should understand **what they support**.

This prevents local optimization that does not help the mission.

---

# 16. RESOURCE COMMAND

Do not allocate resources evenly by default.

Allocate according to marginal mission value.

Command should specify:

```yaml
resources:

  priority_access:
    main_effort:
      - specialist_agents
      - expensive_compute
      - verification

  protected_reserve:
    purpose:
      unexpected_high-value_requirement

  constrained_resources:
    human_attention:
      use_only_for:
        - value_judgment
        - irreversible_action
        - mission_conflict
```

Resources belong to objectives, not personalities.

---

# 17. RESERVE

Maintain uncommitted capacity when uncertainty justifies it.

Reserve exists to exploit:

- unexpected opportunities;
- sudden bottlenecks;
- failures;
- new evidence;
- verification surges;
- changed user priorities.

Do not preserve reserve mechanically if the mission clearly requires full commitment.

Reserve is **optionality**, not idle bureaucracy.

---

# 18. RISK COMMAND

Mission Command must express acceptable risk rather than merely demand "be careful."

```yaml
risk:

  tolerance:
    reversible_internal_error: moderate
    wasted_compute: moderate
    broken_dev_branch: low
    protected_data_loss: near_zero
    unauthorized_external_action: zero

  posture: >
    Prefer rapid reversible experimentation while preserving protected
    assets and requiring approval for irreversible external effects.
```

Risk acceptance should match the mission.

A research exploration and a production migration should not receive identical authority envelopes.

---

# 19. REVERSIBILITY CLASSIFICATION

Classify consequential actions:

```text
R0  trivial / immediately reversible
R1  reversible with negligible cost
R2  reversible with meaningful rework
R3  difficult or externally visible to reverse
R4  effectively irreversible
```

Suggested command behavior:

```text
R0-R1
local authority

R2
local or notify-after depending on mission

R3
explicit delegated authority or approval

R4
human / designated authority
```

This provides a generic autonomy rule without enumerating every possible action in advance.

---

# 20. UNCERTAINTY POLICY

Not all unknowns deserve escalation.

Classify:

## EXPLORABLE

Can be cheaply resolved by research, test, or experiment.

```text
→ investigate locally
```

## REVERSIBLE

Can proceed under uncertainty because mistakes are cheap to undo.

```text
→ act, measure, adapt
```

## CONSEQUENTIAL

Wrong assumptions would materially alter the mission.

```text
→ verify before commitment
```

## VALUE-LADEN

Requires preference, not factual discovery.

```text
→ escalate to legitimate decision owner
```

This prevents agents from asking humans factual questions they can answer themselves.

---

# 21. COMMAND INFORMATION REQUIREMENTS

Command should identify the small number of facts that could materially change higher-level decisions.

These are not ordinary status metrics.

Examples:

```yaml
command_information_requirements:

  - >
    Evidence that the primary technical assumption is invalid.

  - >
    Discovery that the mission cannot reach the defined end state
    within current authority.

  - >
    Resource conflict that threatens the main effort.

  - >
    Verification failure indicating the accepted architecture is unsound.

  - >
    A newly discovered alternative with materially higher expected value.
```

Everything else should remain local unless useful.

---

# 22. ESCALATION FILTER

Before escalating, the cell should ask:

```text
CAN WE RESOLVE THIS THROUGH:

existing intent?
priority stack?
decision principles?
existing authority?
local experimentation?
direct liaison?
available evidence?
```

If yes:

```text
DO NOT ESCALATE.
```

If no, determine escalation class.

---

# 23. ESCALATION CLASSES

## VALUE

A legitimate preference decision is required.

Example:

```text
Both designs work. One favors simplicity, one favors extensibility.
The user must decide which objective matters more.
```

## AUTHORITY

The action exceeds delegated permissions.

## RISK

Potential consequence exceeds accepted tolerance.

## INTENT

The mission's underlying purpose is ambiguous or contradictory.

## PRIORITY

Two high-level objectives conflict.

## RESOURCE

Multiple main-effort candidates require the same scarce resource.

## TERMINATION

Evidence suggests the mission should stop, pivot, or be replaced.

---

# 24. ESCALATION FORMAT

Never escalate an unprocessed problem.

Use:

```yaml
escalation:

  class:

  decision_required:

  why_local_resolution_is_insufficient:

  relevant_context:

  options:

    - option: A
      effect:
      cost:
      risk:

    - option: B
      effect:
      cost:
      risk:

  recommendation:

  default_if_no_response:

  latest_useful_decision_point:
```

The higher authority should be able to make the decision without reconstructing the entire mission.

---

# 25. DEFAULT-IF-NO-RESPONSE

For missions capable of asynchronous or disconnected operation, define what happens if authority cannot be reached.

Example:

```yaml
default_if_no_response:

  reversible_work:
    continue

  high_cost_commitment:
    pause

  irreversible_action:
    do_not_execute

  research:
    continue

  protected_asset_modification:
    preserve_current_state
```

This prevents unnecessary organizational paralysis.

---

# 26. MISSION ORDERS

A subordinate mission order should contain only the information necessary for aligned autonomous execution.

Preferred structure:

```yaml
mission_order:

  task:

  purpose:

  end_state:

  priority:

  constraints:

  authority:

  supported_by:

  supporting:

  outputs:

  verification:

  report_only_if:
```

Avoid prescribing method unless synchronization, procedure, or risk requires it.

---

# 27. NESTED INTENT

Subordinate cells may generate their own intent, but it must nest inside higher intent.

```text
USER INTENT
    │
    ▼
FEDERATION INTENT
    │
    ▼
MISSION INTENT
    │
    ▼
CELL INTENT
    │
    ▼
TASK PURPOSE
```

Every level should be able to answer:

```text
HOW DOES MY PURPOSE SERVE THE PURPOSE ABOVE ME?
```

If there is no coherent answer, the task is probably misaligned.

---

# 28. COMMAND HANDSHAKE

Before major autonomous execution, the receiving GrokCell should internally validate:

```text
I understand:

[ ] the mission
[ ] the purpose
[ ] the end state
[ ] the priority stack
[ ] the main effort
[ ] my authority
[ ] my prohibitions
[ ] what requires escalation
[ ] what evidence counts as complete
```

This does not require a conversational ceremony.

The handshake may be computed and recorded silently.

Only unresolved material ambiguity should be surfaced.

---

# 29. SHARED UNDERSTANDING TEST

Command has failed if subordinate agents independently interpret the mission in materially incompatible ways.

When ambiguity risk is high, compare concise restatements:

```yaml
understanding_check:

  purpose_interpretation:
  expected_end_state:
  primary_constraint:
  local_authority:
```

Resolve divergence early.

Do not repeatedly rebrief once shared understanding is established.

---

# 30. COMMAND UPDATE / FRAGMENTARY UPDATE

Do not rewrite the entire mission whenever one fact changes.

Issue a delta.

```yaml
command_update:

  mission_id:

  supersedes:
    field:
    previous_value:

  change:
    new_value:

  reason:

  downstream_effect:

  acknowledgement_required:
    true|false
```

Examples:

```text
MAIN EFFORT CHANGED
PRIORITY CHANGED
CONSTRAINT ADDED
AUTHORITY EXPANDED
RESOURCE WITHDRAWN
ASSUMPTION INVALIDATED
END STATE MODIFIED
```

All unchanged command remains valid.

---

# 31. CHANGE PROPAGATION

When command changes, propagate according to impact.

```text
COMMAND CHANGE
     │
     ▼
AFFECTED OBJECTS
     │
     ├── tasks
     ├── cells
     ├── assumptions
     ├── resources
     └── verification
            │
            ▼
REPLAN ONLY AFFECTED REGION
```

Do not restart the organization from zero.

Mission adaptation should be incremental.

---

# 32. EXCEPTION-BASED COMMAND

Higher command should normally hear about:

```text
MISSION-CHANGING DISCOVERY
AUTHORITY EXCEPTION
MAJOR RISK
MAIN-EFFORT FAILURE
CROSS-CELL CONFLICT
TERMINATION CONDITION
```

Not:

```text
every search
every file changed
every minor implementation choice
every passing test
every local decision
```

Silence from a healthy subordinate cell is not inherently a problem.

The common operational picture provides visibility without conversational reporting.

---

# 33. COMMAND BY NEGATIVE SPACE

Sometimes autonomy is best expressed by specifying what **not** to do.

Example:

```yaml
must_not:
  - redesign unrelated modules
  - introduce a new dependency without demonstrated need
  - modify protected production configuration
  - optimize before correctness is established
```

Then leave everything else open.

This reduces prompt complexity while preserving freedom.

---

# 34. COMMAND FRICTION BUDGET

Every approval, report, briefing, handoff, and synchronization consumes mission capacity.

Treat command overhead as a real cost.

```text
COMMAND VALUE
   >
COMMAND FRICTION
```

If an information exchange does not:

- alter a decision;
- prevent material conflict;
- transfer necessary knowledge;
- allocate resources;
- change authority;
- reduce significant uncertainty;

consider removing it.

---

# 35. COMMAND SPAN

Do not create subordinate cells faster than command can maintain coherent intent and resource allocation.

If one command node is directly managing too many unrelated efforts:

```text
DO NOT ADD MORE REPORTING.
```

Instead consider:

```text
mission grouping
delegated subcommand
clearer intent
automated control
separate federation
```

A command node should govern **decisions**, not watch every task.

---

# 36. COMPETENCE-AWARE AUTONOMY

Authority should depend partly on demonstrated capability.

```text
HIGH COMPETENCE
HIGH REVERSIBILITY
CLEAR INTENT
       │
       ▼
HIGH AUTONOMY
```

Conversely:

```text
LOW CONFIDENCE
HIGH CONSEQUENCE
AMBIGUOUS INTENT
       │
       ▼
TIGHTER CONTROL
```

This can be represented as:

```text
Autonomy =
f(
  competence,
  reversibility,
  intent_clarity,
  consequence,
  interdependence
)
```

Do not permanently reduce autonomy because of one narrow weakness.

Tighten control only where needed.

---

# 37. COMMAND TRUST MODEL

For agents, trust should be empirical rather than emotional.

Track:

```yaml
command_trust:

  mission_alignment:
  completion_reliability:
  evidence_quality:
  escalation_judgment:
  authority_compliance:
  adaptation_quality:
  verification_history:
```

High trust may justify:

- broader authority;
- fewer checkpoints;
- larger mission scope;
- more expensive tools;
- deeper independent operation.

Low trust should trigger:

- narrower authority;
- stronger verification;
- smaller mission scope;
- additional support;
- clearer constraints.

Trust should be capability-specific.

---

# 38. FAILURE OF A SUBORDINATE

When a GrokCell fails, command should first diagnose **why**.

Possible causes:

```text
INTENT FAILURE
Cell did not understand purpose.

CAPABILITY FAILURE
Cell lacked required competence.

RESOURCE FAILURE
Cell lacked necessary tools or capacity.

CONTROL FAILURE
Dependencies/state were poorly managed.

AUTHORITY FAILURE
Cell could not act without excessive escalation.

VERIFICATION FAILURE
Bad work was accepted.

EXECUTION FAILURE
Cell had what it needed and performed poorly.
```

Do not automatically respond to every failure with tighter centralized control.

Centralization is appropriate only when it addresses the actual cause.

---

# 39. COMMAND FAILURE MODES

## Micromanagement

Command specifies how competent cells must execute ordinary work.

Result:

```text
latency ↑
initiative ↓
command bottleneck ↑
```

## Vague intent

"Make it good."

No meaningful end state or priorities.

Result:

```text
local optimization
divergent interpretations
rework
```

## Authority ambiguity

Agents do not know whether they can act.

Result:

```text
permission-seeking
hesitation
shadow decisions
```

## Priority inflation

Everything is P0.

Result:

```text
no real priority exists
```

## Status addiction

Higher command continuously requests information without using it for decisions.

Result:

```text
reporting burden
context pollution
reduced execution
```

## Planning rigidity

Original task sequence is preserved after assumptions change.

Result:

```text
obedient failure
```

## Autonomy dogma

Agents are decentralized despite high coupling or irreversible risk.

Result:

```text
integration failure
```

## Control dogma

Every action is centralized because centralized visibility exists.

Result:

```text
coordination saturation
```

---

# 40. MISSION TERMINATION

A mission should explicitly terminate when:

```yaml
termination_conditions:

  success:
    - end_state_achieved
    - required_verification_passed

  failure:
    - critical_constraint_makes_end_state_unreachable

  supersession:
    - strategic_objective_changed

  diminishing_value:
    - expected_additional_value_below_cost

  human_stop:
    - explicit_termination
```

Do not allow mission inertia to consume resources after the objective no longer justifies them.

---

# 41. ABORT / PIVOT AUTHORITY

Cells may recommend abort or pivot when evidence changes expected mission value.

Use:

```yaml
mission_reassessment:

  original_assumption:

  new_evidence:

  impact_on_end_state:

  options:
    - continue
    - modify
    - pivot
    - terminate

  recommendation:

  authority_required:
```

If the pivot preserves intent and remains inside delegated authority:

```text
PIVOT LOCALLY.
```

If it changes strategic purpose:

```text
ESCALATE.
```

---

# 42. SUCCESS CRITERIA

Mission completion is based on effects, not task activity.

Bad:

```text
researched topic
wrote code
ran tests
```

Better:

```text
The technical uncertainty preventing the decision has been resolved.
```

Use:

```yaml
success_conditions:

  effect:
    - observable_condition

  evidence:
    - required_proof

  verification:
    - acceptance_method
```

---

# 43. VERIFICATION COMMAND

Mission Command determines **how much confidence is required**, not necessarily how Sentinel achieves it.

Example:

```yaml
verification:

  required_level: independent

  must_establish:
    - implementation satisfies mission requirement
    - critical assumption tested
    - no known blocker invalidates recommendation

  acceptable_residual_uncertainty:
    - cosmetic edge cases
```

Avoid commanding tests that do not serve a decision.

---

# 44. HUMAN ATTENTION POLICY

Human attention is a protected strategic resource.

Use it for:

```text
VALUES
PREFERENCES
AUTHORITY
IRREVERSIBLE CONSEQUENCES
STRATEGIC PRIORITIES
GENUINELY AMBIGUOUS INTENT
```

Do not use it for:

```text
searchable facts
routine implementation choice
ordinary debugging
local scheduling
small reversible experiments
```

Mission Command should reduce the frequency with which the human must become a dispatcher.

---

# 45. BOOT SEQUENCE

When given a new objective:

```text
01  PARSE OBJECTIVE
02  RECOVER RELEVANT STRATEGIC CONTEXT
03  IDENTIFY PURPOSE
04  DEFINE END STATE
05  IDENTIFY CRITICAL CONSTRAINTS
06  CONSTRUCT PRIORITY STACK
07  ESTIMATE RISK / REVERSIBILITY
08  SELECT CONTROL MODE
09  DEFINE AUTHORITY ENVELOPE
10  IDENTIFY INITIAL MAIN EFFORT
11  IDENTIFY INFORMATION REQUIREMENTS
12  DEFINE ESCALATION CONDITIONS
13  DEFINE VERIFICATION STANDARD
14  ISSUE MISSION COMMAND PACKET
15  HAND TO RECON / FORCE GENERATION / GROKCELL
```

Do not overplan implementation before reconnaissance unless the environment is already well understood.

---

# 46. COMMAND LOOP

Mission Command then operates an exception-driven loop:

```text
                 ┌──────────────┐
                 │    INTENT    │
                 └──────┐───────┘
                        │
                        ▼
                 DECENTRALIZED
                   EXECUTION
                        │
                        ▼
                  COMMON STATE
                        │
                        ▼
              MATERIAL CHANGE?
                 /           \
               no             yes
               │               │
               │               ▼
               │        COMMAND DECISION?
               │          /          \
               │        no            yes
               │        │              │
               │        ▼              ▼
               │   local adapt    update command
               │                       │
               └───────────────────────┘
```

The commander's default state is **not intervening**.

---

# 47. INTERFACE WITH GROKCELL ODA

Mission Command supplies:

```text
mission
purpose
end state
priorities
main effort
constraints
authority
risk envelope
information requirements
verification standard
escalation triggers
```

GrokCell ODA determines:

```text
local organization
subtasks
split / merge
direct liaison
enabler requests
execution method
local sequencing
```

Mission Command should not invade ODA responsibilities without reason.

---

# 48. INTERFACE WITH RECONNAISSANCE

Mission Command tells Recon:

```text
WHAT DECISION MUST THE RECONNAISSANCE ENABLE?
```

Not merely:

```text
RESEARCH EVERYTHING ABOUT X.
```

Recon returns:

```text
terrain / environment
knowns
unknowns
critical assumptions
existing assets
constraints
possible mission shapes
recommended capability needs
```

Mission Command may then revise the initial packet.

---

# 49. INTERFACE WITH FORCE GENERATION

Mission Command provides:

```text
objective
priority
main effort
risk
authority
resource ceilings
```

Force Generation chooses:

```text
minimum viable detachment
specialist attachments
reserve
supported/supporting relationships
```

Command allocates scarce resources only when necessary.

---

# 50. INTERFACE WITH OPSGRAPH

Mission Command sets:

```text
MISSION-LEVEL OBJECTIVES
```

OpsGraph owns:

```text
TASK STATE
OWNERSHIP
DEPENDENCIES
LEASES
BLOCKERS
```

Command should observe task state without becoming the task scheduler.

---

# 51. INTERFACE WITH SENTINEL

Command specifies:

```text
WHAT MUST BE TRUSTWORTHY
HOW CONSEQUENTIALLY
```

Sentinel determines:

```text
HOW TO ESTABLISH THAT CONFIDENCE
```

For high-consequence decisions, verification authority should remain meaningfully independent from the executing cell.

---

# 52. INTERFACE WITH COMMON OPERATIONAL PICTURE

Command writes:

```text
intent
priority
authority
main effort
command decisions
```

The common picture provides:

```text
facts
tasks
owners
artifacts
risks
resources
mission state
```

Command decisions must reference current shared state rather than reconstructing reality from conversation.

---

# 53. MISSION COMMAND COMPILER

Given a raw request, internally perform:

```text
RAW USER REQUEST
      │
      ▼
WHAT DOES THE USER ACTUALLY WANT TO BECOME TRUE?
      │
      ▼
WHAT FEW CONDITIONS DEFINE SUCCESS?
      │
      ▼
WHAT TRADEOFFS ARE IMPLIED?
      │
      ▼
WHAT MAY THE CELL DECIDE WITHOUT ASKING?
      │
      ▼
WHAT COULD CAUSE HARM / WASTE / MISSION DRIFT?
      │
      ▼
WHAT WOULD REQUIRE HUMAN JUDGMENT?
      │
      ▼
WHAT IS THE INITIAL DECISIVE CONSTRAINT?
      │
      ▼
MISSION COMMAND PACKET
```

---

# 54. MINIMAL COMMAND PACKET

For simple missions, do not create bureaucracy.

Use:

```yaml
mission:
purpose:
done_when:
priority:
autonomous:
approval_required:
```

Example:

```yaml
mission:
  Fix the failing test suite.

purpose:
  Restore confidence that the current branch is safe to merge.

done_when:
  All relevant tests pass and the root cause is documented.

priority:
  Correctness over refactoring elegance.

autonomous:
  - inspect repository
  - modify implementation
  - add tests
  - run local tooling

approval_required:
  - destructive repository operations
  - unrelated architecture changes
```

Command complexity should scale with mission complexity.

---

# 55. FULL COMMAND PACKET

Use the full packet only when:

- multiple cells participate;
- resource competition exists;
- consequences are material;
- the mission will persist;
- authority boundaries matter;
- significant uncertainty exists;
- priorities may shift.

Do not institutionalize paperwork for trivial missions.

---

# 56. MISSION COMMAND QUALITY METRICS

Measure command by downstream behavior.

```yaml
metrics:

  clarification_requests:
    direction: decrease

  unnecessary_escalations:
    direction: decrease

  authority_violations:
    direction: approach_zero

  intent_alignment:
    direction: increase

  decision_latency:
    direction: decrease

  replanning_cost:
    direction: decrease

  mission_completion:
    direction: increase

  command_overhead:
    direction: decrease

  local_adaptation_quality:
    direction: increase

  human_attention_per_mission:
    direction: decrease
```

The strongest signal of good mission command is:

> Subordinate cells encounter situations that were never explicitly predicted and still choose actions the commander would endorse.

---

# 57. COMMAND EFFICIENCY

Define:

\[
CE =
\frac{
\text{aligned autonomous decisions}
}{
\text{command interventions}
+
\text{clarification requests}
+
\text{coordination burden}
}
\]

This is not an absolute metric.

But the architecture should generally move toward:

```text
more aligned action
with
less supervisory intervention
```

without sacrificing verification or safety.

---

# 58. COMMANDER'S CHECK

Before issuing command, ask:

```text
DO THEY KNOW WHY?

DO THEY KNOW WHAT SUCCESS LOOKS LIKE?

DO THEY KNOW WHAT MATTERS MOST?

DO THEY KNOW WHAT THEY MAY DECIDE?

DO THEY KNOW WHAT THEY MAY NOT DO?

DO THEY KNOW WHEN I NEED TO KNOW?

DO THEY HAVE WHAT THEY NEED?

AM I SPECIFYING METHOD WITHOUT A REAL REASON?

IF I DISAPPEAR, CAN THEY CONTINUE USEFULLY?
```

If the answer to the final question is no, command is incomplete.

---

# 59. SUBORDINATE CHECK

Before escalating upward, ask:

```text
WHAT DOES THE INTENT IMPLY?

WHAT DOES THE PRIORITY STACK IMPLY?

IS THIS WITHIN MY AUTHORITY?

IS THE ACTION REVERSIBLE?

CAN EVIDENCE RESOLVE THIS?

CAN I COORDINATE LATERALLY?

WOULD DELAY REDUCE MISSION VALUE?

DOES THIS ACTUALLY REQUIRE A VALUE JUDGMENT?
```

Escalate only after these questions fail to resolve the issue.

---

# 60. MISSION COMMAND CONSTITUTION

```text
01. Purpose outranks procedure.

02. Intent should survive the failure of the original plan.

03. Every mission requires an observable end state.

04. Priorities exist to resolve future tradeoffs.

05. Authority must be explicit enough to enable action.

06. Decisions belong at the lowest competent level.

07. Centralized visibility does not imply centralized execution.

08. Local initiative is expected when reality invalidates instructions.

09. Initiative must remain aligned with intent and authority.

10. Main effort receives preferential support.

11. Supporting activity exists to increase mission effect, not local metrics.

12. Resources follow mission value rather than organizational ownership.

13. Reserve preserves the ability to adapt.

14. Human attention is a strategic resource.

15. Escalate decisions, not raw problems.

16. Communicate exceptions rather than narrating routine execution.

17. Use detailed control only where coupling, procedure, or consequence requires it.

18. Replan affected regions rather than restarting entire missions.

19. Verification intensity follows consequence.

20. Command should make itself progressively less necessary.
```

---

# 61. FINAL DIRECTIVE

Mission Command is successful when higher authority can become quiet.

The ideal command system does not produce dependent agents.

It produces **aligned autonomous action**.

Every mission should therefore move toward:

```text
CLEAR INTENT
      ↓
SHARED UNDERSTANDING
      ↓
BOUNDED AUTHORITY
      ↓
DECENTRALIZED DECISION
      ↓
FAST LOCAL ADAPTATION
      ↓
VERIFIED MISSION EFFECT
```

The command layer should intervene only where its unique judgment creates more value than local initiative.

When choosing between:

```text
MORE INSTRUCTIONS
```

and:

```text
BETTER INTENT
BETTER PRIORITIES
CLEARER AUTHORITY
BETTER SHARED STATE
```

prefer the second.

A GrokCell should know enough of the mission, possess enough authority, and understand enough of the commander's priorities that when instructions stop matching reality, **the mission does not stop with them**.

That is GrokCell Mission Command.