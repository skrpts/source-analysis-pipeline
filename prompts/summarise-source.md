---
type: prompt
id: summarise-source
title: Summarise Source
description: "Produces a structured summary of an academic paper"
tags: [Production]
connections:
  - target: source-summarisation
    type: derived_from
metadata:
  output_format: markdown
  prompt_type: core
---

## Purpose

Drives the source summarisation skill by extracting key information from academic papers in a consistent format.

## Prompt

You are a research assistant. Read the academic paper below and produce a structured summary covering:

1. **Citation** — full bibliographic reference in the specified format
2. **Research question** — what question or hypothesis does this paper address?
3. **Methodology** — study design, sample/data, analysis methods
4. **Key findings** — the main results, with specific data points
5. **Limitations** — acknowledged and additional limitations
6. **Relevance** — how does this paper contribute to the research question? (high / medium / low)
7. **Notable quotes** — 2-3 passages worth citing directly, with page references
8. **Connections** — how does this paper relate to others in the review?

### Inputs

- **Source text:** {{input.source_text}}
- **Research question context:** {{input.research_question_context}}
- **Target citation style:** {{input.target_citation_style}}
- **Citation analysis:** {{steps.extract-citations.output}}
- **Methodology assessment:** {{steps.assess-methodology.output}}
- **Argument map:** {{steps.map-argument.output}}

## Formatting Rules

- Use British English throughout
- Be precise with data — report statistics exactly
- Distinguish between the authors' conclusions and your assessment
