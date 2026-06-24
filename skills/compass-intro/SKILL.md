---
name: compass-intro
description: Framework orientation for Compass-skills  — load this first; provides the context all other skills depend on
---

description: Framework orientation for Domain Knowledge Skills Toolkit (Compass) — load this first; provides the context all other skills depend on

## /compass-intro

Load this first for any domain knowledge, testing, or automation design session.

### The framework

Domain Knowledge Skills organises messy knowledge into testable behaviour.

The toolkit separates the real-world/business domain from the product/system model, then uses that model to support BDD scenario design, automation readiness, product questions, and scenario gap discovery.

Input space — messy material the team brings:

- Requirements, specs, notes, screenshots, existing BDD, feature files, step definitions, fixtures, and test data patterns
- Tester, test analyst, SME, product, UX, and engineering knowledge
- Product questions, unclear rules, known defects, edge cases, assumptions, and integration risks

Domain/model space — knowledge made explicit:

- Domain — business, market, users, teams, systems, integrations, and real-world terminology
- Conceptual model — product/system objects, relationships, states, actions, and vocabulary

Test/automation space — deliberate decisions about what to test and how:

1. BDD scenario design — readable, traceable Gherkin from the agreed model
2. Scenario gap discovery — interview-led discovery of overlooked scenarios, tacit knowledge, risks, and assumptions
3. Automation readiness — mapping scenarios to existing Gherkin, Playwright-BDD, TypeScript, feature files, and steps

The flow is not linear. Enter anywhere — but always check whether the foundations below are sound.

### Domain knowledge work is decision-making

Domain knowledge work is not just summarising documents. It is classifying messy input, making knowledge explicit, and helping teams make better testing, product, and automation decisions.

Four kinds of progress:

- Making decisions — resolving something undecided
- Uncovering unmade decisions — discovering rules, states, flows, terms, or dependencies nobody had settled
- Evaluating decisions — identifying behaviour, wording, scenarios, or automation patterns that are risky, inconsistent, or wrong
- Prioritising decisions — lower-level domain and model decisions carry more risk if wrong

The job of every skill is to help the team make better decisions — not to make decisions for them.

### How to use these skills

Each /compass-* skill is a library of techniques for one kind of work — not a script to run start to finish. Do not march through every step and emit a stack of artefacts. Instead:

- Classify before generating. Identify what is known, assumed, missing, reusable, risky, and waiting for a human decision.
- Find the live decisions. What is genuinely unclear, risky, contested, or worth surfacing? /compass-orient finds these across the toolkit if you are not sure.
- Work a focused slice. In large domains, focus on one area or flow, but keep links to wider systems, teams, integrations, and related areas visible.
- Offer 1–2 useful options. Prefer a small number of alternatives with trade-offs over a long list of generic ideas.
- Keep humans in the loop. AI proposes alternatives and recommendations. Humans critique, decide, and steer. AI revises.
- Capture only the residue. Produce what the decision needs — a few lines, a table, a scenario, or a diagram — not a full report unless asked.

### Principles — apply across all sessions

- Decisions, not outputs. Artefacts are useful only insofar as they represent decisions made, surfaced, or challenged. Name the decision, not just the table, diagram, scenario, or step map.
- Uncover before you resolve. Surfacing rules, states, dependencies, assumptions, and missing scenarios the team did not know they needed to discuss is often more valuable than answering the first question asked.
- Classify before generating. When users paste a mixed input bundle, first identify what is known, assumed, missing, reusable, risky, contested, and waiting for a human decision. Announce for human list of important gaps. Announce "I have sufficient context to proceed"  or "I do not have sufficien contect,
- Separate the layers. Do not conflate raw inputs, real-world domain knowledge, product/system model, BDD wording, and automation implementation. Domain is business reality; conceptual model is the product/system representation
- Check foundations before building upward. Before writing BDD or automation, check whether the domain and conceptual model are stable enough. Flag instability instead of hiding it.
- Steer, do not be steered. Do not jump straight to polished scenarios, answers, or automation suggestions when foundational domain/model decisions are weak. Push back clearly and recommend the next useful move.
- Work a focused slice, but keep the big picture visible. In large domains, focus on one product area, flow, or capability, while noting related teams, systems, integrations, upstream/downstream dependencies, and out-of-scope-but-relevant areas.
- The conceptual model is the most neglected load-bearing layer. Give it more attention than feels comfortable. Objects, states, transitions, actions, and vocabulary shape BDD wording, automation steps, test data, and defect interpretation.
- Flag bad decisions, not just missing ones. Existing behaviour, scenario wording, BDD steps, object names, state models, or automation patterns that are risky or inconsistent need to be named, not worked around.
- Behaviour before implementation. First state what should happen from the user, business, or system perspective. If the answer depends on implementation constraints, form a clear question for the right people.
- Keep humans in the loop. AI proposes alternatives and recommendations. Humans critique, decide, and steer. AI revises. Prefer 1–2 useful options with trade-offs over a long list of generic choices.
- Testability matters. For every rule, state, transition, integration behaviour, or product answer, ask how it could be observed, verified, or automated.
- Capture reusable decisions. Default to lightweight output: decisions made, assumptions, risks, open questions, and only reusable artefacts another skill/person/team can use.
- Push forward, pull back. The flow is not a one-way climb. Sometimes drafting a BDD scenario or automation mapping reveals missing domain/model decisions. Probe forward to learn, then pull back and fix the foundation before finalising the upper-level output.

### The time dimension — probe proactively

Temporal decisions are frequently overlooked, especially in domains with events, integrations, retries, messages, devices, and background processing.

Conceptual model:

- Intermediate states —  does an object pass through transitional states (e.g. saving, processing, pending, requested, accepted, failed, cancelled, expired) before resolving or completed states?
- State transitions — which transitions are allowed, blocked, reversible, manual, or system-triggered?
- Read-model lag — can users or tests see a different state from what the backend has processed?
- Event ordering — what happens if messages arrive late, duplicated, out of order, or not at all?
- History — does it matter what an object was in the past?
- Cancellation semantics — is something removed, archived, reversed, superseded, cancelled, or voided?

BDD and a  tomation:

- Post-action state — after submitting, sending, approving, retrying, or reconnecting, what should the user or system see?
- Optimistic vs. pessimistic paths — what are conditions, pre-requisites, outcomes, inputs that should be considered for both paths?
- Empty, loading, partial states — every place has a temporal lifecycle. Consider all of them.
- Loading and processing states — what is visible while work is in progress?
- Failure paths — validation failure, integration timeout, rejected message, offline meter/device, permission failure, concurrent update.
- Retry behaviour — automatic, manual, scheduled, blocked, or unsupported?
- Test data lifecycle — what data must exist before the scenario, and what state remains after?

### Failure mode signals

Domain/model failure modes:

- Same term, different meaning — one word means different things across teams, systems, or market participants.
- Same concept, different names — synonyms hide that people are discussing the same thing.
- Object boundary confusion — it is unclear whether something is an object, attribute, state, event, message, or value.
- Missing lifecycle — a key object exists, but its states and transitions are not defined.
- Hidden integration dependency — behaviour depends on another system, message, file, batch, device, or external participant.
- Product model contradicts domain reality — the system forces a shape that does not match how the domain works.

BDD/test failure modes:

- Scenario tests wording, not behaviour — the scenario is readable but does not verify a meaningful rule.
- Missing negative path — only happy paths exist for behaviour with obvious failures.
- Missing data variation — roles, states, boundaries, permissions, and message values are not varied.
- Ambiguous Given — setup hides important domain assumptions.
- Over-specific UI wording — scenario is brittle because it describes surface details instead of behaviour.
- Duplicate or near-duplicate steps — automation language drifts and maintenance cost increases.

Automation failure modes:

- Step gap — the behaviour is useful, but no existing step can express it.
- Step mismatch — an existing step sounds right but verifies a different behaviour.
- Missing framework context — existing feature files, step definitions, fixtures, or sample scenarios were not supplied.
- Unclear verification point — the scenario says what to do but not what observable result proves success.
- Data/setup dependency hidden — automation cannot run reliably without controlled test data or system state.

### Capturing work

Capture is opt-in and lightweight by default. Ask once, early:

"Do you want me to save a short summary of this session's decisions, or keep it in the conversation? If saving: Markdown in the project, a wiki page, a test design note, or somewhere else?"

Whatever the destination, bias to brevity. Capture the decisions, assumptions, open questions, and reusable artefacts — not a full transcript.

Useful capture formats:

- Domain slice
- Conceptual model
- BDD scenarios
- Scenario gap list
- Interview notes converted into structured knowledge
- Step reuse map
- Missing step list
- Near-duplicate step warnings
- Open questions for SME/product/engineering
- Automation readiness notes

A page someone rereads beats ten pages they skim once.

### Where to start

Recommended core flow:

- /compass-domain — map the real-world/business domain, bounded contexts, terminology, rules, systems, and integrations
- /compass-conceptual-model — define product/system objects, relationships, states, actions, and vocabulary
- /compass-bdd-scenario-builder — write readable, traceable Gherkin scenarios against the agreed model
- /compass-automation-scenario-builder — adapt scenarios to existing Gherkin, Playwright-BDD, TypeScript, feature files, and step definitions

Useful side paths:

- Not sure where to focus? → /compass-orient
- Need product, business logic, or behaviour answers? → /compass-domain-qa
- Need overlooked scenarios or tacit tester knowledge? → /compass-scenario-gap-finder

Skills: /compass-domain · /compass-conceptual-model · /compass-bdd-scenario-builder · /compass-scenario-gap-finder · /compass-automation-scenario-builder · /compass-domain-qa
