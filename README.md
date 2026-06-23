<h1 align="center">Compass Skills</h1>

<p align="center">
  <strong>Domain Knowledge Skills Toolkit for QA, BDD, automation, and product decisions.</strong><br>
  <a href="#tldr">TLDR</a> - <a href="#quick-start">Quick Start</a> - <a href="#structure">Structure</a> - <a href="#how-to-use">How to Use</a> - <a href="#how-it-works">How It Works</a>
</p>

```shell
 ██████╗ ██████╗ ███╗   ███╗██████╗  █████╗ ███████╗███████╗
██╔════╝██╔═══██╗████╗ ████║██╔══██╗██╔══██╗██╔════╝██╔════╝
██║     ██║   ██║██╔████╔██║██████╔╝███████║███████╗███████╗
██║     ██║   ██║██║╚██╔╝██║██╔═══╝ ██╔══██║╚════██║╚════██║
╚██████╗╚██████╔╝██║ ╚═╝ ██║██║     ██║  ██║███████║███████║
 ╚═════╝ ╚═════╝ ╚═╝     ╚═╝╚═╝     ╚═╝  ╚═╝╚══════╝╚══════╝

███████╗██╗  ██╗██╗██╗     ██╗     ███████╗
██╔════╝██║ ██╔╝██║██║     ██║     ██╔════╝
███████╗█████╔╝ ██║██║     ██║     ███████╗
╚════██║██╔═██╗ ██║██║     ██║     ╚════██║
███████║██║  ██╗██║███████╗███████╗███████║
╚══════╝╚═╝  ╚═╝╚═╝╚══════╝╚══════╝╚══════╝
```

## TLDR

A set of AI skills that guide teams through building, structuring, questioning, and applying domain knowledge.

Compass is designed for testers, test analysts, QA engineers, test automation engineers, product managers, product designers, and UX researchers working with complex products, systems, integrations, requirements, BDD scenarios, knowledge base notes, and tester interviews.

## Quick Start

```powershell
/compass-intro              # load framework context
/compass-orient             # find the best focus area
/compass-conceptual-model   # model one product/system area
```

Load `/compass-intro` at the start of any session. It provides the framework context all other skills depend on. Then run `/compass-orient` to find where to focus, or jump directly to the skill that matches your current work.

## Structure

```bash
compass-skills/
├── README.md                              # generated toolkit overview
└── skills/
  ├── compass-intro/                       # framework orientation
  ├── compass-orient/                      # diagnostic audit; decide where to start
  ├── compass-conceptual-model/            # product/system model skill; define how system behaves
  ├── compass-automation-scenario-builder/ # automation-ready BDD; make behaviour executable
  ├── compass-bdd-scenario-builder/        # readable, traceable Gherkin; describe behaviour as examples
  ├── compass-domain/                      # business/domain mapping; understand the world
  ├── compass-domain-qa/                   # product and domain Q&A
  └── compass-scenario-gap-finder/         # missing scenario discovery; find missing behaviour
```

| Skill                                                                                | What it does or produces                                                                                                                           |
| ------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| [skills/compass-intro/SKILL.md](skills/compass-intro/SKILL.md)                       | Framework orientation — load this first.                                                                                                           |
| [skills/compass-orient/SKILL.md](skills/compass-orient/SKILL.md)                     | Diagnostic audit across domain knowledge, conceptual model, BDD design, automation readiness, product questions, and scenario gaps.  Use when unsure where the problem is — it finds the weakest layer so you don’t misuse other skills prematurely               |
| [skills/compass-conceptual-model/SKILL.md](skills/compass-conceptual-model/SKILL.md) | Business objects, attributes, relationships, states, transitions, actions, ubiquitous language, testable behaviours, assumptions, and model risks. Use when system behaviour is unclear or inconsistent (transforms domain into testable structure). |

<details>
<summary>Read more. Skill catalogue, including planned skills</summary>

| Skill                                                                                                      | What it does or produces                                                                                                                                                                       |
| ---------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [skills/compass-domain/SKILL.md](skills/compass-domain/SKILL.md)                                           | Focused domain slice covering scope, actors, concepts, terminology conflicts, bounded contexts, rules, processes, integrations, risks, open questions, and optional JSON/YAML.  Use when real-world concepts, rules, or terminology are unclear               |
| [skills/compass-bdd-scenario-builder/SKILL.md](skills/compass-bdd-scenario-builder/SKILL.md)               | Input triage, extracted facts/rules/flows, scenario intent, Gherkin scenarios, assumptions, gaps, traceability, and interview follow-ups. Use when you understand behaviour and need readable scenarios (depends on conceptual model)                                                     |
| [skills/compass-scenario-gap-finder/SKILL.md](skills/compass-scenario-gap-finder/SKILL.md)                 | Interview-led discovery of missing scenarios, edge cases, tacit tester knowledge, business rules, data variations, risks, assumptions, and candidate BDD scenarios. Use when scenarios already exist but feel incomplete — it expands coverage by surfacing edge cases and tester knowledge                           |
| [skills/compass-automation-scenario-builder/SKILL.md](skills/compass-automation-scenario-builder/SKILL.md) | Automation-ready Gherkin using existing feature files, step definitions, sample scenarios, reusable step map, missing steps, near-duplicates, alternatives, trade-offs, and confidence rating. Use when BDD exists but must align with code and reuse or identify missing BDD steps |
| [skills/compass-domain-qa/SKILL.md](skills/compass-domain-qa/SKILL.md)                                     | Direct domain answers with rules, examples, affected systems, testing impact, automation impact, assumptions, risks, and open questions. Use when you need precise answers about rules/integrations                                                      |

</details>

## How to Use

```powershell
/compass-intro                       # understand the toolkit stance
/compass-orient                      # audit known, assumed, missing, risky areas
/compass-domain                      # map business/domain knowledge when needed
/compass-conceptual-model            # define objects, relationships, states, actions
/compass-bdd-scenario-builder        # draft readable, traceable Gherkin
/compass-automation-scenario-builder # fit scenarios to existing automation steps
```

Each skill facilitates one kind of domain knowledge work: orienting, mapping the domain, defining the product/system model, generating BDD scenarios, adapting scenarios to automation, answering product questions, or uncovering overlooked scenarios through structured interviews.

## Usage examples

```shell
User: /compass-intro
User: We work on energy market and smart metering solutions. Help me understand how to use this toolkit.
AI: I’ll explain the workflow: domain, conceptual model, BDD, automation, Q&A, and human-in-the-loop decisions.
```

<details>
<summary>Read more </summary>



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

</details>

## How It Works

Domain knowledge work starts with messy inputs: requirements, product specs, user stories, support notes, market procedure notes, existing BDD, feature files, step definitions, tester knowledge, and questions from other teams.
The toolkit separates the real-world domain from the product/system model, turns that model into readable BDD scenarios, adapts selected scenarios to existing automation patterns, and keeps humans in the loop.
AI proposes. Humans critique. AI revises. Humans decide and steer. Interactive sessions with frequent feedback loops. Each skill has a specific focus and expected output, but the process is flexible and iterative.

```shell
/compass-intro
  -> provides the framework context that all other /compass-* skills depend on, shared principles, and human-in-the-loop working mode

/compass-orient
  -> audits the current situation and recommends where to start
```

<details>
<summary>Read more</summary>

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

</details>

## Star and check other projects

Found something helpful or useful? Give it a star. Share with others. 

What else do I have? Check the links 

- [🌵Tiny CLI that validates markdown spec docs against rules embedded directly in the document](https://github.com/MaksimZinovev/docfence)
- [🦎Automatify Jira TestOps bdd plugin for small teams who got tired of bloated test management tools and complex integrations ](https://marketplace.atlassian.com/apps/3116680415/automatify-testops-for-jira?hosting=cloud&tab=overview)
- [🦘 Markdown File Viewer with mermaidjs diagrams support and themes. Export as standalon HTML or PDF.](https://github.com/MaksimZinovev/md-viewer)

License: MIT — see LICENSE. Fork it, adapt it, ship it. Attribution is appreciated but not required.