---
name: compass-conceptual-model
description: Turns messy domain knowledge into the product/system objects, relationships, states, actions, and vocabulary needed for QA, BDD, automation, and product alignment
---

# /compass-conceptual-model

*Assumes `/compass-intro` has been loaded for framework context.*

This skill helps a mixed workshop — QA, test analysts, automation engineers, product, UX, BA, and engineering — build a practical conceptual model of the system under test or its specific area.

It turns messy notes, requirements, domain knowledge, existing BDD, tester experience, and product behaviour into shared understanding of:

- what exists in the system
- how it behaves
- how it is testable
- objects the product/system recognises
- object boundaries
- relationships and cardinality
- named roles where one object plays several parts
- actions users, systems, or integrations can perform
- states and transitions that affect behaviour
- shared vocabulary: one name per concept, one concept per name
- BDD scenario seeds and automation implications

The goal is not to create a perfect design artefact. The goal is to uncover decisions, reduce misunderstanding, and prepare better scenarios and tests.

## Before proceeding: ask for focus area

Always ask:

"What specific area should we model first?"

Examples:

- remote disconnect / reconnect
- service orders
- meter lifecycle
- market message retries
- failed integration handling
- customer move-in / move-out
- billing exception workflow

If the user gives a focus area, announce before working:

"Focus area: [given focus area]"

If the user does not give a focus area, say:

"No specific focus area provided. I’ll focus on the fundamental concepts of the system under test."

Then proceed.

## Optimize tools selection and do research for additional context

1. Enumerate available tools and resources
2. Announce, in most cases, 3-5 most relevant, tools and resources and the result

<example>
I have considered and used the following tools and resources:
- success: Atlassian MCP (search Confluence)
- success: Existing skill documentation under `references/` folder
- success: files provided by user
- fail: internet search (no access)
</example>

## Mixed input bundle first

Before generating a model, classify the input:

- Known — stated clearly in the material
- Assumed — likely but not proven
- Missing — needed but absent
- Reusable — useful for future BDD, tests, automation, onboarding
- Risky — likely to cause bugs, misunderstandings, or brittle tests
- Contested — different sources use different terms or imply different behaviour
- Human decision needed — AI should not decide this silently

Do this before producing objects, diagrams, or scenarios.

## What this skill decides

Use the conceptual model to clarify these decisions:

1. What objects does the product/system recognise?
   - Is this a real first-class concept in the system?
   - Is it only a domain concept?
   - Is it an attribute, value, event, or temporary thing?
   - Does it matter enough for testing or BDD?

2. Where is each object’s boundary?
   - What belongs inside this object?
   - What is separate?
   - What should not be merged?

3. How do objects relate?
   - One-to-one, one-to-many, many-to-many?
   - Is the relationship temporary or historical?
   - Does the object play different roles in different relationships?

4. What actions can happen?
   - User actions
   - System actions
   - Integration actions
   - Scheduled/background actions
   - Retry/recovery actions

5. What states can objects be in?
   - Stable states
   - Transitional states
   - Failure states
   - Waiting/pending states
   - Retried/expired/cancelled states

6. What vocabulary should the team use?
   - Chosen term
   - Rejected alternatives
   - Where confusion appears
   - BDD wording recommendation

## Domain/system separation

Use a pragmatic blend.

Classify concepts as:

- System concept — exists and behaves in the system. Example: Meter, Service Order, Market Message
- Domain concept — useful for testers and business reasoning, even if not directly implemented. Examples: Customer premises, Remote disconnect, Billing exception
- Integration concept — belongs mainly to an external system/message/protocol. Examples: Market message, API request, External event
- Test concept — useful for scenarios, fixtures, mocks, or automation. Examples: Test user, Mock service, Scenario setup
- Unclear — needs human decision

Rules:

- Only system concepts drive behaviour
- Domain concepts must be labelled
- Do not silently mix them
- Model system concepts directly.

## Disciplines

### Real objects only, but test-useful concepts are allowed

A strong object is:

- instanceable — there can be many
- structured — it has attributes
- useful — people care about it on its own
- behaviour-bearing — actions or states depend on it
- test-relevant

But for QA, keep non-object concepts if they help scenario design. Label them as domain, integration, test condition, or unclear.

### Object elevation: can-be ≠ should-be

Not everything that can be an object SHOULD be one.

Ask:

- Does it persist?
- Does it hold state?
- Do scenarios depend on it being revisitable?

If NO:
→ treat as transient (event/state/condition)

Mark uncertain objects as:
→ **provisional**

### Attributes vs relationships

If something references another object → it is a relationship.
Avoid duplication.

If an attribute is actually another recognised object, model it as a relationship.

Example:

- Avoid: Service Order has meterId as just a field
- Prefer: Service Order targets one Meter

## Define boundaries explicitly

For each object:

- what it includes
- what it excludes
- what it interacts with
- what should NOT be merged into it

Boundary mistakes = major source of bugs and test confusion

### No speculative additions

Every item must trace to:

- domain evidence
- observed behaviour
- requirement
- scenario need

If not:
→ remove or mark as assumption

### Name roles explicitly

If the same object appears in different roles, name the role.

Example:

- Customer as account holder
- Customer as authorised contact
- Meter as source meter
- Meter as replacement meter

### Do not hide behaviour behind generic verbs

Generic verbs often hide different test paths.

Check verbs like:

- update
- process
- complete
- cancel
- retry
- fail
- close
- edit

Ask whether they mean different things in different contexts.

Example:

- "Update meter status" may hide:
  - record remote disconnect result
  - mark meter unreachable
  - apply market response
  - correct incorrect state

These deserve separate actions if they produce different behaviour or tests.

### State changes are testing gold

Prioritise state models where:

- actions depend on state
- permissions change
- available actions change
- messages are sent
- retries happen
- failures branch behaviour
- audit/history matters
- automation needs stable assertions
- integration responses affect outcomes

### Temporal modelling (MISSING in most teams — do it here)

Explicitly decide:

- Does state update instantly or later? (eventual consistency)
- Can users/tests see stale data?
- Do relationships change over time?
- What does “delete” mean? (archive vs hard delete)
- Is history required or observable?

Flag anything unclear.

## Visualisation rubric

- Classify each part of the output before visualising.
- Use diagrams when the visual form reduces ambiguity or helps testers spot gaps.
- Visual models make it easier for humans to build mental models. Aim for at least 40% visual output when the input supports it.
- Break down complex models into multiple diagrams if needed, rather than trying to fit everything into one

## Default output structure

### 1. Focus area

State the focus area.

### 2. Input classification

Classify:

- Known
- Assumed
- Missing
- Reusable
- Risky
- Contested
- Human decision needed

### 3. Concept classification

List candidate concepts as:

- System concept
- Domain concept
- Integration concept
- Test concept
- Unclear

### 4. Concise model summary

Capture:

- Objects + boundaries
- Relationships
- Actions
- States
- Vocabulary decisions

### 5. Visuals

Include whichever are useful:

- object map
- state diagram
- action matrix
- vocabulary map
- scenario seed map
- see references/visual-models.md for when to use each type

### 6. BDD scenario seeds

Produce lightweight seeds:

```gherkin
Given [object/state/context]
When [action/event]
Then [expected state/result/message]
````

Mark each as:

- @happy-path
- @rule/constraint
- @edge-case
- @failure-path
- @integration-path
- @state-transition
- @regression-risk

### 7. QA and automation implications

Call out:

- test data needed
- state setup needed
- mocks/stubs likely needed
- reusable BDD step candidates
- risky assertions
- possible flaky areas
- open decisions blocking automation

### 8. Open questions

Keep only questions that affect decisions, scenarios, or automation.

## Techniques

Pick the technique that fits. Do not run all of them.

- Noun harvest. Use when input is messy: requirements, tickets, notes, interviews, existing BDD. Extract nouns and classify them as: object / attribute / state / event / role / value / external / unclear
- Object definition. Use when an important object is known but fuzzy. For each object: what it is / what it is not / key attributes / key relationships / test relevance / BDD wording
- Relational object map. Use when relationships are the source of confusion. Show:  objects / cardinality / roles / ownership / containment / external links
- State transition model. Use when behaviour depends on lifecycle. Show: states / transitions / triggers / allowed actions per state / forbidden actions per state / failure/retry paths
- Action inventory. Use when scenarios or step definitions are inconsistent. Group actions by:  user action / system action / integration action / scheduled/background action / recovery action
- Ubiquitous language list. Use when teams use inconsistent terms. Capture: chosen term / rejected alternatives / context / reason / BDD wording / automation naming impact
- Push forward, pull back. If object boundaries are unclear, briefly sketch likely scenarios or flows to see what must persist, hold state, or be asserted. Then pull back to update the model. Do not finalise BDD or automation structure on unstable model decisions.

**Quality signals — what good looks like:**

- Every object is independently meaningful to the user —  not a vague abstraction
- Relationship roles are explicitly named when an object can play multiple roles
- Attributes that are really relationships have been challenged and converted
- No speculative additions — “Every object/action/state must trace to: domain evidence OR observed behaviour OR scenario need”
- State transitions are defined for objects whose status materially changes what users can do
- Temporal decisions are addressed: deletion semantics, relationship temporality, history
- Ubiquitous language is established: one name per concept, one concept per name


## Working mode (important)

- Find what is undecided
- Find what is risky
- Do the next useful thing
- Do NOT generate everything
- Capture only reusable decisions

Say explicitly if:
→ “Nothing meaningful to model at this layer”

## Quality checks

Before finishing, check:

- Can testers explain the feature using the model?
- Can product/business see whether vocabulary is consistent?
- Can BDD scenarios be written directly?
- Can automation engineers identify reusable steps and setup states?
- Are domain-only concepts labelled?
- Are assumptions visible?
- Are risky or contested decisions explicit?
- Are diagrams useful rather than decorative?
- Used simple, beginner-friendly casual language, phrases that you would see in the engineering chat in Slack or Teams? 
- Used examples instead of abstract concepts where possible? 
- Avoided technical jargon unless necessary, and if used, explained it in simple terms?
- Minimized as much as possible, removed fluff text?
- Stripped minor, unimportant details?
- Any outputted file is less then 50 lines? 
- When needed, split into multiple files with clear names and references to each other.


## Suggested next skills

After this skill:

- Use /compass-bdd-scenario-builder when objects, actions, states, and rules are stable enough to write readable Gherkin.
- Use /compass-scenario-gap-finder when tester knowledge suggests missing edge cases or state combinations.
- Use /compass-automation-scenario-builder when existing feature files and step definitions need alignment with the model.
- Return to /compass-domain if the real-world domain language is still too confused.
