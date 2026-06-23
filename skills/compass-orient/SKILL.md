---
name: compass-orient
description: Rapid diagnostic across domain knowledge skills — identifies the live bottleneck and recommends where to focus next
---

# /compass-orient

Assumes `/compass-intro` has been loaded for toolkit context.

Orient is the front door for the Domain Knowledge Skills Toolkit. It rapidly audits the current state of shared understanding across domain knowledge, conceptual model, BDD scenario readiness, automation fit, and QA risk.

It finds the live decision bottleneck: the most foundational unresolved, assumed, risky, or contested area blocking useful BDD, automation-ready tests, or product decisions.

It is not a deep dive and not a document-generation step. The output is a short audit, a bottleneck call, and one recommended next skill.

Orient should preserve the toolkit stance:
- decisions over artefact dumping
- lightweight capture only where reusable
- library of techniques, not a script
- uncover decisions, assumptions, gaps, and risks
- push forward when enough is known; pull back when foundations are weak
- AI proposes, human critiques and decides

---

## Guided session

Ask the user to provide a mixed input bundle if they have one:

- requirements, specs, tickets, KB notes, diagrams
- existing BDD feature files or scenarios
- test cases, defects, logs, data examples
- notes from testers, analysts, product, UX, SMEs
- integration details, APIs, messages, states, retries
- anything contested, confusing, risky, or assumed

If they do not have a bundle, ask:

1. What product, feature, process, or domain area are we orienting around?
2. What prompted this now: new scenarios, confusing requirements, automation work, defects, delivery pressure, or team disagreement?
3. Is this early discovery, active analysis, existing BDD improvement, automation implementation, or production/support learning?
4. Who needs the outcome most right now: testers, test analysts, automation engineers, product/UX, developers, or SMEs?

---

## First move: classify the input bundle

Before generating recommendations, classify the current context:

```shell
Known:
Assumed:
Missing:
Reusable:
Risky:
Contested:
Human-decision-needed:
```

Use this classification to avoid pretending weak knowledge is solid.

Guidance:

* Known means evidenced by artefacts, examples, SMEs, production behaviour, or existing tests.
* Assumed means plausible but not confirmed.
* Missing means needed to proceed safely.
* Reusable means useful residue for future testers, automation engineers, product people, or other skills.
* Risky means likely to cause defects, poor scenarios, brittle automation, or bad decisions.
* Contested means people or artefacts disagree.
* Human-decision-needed means AI should not decide alone.

*

## Skill audit

Work through each area with one or two targeted questions. Rate each as:

Strong / Partial / Assumed / Weak / Not started / N/A

### Orientation and goal

"Do we know what decision or outcome we are trying to improve: shared understanding, BDD scenarios, automation fit, product decision, or QA risk?"

### Domain knowledge

"Do we understand the real-world/business/market concepts and terminology before the product/system enters the picture?"

Example probes:

* What are the key business concepts?
* What terms do SMEs, testers, customers, or market participants use?
* Which rules exist outside the software?

### Conceptual model

"Do we understand the product/system objects, relationships, states, actions, and vocabulary?"

Example probes:

* What objects exist in the system?
* What states can they be in?
* What actions or events change those states?
* Is vocabulary shared across teams, BDD, UI, APIs, and tests?

Do not collapse this into domain knowledge. Domain is the real-world/business space. Conceptual model is how the product/system represents and acts on it.

### BDD scenario readiness

"Do we have enough shared understanding to produce readable, traceable Gherkin with assumptions, examples, gaps, and follow-ups?"

Example probes:

* Are rules and examples clear?
* Are actors, preconditions, triggers, outcomes, and exceptions known?
* Are existing BDD scenarios reusable or misleading?

### Scenario coverage and gaps

"Have testers or analysts surfaced tacit knowledge, edge cases, data variations, risks, and overlooked behaviours?"

Example probes:

* What do experienced testers check that is not written down?
* What failures, retries, state transitions, or integration issues are easy to miss?
* What production defects or support issues reveal hidden scenarios?

### Automation fit

"Do we have existing feature files, step definitions, sample scenarios, and team conventions needed to design automation-ready scenarios?"

Example probes:

* Is the stack Gherkin + Playwright-BDD + TypeScript?
* Are reusable steps discoverable?
* Are there near-duplicate steps or wording inconsistencies?
* Are scenarios written in a way that automation should support?

### Domain QA

"Can current product/business/integration questions be answered with testing impact, automation impact, assumptions, risks, and open questions?"

Example probes:

* What decision depends on this answer?
* What would testers need to verify?
* What automation would become possible, brittle, or unnecessary?

*

## Decision landscape

Produce a short audit table:

```text
Area                         | State       | Notes
-----------------------------|-------------|----------------------------------------
Orientation and goal         |             |
Domain knowledge             |             |
Conceptual model             |             |
BDD scenario readiness       |             |
Scenario coverage and gaps   |             |
Automation fit               |             |
Domain QA                    |             |
```

Keep notes decision-focused. Do not dump artefacts.

*

## Bottleneck analysis

Identify the bottleneck: the most foundational area with Weak, Assumed, Not started, risky, contested, or human-decision-needed status.

State clearly:

* what decision or understanding is missing
* why it blocks the next useful move
* what risk it creates for BDD, automation, QA, product, or integrations
* whether the team should push forward or pull back

Also flag assumed areas separately. Assumptions treated as settled are often where bad scenarios and brittle automation start.

If deadlines or delivery constraints mean the team cannot fix the deepest issue now, name the trade-off explicitly and recommend the safest lightweight move.

*

## Recommendation

Recommend one next skill:

* unclear start, unclear goal, or mixed mess → `/compass-orient`
* weak real-world/business understanding → `/compass-domain`
* weak product/system objects, states, actions, or vocabulary → `/compass-conceptual-model`
* ready to turn knowledge into readable Gherkin → `/compass-bdd-scenario-builder`
* existing BDD may miss risks, edge cases, tacit tester knowledge → `/compass-scenario-gap-finder`
* scenarios need to fit existing Playwright-BDD + TypeScript automation → `/compass-automation-scenario-builder`
* specific product/business/integration question needs testing-aware answer → `/compass-domain-qa`

Default core flow when foundations are adequate:

`/compass-domain` → `/compass-conceptual-model` → `/compass-bdd-scenario-builder` → `/compass-automation-scenario-builder`

Close with:

"Recommended next skill: `/compass-[skill]` because \[reason]. Want to run it now, or is there something in this audit to challenge first?"
