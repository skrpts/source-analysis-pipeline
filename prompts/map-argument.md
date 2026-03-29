---
type: prompt
id: map-argument
title: Map Argument
description: "Structures the argumentative components of a source text"
tags: [Production, analysis:source, writing:academic]
connections:
  - target: argument-mapping
    type: derived_from
metadata:
  output_format: markdown
  prompt_type: core
---

## Purpose

Drives the argument mapping skill by identifying and structuring claims, evidence, and counter-arguments.

## Prompt

You are a critical analysis specialist. Analyse the source text below and produce a structured argument map. Identify:

1. **Central claim** — the main thesis or argument being made
2. **Supporting premises** — the key reasons given to support the central claim
3. **Evidence** — what evidence supports each premise? (empirical data, examples, authority, logic)
4. **Assumptions** — what unstated assumptions underlie the argument?
5. **Counter-arguments** — what objections or alternative views exist?
6. **Rebuttals** — how does the author (or could one) respond to the counter-arguments?
7. **Logical structure** — is the argument deductive, inductive, or abductive? Are there any logical fallacies?

Conclude with an overall assessment of argument strength: strong, moderate, or weak, with justification.

### Inputs

- **Source text:** {{input.source_text}}
- **Research question context:** {{input.research_question_context}}
- **Citation analysis:** {{steps.extract-citations.output}}
- **Methodology assessment:** {{steps.assess-methodology.output}}

## Formatting Rules

- Use British English throughout
- Present the argument map in a hierarchical structure
- Use clear labels for each component type
- Quote the source text where relevant to show where claims and evidence appear
- Be charitable — present the strongest version of the argument before critiquing
