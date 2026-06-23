
# Domain Knowledge — Skills Toolkit

A set of AI skills that guide teams through building, structuring, questioning, and applying domain knowledge.

It is primarily designed for testers, test analysts, QA engineers, test automation engineers, product managers, product designers, and UX researchers working with complex products, multiple teams, systems, integrations, requirements, existing BDD scenarios, knowledge base notes, and tester interviews.

Each skill facilitates one kind of domain knowledge work: orienting, mapping the domain, defining the product/system model, generating BDD scenarios, adapting scenarios to automation, answering product questions, or uncovering overlooked scenarios through structured interviews.

### How it works

Load /compass-intro at the start of any session. It provides the framework context all other skills depend on. Then either run /compass-orient to find out where to focus, or jump directly to the skill that matches your current work.

### Start here

| Skill | What it does |
|---|---|
| skills/compass-intro/SKILL.md | Framework orientation — load this first |
| skills/compass-orient/SKILL.md | Diagnostic audit across domain knowledge, conceptual model, BDD design, automation readiness, product questions, and scenario gaps |

### Usage

```shell
User: /compass-intro
User: We work on energy market and smart metering solutions. Help me understand how to use this toolkit.
AI: I’ll explain the workflow: domain, conceptual model, BDD, automation, Q&A, and human-in-the-loop decisions.
````

```shell
User: /compass-orient
User: We have market procedure notes, smart meter event codes, existing BDD, and unclear remote reconnect rules.
AI: I’ll audit the situation and recommend whether to start with domain mapping, conceptual model, BDD, automation, Q&A, or gap discovery.
```

```shell
User: /compass-automation-scenario-builder
User: Fit this reconnect failure scenario to our Playwright-BDD feature files and step definitions.
AI: I’ll map reusable steps, flag missing or near-duplicate steps, propose 1–2 wording options, and recommend the best fit.
```

### Domain understanding

Work here maps the real-world/business domain before generating scenarios or automation, while keeping awareness of the wider product, teams, systems, and integrations.

| Skill                      | What it produces                                                                                                                                                                                  |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| skills/compass-domain/SKILL.md | Focused domain slice covering scope, actors, real-world concepts, terminology conflicts, bounded contexts, business rules, processes, integrations, risks, open questions, and optional JSON/YAML |

### Product/system model

Work here turns domain knowledge into the product or system model that scenarios, tests, and automation should align to.

| Skill                                | What it produces                                                                                                                                  |
| ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| skills/compass-conceptual-model/SKILL.md | Business objects, attributes, relationships, states, transitions, actions, ubiquitous language, testable behaviours, assumptions, and model risks |

### Test design

Work here converts mixed input bundles into readable, traceable BDD scenarios.

| Skill                                    | What it produces                                                                                                                                                   |
| ---------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| skills/compass-bdd-scenario-builder/SKILL.md | Input triage, extracted facts/rules/flows, scenario intent, Gherkin scenarios, assumptions, gaps, traceability, and interview follow-ups                           |
| skills/compass-scenario-gap-finder/SKILL.md  | Interview-led discovery of missing scenarios, edge cases, tacit tester knowledge, business rules, data variations, risks, assumptions, and candidate BDD scenarios |

### Automation readiness

Work here adapts BDD scenarios to the team’s existing Gherkin, Playwright-BDD, and TypeScript automation conventions.

| Skill                                           | What it produces                                                                                                                                                                                             |
| ----------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| skills/compass-automation-scenario-builder/SKILL.md | Automation-ready Gherkin using existing feature files, step definitions, and sample scenarios; reusable step map, missing steps, near-duplicates, 1–2 design alternatives, trade-offs, and confidence rating |

### Product/domain support

Work here helps mixed teams answer product, business logic, integration, and behaviour questions without losing testing impact.

| Skill                         | What it produces                                                                                                                        |
| ----------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| skills/compass-domain-qa/SKILL.md | Direct domain answers with rules, examples, affected systems, testing impact, automation impact, assumptions, risks, and open questions |

## End-to-end flow



```shell
/compass-intro
  -> provides the framework context that all other /compass-* skills depend on, shared principles, and human-in-the-loop working mode

/compass-orient
  -> audits the current situation and recommends where to start

/compass-domain
  -> maps the real-world/business domain, bounded contexts, and messy terminology

/compass-conceptual-model
  -> turns that into the product/system objects, relationships, states, actions, and vocabulary

/compass-domain-qa
  -> answers product, business logic, integration, and behaviour questions with testing impact and risks

/compass-scenario-gap-finder
  -> interviews testers to uncover missing scenarios, edge cases, tacit knowledge, and assumptions

/compass-bdd-scenario-builder
  -> writes readable, traceable Gherkin scenarios against the agreed model and discovered knowledge

/compass-automation-scenario-builder
  -> maps scenarios to existing Gherkin + Playwright-BDD steps, flags missing steps, and proposes alternatives
```

## The workflow in brief

Domain knowledge work starts with messy inputs: requirements, product specs, user stories, support notes, market procedure notes, existing BDD, feature files, step definitions, tester knowledge, and questions from other teams.

The toolkit separates the real-world domain from the product/system model, turns that model into readable BDD scenarios, adapts selected scenarios to existing automation patterns, and keeps humans in the loop.

AI proposes. Humans critique. AI revises. Humans decide.

### License

MIT — see LICENSE. Fork it, adapt it, ship it. Attribution is appreciated but not required.


